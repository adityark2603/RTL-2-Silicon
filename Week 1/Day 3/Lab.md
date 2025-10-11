# RISC-V SoC Tapeout Program VSD
## 🔭 Combinational & Sequential Optimizations
### ☀️ <ins>Combinational Logic Optimization:</ins>

``` bash
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog opt_check.v
$ synth -top opt_check
$ opt_clean -purge
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ show
```

#### 1. <ins>opt_check.v</ins>
##### Verilog file:
![opt_check1](https://github.com/user-attachments/assets/e9c042ce-429a-4c7b-a9cb-767fb9597048)

##### Realisation of logic:
![opt_check1_diagram](https://github.com/user-attachments/assets/f865104b-1c08-453c-bb12-ef2a36789dfc)

#### 2. <ins>opt_check2.v</ins>
##### Verilog file:
![opt_check2](https://github.com/user-attachments/assets/37ef005f-dd9a-4114-b274-746d7cdcfab8)

##### Realisation of logic:
![opt_check2_diagram](https://github.com/user-attachments/assets/d05d112e-9c6d-4103-9f83-b0ef257870af)

#### 
