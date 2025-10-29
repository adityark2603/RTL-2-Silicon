# RISC-V SoC Tapeout Program VSD
## 🗞️ Good floorplan vs Bad floorplan and Introduction to library cells

### 🍁 <ins>Chip Floor Planning Considerations:</ins>
####  <ins>Core and Die Concept:</ins> 
The **core** is the area in a chip used to place all the **logic cells and components**. It is the region where the actual **logic implementation** of the chip resides.
The **die** is the area that **encircles the core area** and is used for placing **I/O-related components**.


<img width="913" height="660" alt="image" src="https://github.com/user-attachments/assets/5292a1b0-1713-4366-ade6-e5207bd7db4d" />


#### <ins>Core and Die Dimensions:</ins>  
The **height** and **width** of the **core area** are determined by the **netlist of the design**. It will be based on the number of components required in order to execute the logic, and the height and width of the die area will be dependent on the core area height and width.
The **die area** dimensions depend on the **core area** dimensions.


For example, consider a **netlist** that has 2 logic gates and 2 flip-flops: <br>

<img width="848" height="671" alt="image" src="https://github.com/user-attachments/assets/531a0b97-1c4d-40ab-86f9-c042ea7dca37" />

Each component has an area of **1 sq. unit**.  
Thus, the **minimum total area required** for the **core** = `4 sq. units`.

<img width="384" height="330" alt="image" src="https://github.com/user-attachments/assets/ee5514be-897f-48ab-8b2a-65ce9daa8d0a" />


#### <ins>Utilization Factor: </ins>
The ratio of the core area occupied by the netlist to the total core area.

$$\[
\text{Utilization Factor} = \frac{\text{Area occupied by netlist}}{\text{Total core area}}
\]$$

⚠️ <ins>**Note:**</ins>  For a good floorplan, the **Utilization Factor should never be 1**, because a uUtilization Factor of 1 means **no extra space** is available for routing or adding additional logic. Such a design is considered a **bad floorplan**.

#### <ins>Aspect Ratio:</ins>
The ratio of the height of the core to the width of the core.

$$\[
\text{Aspect Ratio} = \frac{\text{Height of the core}}{\text{Width of the core}}
\]$$

  - If **Aspect Ratio = 1**, the core is **square-shaped**.  
  - If **Aspect Ratio ≠ 1**, the core is **rectangular**.


**For example:** <br>
<ins>**Case 1**</ins>:
Core area = 4 sq. units (2 × 2)

$$\[
\text{Utilization Factor} = \frac{4}{4} = 1
\]  
\[
\text{Aspect Ratio} = \frac{2}{2} = 1
\]$$

∴ The core is **square-shaped**.

<img width="348" height="327" alt="image" src="https://github.com/user-attachments/assets/a8840384-85fe-4488-a7fe-ac958efe10e6" /> 


<ins>**Case 2**</ins>:
Core area = 8 sq. units (2 × 4)

$$\[
\text{Utilization Factor} = \frac{4}{8} = 0.5
\]  
\[
\text{Aspect Ratio} = \frac{2}{4} = 0.5
\]$$

∴ The core is **rectangular-shaped**.

<img width="348" height="327" alt="image" src="https://github.com/user-attachments/assets/0cadd262-2e8c-4997-8e33-0bb5b119ce0d" /> <br>

#### <ins>Preplaced cells:</ins>
Preplaced cells are fixed standard cells or macros whose locations are defined before the automated placement stage in VLSI physical design. These cells are “pre-placed” at specific coordinates and are not moved during the regular placement optimization process.

<img width="2924" height="1964" alt="Screenshot 2025-10-26 213400" src="https://github.com/user-attachments/assets/c10561bf-4b31-4cfe-bddd-d4f08cac003f" /> <br>

<img width="1948" height="1028" alt="Screenshot 2025-10-26 213558" src="https://github.com/user-attachments/assets/76a2596c-5787-439d-a39a-6d71980959ec" /> <br>


