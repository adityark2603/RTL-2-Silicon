# 🌍 RISC-V SoC Tapeout Program VSD
## 💪 Power Distribution Network & Routing

## <ins>Power Distribution network</ins>
``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane
$ docker
$ ./flow.tcl -interactive
$ package require openlane 0.9
$ prep -design picorv32a
$ set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
$ add_lefs -src $lefs
$ set ::env(SYNTH_STRATEGY) "DELAY 3"
$ set ::env(SYNTH_SIZING) 1
$ run_synthesis
$ init_floorplan
$ place_io
$ tap_decap_or
$ run_placement
$ unset ::env(LIB_CTS) # Not required unless you get an error
$ run_cts
$ gen_pdn
```

**Outputs:**
![1](https://github.com/user-attachments/assets/a5ef0730-346c-4f8f-a870-d0eb07ad4b02) <br>

![2](https://github.com/user-attachments/assets/158f78fd-5f0c-46f7-b677-ce179c148a86) <br>

![3](https://github.com/user-attachments/assets/157a139a-2956-4ac4-a9aa-bd64d31456cb) <br>

![4](https://github.com/user-attachments/assets/356e4e81-39f7-4ef6-82fd-c2ea25686b46) <br>

![5](https://github.com/user-attachments/assets/e2dc7eab-a968-4c94-80ce-859bd2187e2c) <br>

![6](https://github.com/user-attachments/assets/b8ee2383-7375-41e4-9a23-a4b7a2a18c44) <br>

![7](https://github.com/user-attachments/assets/e7b8c993-cc1c-4585-939d-fa089a7dd993) <br>

![8](https://github.com/user-attachments/assets/64d3dc35-3ac7-49f4-bd56-016dbf38afcb) <br>

![9](https://github.com/user-attachments/assets/6bae76a9-5d8b-48f0-b03f-592dcb923c88) <br>

![10](https://github.com/user-attachments/assets/2a086032-a27b-4d62-9292-69e520e77071) <br>

Load the Power Distribution Network on Magic using following commands:
``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/05-01_15-29/tmp/floorplan/
$ magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read 14-pdn.def &
```

**Output:**
![11](https://github.com/user-attachments/assets/67f51c31-87b1-4d1e-a6db-baac9d43b4b6) <br>

![12](https://github.com/user-attachments/assets/0f605d43-bab2-41f1-a22b-a8ebcfe1ce5e)


## <ins>Routing</ins>
``` bash
$ run_routing
```

**Outputs:**
![13](https://github.com/user-attachments/assets/e3428a40-2252-4b30-8c21-45c987d0f48e) <br>

View the routing in Magic using the following commands:
``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/05-01_15-29/results/routing/
$ magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.def &
```

**Output:**
![14](https://github.com/user-attachments/assets/9351e9f4-3cce-4bd9-b175-c76989b7f86e) <br>

![15](https://github.com/user-attachments/assets/4a7b171a-ad0b-4074-a9c0-a78b700927e5) <br>


View the `.spef` file generated after routing:

![16](https://github.com/user-attachments/assets/0efd1bf8-4b1b-4df4-a50a-b4f246b309d3)


## <ins>Post-Routing Timing Analysis</ins>
``` bash
$ openroad
$ read_lef /openLANE_flow/designs/picorv32a/runs/05-01_15-29/tmp/merged.lef
$ read_def /openLANE_flow/designs/picorv32a/runs/05-01_15-29/results/routing/picorv32a.def
$ write_db pico_route.db
$ read_db pico_route.db
$ read_verilog /openLANE_flow/designs/picorv32a/runs/05-01_15-29/results/synthesis/picorv32a.synthesis_preroute.v
$ read_liberty /openLANE_flow/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib
$ link_design picorv32a
$ read_sdc /openLANE_flow/designs/picorv32a/src/my_base.sdc
$ set_propagated_clock [all_clocks]
$ read_spef /openLANE_flow/designs/picorv32a/runs/05-01_15-29/results/routing/picorv32a.spef 
$ report_checks -path_delay min_max -fields {slew trans net cap input_pins} -format full_clock_expanded -digits 4
$ exit
```

**Output:**
![17](https://github.com/user-attachments/assets/7ada6dd5-5eda-4bc9-a4ec-d78a6418fc19) <br>

![18](https://github.com/user-attachments/assets/e905084a-ea63-4295-8031-e5b4665ea21a) <br>

![19](https://github.com/user-attachments/assets/74498f48-8bbc-4e59-a88f-2362354ab782) <br>

## <ins>Final Output</ins>
![20](https://github.com/user-attachments/assets/13b4246f-7274-47f4-bd1b-9bbcb1f92491)




