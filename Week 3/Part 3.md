# 🧮 RISC-V SoC Tapeout Program VSD
## ✉️ Post-Synthesis GLS & STA Fundamentals
### <ins>Installation of OpenSTA:</ins>

``` bash
$ cd /OpenSTA
$ sudo docker build -f Dockerfile.ubuntu22.04 -t opensta .
```

#### Output:
![Screenshot 2025-10-06 205251](https://github.com/user-attachments/assets/7a8734b5-5c89-48c0-b7ff-832938770876)

## 🕑 <ins> Static Timing Analysis using OpenSTA</ins>
#### <ins>Timing analysis using in-line commands:</ins>
``` bash
$ cd /OpenSTA/examples
$ sta
$ read_liberty nangate45_slow.lib.gz
$ read_verilog example1.v
$ link_design top
$ create_clock -name -clk -period 10 {clk1 clk2 clk3}
$ set_input_delay -clock clk 0 {in1 in2}
$ report_checks
```

#### Output:
![sta example 1](https://github.com/user-attachments/assets/c5690d76-2a0a-42bb-ba3d-4ceae80a4f0e)


#### <ins>Timing analysis using TCL file:</ins>
``` bash
$ read_liberty -max nangate45_slow.lib.gz
$ read_liberty -min nangate45_slow.lib.gz
$ read_verilog example1.v
$ link_design top
$ create_clock -name -clk -period 10 {clk1 clk2 clk3}
$ set_input_delay -clock clk 0 {in1 in2}
$ report_checks -path_delay min_max
```

#### Output:

![sta example 2](https://github.com/user-attachments/assets/9f182d41-bfe7-4520-a890-3e2c6a493efd)

#### <ins>Timing analysis of VSDBabySoC:</ins>
``` bash
$ read_liberty -min sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_liberty -max sky130_fd_sc_hd__tt_025C_1v80.lib
$ read_liberty -min avsddac.lib
$ read_liberty -max avsddac.lib
$ read_liberty -min avsdpll.lib
$ read_liberty -max avsdpll.lib
$ read_verilog vsdbabysoc.synth.v
$ link_design vsdbabysoc
$ read_sdc vsdbabysoc_synthesis.sdc
$ report_checks
```

#### Output: 

![sta example 3](https://github.com/user-attachments/assets/5fc6fe2b-95da-4801-a909-93a082f12c3f)

