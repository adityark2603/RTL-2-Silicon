# 🌍 RISC-V SoC Tapeout Program VSD
## 🖥️ Velocity Saturation and Basics of CMOS inverter VTC
### 🌶️ <ins>SPICE Simulation for lower nodes and velocity saturation effect: </ins>
<img width="2602" height="1730" alt="image" src="https://github.com/user-attachments/assets/97ce8575-fd6a-4071-b149-a3697ba50085" />  <br>



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


### 📈 <ins>CMOS Voltage Transfer Characteristics (VTC): </ins>
#### <ins>NMOS as a Switch: </ins>
In cutoff ($V_{GS} < V_T$), NMOS is OFF — open switch, no current flow.  
In linear/triode region ($V_{GS} > V_T$, $V_{DS}$ small), NMOS is ON — a closed switch, conducts with low resistance.  
Used for digital logic and analog switching.

<img width="1342" height="585" alt="image" src="https://github.com/user-attachments/assets/bcfadfa2-ff3f-4c10-9540-9a12d4259c5f" />

#### <ins>Introduction to Standard MOS Voltage-Current Parameters:</ins>

- **$V_T$ (Threshold Voltage)**: Minimum gate voltage needed to form inversion channel
- **$V_{GS}$ (Gate-Source Voltage)**: Controls channel formation and current flow
- **$V_{DS}$ (Drain-Source Voltage)**: Determines operating region (triode/saturation)
- **$I_D$ (Drain Current)**: Output current dependent on $V_{GS}$ and $V_{DS}$

<img width="1765" height="685" alt="image" src="https://github.com/user-attachments/assets/403e35d2-9c9e-48c7-a6dc-9ea5ca1211b3" /> <br>








#### **<ins>s1 - Convert PMOS Gate-Source Voltage to $V_{in}$</ins>**
For PMOS transistor:
- Gate-source voltage: $V_{SG} = V_{DD} - V_{in}$
- PMOS turns ON when $V_{SG} > |V_{TP}|$ → $V_{DD} - V_{in} > |V_{TP}|$ → $V_{in} < V_{DD} - |V_{TP}|$
- PMOS turns OFF when $V_{in} > V_{DD} - |V_{TP}|$


<img width="1187" height="970" alt="image" src="https://github.com/user-attachments/assets/108ed63d-0af0-4b19-b573-fdd25c0f193f" /> <br>


#### **<ins>s2 - Convert PMOS Drain-Source Voltage to $V_{out}$</ins>**
For PMOS transistor:
- Drain-source voltage: $V_{SD} = V_{DD} - V_{out}$
- When PMOS is ON and in linear region: $V_{SD} < V_{SG} - |V_{TP}|$
- When PMOS is in saturation: $V_{SD} \geq V_{SG} - |V_{TP}|$

#### **<ins>s3 - Convert NMOS Drain-Source Voltage to $V_{out}$</ins>**
For NMOS transistor:
- Drain-source voltage: $V_{DS} = V_{out}$
- When NMOS is ON and in linear region: $V_{DS} < V_{GS} - V_{TN}$
- When NMOS is in saturation: $V_{DS} \geq V_{GS} - V_{TN}$


<img width="1775" height="600" alt="image" src="https://github.com/user-attachments/assets/c8fb15fa-4a12-455d-9dbc-4ba036aad5a4" /> <br>


#### **<ins>s4 - Merge Load Curves and Plot VTC</ins>**

-  **Plot I-V curves** for both transistors
-  **Find intersections** where $I_{DN} = I_{DP}$  
-  **Map $(V_{in}, V_{out})$** pairs from intersections
-  **Draw VTC curve** showing all operating regions

<img width="1800" height="1000" alt="image" src="https://github.com/user-attachments/assets/b789b099-a8ca-4697-bcc5-f80a4aae6096" />
