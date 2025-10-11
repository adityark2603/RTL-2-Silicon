# RISC-V SoC Tapeout Program VSD
## ⚓ Gate Level Simulation(GLS), Blocking vs Non-blocking and Synthesis-Simulation Mismatch

### 1. <ins>ternary_operator</ins>
#### Verilog File:
![ternary_operator_mux code ](https://github.com/user-attachments/assets/65b6abf5-86fd-4ebb-bac4-3960049c4b2b)

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
<img width="722" height="290" alt="image" src="https://github.com/user-attachments/assets/3c21ffdc-622f-4981-a640-82a0fd785be8" />

#### GTK Wave:
``` bash
$ iverilog bad_mux.v tb_bad_mux.v
$ ./a.out
$ gtkwave tb_bad_mux.vcd
```

##### Output:
![tb_bad_mux gtkwave](https://github.com/user-attachments/assets/3e127d87-b360-4716-8ff1-829f78bdbf55)

#### Statistics: 
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog bad_mux.v
$ synth -top bad_mux
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:
<img width="1024" height="1024" alt="ChatGPT Image Oct 11, 2025, 09_49_52 AM" src="https://github.com/user-attachments/assets/2dfb62a3-00e6-47f3-9809-18c0deda6b17" />



#### Write the netlist file:
```bash
$ write_verilog -noattr bad_mux_net.v
```

##### Output:
<img width="1275" height="695" alt="image" src="https://github.com/user-attachments/assets/104d1d3a-9e13-4ab9-a469-6cf50cd416a1" />

#### Realisation of logic:
``` bash
$ show
```



