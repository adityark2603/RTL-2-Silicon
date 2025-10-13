# 🌍 RISC-V SoC Tapeout Program VSD
## 🖥️ Velocity Saturation and Basics of CMOS inverter VTC
### <ins>SPICE Simulation for lower nodes and velocity saturation effect: </ins>
<img width="2602" height="1730" alt="image" src="https://github.com/user-attachments/assets/97ce8575-fd6a-4071-b149-a3697ba50085" />

---

1. **<ins>Linear region:</ins>**
  	- MOSFET behaves like a voltage-controlled resistor
  	- Condition:
    $$V_{DS} < V_{GS} - V_T$$
  	- Current Equation:
<p align="center">
    $$I_D = k_n \left[ (V_{GS} - V_T)V_{DS} - \frac{V_{DS}^2}{2} \right]$$ 

</p>


2. **<ins>Saturation region:</ins>**
   - MOSFET behaves like a current source
   - Condition:
     $$V_{DS} \geq V_{GS} - V_T$$
  	- Current Equation:
<p align="center">
    $$I_D = \frac{k_n}{2} \frac{W}{L} (V_{GS} - V_T)^2 [1 + \lambda V_{DS}]$$
	​
</p>


### <ins>Quadratic Dependance:</ins>
When $V_{GS}$ increases above the threshold voltage $V_T$, an inversion channel of electrons forms under the MOS gate.

Mathematically:
​<br>
<p align="center">
$$I_D \propto (V_{GS} - V_T)^2$$
</p>


### <ins>Velocity Saturation:</ins>
Velocity saturation occurs when carrier velocity stops increasing with the electric field. This limits the current below the square-law model prediction at high fields.

Mathematically:
<br>
<p align="center">
$$I_{Dsat} = W C_{ox} (V_{GS} - V_T) v_{sat}$$
</p>
