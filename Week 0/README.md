# RISC-V SoC Tapeout Program VSD

## Tools Installation & Setup 🔨
### **<ins>System Requirements</ins>**:
1. 6GB RAM
2. 50GB HDD
3. Ubuntu 20.04 or higher version
4. 4v CPUs

### **<ins>Tool Installation Check</ins>**:

### <ins>**Yosys Tool**</ins>:
#### 1. Set up & get source code
```bash
$ sudo apt-get update
$ git clone https://github.com/YosysHQ/yosys.git
```
#### 2. Install dependencies & configure 
``` bash
$ cd yosys
$ sudo apt install make               
$ sudo apt-get install build-essential clang bison flex \
    libreadline-dev gawk tcl-dev libffi-dev git \
    graphviz xdot pkg-config python3 libboost-system-dev \
    libboost-python-dev libboost-filesystem-dev zlib1g-dev
$ make config-gcc
$ git submodule update --init --recursive
```
#### 3. Build & Install Yosys
```bash
$ make 
$ sudo make install
```

#### Output:

![WhatsApp Image 2025-09-20 at 16 39 36_3dce6e79](https://github.com/user-attachments/assets/9bca2ee7-d005-48c1-8538-dcfabff337c1)


### <ins>**Iverilog Tool**</ins>:
```bash
$ sudo apt-get update
$ sudo apt-get install iverilog
```

#### Output:

![WhatsApp Image 2025-09-20 at 14 55 02_24491e66](https://github.com/user-attachments/assets/c7049acd-6df0-4ee8-85b7-7de1124cf8c4)

### <ins>**gtkwave Tool**</ins>:
```bash
$ sudo apt-get update
$ sudo apt install gtkwave
```
#### Output: 

![WhatsApp Image 2025-09-20 at 14 58 13_be117a43](https://github.com/user-attachments/assets/0e2ff7c1-2c93-4d2e-ad64-5d04be3f2733)


### <ins>**NGSpice Tool**</ins>:
#### 1. Prepare the system & download NGSpice
```bash
$ sudo apt update && sudo apt upgrade -y
$ sudo apt install -y build-essential libx11-dev libxaw7-dev libreadline-dev \
gfortran git wget
$ cd ~/Downloads
$ wget https://downloads.sourceforge.net/project/ngspice/ng-spice-rework/45.2/ngspice-45.2.tar.gz
$ tar -zxvf ngspice-45.2.tar.gz
$ cd ngspice-45.2
```
#### 2. Configure the build
```bash
$ mkdir release
$ cd release
$ ../configure --with-x --with-readline=yes --disable-debug
```
#### 3. Build NGSpice
```bash
$ make
$ sudo make install
```

#### Output:

![WhatsApp Image 2025-09-20 at 15 45 39_fc6fe343](https://github.com/user-attachments/assets/76ae501c-8906-40bf-84a8-8c95b8f97e24)

### <ins> **Magic VLSI Tool**</ins>:
#### 1. Prepare the system & get the source
``` bash
$ sudo apt update && sudo apt upgrade -y
$ sudo apt install -y m4 tcsh csh libx11-dev tcl-dev tk-dev \
libcairo2-dev mesa-common-dev libglu1-mesa-dev libncurses-dev \
build-essential git
$ cd ~/Downloads
$ git clone https://github.com/RTimothyEdwards/magic
$ cd magic
```
#### 2. Configure & Build
```bash
$ ./configure
$ make
$ sudo make install
```
#### Output
![WhatsApp Image 2025-09-20 at 15 53 35_392bcdb4](https://github.com/user-attachments/assets/6d5c0e36-d0ce-4d40-8a2c-6143d3f1715c)


### <ins> **Docker Tool** </ins>:
#### 1. Setup Docker
``` bash
$ sudo apt-get update
$ sudo apt-get install ca-certificates curl
$ sudo install -m 0755 -d /etc/apt/keyrings
$ sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
$ sudo chmod a+r /etc/apt/keyrings/docker.asc
```
#### 2. Add Docker's official repository
``` bash
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
#### 3. Install and verify Docker
``` bash
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
$ sudo docker run hello-world
```
#### Output
![WhatsApp Image 2025-09-20 at 16 15 25_f8fc9ea8](https://github.com/user-attachments/assets/409b7856-4391-4687-beb8-8c5ad8bdcc81)

## <ins>**OpenLane Tool**</ins>:
#### 1. Verify tools
``` bash
$ git --version
$ docker --version
$ python3 --version
$ python3 -m pip --version
$ make --version
$ python3 -m venv -h
```
#### 2. Update and get the OpenLane source
``` bash
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt install -y build-essential python3 python3-venv python3-pip python3-tk curl make git
$ cd $HOME
$ git clone https://github.com/The-OpenROAD-Project/OpenLane
$ cd OpenLane
```
#### 3. Build OpenLane
``` bash
$ make
$ make test
```
#### Output
![WhatsApp Image 2025-09-20 at 16 19 55_19f6ee36](https://github.com/user-attachments/assets/0d439958-b9dd-4ff3-9e7c-d74c466d21df)

<p align="center"><i>Completed week 0 tasks successfully 🥰🥰🥰</i></p>




