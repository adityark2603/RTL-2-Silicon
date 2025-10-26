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

**Output:**

![build ](https://github.com/user-attachments/assets/c2c26326-0e51-4a64-9582-33a396747ad9)


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

**Output:**

![make ](https://github.com/user-attachments/assets/06d33fff-2070-4f28-b39e-f3461e72c752)


#### 6. Launch the GUI and visualize the final layout:

``` bash
$ make gui_final
```

**Output:**

![make gui final](https://github.com/user-attachments/assets/7a579f37-dc7e-4d4a-80ba-f4d16f503b7d)



