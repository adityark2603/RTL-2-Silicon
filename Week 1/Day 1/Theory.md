# RISC-V SoC Tapeout Program VSD
## Introduction to Verilog RTL Design & Synthesis ✏️
### Simulator:
RTL Design is checked for adherence to the specifications by simulating the design.  
**Example:** `iverilog` <br>

![iverilog Based Simulation flow](https://github.com/user-attachments/assets/b5169cdb-20c0-4105-a0c9-c1daeee4ca0c)


### Design:
Actual Verilog code that has the intended functionality to meet the required specifications. 

### Testbench:
Set up to apply stimulus (test vectors) to the design to check its functionality. <br>

![Testbench flow](https://github.com/user-attachments/assets/2caed17b-2577-4d44-924b-c6b6a8011846)


### Working of a Simulator:
1. The simulator looks for the changes in the input signals.  
2. Upon a change to the input, the output is evaluated.  
3. The simulator is looking for a change in the values of the input.  

---

### Synthesizer:
A tool used to convert RTL to a netlist.  
**Example:** `Yosys`

### Logic Synthesis:
- **RTL Design** → Behavioural representation of the required specification.  
- **Synthesis** → RTL to Gate level translation.  
  The design is converted into gates and the connections are made between gates.  
  This is given out as a file called **`netlist`**.

---

### What is `.lib`?
- Collection of logical modules.  
- Includes basic logic gates like **AND, OR, NOT, etc.**  
- Contains different flavours of the same gate: **Slow, Fast, Medium**  

---

### Why are different flavours of gates needed?
The **combinational delay** in the logic path determines the maximum speed of operation of a digital logic circuit.  

$$
T_{CLK} \>\ T_{CQ_A} \+\ T_{COMBINATIONAL} \+\ T_{SETUP}
$$

$$
f_{clk_{MAX}} \=\ \frac{1}{T_{clk_{MIN}}}
$$


- We need **fast cells** to make `T_COMBINATIONAL` small and meet required performance.  
- We need **slow cells** to ensure there are no **HOLD issues** at `DFF_B`.  

⚡ **Cell Selection is Important!**  
- Overuse of faster cells → Bad circuit in terms of **power & area**, plus **hold time violations**.  
- Overuse of slower cells → **Sluggish circuit**, may fail to meet performance requirements.  

---

## Faster Cells vs Slower Cells

In digital logic circuits, the **load** is represented by **capacitance**.  
The charging/discharging speed of this capacitance determines the **cell delay**.

- Faster charging/discharging → Lesser delay  
- Slower charging/discharging → More delay  

To achieve faster charging/discharging, transistors must be able to source more current.  
This introduces a trade-off between **speed, area, and power**.

---

## Comparison Table 📜

| **Aspect**                       | **Faster Cells**                              | **Slower Cells**                             |
|----------------------------------|-----------------------------------------------|----------------------------------------------|
| Load in Digital Logic Circuit    | Capacitance (charged/discharged quickly)       | Capacitance (charged/discharged slowly)       |
| Cell Delay                       | Lesser (due to faster charging/discharging)    | More (due to slower charging/discharging)     |
| Transistor Requirement           | Wider transistors (source more current)        | Narrow transistors (source less current)      |
| Delay                            | Low delay                                      | More delay                                    |
| Area                             | More area                                      | Less area                                     |
| Power                            | More power                                     | Less power                                    |
| Trade-off                        | High speed at the cost of area and power       | Low power and area but higher delay           |
