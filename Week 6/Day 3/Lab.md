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


### <ins>Magic Cases:</ins>
``` bash
$ cd
$  wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz
$ tar xfz drc_tests.tgz
$ cd drc_tests
$ ls -al
$ gvim .magicrc
$ magic -d XR &
```

**Output:**
![2](https://github.com/user-attachments/assets/339caf9d-5c0f-44c9-ac86-8aa0b527e39f)

**Magic file:** 

![1](https://github.com/user-attachments/assets/c2c84dbe-5f47-4247-958e-9f619274854f)

#### <ins>NOTE:</ins>
Go through all the rules in this website prior to implementing the changes: <br>
https://skywater-pdk.readthedocs.io/en/main/rules.html

### <ins>Incorrectly Implemented `poly.9`:</ins>
#### 1. Load `poly.mag` file:
![3](https://github.com/user-attachments/assets/f9193f6a-9da0-418e-80f1-9a926ab87fee)

#### 2. Add the following lines in the `sky130A.tech` file to avoid DRC errors:
![4](https://github.com/user-attachments/assets/11ca8a8e-561e-4403-a5c8-8d8a54c6004d) <br>

![5](https://github.com/user-attachments/assets/44fb7f31-316b-401d-ab87-0ed6ea68ab47)

### <ins>Incorrectly Implemented `nwell.4`:</ins>
#### 1. Update the following lines in the `sky130A.tech` file to avoid DRC errors:
![6](https://github.com/user-attachments/assets/ea464b07-43b8-45ec-aeed-e7429e339ee6) <br>

![7](https://github.com/user-attachments/assets/4887fa10-329a-4d20-bb4a-7ad2ab2c0994)

#### Execute the following commands in the `tkcon 2.3 Main` window:
``` bash
tech load sky130A.tech
drc check
drc why
```

**Output:**
![8](https://github.com/user-attachments/assets/72295e2b-8968-4ae3-a830-d0fa5e929930)





