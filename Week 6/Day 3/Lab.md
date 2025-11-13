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

#### <ins>Rise Time Calculation:</ins>
<p align = "center">
<b>Rise transition time = Time taken for output to rise to 80% - Time taken for output to rise to 20%</b>
</p>

<p align="center">
  <b>20% of output = 660 mV</b> <br>
  <b>80% of output = 2.64 V</b>
</p>

**20% Output:**
![1](https://github.com/user-attachments/assets/595543fe-2969-4409-af49-50cace9ea889) <br>

![2](https://github.com/user-attachments/assets/a6cb7d11-ddcb-445c-a3fd-63c5f1a0aa36)


**80% Output:**
![3](https://github.com/user-attachments/assets/1ae3d77e-18c5-4469-8d1a-6262fa805949) <br>

![4](https://github.com/user-attachments/assets/40cc3507-aa81-459e-b4bf-dcdc9a481e29)

**Conclusion:**
<p align="center">
  <b>Rise transition time = 2.24638 - 2.18242 = 0.06396 ns = 63.96 ps </b>
</p>

#### <ins>Fall Time Calculation:</ins>
<p align = "center">
<b>Fall Transition Time = Time taken for output to fall to 20% - Time taken for output to fall to 80%</b>
</p>

<p align="center">
  <b>20% of output = 660 mV </b> <br>
  <b>80% of output = 2.64 V</b>
</p>

**20% Output:**
![5](https://github.com/user-attachments/assets/59a0e87a-557a-4095-aefe-e5212ee13905) <br>

![6](https://github.com/user-attachments/assets/b9f24d95-bc4c-421e-a83a-0678aec1c15b)


**80% Output:**
![7](https://github.com/user-attachments/assets/82632702-619a-42ec-bd87-08defb7c038a) <br>

![8](https://github.com/user-attachments/assets/1bca4f36-b3c7-4504-81d3-562bb39fbb0e)

**Conclusion:**
<p align="center">
  <b>Fall transition time = 4.0955 - 4.0536 = 0.0419 ns = 41.9 ps <</b>
</p>

#### <ins>Rise Cell delay Calculation:</ins>
<p align = "center">
<b>Rise Cell Delay = Time taken for output to rise to 50% - Time taken for input to fall to 50% </b>
  </p>
<p align = "center">
  <b>50% of 3.3 V = 1.65 V</b>
  </p>

**50% Output:**

![9](https://github.com/user-attachments/assets/32d264d9-dbc6-4266-b5a1-3d38adc5f956) <br>

![10](https://github.com/user-attachments/assets/ac8a8d54-dfe9-47ae-b42f-708f5814dc06)

**Conclusion:**
<p align = "center">
<b>Rise cell delay = 2.21144 - 2.15008 = 0.06136 ns = 61.36 ps</b>
</p>

#### <ins>Fall Cell delay Calculation:</ins>
<p align = "center">
<b>Fall Cell delay = Time taken for output to fall to 50% - Time taken for input to 50% </b>
</p>

<p align="center">
<b>50% of 3.3 V = 1.65 V</b>
</p>

**50% Output:**
![11](https://github.com/user-attachments/assets/7a92abb6-5656-43eb-b665-ac12a6da3d08) <br>

![12](https://github.com/user-attachments/assets/3c571907-782b-415d-8909-7a46a5e5ff6a)

**Conclusion:**
<p align = "center">
<b>Fall cell delay = 4.07 - 4.05 = 0.02 ns = 20 ps </b>
</p>



