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
<img width="425" height="257" alt="image" src="https://github.com/user-attachments/assets/7c1e6fe9-ec7b-4d74-aca4-86eef14f5acb" />



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
##### Output:
![bad mux diagram](https://github.com/user-attachments/assets/efb5eae4-40b6-42f8-ad78-5fce4e0d0a8a)


#### Gate Level Simulation:
``` bash
$ iverilog home/aditya/sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/primitives.v /home/aditya/sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/sky130_fd_sc_hd.v bad_mux_net.v tb_bad_mux.v
$ ./a.out
$ gtkwave tb_bad_mux_net.vcd
```

##### Output:
![gls bad mux](https://github.com/user-attachments/assets/b8098383-220e-4b6a-9117-165699e72e8c)

### 3. <ins>blocking_caveat.v</ins>
#### Verilog file:
![blocking caveat code](https://github.com/user-attachments/assets/4319c8bc-aa77-439c-83d3-2a493dd824aa)

#### GTK Wave:
``` bash
$ iverilog blocking_caveat.v tb_blocking_caveat.v
$ ./a.out
$ gtkwave tb_blocking_caveat.vcd
```

##### Output:
![blocking caveat gtkwave](https://github.com/user-attachments/assets/8ee83e18-9e41-41d4-b6a1-d68c9ed40eb9)

#### Statistics: 
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog blocking_caveat.v
$ synth -top blocking_caveat
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
##### Output:
<img width="441" height="275" alt="image" src="https://github.com/user-attachments/assets/e173e672-b076-47ff-96db-405f0cb02f62" />

#### Realisation of logic:
``` bash
$ show
```

##### Output:
![blocking caveat diagram](https://github.com/user-attachments/assets/d6636baf-b857-4b42-8411-105b8502b767)

#### Gate Level Simulation:
``` bash
$ iverilog home/aditya/sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/primitives.v /home/aditya/sky130RTLDesignAndSynthesisWorkshop/my_lib/verilog_model/sky130_fd_sc_hd.v blocking_caveat_net.v tb_blocking_caveat.v
$ ./a.out
$ gtkwave tb_blocking_caveat_net.vcd
```

###### Output:
![blocking caveat gls](https://github.com/user-attachments/assets/fee852cb-83e8-461a-b3e2-1472a451e1ee)


