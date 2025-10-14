# 🌍 RISC-V SoC Tapeout Program VSD
## 🪶 CMOS Power Supply and Device Variation Robustness Evaluation
### 💪 <ins>Power Supply Variation:</ins>
#### <ins>Key Learnings:</ins>
1. **Technology Scaling**: Moving from 250nm to lower nodes (e.g., 20nm) requires supply voltage scaling (e.g., 1V → 0.7V)
2. **CMOS inverters can operate at 0.5V** with trade-offs:<br>
      1) Advantages:
            - **50% improvement** in gain
            - **90% reduction** in energy consumption<br>
      2) Disadvantages:
            - **Performance impact** due to insufficient voltage for complete capacitance charging/discharging

### 〰️ <ins>Device Variation:</ins>
#### <ins>Sources of Variation:</ins>

#### 1. Etching Process Variation
- Defines structural layout (width and height)
- Directly impacts delay
- Key layout components:
  - **P-diffusion** (green) - PMOS gate width
  - **N-diffusion** (yellow) - NMOS gate width  
  - **Poly-silicon** (red) - Gate length (defines technology node)
  - **Metal layers** (blue)
  - **Contacts** (black crosses)

#### 2. Oxide Thickness Variation
- Ideal: Constant gate oxide thickness
- Real: Varies along gate length and between transistors
- Affects capacitance (C<sub>ox</sub>) and current equations

### Device Strength Definitions:

| Configuration | Resistance | Size |
|---------------|------------|------|
| **Strong PMOS** | Low resistance | Wider |
| **Weak PMOS** | High resistance | Smaller |
| **Strong NMOS** | Low resistance | Wider |
| **Weak NMOS** | High resistance | Smaller |

#### <ins>Inverter Chain Characteristics:</ins>
- **Middle gates**: Similar structures, repeated distortions
- **End gates**: Different structures due to external connections

#### <ins>Performance Analysis:</ins>
- **Switching threshold range**: 0.7V to 1.4V (acceptable variation)
- **Noise Margin High (NM<sub>H</sub>)**: 2.1V to 2.5V (400mV variation)
- **Noise Margin Low (NM<sub>L</sub>)**: 0V to 0.3V (300mV variation)



