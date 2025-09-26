# Introduction to Verilog RTL Design & Synthesis

Simulator: RTL Design is checked for adherence to the specifications by simulating the design. Eg: iverilog

Design: Actual Verilog code which has the intended functionality to meet with the required specifications. 

Testbench: Setup to apply stimulus (test vectors) to the design to check its functionality. 

Working of a Simulator:
1. Simulator looks for the changes on the input signals
2. Upon change to the input, the output is evaluated.
3. Simulator is looking for change in values of input.

 

Synthesizer:
Tool used to convert RTL to netlist, Eg: Yosys

Logic Synthesis:
RTL Design - Behavioural representation of the required specification
Synthesis - RTL to Gate level translation. Design is converted into gates and the connections are made between gates. This is given out as a file called 'netlist'

What is .lib?
Collection of logical modules. Includes basic logic gates like AND, OR, NOT, etc
Contains different flavours of the same gate: Slow, Fast, Medium

Why different flavours of gates are needed?
Combinational delay in logic path determines the maximum speed of operation of digital logic circuit. 

T CLK > T CQ_A + T COMBINATIONAL + T SETUP 

f clk MAX = 1/ T clk MIN
So we need cells that work fast to make T COMBINATIONAL small. 
Hence we need fast cells, to meet required performance.

We need slow cells to ensure there are no 'HOLD' issues at DFF_B. 

Selection of cells is very important as overuse of faster cells will result in bad circuit in terms of power and area, plus the factor of hold time violations. Overuse of slower cells will result in a sluggish circuit, may not even meet the performance requirements. 