#### <ins>Decoupling Capacitors:</ins> 
Decoupling capacitors (or decaps) are capacitors placed between the power (VDD) and ground (VSS) lines in an integrated circuit to stabilize the supply voltage and reduce noise. They act as local energy reservoirs that supply instant current to nearby logic cells when there are sudden changes in current demand, preventing voltage drops and fluctuations.

<img width="2569" height="1136" alt="Screenshot 2025-10-26 214148" src="https://github.com/user-attachments/assets/427ad66a-6478-412e-8fb0-16bf8d79ee00" /> <br>

#### <ins>Power Planning: </ins>
Power planning is the process of designing the power and ground distribution network in an IC to ensure that every cell receives a stable voltage. It involves creating power rings, straps, and grids to minimize IR drop and maintain uniform power delivery.

#### <ins>Problem with having a single power supply:</ins>
A single power supply can cause uneven voltage distribution, leading to IR drops, noise coupling, and poor performance, especially in large chips with high current demands.

<img width="2697" height="1833" alt="Screenshot 2025-10-26 215358" src="https://github.com/user-attachments/assets/bc390448-66a8-4a43-8184-cc7c2178f6d3" /> <br>

**Problem 1:** Ground bounce occurs when a sudden switching current through the package inductance causes a temporary rise in ground potential, leading to noise and logic errors. It’s common in high-speed circuits with many simultaneous switching outputs.

<img width="2890" height="1726" alt="Screenshot 2025-10-26 215126" src="https://github.com/user-attachments/assets/28faaef8-2d55-496c-9f8c-e6119a444028" /> <br>


**Problem 2:** Voltage droop is the temporary reduction in supply voltage due to high current demand and resistance in power lines. It can slow down or even malfunction logic circuits if the voltage drops below threshold levels.

<img width="2932" height="1802" alt="Screenshot 2025-10-26 215143" src="https://github.com/user-attachments/assets/f8c4d75d-c29b-4258-87aa-39d928700356" /> <br>

**Advantage of Distributed Power Supply:**
A distributed power supply network provides uniform voltage, reduces IR drop and noise, and improves reliability by delivering power locally to each region of the chip through multiple well-planned routes.

<img width="2777" height="2027" alt="Screenshot 2025-10-26 215418" src="https://github.com/user-attachments/assets/0ea30595-fc4d-4bcc-8251-0b751b29dc6c" /> <br>

#### <ins>Pin Placement:</ins>
Pin placement refers to the process of assigning and fixing the input/output (I/O) pins of a design on the periphery of the chip or block. Proper pin placement ensures efficient routing, minimizes signal delay, and reduces congestion. It plays a crucial role in achieving timing closure and optimizing power and performance.

<img width="2215" height="2117" alt="Screenshot 2025-10-27 211004" src="https://github.com/user-attachments/assets/d713efbc-dd5f-4b11-b110-723890906550" /> <br>


#### <ins>Logical Cell Placement Blockage: </ins>
A logical cell placement blockage is a restricted region defined in the floorplan where no standard cells (logic cells) can be placed.

<img width="2668" height="1944" alt="Screenshot 2025-10-27 211037" src="https://github.com/user-attachments/assets/8d3d3b03-eed1-4821-835f-ddbb3e50c10f" /> <br>


### 📌 <ins>Library Binding & Placement:</ins>
#### <ins>Netlist Binding & Initial Place Design:</ins>
Netlist binding and initial place design involve mapping the logical netlist to its corresponding physical library cells (binding), ensuring that each gate or component is associated with a real, manufacturable cell. Once bound, the placement stage arranges these cells within the chip’s floorplan to optimize area, timing, and interconnect length before detailed routing.

<img width="1785" height="782" alt="image" src="https://github.com/user-attachments/assets/f8adae5c-631c-41ee-86f6-be09beefc55f" />

