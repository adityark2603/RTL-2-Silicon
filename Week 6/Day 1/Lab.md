# RISC-V SoC Tapeout Program VSD
## ⛅ Inception of open-source EDA, OpenLANE, and Sky130 PDK

#### 1. Prepare 'picorv32a' design using OpenLANE flow:

``` bash
$ cd Desktop/work/tools/openlane_working_dir/openlane
$ docker
```

**Inside Docker:**

``` bash
$ ./flow.tcl -interactive
$ package require openlane 0.9
$ prep -design picorv32a
```

**Output:**

![1](https://github.com/user-attachments/assets/96216f46-d007-4741-99f6-c16afc73b5ea)


#### 2. Run synthesis for 'picorv32a':

``` bash
$ run_synthesis
```

**Output:**

![synth success](https://github.com/user-attachments/assets/322dec98-87ba-4b93-a33f-918fc742b75d)

#### 3. Calculate Flop Ratio using Highlighted Values:

![print stats picorv32](https://github.com/user-attachments/assets/5b73a25a-0cd3-4045-959f-17521b305d05)

Calculation of Flop Ratio and DFF % from synthesis statistics report file

$$Flop \ Ratio = \frac{1613}{14876} = 0.108429685$$

$$Percentage \ of \ DFF's = 0.108429685 * 100 = 10.84296854\%$$
