# RISC-V SoC Tapeout Program VSD 
## 🗺️ OpenROAD Flow Setup and Floorplan + Placement
OpenROAD is an open-source, fully automated RTL-to-GDSII flow for digital integrated circuit (IC) design. It supports synthesis, floorplanning, placement, clock tree synthesis, routing, and final layout generation. OpenROAD enables rapid design iterations, making it ideal for academic research and industry prototyping.

⚠️ <ins>**NOTE:**</ins> These commands were all run on **Ubuntu 22.04** version. Running these on higher versions of Ubuntu may bring up errors. Hence, it is recommended to run these on Ubuntu versions **20.04** or **22.04** <br>

### <ins>Steps to Install & Setup OpenROAD: </ins>
#### 1. Clone the OpenROAD Repository:

``` bash
$ git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
$ cd OpenROAD-flow-scripts
```

#### 2. Run the Setup script:

``` bash
$ sudo ./setup.sh
```

#### 3. Build OpenROAD:

``` bash
$ ./build_openroad.sh --local
```

#### 4. Verify Installation:

``` bash
$ source ./env.sh
$ yosys -help
$ openroad -help
```

**Output:**

![verify install](https://github.com/user-attachments/assets/4ff0af11-4ad8-4e7f-9aa8-15384a589fdc)


#### 5. Run the OpenROAD flow:

``` bash
$ cd flow
$ make
```


#### 6. Launch the GUI and visualize the final layout:

``` bash
$ make gui_final
```

**Output:**
![1 orgin](https://github.com/user-attachments/assets/cdfd71db-17da-43c7-b250-7a5ddfda95db)


After completion of Logic synthesis, Chip outline (floorplanning) and placement, files will be available in the following directory: 

```
results/nangate45/gcd/base/
```

<img width="1252" height="550" alt="image" src="https://github.com/user-attachments/assets/3eddf3f1-dbd5-4045-b9e2-919d091c75a5" />

### <ins>Steps to Visualize physical layout: </ins>
``` bash
$ cd ~/OpenROAD-flow-scripts
$ source ./env.sh
$ cd flow
$ openroad -gui
```

#### 1. Floorplan:

![1](https://github.com/user-attachments/assets/1be72b1f-5fb2-4b1f-b2a6-b3e7671f605d)

#### 2. Placement & CTS:

![2](https://github.com/user-attachments/assets/49eda154-50ec-43f2-ae8f-2e23096c9147)

#### 3. Routing & Final layout:

![3](https://github.com/user-attachments/assets/f8e8d713-e4aa-4905-b794-5ce8906d7480)


