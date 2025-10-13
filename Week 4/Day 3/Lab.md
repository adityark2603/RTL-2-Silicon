# 🌍 RISC-V SoC Tapeout Program VSD
## CMOS Switching Threshold & Dynamic Simulations
### <ins>VTC Characteristics of CMOS Inverter:</ins>
``` bash
$ cd sky130CircuitDesignWorkshop/design/
$ ngspice day3_inv_vtc_Wp084_Wn036.spice
```

#### Output:

![1](https://github.com/user-attachments/assets/3077606d-f1dd-4c13-bedd-5b8f4349d5f3)

``` bash
$ plot out vs in
```
#### Output:

![2](https://github.com/user-attachments/assets/2fee30d4-e307-4aa0-bb90-c8dc814bdceb)


### <ins>Transient Analysis of CMOS Inverter:</ins>
``` bash
$ ngspice day3_inv_tran_Wp084_Wn036.spice
```

#### Output:

![3](https://github.com/user-attachments/assets/324f4f5b-cdd9-4580-a177-1e4697cfc7a6)

``` bash
$ plot out vs time in
```

#### Output:

![4](https://github.com/user-attachments/assets/0578767b-16db-4ac0-9f1a-f537d059bc34)



