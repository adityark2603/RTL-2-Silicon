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


### ⌛<ins>VSDBabySoC PVT Corner Analysis</ins>
Timing libraries can be downloaded from:
``` bash
https://github.com/efabless/skywater-pdf-libs-sky130_fd_sc_hd/tree/master/timing
```



#### The TCL file is:
``` bash
set list_of_lib_files(1) "sky130_fd_sc_hd__tt_025C_1v80.lib"
set list_of_lib_files(2) "sky130_fd_sc_hd__ff_100C_1v65.lib"
set list_of_lib_files(3) "sky130_fd_sc_hd__ff_100C_1v95.lib"
set list_of_lib_files(4) "sky130_fd_sc_hd__ff_n40C_1v56.lib"
set list_of_lib_files(5) "sky130_fd_sc_hd__ff_n40C_1v65.lib"
set list_of_lib_files(6) "sky130_fd_sc_hd__ff_n40C_1v76.lib"
set list_of_lib_files(7) "sky130_fd_sc_hd__ss_100C_1v40.lib"
set list_of_lib_files(8) "sky130_fd_sc_hd__ss_100C_1v60.lib"
set list_of_lib_files(9) "sky130_fd_sc_hd__ss_n40C_1v28.lib"
set list_of_lib_files(10) "sky130_fd_sc_hd__ss_n40C_1v35.lib"
set list_of_lib_files(11) "sky130_fd_sc_hd__ss_n40C_1v40.lib"
set list_of_lib_files(12) "sky130_fd_sc_hd__ss_n40C_1v44.lib"
set list_of_lib_files(13) "sky130_fd_sc_hd__ss_n40C_1v76.lib"

read_liberty /OpenSTA/examples/timing_libs/avsdpll.lib
read_liberty /OpenSTA/examples/timing_libs/avsddac.lib

for {set i 1} {$i <= [array size list_of_lib_files]} {incr i} {
read_liberty /OpenSTA/examples/timing_libs/$list_of_lib_files($i)
read_verilog /OpenSTA/examples/BabySOC/vsdbabysoc.synth.v
link_design vsdbabysoc
current_design
read_sdc /OpenSTA/examples/BabySOC/vsdbabysoc_synthesis.sdc
check_setup -verbose
report_checks -path_delay min_max -fields {nets cap slew input_pins fanout} -digits {4} > 
/OpenSTA/examples/BabySOC/STA_OUPUT/min_max_$list_of_lib_files($i).txt

exec echo "$list_of_lib_files($i)" >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_worst_max_slack.txt
report_worst_slack -max -digits {4} >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_worst_max_slack.txt

exec echo "$list_of_lib_files($i)" >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_worst_min_slack.txt
report_worst_slack -min -digits {4} >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_worst_min_slack.txt

exec echo "$list_of_lib_files($i)" >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_tns.txt
report_tns -digits {4} >> /OpenSTA/examples/BabySoO/STA_OUPUT/sta_tns.txt

exec echo "$list_of_lib_files($i)" >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_wns.txt
report_wns -digits {4} >> /OpenSTA/examples/BabySOC/STA_OUPUT/sta_wns.txt
}
```

#### Output:

<div align="center">

| PVT Corner | Worst Setup Slack | Worst Hold Slack | WNS | TNS |
|------------|------------------|------------------|-----|-----|
| tt_025C_1v80 | -7.4413 | -2.8912 | -7.4413 | -7478.7692 |
| ff_100C_1v65 | -6.4167 | -2.9516 | -6.4167 | -6049.2218 |
| ff_100C_1v95 | -4.7495 | -3.0047 | -4.7495 | -4156.6299 |
| ff_n40C_1v56 | -6.2611 | -2.9093 | -6.2611 | -6313.1378 |
| ff_n40C_1v65 | -5.1690 | -2.9456 | -5.1690 | -5054.1149 |
| ff_n40C_1v76 | -4.2369 | -2.9764 | -4.2369 | -4005.4895 |
| ss_100C_1v40 | -27.9280 | -2.2954 | -27.9280 | -32116.2153 |
| ss_100C_1v60 | -18.2365 | -2.5587 | -18.2365 | -20116.0846 |
| ss_n40C_1v28 | -51.4463 | -1.8470 | -51.4463 | -72155.9381 |
| ss_n40C_1v35 | -37.8023 | -1.9123 | -37.8023 | -51689.5162 |
| ss_n40C_1v40 | -31.4806 | -2.0758 | -31.4806 | -42061.9811 |
| ss_n40C_1v44 | -27.4643 | -2.2098 | -27.4643 | -36006.7115 |
| ss_n40C_1v76 | -12.3813 | -2.6969 | -12.3813 | -14294.3414 |
</div>


#### <ins>Timing Graphs:</ins>
![worst setup slack](https://github.com/user-attachments/assets/70e8db37-69c0-4cb5-b9c6-0e1d68e40d22)

![worst hold slack](https://github.com/user-attachments/assets/4a230549-e5da-4853-9692-026d9dd3b81b)

![worst negative slack](https://github.com/user-attachments/assets/2d062ef0-ebf8-4fc0-9a7a-238fe54eb499)

![total negative slack](https://github.com/user-attachments/assets/70161805-3561-48b6-bd4d-3de36894831a)


