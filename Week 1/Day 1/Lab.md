# RISC-V SoC Tapeout Program VSD
## Introduction to Verilog RTL Design & Synthesis: ⌨️
#### 1. Set up & clone files
```bash
$ git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
$ cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
$ ls
```

#### 2. Install required tools (if not done already)
``` bash
$ sudo apt install gtkwave
$ sudo apt install iverilog
```
#### 3. Simulate the design & run the simulation to view the waveform
```bash
$ iverilog good_mux.v tb_good_mux.v
$ ./a/out
$ gtkwave tb_good_mux.vcd
```

#### Output:
![2-to-1 MUX gtkwave Simulation Waveform](https://github.com/user-attachments/assets/3093e711-a83b-460c-874d-e80675d451de)

#### 4. **Verilog code for MUX (`good_mux.v`):** 
```verilog
module good_mux (input i0, input i1, input sel, output reg y);
always @ (*)
begin
    if(sel)
        y <= i1;
    else 
        y <= i0;
end
endmodule
```

#### 5. Checking with Yosys:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog good_mux.v
$ synth -top good_mux
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
#### Output:
![2-to-1 MUX Printing statistics](https://github.com/user-attachments/assets/81bbd476-a8af-4145-9cee-f5037d66fc11)

#### 6. View the gate-level netlist:
```bash
$ show
```
#### Output:
![2-to-1 Good MUX Diagram](https://github.com/user-attachments/assets/4c8f2545-7294-41ef-a08a-ea0af5792719)







