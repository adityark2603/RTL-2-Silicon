# 🌏 RISC-V SoC Tapeout Program VSD
## ⚡Basics of NMOS Drain Current (Id) vs Drain-to-Source Voltage (Vds)
### ✨ <ins>Introduction to Circuit Design & SPICE Simulations:</ins>

**Why do we need SPICE Simulations?**

SPICE simulations are essential for designing and analyzing electronic circuits before physical implementation. They help engineers predict circuit behavior, identify design flaws, and optimize performance without needing costly or time-consuming prototypes. SPICE allows simulation of analog, digital, and mixed-signal circuits, enabling accurate prediction of voltage, current, power, and signal behavior under various conditions.

#### ⚛ <ins>NMOS Device:</ins> 
n-Channel Metal Oxide Semiconductor (NMOS) Characteristics:

1. **Source & Drain**: Two heavily doped n+ regions that facilitate the flow of electron current when the device is turned on.
2. **Gate Electrode**: Acts as the control terminal, typically made of polycrystalline silicon (Poly-Si), to which the input voltage is applied.
3. **Gate Oxide**: A critical, thin insulating layer of silicon dioxide (SiO₂) that separates the gate from the substrate. This layer enables the gate to create an electric field in the channel without conducting DC current.
4. **Body (B)**: The p-type substrate itself, which serves as the foundation and the fourth terminal, influencing the device's threshold voltage.

<br>
<img width="3662" height="1453" alt="Screenshot 2025-10-12 110219" src="https://github.com/user-attachments/assets/e1dc65f1-f637-4230-8f70-9f466bdd5edb" />


#### <ins>Working of NMOS:</ins>
1. Initially, gate-source voltage (Vgs) is zero, and all terminals are at ground, so no current flows.
2. The p-type substrate forms reverse-biased p–n junctions at bulk-source and bulk-drain, keeping the device OFF.
3. Source-drain resistance is very high as no conduction path exists between them.
4. When a positive Vgs is applied, electrons are attracted under the gate toward the interface.
5. Increasing Vgs further accumulates more electrons at the gate-oxide/semiconductor interface.
6. When enough electrons are gathered, a conducting n-channel forms by the process called strong inversion.
7. The specific Vgs at which this occurs is called the threshold voltage (Vt).
8. Raising Vgs above Vt increases the channel's conductivity by attracting more electrons into the inversion layer.
9. Electrons flow from the n+ source region into the channel, allowing current from the source to the drain, controlled by Vgs.

![1](https://github.com/user-attachments/assets/fc3b4477-4da4-4077-8856-bed78b2d588f)

#### <ins>Threshold Voltage with Positive Substrate Potential:</ins>
Applying a positive bias to the substrate (body) in an n-channel MOSFET increases the depletion region width and requires a higher gate voltage to induce strong inversion, resulting in a higher threshold voltage compared to zero substrate bias (body effect).

![2](https://github.com/user-attachments/assets/12fe3143-1d80-4a28-b343-d2fca1e98e98)

#### <ins>Some Important Terms:</ins>
1. **Strong Inversion:**
Strong inversion refers to the condition when the gate voltage exceeds the threshold voltage, causing a large number of electrons to form a conducting n-channel under the gate oxide, allowing significant current to flow from source to drain.​​

2. **Subthreshold Conduction:**
Subthreshold conduction is the phenomenon where a MOSFET conducts a small leakage current even when the gate voltage is below the threshold voltage, due to minority carriers moving across the channel; this current increases exponentially as the gate voltage approaches the threshold voltage.

#### <ins>Threshold Voltage Equation:</ins>
$$
V_t = V_{t0} + \gamma \left( \sqrt{|{-2\phi_F + V_{SB}}|} - \sqrt{|{-2\phi_F}|} \right)
$$

<img width="1772" height="912" alt="image" src="https://github.com/user-attachments/assets/e8d51a86-8a7b-4854-9266-20ef361b8a4c" />

### 🧨<ins> NMOS Resistive & Saturation Region of Operation:</ins>
#### <ins>NMOS in Resistive Operation (Triode Region):</ins>
In the **triode region**, the NMOS transistor acts like a **voltage-controlled resistor**.
The drain current Id is given by:

$$ I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})^2 $$


For **small $$\(V_{DS}\)$$**, (when $$\(V_{DS}\ll V_{GS} - V_{th}\))$$, the quadratic term is negligible:

$$
I_D \approx \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th}) V_{DS}
$$

#### <ins>Effective Resistance:</ins>

Comparing with Ohm’s law $$\(I = \frac{V}{R}\)$$, the effective **on-resistance** $$\(R_{on}\)$$ of the NMOS is:

$$
R_{on} = \frac{1}{\mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})}
$$


#### 🌊 <ins>Drift Current Theory:</ins>
Drift current is the movement of charge carriers (electrons and holes) in a semiconductor due to an applied electric field (current due to potential difference)

The channel current at any point `x` along the channel is:

$$
I_D = -V_n(x) \cdot Q_i(x) \cdot W
$$

The carrier drift velocity is defined as:

$$
v_d = \mu E
$$

#### <ins>Drain current model for linear region of operation: </ins>
<img width="637" height="922" alt="image" src="https://github.com/user-attachments/assets/050a70cc-4e19-4975-a2e4-9d956de0c41d" />

#### <ins>Pinch-Off Region Condition:</ins>
Pinch-off is the critical condition in a MOSFET where the conductive channel between the source and drain becomes constricted at the drain end, marking the transition from linear to saturation region operation.

The MOSFET enters pinch-off when:

$$
V_{DS} = V_{GS} - V_{th}
$$

<img width="1672" height="887" alt="image" src="https://github.com/user-attachments/assets/41e6c87f-22f0-425f-838f-12a6d427a0b4" />

### 🌶️ <ins>SPICE Simulations:</ins>
**SPICE** - Simulation Program with Integrated Circuit Emphasis

<img width="1740" height="900" alt="image" src="https://github.com/user-attachments/assets/7b85e4be-2f63-4ceb-a994-bd513d441bc3" />


The fundamental NMOS SPICE parameters are:

$$
V_{t0},\quad k_n,\quad \gamma,\quad \mu_n,\quad C_{ox},\quad \frac{W}{L}, \quad \lambda
$$

SPICE simulation involves using extracted device parameters to generate a netlist, which is then processed by the simulation engine to numerically solve circuit equations and produce characteristic waveforms and data.

SPICE Netlist for the given diagram:
<img width="795" height="487" alt="image" src="https://github.com/user-attachments/assets/4fc554e4-fb2b-4eba-963f-4a7fdfa938b1" />

``` bash
# SPICE Netlist Generated for MOSFET Circuit

* Generated SPICE Netlist
M1 vdd n1 0 0 nmos W=1.8u L=1.2u
R1 in n1 55
Vdd vdd 0 DC 2.5  
Vin in 0 DC 2.5

.MODEL nmos NMOS (VTO=0.7 KP=120U GAMMA=0.5)

.OP
.DC Vin 0 2.5 0.01
.PRINT DC V(n1) I(R1)
.END
EOF
```
