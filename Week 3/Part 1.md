# 🧮 RISC-V SoC Tapeout Program VSD
## ✉️ Post-Synthesis GLS & STA Fundamentals
### <ins>Purpose of GLS:</ins>
Gate-Level Simulation is used to verify the functionality of a design after the synthesis process. Unlike behavioral or RTL (Register Transfer Level) simulations, which are performed at a higher level of abstraction, GLS works on the netlist generated post-synthesis. This netlist includes the actual gates and connections used to implement the design.

### <ins>Key Aspects for BabySoC:</ins>

- Timing-Accurate Validation: GLS uses Standard Delay Format (SDF) files to back-annotate precise timing delays into the simulation. This verifies that the BabySoC meets all setup, hold, and propagation requirements, catching violations that are invisible in pre-synthesis RTL simulation.

- Post-Synthesis Logic Integrity: It confirms that the gate-level netlist—comprising the RISC-V core, PLL, DAC, and other modules—retains its intended logical behavior after synthesis and optimization, guarding against issues like metastability and glitches.

- Toolchain & Analysis: The simulation is executed using tools like Icarus Verilog to run the gate-level netlist with SDF timing, with waveform analysis in GTKWave to debug and confirm timing closure.

- Critical for Integration: For BabySoC, where multiple complex modules interact, GLS is indispensable for ensuring robust and reliable system-level performance in the final silicon.

