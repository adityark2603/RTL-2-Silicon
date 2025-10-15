# RISC-V SoC Tapeout Program VSD
## ⚓ Gate Level Simulation(GLS), Blocking vs Non-blocking and Synthesis-Simulation Mismatch
#### **What is Gate Level Simulation?** <br>
Running the testbench against the synthesized netlist output as a DUT is known as Gate Level Simulation (GLS). The output netlist should logically be the same as the RTL code so that the testbench will align itself when we simulate both files to obtain the waveforms.

#### **Advantages of GLS:**
1. To logically verify the correctness of the design after Synthesis <br>
2. During RTL Simulation, timing was not accounted for, but for practical applications, there is a need to ensure the timing of the design is met

``` verilog
// Consider a netlist
and uand (.a(a), .b(b));
or uor (.a(a), .b(b));

// There is a need to define the meaning of AND and OR
// Thus we need netlist, testbench and Verilog models of the standard cells
```

Netlist consists of all standard cells instantiated, and its meaning is conveyed to the iVerilog using Gate Level Verilog Models. Gate-level Verilog Models can be functional or timing aware. If the gate-level models are delay-annotated, then GLS can be performed for timing validation in addition to functional validation.

### ✨ <ins>Synthesis Simulation Mismatch:</ins>
If the netlist is a true representation of RTL, what is the need to validate the functionality of the netlist? There may be a synthesis and simulation mismatch due to the following reasons:
  - Missing Sensitivity List
  - Blocking Vs Non-Blocking Assignments
  - Non-Standard Verilog Coding

### 1. **<ins>Missing Sensitivity List</ins>**
``` verilog
module mux(
    input i0, input i1,
    input sel,
    output reg y
);
always @ (sel)
begin
    if (sel)
        y = i1;
    else 
        y = i0;          
end
endmodule
```
The output of the Simulator changes only when the input changes. The output is not evaluated when there is no activity. In the above 2x1 mux code, when select is changing (when select is 1), the output is 1 when input is 1 else the output is 0. The always block evaluates only when there is a transition change in select pin, and is not sensitive (output does not reflect) to changes in the inputs i0 and i1.

**Corrected Code for Missing Sensitivity List:**
``` verilog
module mux(
    input i0, input i1,
    input sel,
    output reg y
);
always @ (*)
begin
    if (sel)
        y = i1;
    else 
        y = i0;        
end
endmodule

```

Mismatch is corrected by having always @ (*) where the always block is evaluated when any signal changes. So, any changes in inputs will also be seen in the output.



### 2. **<ins>Blocking Vs Non-Blocking Assignments in Verilog</ins>**
Blocking and Non-blocking statements are procedural assignment statements that can be implemented only inside an always block.

1. **Blocking Assignments:**
   - Denoted by `=`
   - Executes the statements in the order in which they are coded
  
2. **Non-blocking Assignments:**
   - Denoted by `<=`
   - Executes the RHS of all such assignments when the always block is entered and assigned to LHS in a parallel evaluation
  
  
#### **<ins>CAVEAT 1:</ins>**
**Problematic Code:**

``` verilog
module code (
    input clk, input reset,
    input d,
    output reg q
);
reg q0;
always @ (posedge clk, posedge reset)
begin
    if(reset)
    begin
        q0 = 1'b0;
        q = 1'b0;
    end
    else
        q = q0;
        q0 = d;    
end
endmodule
```

The assignments inside the code represent blocking statements. q0 and q are assigned to 1 bit 0s - so asynchronous reset connection happens. However, in the later parts, q0 is assigned to q and then d gets assigned to q0.

**Corrected Code:**
``` verilog
module code (
    input clk, input reset,
    input d,
    output reg q
);
reg q0;
always @ (posedge clk, posedge reset)
begin
    if(reset)
    begin
        q0 = 1'b0;
        q = 1'b0;
    end
    else
        q0 = d;
        q = q0;    
end
endmodule
```

In this case, d is assigned to q0 and then q0 is assigned to q. So, by the time the second statement gets executed, q0 has the value of d. This will lead to implementation of only one flop. Previously, q has the value of q0 and q0 has the value of d - which led to implementation of 2 storage elements.

**<ins>NOTE</ins>:**
Always Use Non-Blocking Statements when writing Sequential circuit code

#### **<ins>CAVEAT 2:</ins>**
**Problematic Code:**
``` verilog
module code (
    input a, b, c,
    output reg y
);
reg q0;
always @ (*)
begin
    y = q0 & c;
    q0 = a | b;    
end 
endmodule
```

The code is aimed at creating a function of `y = (A+B).C` In the above code, when the code enters the always block, due to the presence of blocking statements, they get evaluated in order. So y gets evaluated first (q0.C), where the q0 results correspond to the previous iteration's result. The q0 value gets updated only in the second statement.

**Corrected Code:**
``` verilog
module code (
    input a, b, c,
    output reg y
);
reg q0;
always @ (*)
begin
    q0 = a | b;
    y = q0 & c;
end 
endmodule
```

When the order of the statements is changed: In this case, a OR b is evaluated first and the latest value is used for calculating y.
