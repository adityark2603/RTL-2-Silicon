# 🌍 RISC-V SoC Tapeout Program VSD
## 🕯️ CMOS Switching Threshold & Dynamic Simulations
### <ins>Voltage Transfer Characteristics - SPICE Simulation</ins>
#### <ins>SPICE Deck:</ins>
A SPICE deck is the set of input files (or commands) that you provide to a SPICE simulator to describe and analyze an electronic circuit.
At its core, a SPICE deck is a plain text file that contains:
  - A description of the circuit components and how they are connected.
  - Commands telling SPICE what kind of analysis to perform (e.g., DC, AC, transient).
  - Commands to output the results (e.g., .PRINT, .PLOT). <br>

  <img width="1690" height="727" alt="image" src="https://github.com/user-attachments/assets/008b8888-2743-46c8-9525-88ee7ce1338f" />

  
#### <ins>Switching Threshold:</ins>
The input voltage where $$V_{in} = V_{out}$$, representing the trip point where the output flips state.
  - Also known as the **trip point** or **metastable point**
  - For CMOS inverters: Typically designed to be $$V_{dd}/2$$ for symmetric switching
  - Represents the boundary between logical '0' and '1' states

