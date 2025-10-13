# 🌍 RISC-V SoC Tapeout Program VSD
## 🖥️ Velocity Saturation and Basics of CMOS inverter VTC
### <ins>Ids vs Vds for short channel device: </ins>
``` bash
$ cd sky130CircuitDesignWorkshop/design/
$ ngspice day2_nfet_idvds_L015_W039.spice
```

#### Output:

![day 2 -3](https://github.com/user-attachments/assets/299475e2-6646-4808-83a4-99cfd85c66fd)


```bash
$ plot -vdd#branch
```
#### Output:

![day 2 -1](https://github.com/user-attachments/assets/4160a1ef-7983-4cef-8599-45cffdd656a6)


### <ins>Ids vs Vds for short channel device without the sweep for Vdd: </ins>
``` bash
$ ngspice day2_nfet_idvgs_L015_W039.spice
```

#### Output:

![day 2 - 4](https://github.com/user-attachments/assets/21c84e62-de8e-4882-aed8-d9dd557eeef9)


``` bash
$ plot -vdd#branch
```

#### Output:

![day 2 -2](https://github.com/user-attachments/assets/00f2e170-de56-42b8-b7c4-0025dfd1680d)

