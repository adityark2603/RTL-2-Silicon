# 🌍 RISC-V SoC Tapeout Program VSD
## ⚡Basics of NMOS Drain Current (Id) vs Drain-to-Source Voltage (Vds)
### <ins>Id vs Vds Simulation of nfet:</ins>

``` bash
$ git clone https://github.com/kunalg123/sky130CircuitDesignWorkshop.git
$ cd sky130CircuitDesignWorkshop/design/
$ ngspice day1_nfet_idvds_L2_W5.spice
```

#### Output:

<img width="915" height="680" alt="image" src="https://github.com/user-attachments/assets/2c1d8b44-4a66-4c26-8ee1-40b0fd9fa74c" />


#### Plot Id vs Vds:

``` bash
$ plot -vdd#branch
```

#### Output:

<img width="1422" height="845" alt="image" src="https://github.com/user-attachments/assets/1528836f-1060-4f95-9f94-81cb72179516" />
