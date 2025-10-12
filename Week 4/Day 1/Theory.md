# 🌏 RISC-V SoC Tapeout Program VSD
## ⚡Basics of NMOS Drain Current (Id) vs Drain-to-Source Voltage (Vds)
<br>

**Why do we need SPICE Simulations?**

SPICE simulations are essential for designing and analyzing electronic circuits before physical implementation. They help engineers predict circuit behavior, identify design flaws, and optimize performance without needing costly or time-consuming prototypes. SPICE allows simulation of analog, digital, and mixed-signal circuits, enabling accurate prediction of voltage, current, power, and signal behavior under various conditions.

### ⚛ <ins>NMOS Device:</ins> 
n-Channel Metal Oxide Semiconductor (NMOS) Characteristics:

1. The NMOS transistor has four terminals—Gate (G), Source (S), Drain (D), and Body/Substrate (B). Each serves a distinct function in device operation.
2. The main body of the device, made from p-type silicon, acts as the substrate upon which other regions are built.
3. n+ Diffusion Regions are heavily doped n-type regions forming the source and drain, enabling conduction when the device is ON.
4. Gate oxide is a thin layer of insulating silicon dioxide that separates the gate from the substrate. This allows the gate to control current flow without direct conduction.
5. The gate electrode is typically made from polycrystalline silicon (poly-Si) or metal and is positioned above the gate oxide.

<br>
<img width="3662" height="1453" alt="Screenshot 2025-10-12 110219" src="https://github.com/user-attachments/assets/e1dc65f1-f637-4230-8f70-9f466bdd5edb" />


### <ins>Working of NMOS:</ins>
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
1. <ins>Strong Inversion</ins>
Strong inversion refers to the condition when the gate voltage exceeds the threshold voltage, causing a large number of electrons to form a conducting n-channel under the gate oxide, allowing significant current to flow from source to drain.​​

2. <ins>Subthreshold Conduction</ins>
Subthreshold conduction is the phenomenon where a MOSFET conducts a small leakage current even when the gate voltage is below the threshold voltage, due to minority carriers moving across the channel; this current increases exponentially as the gate voltage approaches the threshold voltage.



