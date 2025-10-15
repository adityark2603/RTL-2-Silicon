# RISC-V SoC Tapeout Program VSD
## 🔨 Optimization in synthesis

### <ins>IF Constructs:</ins>
The `if` statement is a conditional statement that uses Boolean conditions to determine which blocks of Verilog code to execute. `if` always translates into a Multiplexer. It is used for priority logic and is always used inside `always` blocks. The variable should be assigned as a register.

``` verilog
if (<cond>) begin
    // ...
    // ...
end else begin
    // ...
    // ...
end
```

### <ins>IF-ELSE-IF Statement:</ins>
``` verilog
if (<cond1>) begin
    // ...
    // executes cb1
    // ...
end else if (<cond2>) begin
    // ...
    // executes cb2
    // ...
end else if (<cond3>) begin
    // ...
    // executes cb3
    // ...
end else begin
    // ...
    // executes cb4
    // ...
end
```

**<ins>NOTE</ins>:** IF statements translate to multiplexers in hardware.

#### <ins>Cautions with Using IF Statements:</ins>
Inferred latches can serve as a 'warning sign' that the logic design might not be implemented as intended. They represent a bad coding style, which happens because of incomplete if statements/crucial statements missing in the design.

### <ins>CASE Statements:</ins>
The hardware implementation is a Multiplexer. Similar to IF Statements, Case statements are also used inside `always` blocks and the variable should be a register variable.

``` verilog
reg y;
always @ (*) begin
    case (sel)
        2'b00: begin
            // ...
            // ...
        end
        2'b01: begin
            // ...
            // ...
        end
        // ...
        // ...
    endcase
end
```

### <ins>Caveats in CASE Statements:</ins>
1. Case statements are dangerous when there is an incomplete Case Statement Structure may lead to inferred latches. To avoid inferred latches, code Case with default conditions.

``` verilog
reg y;
always @ (*) begin
    case (sel)
        2'b00: begin
            // ...
            // ...
        end
        2'b01: begin
            // ...
            // ...
        end
        // ...
        // ...
        default: begin
            // ...
            // ...
        end
    endcase
end
```

2. Partial Assignments in Case statements - not specifying the values. This will also create inferred latches. To avoid inferred latches, assign all the inputs in all the segments of the case statement.

