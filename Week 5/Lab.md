# RISC-V SoC Tapeout Program VSD 
## 🗺️ OpenROAD Flow Setup and Floorplan + Placement
### <ins>Steps to Install & Setup OpenROAD: </ins>
#### 1. Install necessary build tools and gcc-9:

``` bash
$ sudo apt update
$ sudo apt install build-essential git cmake swig python3-dev
$ sudo add-apt-repository ppa::ubuntu-toolchain-r/test -y
$ sudo apt update
$ sudo apt install g++-9 -y
```
#### 2. Build & Install `or-tools`:

``` bash
$ git clone https://github.com/google/or-tools.git
$ cd or-tools
$ mkdir build && cd build
$ make -j$(nproc)
$ sudo make install
```

#### 3. Clone OpenROAD & fix Submodule Corruption:

``` bash
$ git clone https://github.com/The-OpenROAD-Project/OpenROAD.git
$ cd OpenROAD
$ cd third-party
$ git clone https://github.com/gabime/spdlog.git
```


#### 4. Patch OpenROAD Source and Root `CMakeLists.txt`
**<ins>Part A</ins>:** Patch `src/CMakeLists.txt`:

1.  Open the source-level CMake file:
``` bash 
$ nano src/CMakeLists.txt
```
2.  **Find and comment out** the existing `find_package` line for `spdlog`. This is done because we'll be building `spdlog` as a dependency target rather than relying on a system-wide package.

```cmake
# find_package(spdlog REQUIRED)
```
<ins>**NOTE**</ins>: Ensure a `#` is placed at the beginning of the line.



**<ins>Part B</ins>:** Patch Root `CMakeLists.txt`

1.  Open the top-level CMake file:
     
```bash
$ nano CMakeLists.txt
```
2.  **Add the following line** immediately after the existing `add_subdirectory(third-party)` line and before `add_subdirectory(src)`:

 ```cmake
 add_subdirectory(third-party/spdlog) 
```
This ensures the `spdlog` dependency is built and available before the main OpenROAD source is configured.

#### 5. Build the Directory and run CMake:

``` bash
$ rm -rf build
$ mkdir build
$ cd build
$ cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_CXX_FLAGS="-Wno-error" -DCMAKE_PREFIX_PATH="/usr/local" -DCMAKE_CXX_COMPILER=/usr/bin/g++-9
```

#### 6. Compile and Install OpenROAD:

``` bash
$ make -j$(nproc)
$ sudo make install
```

**Output:**

![2](https://github.com/user-attachments/assets/67d828ef-c4d2-4bcd-a1ba-a04ccc3847c2)

