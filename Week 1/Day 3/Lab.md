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
---

#### 2. <ins>opt_check2.v</ins>
##### Verilog file:
![opt_check2](https://github.com/user-attachments/assets/37ef005f-dd9a-4114-b274-746d7cdcfab8)

##### Realisation of logic:
![opt_check2_diagram](https://github.com/user-attachments/assets/d05d112e-9c6d-4103-9f83-b0ef257870af)
---

#### 3. <ins>opt_check3.v</ins>
##### Verilog file:
![opt_check3](https://github.com/user-attachments/assets/9bb545ef-0d03-4cd2-a01d-c7469109764d)

##### Realisation of logic:
![opt_check3_diagram](https://github.com/user-attachments/assets/32abb3be-e1db-4bb5-936f-c3b9e9e2e273)
---

#### 4. <ins>opt_check4.v</ins>
##### Verilog file:
![opt_check4](https://github.com/user-attachments/assets/497ae188-27c9-44f1-9418-9fdc7f81e783)

##### Realisation of logic:
![opt_check4_diagram](https://github.com/user-attachments/assets/979410ad-066a-4d80-b506-c3763f6b52ce)
---


### 🌙 <ins>Sequential Logic Optimization:</ins>

```bash
$ iverilog dff_const.v tb_dff_const.v
$ ./a.out
$ gtkwave tb_dff_const.vcd
$ yosys
$ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog dff_const.v
$ synth -top dff_const
$ dfflibmap -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ show
```

#### 1. <ins>dff_const1.v</ins>
##### Verilog file:
![dff_const1_code](https://github.com/user-attachments/assets/6804d41e-ba54-4dca-9a23-f5137e99f6e8)

##### GTK Wave:
![gtkwave_tb_dff_const1](https://github.com/user-attachments/assets/f0117fbd-3861-49a4-bf8c-be19db87bbc7)

##### Statistics:
![printing_stats_dff_const1](https://github.com/user-attachments/assets/00ef5f20-59f6-4c29-84e3-b0754ece169d)

##### Realisation of logic:
![dff_const1_diagram](https://github.com/user-attachments/assets/7655e180-9a7e-4c61-83f9-3dbf79bc6d45)
---

#### 2. <ins>dff_const2.v</ins>
##### Verilog file:
![dff_const2_code](https://github.com/user-attachments/assets/d2d2b962-b996-44ad-b13b-5973e6d8c2a3)

##### GTK Wave:
![gtkwave_tb_dff_const2](https://github.com/user-attachments/assets/e5242ad4-09fb-4c41-b578-2f46dfdaa1d8)

##### Statistics:
![printing_stats_dff_const2](https://github.com/user-attachments/assets/bab70c35-cd18-4f09-b94b-865ced24578b)

##### Realisation of logic:
![dff_const2_diagram](https://github.com/user-attachments/assets/33d1fb08-5256-41a7-a7b8-6d83008d3800)
---

#### 3. <ins>dff_const3.v</ins>
##### Verilog file:
![dff_const3_code](https://github.com/user-attachments/assets/ac8d6b8a-6ca8-40ce-ae8f-fa63f6fff5be)

##### GTK Wave:
![gtkwave_tb_dff_const3](https://github.com/user-attachments/assets/f4fdf140-23f6-42e0-9397-2ef9db45a705)

##### Statistics:
![printing_stats_dff_const3](https://github.com/user-attachments/assets/bfb2efcf-ff97-469b-ab8d-e76ba83f28b7)

##### Realisation of logic:
![dff_const3_diagram](https://github.com/user-attachments/assets/25101b04-4e9c-482c-8474-2d6d7010febd)
---

#### 4. <ins>dff_const4.v</ins>
##### Verilog file:
![dff_const4_code](https://github.com/user-attachments/assets/3070980d-2184-49fa-852e-d9e2238d9c13)

##### GTK Wave:
![gtkwave_tb_dff_const4](https://github.com/user-attachments/assets/4e875d28-d5ca-47cd-a74b-116e42159f61)

##### Statistics:
![printing_stats_dff_const4](https://github.com/user-attachments/assets/71314b1f-445b-4f10-b676-2a187259542d)

##### Realisation of logic:
![dff_const4_diagram](https://github.com/user-attachments/assets/f29bb1ce-0d21-4f31-a39d-aabf4b2654c1)
---

#### 5. <ins>dff_const5.v</ins>
##### Verilog file:
![dff_const5_code](https://github.com/user-attachments/assets/4128a7cc-5213-4352-b640-5f045a415334)

##### GTK Wave:
![gtkwave_tb_dff_const5](https://github.com/user-attachments/assets/b0614677-fc7c-4821-88f7-9e4bf8d78a9a)

##### Statistics:
![printing_stats_dff_const5](https://github.com/user-attachments/assets/44d647e0-ab99-402e-9d4c-6a99cfdf1a88)

##### Realisation of logic:
![dff_const5_diagram](https://github.com/user-attachments/assets/576e6388-0cb2-46f2-a194-380535f8359e)
---

### 🪐 <ins>Sequential Unused Output Optimization:</ins>

``` bash
$ gvim counter_opt.v
$ yosys
$ $ read_liberty -lib /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_verilog counter_opt.v
$ synth -top counter_opt
$ opt_clean -purge
$ abc -liberty /home/aditya/sky130RTLDesignAndSynthesisWorkshop/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
$ show
```
#### 1. <ins>counter_opt.v</ins>
##### Verilog file:
![counter_opt_code](https://github.com/user-attachments/assets/59b68c6a-617e-435e-babe-8ec0fda81cac)

##### Statistics:
![printiing_stats_counter_opt](https://github.com/user-attachments/assets/12b3c7a6-b0ab-4ebb-b745-800403f1ed0a)

##### Realisation of logic:
![counter_opt_diagram](https://github.com/user-attachments/assets/e95c297a-46a6-4f11-aec2-38592d5fd2c7)


#### 2. <ins>counter_opt2.v</ins>
##### Verilog file:
![code_counter_opt2](https://github.com/user-attachments/assets/21466112-51ac-4faa-b4f6-35943564be97)

##### Statistics:
![printiing_stats_counter_opt2](https://github.com/user-attachments/assets/c737293c-2095-4342-bc88-f82697db24ac)

##### Realisation of logic:
![counter_opt2_diagram](https://github.com/user-attachments/assets/1c0171f6-2d7b-4f00-a676-597bc7e82103)



