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

#### <ins>CMOS Inverter Robustness:</ins>
<img width="1765" height="750" alt="image" src="https://github.com/user-attachments/assets/919f1df2-1e5a-467a-b2f1-43d46bbd0231" /> <br>


#### <ins>Current Equations: </ins>
$$I_{dSN} = k_n \left[ (V_m - V_t) \cdot V_{dsatN} - \frac{V_{dsatN}^2}{2} \right]$$
$$I_{dSP} = k_p \left[ (V_m - V_{dd} - V_t) \cdot V_{dsatP} - \frac{V_{dsatP}^2}{2} \right]$$

#### <ins>Current Matching Condition: </ins>
$$k_n \left[ (V_m - V_t) \cdot V_{dsatN} - \frac{V_{dsatN}^2}{2} \right] = k_p \left[ (-V_m + V_{dd} + V_t) \cdot V_{dsatP} - \frac{V_{dsatP}^2}{2} \right]$$

#### <ins>Switching Threshold ($V_m$): </ins>
$$V_m = \frac{R \cdot V_{dd}}{1 + R}$$
$$R = \frac{k_p \cdot V_{dsatP}}{k_n \cdot V_{dsatN}} = \frac{\left( \frac{W_P}{L_P} \right) k_p' V_{dsatP}}{\left( \frac{W_N}{L_N} \right) k_n' V_{dsatN}}$$

#### <ins>Aspect Ratio Design: </ins>
$$\frac{\left( \frac{W_P}{L_P} \right)}{\left( \frac{W_N}{L_N} \right)} = \frac{k_n' \cdot V_{dsatN} \cdot \left[ (V_m - V_t) - \frac{V_{dsatN}}{2} \right]}{k_p' \cdot V_{dsatP} \cdot \left[ (-V_m + V_{dd} + V_t) - \frac{V_{dsatP}}{2} \right]}$$


### 🌊 <ins>Conclusions from PMOS & NMOS Sizes:</ins>
#### <ins>Optimal Clock Inverter Design: </ins>
- **Condition:** `(Wp/Lp) = 2 × (Wn/Ln)`
- **Result:** Approximately equal rise-fall delay
- **Application:** Ideal for clock inverters/buffers

#### <ins>Data Path Inverters:</ins>
- Other aspect ratios can be used as regular inverters/buffers
- Preferred for data path applications

#### <ins>Switching Threshold Characteristics:</ins>
$$(Wp/Lp) = 2 × (Wn/Ln) \quad \text{and} \quad (Wp/Lp) = 3 × (Wn/Ln) \quad \text{→ Very small switching threshold}$$
$$(Wp/Lp) = 4 × (Wn/Ln) \quad \text{and} \quad (Wp/Lp) = 5 × (Wn/Ln) \quad \text{→ Also very small switching threshold}$$

#### <ins>PMOS Width Impact:</ins>
- **Increasing Wp/Lp:** Significantly reduces rise delay
- **Reason:** A Larger area provides more current to charge the output capacitor
- **Result:** Faster charging time for output capacitance

#### <ins>On-Resistance Relationship:</ins>
$$R_{on}(PMOS) \approx 2.5 \times R_{on}(NMOS)$$


#### <ins>CMOS Inverter Applications in STA & Clock Tree:</ins>
**In Static Timing Analysis (STA):** Used as reference delay cells for modeling cell timing arcs (rise/fall delays) and calculating setup/hold times.

**In Clock Tree Synthesis:** Serve as clock buffers for signal regeneration, fanout driving, and inserting intentional skew to balance clock network delays across the chip.
