# 🧮 RISC-V SoC Tapeout Program VSD
## ✉️ Post-Synthesis GLS & STA Fundamentals
### <ins>Purpose of GLS:</ins>
Gate-Level Simulation is used to verify the functionality of a design after the synthesis process. Unlike behavioral or RTL (Register Transfer Level) simulations, which are performed at a higher level of abstraction, GLS works on the netlist generated post-synthesis. This netlist includes the actual gates and connections used to implement the design.

### <ins>Key Aspects for BabySoC:</ins>

- Timing-Accurate Validation: GLS uses Standard Delay Format (SDF) files to back-annotate precise timing delays into the simulation. This verifies that the BabySoC meets all setup, hold, and propagation requirements, catching violations that are invisible in pre-synthesis RTL simulation.

- Post-Synthesis Logic Integrity: It confirms that the gate-level netlist—comprising the RISC-V core, PLL, DAC, and other modules—retains its intended logical behavior after synthesis and optimization, guarding against issues like metastability and glitches.

- Toolchain & Analysis: The simulation is executed using tools like Icarus Verilog to run the gate-level netlist with SDF timing, with waveform analysis in GTKWave to debug and confirm timing closure.

- Critical for Integration: For BabySoC, where multiple complex modules interact, GLS is indispensable for ensuring robust and reliable system-level performance in the final silicon.




#### ⚠️ <ins>IMPORTANT NOTE:</ins>
Sometimes, only `rvmyth.tlv` is available. In such cases, we can use `Sandpiper-saas` to convert the `.tlv` file to `.v`:

``` bash
$ sandpiper-saas -i rvmyth.tlv -o rvmyth.v
```

#### Output:

![conversion of tlv to v](https://github.com/user-attachments/assets/0410bdb6-4c2f-45f0-994e-39d452c047e0)



## 🔬 Execution Plan for Post-Synthesis GLS:
#### 1. Load Top-level design and supporting modules:
``` bash
$ yosys
$ read_verilog /home/aditya/VSDBabySoC/src/module/vsdbabysoc.v
$ read_verilog -sv -I /home/aditya/VSDBabySoC/src/include /home/aditya/VSDBabySoC/src/module/rvmyth.v
$ read_verilog -I /home/aditya/VSDBabySoC/src/include /home/aditya/VSDBabySoC/src/module/clk_gate.v
```

#### Output:

![loading](https://github.com/user-attachments/assets/c619e0f6-ab29-448e-9521-0ad7e39d9a89)

#### 2. Load liberty files for synthesis:
``` bash
$ read_liberty -lib /home/aditya/VSDBabySoC/src/lib/avsdpll.lib
$ read_liberty -lib /home/aditya/VSDBabySoC/src/lib/avsddac.lib
$ read_liberty -lib /home/aditya/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

#### Output:

![reading lib ](https://github.com/user-attachments/assets/808b9aaf-a6f7-4072-a903-905856b63fa1)


#### 3. Run synthesis targeting `vsdbabysoc`:
``` bash
$ synth -top vsdbabysoc
```

#### Output:

![print_stats_vsdbabysoc](https://github.com/user-attachments/assets/95f8dea6-60d1-48b4-9cf3-1d5a9f9b7ff8)


#### 4. Mapping DFF to Standard cells:
``` bash
$ dfflibmap -liberty /home/aditya/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib
```

#### 5. Perform Optimisation and Technology mapping:
``` bash
$ opt
$ abc -liberty /home/aditya/VSDBabySoC/src/lib/sky130_fd_sc_hd__tt_025C_1v80.lib -script +strash;scorr;ifraig;retime;{D};strash;dch,-f;map,-M,1,{D}
```
#### 6. Perform final clean-up and renaming:
``` bash
$ flatten
$ setundef -zero
$ clean -purge
$ rename -enumerate
```

#### 7. Check Statistics:
``` bash
$ stat
```

#### Output:

![post_prnt_stat](https://github.com/user-attachments/assets/4e854965-973e-4c56-a1d6-051f5ab63e67)

#### 8. Write a synthesized netlist:
``` bash
$ write_verilog -noattr /home/aditya/VSDBabySoC/output/post_synth_sim/vsdbabysoc.synth.v
```

#### Output:

![dumping](https://github.com/user-attachments/assets/19d9c3ae-3d9e-4edc-be53-d7918ee98f2e)


## 🌊 Post-Synthesis Gate Level Simulation Results:
#### 1. Compile Testbench:
``` bash
$ iverilog -o /home/aditya/VSDBabySoC/output/post_synth_sim/post_synth_sim.out -DPOST_SYNTH_SIM -DFUNCTIONAL -DUNIT_DELAY=#1 -I /home/aditya/VSDBabySoC/src/include -I /home/aditya/VSDBabySoC/src/module /home/aditya/VSDBabySoC/src/module/testbench.v
```

#### 2. Navigate to Post-Synthesis Simulation output directory:
``` bash
$ cd output/post_synth_sim/
```

#### 3. Run simulation:
``` bash
$ ./post_synth_sim.out
```

#### 4. View the waveform in gtkwave:
``` bash
$ gtkwave post_synth_sim.vcd
```

#### Output:

![post_synth_gtkwave](https://github.com/user-attachments/assets/565a0fba-5968-4299-b9b0-6f2100d2da58)

