# RISC-V SoC Tapeout Program VSD
## 🔨 Optimization in synthesis

### <ins>Incomplete_If Statement:</ins>
#### Verilog file:

![incomp_if_code](https://github.com/user-attachments/assets/7102efd7-029a-49c6-95ac-8bb1b187d03b)

#### GTK Wave:
``` bash
$ iverilog incomp_if.v tb_incomp_if.v
$ ./a.out
$ gtkwave tb_incomp_if.vcd
```
##### Output:

![tb_incomp_if_gtkwave](https://github.com/user-attachments/assets/4b2587b3-9200-488f-8509-ed93ae5b836e)

#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog incomp_if.v
$ synth -top incomp_if
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:

![print_stats_incomp_if](https://github.com/user-attachments/assets/77833ddd-aaf3-44d2-ae26-36159dc821b8)


#### Realisation of Logic:
``` bash
$ show
```

##### Output:

![diagram_incomp_if](https://github.com/user-attachments/assets/201d416c-6c94-4f78-8a23-1b4213ead312)


### <ins>Incomplete_If2 Statement:</ins>
#### Verilog file:
![incomp_if2_code](https://github.com/user-attachments/assets/419e4395-059a-4582-bf4c-2bd28eb724cc)

#### GTK Wave:
``` bash
$ iverilog incomp_if2.v tb_incomp_if2.v
$ ./a.out
$ gtkwave tb_incomp_if2.vcd
```

##### Output:

![tb_incomp_if2_gtkwave](https://github.com/user-attachments/assets/f36d7b0a-d30c-499b-b803-a650095f27fc)


#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog incomp_if2.v
$ synth -top incomp_if2
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:

![print_stats_incomp_if2](https://github.com/user-attachments/assets/3eb255f7-7572-439f-965e-571dd73f3f36)


#### Realisation of Logic:
``` bash
$ show
```

##### Output:

![diagram_incomp_if2](https://github.com/user-attachments/assets/ad8e4279-e240-437d-b0ab-87c294edbf0e)


### <ins>Incomplete_Case Statement:</ins>
#### Verilog file:

![incomp_case_code](https://github.com/user-attachments/assets/214e6e28-9732-411c-b4b3-f4edfef02849)


#### GTK Wave:
``` bash
$ iverilog incomp_case.v tb_incomp_case.v
$ ./a.out
$ gtkwave tb_incomp_case.vcd
```

##### Output:

![tb_incomp_case_gtkwave](https://github.com/user-attachments/assets/456626d5-5e6c-455e-9628-2c28f4e58193)

#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog incomp_case.v
$ synth -top incomp_case
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:

![print_stats_comp_case](https://github.com/user-attachments/assets/7a9c079c-f8d0-4d7f-b33f-3f4fcf89860e)


#### Realisation of Logic:
``` bash
$ show
```

##### Output:

![diagram_incomp_case](https://github.com/user-attachments/assets/2d27a9fa-bacd-472f-b1da-670d6e5ce872)



### <ins>Complete_Case Statement:</ins>
#### Verilog file:

![comp_case_code](https://github.com/user-attachments/assets/7b1920cc-7c51-4ec8-a4b3-03912658a929)

#### GTK Wave:
``` bash
$ iverilog comp_case.v tb_comp_case.v
$ ./a.out
$ gtkwave tb_comp_case.vcd
```

##### Output:

![tb_comp_case_gtkwave](https://github.com/user-attachments/assets/69fbed86-ce95-469c-8271-ed3ca4d080a5)

#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog comp_case.v
$ synth -top comp_case
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:

![print_stats_comp_case](https://github.com/user-attachments/assets/61bcec53-455e-4f6a-b733-d36e35e0f4c3)

#### Realisation of Logic:
``` bash
$ show
```

##### Output:

![diagram_comp_case](https://github.com/user-attachments/assets/69aeb332-bfda-4dd9-9ca2-6c06ce5ae78f)

### <ins>Partial_Case Statement:</ins>
#### Verilog file:

![partial_case_code](https://github.com/user-attachments/assets/f830ac59-4ba3-4308-a11d-c6148471f13a)

#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog partial_case.v
$ synth -top partial_case
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:

![print_stats_partial case assign](https://github.com/user-attachments/assets/fd215610-c2a4-439f-809e-96061d912671)



#### Realisation of Logic:
``` bash
$ show
```

##### Output:

![diagram_partial_case_assign](https://github.com/user-attachments/assets/2b5b1871-fe23-4b34-aaca-f7c2c19d9c3f)


### <ins>Mux_Generate Statement:</ins>
#### Verilog file:

