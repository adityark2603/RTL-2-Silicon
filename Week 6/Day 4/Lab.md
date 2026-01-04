# 🌍 RISC-V SoC Tapeout Program VSD
## ⏰ Pre-Layout Timing Analysis & Importance of Good Clock Tree
#### 1. Fix up small DRC errors and verify whether the design is ready to be inserted into our flow
``` bash
$ Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
$ magic -T sky130A.tech sky130_inv.mag &
$ help grid
$ grid 0.46um 0.34um 0.23um 0.17um
```

**Output:**

![1](https://github.com/user-attachments/assets/89a7195f-4da1-4a7d-96f0-9f2682d1b060) <br>

![2](https://github.com/user-attachments/assets/7778bdc8-2554-4745-82f7-8fb4361f5b8c)

**<ins>Condition 1 Verified:<ins>**

<img width="1577" height="890" alt="image" src="https://github.com/user-attachments/assets/f2c2e938-ae75-4c47-9e79-413162c26b16" />

**<ins>Condition 2 Verified:<ins>**

<img width="1577" height="889" alt="image" src="https://github.com/user-attachments/assets/38bb9f65-3766-45e2-ae32-e168609ba6cf" /> <br>

<p align="center">
<b> Horizontal track pitch = 0.46 um <br>
Width of Standard cell = 0.34 um</b>
</p>

**<ins>Condition 3 Verified:<ins>**

<img width="1575" height="887" alt="image" src="https://github.com/user-attachments/assets/e5999b5e-b6e0-48e6-8cbb-46272a1c8f4a" />

<p align="center">
<b> Vertical track pitch = 0.46 um <br>
Height of Standard cell = 0.34 um * 8 = 2.72 um </b>
</p>

#### 2. Save the finalized layout with a custom name and open it 
``` bash
$ save sky130_vsdinv.mag
$ magic -T sky130A.tech sky130_vsdinv.mag
```

#### 3. Generate `.lef` file from layout
``` bash
$ lef write
```

**Output:**
![3](https://github.com/user-attachments/assets/ebd4dae7-d27b-411a-91ad-0c18b00d395d) <br>

**Newly created `.lef` file:**

![4](https://github.com/user-attachments/assets/181138b8-d8d7-414c-9e98-01259595e2e1) <br>

#### 4. Copy the newly generated `.lef` file and associated required lib files to `picorv32a` design `src` directory.

``` bash
$ cp sky130_vsdinv.lef ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
$ ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
$ cp libs/sky130_fd_sc_hd__* ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
$ ls ~/Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/src/
```

#### 5. Edit `config.tcl` to change `.lib` file and add the new extra `.lef` into the openlane flow

``` bash
set ::env(LIB_SYNTH) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"
set ::env(LIB_FASTEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__fast.lib"
set ::env(LIB_SLOWEST) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__slow.lib"
set ::env(LIB_TYPICAL) "$::env(OPENLANE_ROOT)/designs/picorv32a/src/sky130_fd_sc_hd__typical.lib"

set ::env(EXTRA_LEFS) [glob $::env(OPENLANE_ROOT)/designs/$::env(DESIGN_NAME)/src/*.lef]
```

**Output:**
![5](https://github.com/user-attachments/assets/776ee6dc-94c3-45f1-beb6-97ef74f3dbb3)

#### 6. Run openlane flow synthesis with newly inserted custom inverter cell
``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane
$ docker
$ ./flow.tcl -interactive
$ package require openlane 0.9
$ prep -design picorv32a
$ set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
$ add_lefs -src $lefs
$ run_synthesis
```

**Output:**
![6](https://github.com/user-attachments/assets/017628db-55b2-4bf2-8691-8f832d7b0006) <br>

![7](https://github.com/user-attachments/assets/95ce54f7-014d-406c-b4bf-45273bbd1f12)

#### 7. Remove/reduce the newly introduced violations with the introduction of custom inverter cell by modifying design parameters.

``` bash
$ prep -design picorv32a -tag 24-03_10-03 -overwrite
$ set lefs [glob $::env(DESIGN_DIR)/src/*.lef]
$ echo $::env(SYNTH_STRATEGY)
$ set ::env(SYNTH_STRATEGY) "DELAY 3"
$ echo $::env(SYNTH_BUFFERING)
$ echo $::env(SYNTH_SIZING)
$ set ::env(SYNTH_SIZING) 1
$ echo $::env(SYNTH_DRIVING_CELL)
$ run_synthesis
```

**Output:**
![8](https://github.com/user-attachments/assets/a513bd04-f80b-4180-a22e-c8e8bcab266d) <br>

![9](https://github.com/user-attachments/assets/6d655415-31f1-4d25-8628-7663f6e147ea)

#### 8. Once synthesis has accepted our custom inverter we can now run floorplan and placement and verify the cell is accepted in PnR flow.

``` bash
$ run_floorplan
```

**Output:**
![10](https://github.com/user-attachments/assets/4ef439af-06cf-428e-a6ab-728cafbe5867)

As we are getting errors, we shall use the below commands instead:
``` bash
$ init_floorplan
$ place_io
$ tap_decap_or
```

**Output:**
![11](https://github.com/user-attachments/assets/cbfcad8d-5bf8-4331-b4af-4ce35a6f3a48)

#### 9. Run Placement 
``` bash
$ run_placement
```

**Output:**
![12](https://github.com/user-attachments/assets/1d4c7a78-f02d-4318-b5a7-a1abb9efed66) <br>

Commands to load placement `.def` in magic in another terminal:
``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/24-03_10-03/results/placement/
$ magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

**Output:**

![13](https://github.com/user-attachments/assets/17f6ae5f-daef-4aee-b6c1-1dda3b516602) <br>

Command to view internal layers of cells:
``` bash
expand
```

![14](https://github.com/user-attachments/assets/9539fafc-76e8-464e-99f8-ede2186e0b86) <br>

![15](https://github.com/user-attachments/assets/66947f2b-225f-4da2-8fa6-fbc4f93c51ce)

