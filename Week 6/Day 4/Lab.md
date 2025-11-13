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

**Condition 2 Verified:**

<img width="1577" height="889" alt="image" src="https://github.com/user-attachments/assets/38bb9f65-3766-45e2-ae32-e168609ba6cf" /> <br>

<p align="center">
<b> Horizontal track pitch = 0.46 um <br>
Width of Standard cell = 0.34 um</b>
</p>

**Condition 3 Verified:**

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
