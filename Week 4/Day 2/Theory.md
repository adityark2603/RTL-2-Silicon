# 🌍 RISC-V SoC Tapeout Program VSD
## 🖥️ Velocity Saturation and Basics of CMOS inverter VTC
### <ins>SPICE Simulation for lower nodes and velocity saturation effect: </ins>
<img width="1547" height="825" alt="image" src="https://github.com/user-attachments/assets/cd5498e3-d5c4-4de0-b666-6eb658a7fe78" />



1. **<ins>Linear region:</ins>**
  	- MOSFET behaves like a voltage-controlled resistor
  	- Condition:
    $$V_{DS} < V_{GS} - V_T$$
  	- Current Equation:
<p align="center">
    $$I_D = k_n \left[ (V_{GS} - V_T)V_{DS} - \frac{V_{DS}^2}{2} \right]$$ 

</p>


2. **<ins>Saturation Region:</ins>**
   - MOSFET behaves like a current source
   - Condition:
     $$V_{DS} \geq V_{GS} - V_T$$
  	- Current Equation:
<p align="center">
    $$I_D = \frac{k_n}{2} \frac{W}{L} (V_{GS} - V_T)^2 [1 + \lambda V_{DS}]$$
	​
</p>


