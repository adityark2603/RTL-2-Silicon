# RISC-V SoC Tapeout Program VSD
## ⚓ Gate Level Simulation(GLS), Blocking vs Non-blocking and Synthesis-Simulation Mismatch

### 1. <ins>ternary_operator</ins>
#### Verilog File:
``` verilog
module ternary_operator_mux (input i0, input i1, input sel, output y);
    assign y = sel?i1:i0;
    endmodule
```
#### GTK Wave:
``` bash
$ iverilog ternary_operator_mux.v tb_ternary_operator_mux.v
$ ./a.out
$ gtkwave tb_ternary_operator_mux.vcd
```
##### Output:
![ternary_operator_gtkwave](https://github.com/user-attachments/assets/10289c16-3590-4089-a715-d792f9967198)

#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog ternary_operator_mux.v
$ synth -top ternary_operator_mux
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:
![ternary_operator_printing_stats](https://github.com/user-attachments/assets/1dcc4d67-b3d2-4613-8a2e-eb30b5c6b4e1)

#### Write the Netlist file:
```bash
$ write_verilog -noattr ternary_operator_mux_net.v
```

##### Output:
![ternary_operator_mux_net code](https://github.com/user-attachments/assets/c36d185d-92da-4f97-9736-f3b71cb966e3)

#### Realisation of logic:
``` bash
$ show
```

##### Output:
![ternary_operator_diagram](https://github.com/user-attachments/assets/e11cf60b-1bb6-493f-b71b-092d8a77964b)

#### Gate Level Simulation:
``` bash
$ iverilog home/aditya/sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/primitives.v /home/aditya/sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/sky130_fd_sc_hd.v ternary_operator_mux_net.v tb_ternary_operator_mux.v
$ ./a.out
$ gtkwave tb_ternary_operator_mux_net.vcd
```

##### Output:
![gls output](https://github.com/user-attachments/assets/0f338272-c04e-44c3-90e7-ab3dbf3398a0)


### 2. <ins>bad_mux</ins>
#### Verilog file:

