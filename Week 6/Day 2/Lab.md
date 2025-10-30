# RISC-V SoC Tapeout Program VSD
## 🗞️ Good floorplan vs Bad floorplan and Introduction to library cells

#### 1. Run 'picorv32a' design floorplan using OpenLANE flow & generate necessary outputs:
``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane
$ docker
```

**Inside Docker:**
``` bash
$ ./flow.tcl -interactive
$ package require openlane 0.9
$ prep -design picorv32a
$ run_synthesis
$ run_floorplan
```

**Output:**

![1](https://github.com/user-attachments/assets/e37c451f-b107-4950-b339-4bc6113367d9) <br>

![2](https://github.com/user-attachments/assets/4c20613e-1cc0-4e97-866f-49d451fe0f26)

#### 2. Calculate the die area in microns from the values in the floorplan def:

![11](https://github.com/user-attachments/assets/b1d1920f-0366-4495-b529-60be198ec2f8)

Based on the floorplan definition:

- **Unit Distance** = 1 Micron
- Die width in unit distance = 660685 - 0 = 660685
- Die height in unit distance = 671405 - 0 = 671405

**Distance in microns** = $\frac{\text{Value in Unit Distance}}{1000}$

- **Die width in microns** = $\frac{660685}{1000} = 660.685$ $Microns$
- **Die height in microns** = $\frac{671405}{1000} = 671.405$ $Microns$

**Area of die in square microns** = $660.685 \times 671.405 = 443587.212425$ $Square$ $Microns$

$$ \text{Area} = 443587.212425 \ \mu m^2 $$


#### 3. Load the generated floorplan def in the magic tool and explore the floorplan:

``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-10_14-48/results/floorplan/
$ magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def &
```

**Output:**

Floorplan def in magic:

![3](https://github.com/user-attachments/assets/0d92246c-a792-4b12-b8db-d357e5ad8e12) <br>

Equidistant placement of ports:

![4](https://github.com/user-attachments/assets/573009b2-ffe9-41f7-aba5-452d8d043759) <br>


![5](https://github.com/user-attachments/assets/027ddf44-63c0-481a-99c9-b33cac0806ec) <br>


![6](https://github.com/user-attachments/assets/6baf245e-cf6d-4f19-8119-dfdc87032053) <br>

#### 4. Run 'picorv32a' design congestion-aware placement using OpenLANE flow and generate necessary outputs:

``` bash
$ run_placement
```

**Output:**

![8](https://github.com/user-attachments/assets/da6d9a11-cc5e-477a-a3f9-f35341fa4554) <br>

#### 5. Load the generated placement def in Magic Tool and explore the placement:

``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane/designs/picorv32a/runs/29-10_14-48/results/floorplan/
$ magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def &
```

**Output:** 

![9](https://github.com/user-attachments/assets/7ee604a1-f8f2-413f-bf45-2edc2433dcf1)

Standard cells legally placed:

![10](https://github.com/user-attachments/assets/5539f039-c02f-4377-8a51-e807f617f1eb)







