# 🌍 RISC-V SoC Tapeout Program VSD
## 🪄  BabySoC Physical Design & Post-Route SPEF Generation
#### 1. Install and set up ORFS (if not installed already)
``` bash
$ git clone --recursive https://github.com/The-OpenROAD-Project/OpenROAD-flow-scripts
$ cd OpenROAD-flow-scripts
$ sudo ./setup.sh
$ ./build_openroad.sh --local
```

#### 2. Verify ORFS Installation
``` bash
$ source ./env.sh
$ yosys -help
$ openroad -help
$ cd flow
$ make
$ make gui_final
```

**Output:**

![1](https://github.com/user-attachments/assets/47d936dd-305b-4ef5-bef5-2c252b291be1) <br>

![2](https://github.com/user-attachments/assets/4b0fcf6d-c4dc-4846-9414-b55b684813ce)

