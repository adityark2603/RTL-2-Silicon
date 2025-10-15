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

![mux_generate_code](https://github.com/user-attachments/assets/c4607f00-606e-4660-8e4c-de1f074e1846)


#### GTK Wave:
``` bash
$ iverilog mux_generate.v tb_mux_generate.v
$ ./a.out
$ gtkwave tb_mux_generate.vcd
```

##### Output:

![tb_mux_generate_gtkwave](https://github.com/user-attachments/assets/e21302fe-9fe0-4b74-bd92-7555cfcd9d1b)

#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog mux_generate.v
$ synth -top mux_generate
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:

![print_stats_mux generate](https://github.com/user-attachments/assets/0d52e010-9d0f-4094-bf9a-572d1457f721)


#### Realisation of Logic:
``` bash
$ show
```

##### Output:

![diagram_mux generate](https://github.com/user-attachments/assets/c70ca020-7479-4b41-b431-bfaa53b6dfd5)

### <ins>Demux_Case Statement:</ins>
#### Verilog file:

![demux_case_code](https://github.com/user-attachments/assets/0d234ff0-9f80-4ded-875b-5c77bee1a537)

#### GTK Wave:
``` bash
$ iverilog demux_case.v tb_demux_case.v
$ ./a.out
$ gtkwave tb_demux_case.vcd
```

##### Output:

![tb_demux_case_gtkwave](https://github.com/user-attachments/assets/47115bc6-f35e-4735-9915-b587f484fd95)

#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog demux_case.v
$ synth -top demux_case
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:

![print_stats_demux_case](https://github.com/user-attachments/assets/4564a21d-05d6-4106-824e-c57e4401799e)


#### Realisation of Logic:
``` bash
$ show
```

##### Output:

![diagram_demux case](https://github.com/user-attachments/assets/419a36f5-44ed-4ed6-ab8d-ec6d507609c2)

### <ins>Demux_Generate Statement:</ins>
#### Verilog file:

![demux_generate_code](https://github.com/user-attachments/assets/d58c9b39-265a-46d7-8b82-03491a27db01)

#### GTK Wave:
``` bash
$ iverilog demux_generate.v tb_demux_generate.v
$ ./a.out
$ gtkwave tb_demux_generate.vcd
```

##### Output:

![tb_demux_generate_gtkwave](https://github.com/user-attachments/assets/a71a5ab9-03b7-4846-8925-3459c92d1c56)


#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog demux_generate.v
$ synth -top demux_generate
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```
##### Output:

![print_stats_demux_generate](https://github.com/user-attachments/assets/6d1bb19b-aac6-435a-ace3-5673a2d327be)

#### Realisation of Logic:
``` bash
$ show
```

##### Output:

![diagram_demux generate](https://github.com/user-attachments/assets/fa62de15-184b-45a0-ae5a-bdac302b9749)

### <ins>Ripple Carry Adder:</ins>
#### Verilog File:

![rca_code](https://github.com/user-attachments/assets/e2bde70b-e06d-47e8-b333-dd1c21f2c83b)

#### GTK Wave:
``` bash
$ iverilog rca.v tb_rca.v
$ ./a.out
$ gtkwave tb_rca.vcd
```

##### Output:

![tb_rca_gtkwave](https://github.com/user-attachments/assets/cf58e08d-f2f1-4b63-b0ea-78998ee0167d)

#### Statistics:
``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog rca.v
$ synth -top rca
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

##### Output:

![print_stats_rca (1)](https://github.com/user-attachments/assets/0a210e2f-5563-4ccf-bcc0-767c6b92e6bd)



#### Realisation of Logic:
``` bash
$ show
```

##### Output:

<img width="1080" height="980" alt="diagram_rca" src="https://github.com/user-attachments/assets/48d8a272-0231-4b1c-919f-564a99387ff6" /> <br>

<img width="1337" height="420" alt="diagram_fa" src="https://github.com/user-attachments/assets/b6f3527a-7828-420a-be5c-b72c800abdf1" />



