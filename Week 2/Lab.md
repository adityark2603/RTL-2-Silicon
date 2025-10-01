# RISC-V SoC Tapeout Program VSD
## 🍼 BabySoC — Fundamentals of SoC Design & Functional Modelling
### 〰️ <ins>Pre-Synthesis Simulation: </ins>
Important for verifying the functional correctness of an RTL Design under ideal conditions, ensuring the intended logic and behavior before hardware implementation. 

```bash
$ cd ~
$ git clone https://github.com/manili/VSDBabySoC.git
$ cd VSDBabySoC
$ make pre_synth_sim
$ gtkwave output/pre_synth_sim/pre_synth_sim.vcd
```
#### Output:

![pre_synth_sim](https://github.com/user-attachments/assets/faf6b04f-752f-40fe-9882-72cbdda8ae4a)


#### <ins>Explanation:</ins> 

The above image represents the simulation results using RTL Verilog code, before hardware synthesis.
- **CLK** - Input clock of the `RVMYTH` Core. The signal arises from the PLL.
- **reset** - Input reset of the `RVMYTH` Core. The signal arises from an external source.
- **OUT** - The output signal of the `VSDBabySoC` module. The signal arises from the DAC (digital-to-analog converter).
- **RV_TO_DAC[9:0]** - The 10-bit output [9:0] port of the `RVMYTH` core. The port arises from the RVMYTH register #17.
- **OUT** - The real datatype wire that can simulate analog values. The signal comes from the DAC. 

### 〰️ <ins>Post-Synthesis Simulation:</ins>
Post-synthesis simulation validates that the synthesized gate-level netlist still meets functional and timing expectations under real-world constraints, catching issues like timing violations and synthesis-related bugs before hardware fabrication.

```bash
$ cd VSDBabySoC
$ make post_synth_sim
$ gtkwave output/post_synth_sim/post_synth_sim.vcd
```

#### Output:

![post_synth_sim](https://github.com/user-attachments/assets/49f67b8d-0b6c-4feb-8b80-9265b502cdfd)

#### <ins>Explanation:</ins> 

The above image represents the simulation results after synthesizing the code for a hardware target (e.g., FPGA or ASIC).
- **\core.CLK** - Input clock of `RVMYTH` Core. The signal arises from the PLL.
- **reset** - Input reset of the `RVMYTH` Core. The signal arises from an external source.
- **OUT** - The output signal of the `VSDBabySoC` module. The signal arises from the DAC (digital-to-analog converter).
- **D[9:0]** - The 10-bit output [9:0] port of the `RVMYTH` core. The port arises from the RVMYTH register #17.
- **OUT** - The real datatype wire that can simulate analog values. The signal comes from the DAC. 


<br>

<p align="center"><i>Completed week 2 tasks successfully 🥰🥰🥰</i></p>
