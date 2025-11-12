# RISC-V SoC Tapeout Program VSD
## 🎨 Design Library cell using Magic Layout & NGSpice Characterization
#### 1. Clone the Customer inverter standard cell design from the GitHub repository, and open the layout using Magic
``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane
$ git clone https://github.com/nickson-jose/vsdstdcelldesign
$ cd vsdstdcelldesign
$ cp /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech .
$ ls
$ magic -T sky130A.tech sky130_inv.mag &
```
**Output:**

![1](https://github.com/user-attachments/assets/fdff1411-d9c0-4779-891d-4a96ca4c3c47)

#### 2. Identify NMOS & PMOS
``` bash
$ what
```
**Output:**
<img width="1575" height="868" alt="image" src="https://github.com/user-attachments/assets/9cd91830-1074-4b95-8c68-daa7aee8d7fc" />

#### 3. SPICE extraction of an inverter in Magic
``` bash
$ pwd
$ extract all
$ ext2spice cthresh 0 rthresh 0
$ ext2spice
```

**Output:**

![2](https://github.com/user-attachments/assets/d6b12f0e-2dd3-4626-b057-dd214428a8d9)

**Created SPICE File:**

![3](https://github.com/user-attachments/assets/a02b1faa-b721-4818-b46e-fe021f653fa5)


#### 4. Editing the SPICE model for analysis through simulation

![4](https://github.com/user-attachments/assets/3acb4ae8-e975-4595-8fe9-bf07150f3900)


**Final Edited SPICE file ready for NGSpice Simulation:**

![5](https://github.com/user-attachments/assets/c0306f0f-59bc-4f24-b855-c59deacb67d6)


#### 5. Post-Layout NGSpice Simulation
``` bash
$ ngspice sky130_inv.spice
$ plot y vs time a
```

**Output:**

![6](https://github.com/user-attachments/assets/b520bd60-0ad1-4704-b4eb-2e043df4966c)<br>

![7](https://github.com/user-attachments/assets/d0e1babc-041c-477c-901a-997863106530)