#### <ins>Optimize Placement using Estimated Wire-Length & Capacitance: </ins>
Involves refining the initial cell positions by estimating interconnect wire lengths and capacitive loads. These estimates guide the placement tool to minimize delay, power consumption, and congestion, ensuring better overall timing and signal integrity before routing.

<img width="1785" height="845" alt="image" src="https://github.com/user-attachments/assets/671aa5dc-c31f-4601-95a5-b0b72ac140e4" />


#### <ins>Library Characterization & Modelling:</ins>
Library characterization and modelling is the process of simulating and analyzing standard cells to extract and model critical electrical parameters such as timing, power, and noise under various operating conditions.

### 🗺️ <ins>Cell Design and Characterization Flows:</ins>
#### <ins>Cell Design Flow:</ins>

<img width="712" height="744" alt="image" src="https://github.com/user-attachments/assets/a9ef6f1d-3e82-4881-97c4-cd0242e8c657" /> <br>

**Standard cells**: Pre-designed, pre-verified logic circuit blocks (like AND, OR, flip-flops, etc.) used in ASIC design. They form the basic building units of the chip’s logic and are placed and interconnected during the physical design phase to implement the synthesized netlist efficiently. <br>
<img width="1630" height="877" alt="image" src="https://github.com/user-attachments/assets/77fb2ab2-5b83-4b61-a2e7-98762974918b" /> <br>


**Circuit Design Step**: In this stage, transistor-level schematics are created and simulated to meet performance, power, and functionality targets using SPICE or similar tools. <br>
<img width="1700" height="982" alt="image" src="https://github.com/user-attachments/assets/e2e4bcf1-4850-4f6c-98ae-69d781f076a9" /> <br>

**Layout Design Step**: The physical representation of the circuit is drawn, defining the exact placement of transistors and interconnections while ensuring design rule compliance and minimal parasitics. <br>

<img width="1595" height="915" alt="image" src="https://github.com/user-attachments/assets/bd0583f3-d87c-4a8e-afbf-2eab6b7d53b2" />

### ⌛ <ins>General Timing Characterization Parameters:</ins>
#### <ins>Timing Threshold Definitions:</ins>
##### **1. slew_low_rise_thr**
The **lower voltage threshold** (e.g., 10% of Vdd) used to mark the **start** of a signal’s rising transition.

##### **2. slew_high_rise_thr**
The **upper voltage threshold** (e.g., 90% of Vdd) used to mark the **end** of a signal’s rising transition.
→ The time between `slew_low_rise_thr` and `slew_high_rise_thr` defines the **rise transition time (rise slew).**

##### **3. slew_low_fall_thr**
The **upper voltage threshold** (e.g., 90% of Vdd) marking the **start** of a falling transition.

##### **4. slew_high_fall_thr**
The **lower voltage threshold** (e.g., 10% of Vdd) marking the **end** of a falling transition.
→ The time between `slew_low_fall_thr` and `slew_high_fall_thr` defines the **fall transition time (fall slew).**


##### **5. in_rise_thr** 
The voltage level (typically 50% of Vdd) at which the **input rising signal** is measured for **propagation delay.**

##### **6. in_fall_thr**
The voltage level (typically 50% of Vdd) at which the **input falling signal** is measured for **propagation delay.**

##### **7. out_rise_thr**
The voltage level (typically 50% of Vdd) at which the **output rising signal** is measured to determine when the output transition occurs.

##### **8. out_fall_thr**
The voltage level (typically 50% of Vdd) at which the **output falling signal** is measured.

<img width="1597" height="845" alt="image" src="https://github.com/user-attachments/assets/f9afbd8b-72a3-4eb0-bcaf-4c1157b0040e" /><br>


**Propagation Delay (tpd)**: The time taken for a signal to travel from the input to the output of a gate, measured between the 50% Vdd points of the input and output waveforms.

**Transition Time (Slew Rate):** The time it takes for a signal to transition between low and high voltage levels, commonly measured between 10% Vdd and 90% Vdd points of the waveform.
