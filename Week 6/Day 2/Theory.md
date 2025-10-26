# RISC-V SoC Tapeout Program VSD
## 🗞️ Good floorplan vs Bad floorplan and Introduction to library cells

###  <ins>Core and Die Concept:</ins> 
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

<img width="348" height="327" alt="image" src="https://github.com/user-attachments/assets/0cadd262-2e8c-4997-8e33-0bb5b119ce0d" />

#### <ins>Preplaced cells:</ins>
Preplaced cells are fixed standard cells or macros whose locations are defined before the automated placement stage in VLSI physical design. These cells are “pre-placed” at specific coordinates and are not moved during the regular placement optimization process.

<img width="2924" height="1964" alt="Screenshot 2025-10-26 213400" src="https://github.com/user-attachments/assets/c10561bf-4b31-4cfe-bddd-d4f08cac003f" /> <br>

<img width="1948" height="1028" alt="Screenshot 2025-10-26 213558" src="https://github.com/user-attachments/assets/76a2596c-5787-439d-a39a-6d71980959ec" />


#### <ins>Decoupling Capacitors:</ins> 
Decoupling capacitors (or decaps) are capacitors placed between the power (VDD) and ground (VSS) lines in an integrated circuit to stabilize the supply voltage and reduce noise. They act as local energy reservoirs that supply instant current to nearby logic cells when there are sudden changes in current demand, preventing voltage drops and fluctuations.

<img width="2569" height="1136" alt="Screenshot 2025-10-26 214148" src="https://github.com/user-attachments/assets/427ad66a-6478-412e-8fb0-16bf8d79ee00" /> <br>

#### <ins>Power Planning: </ins>
Power planning is the process of designing the power and ground distribution network in an IC to ensure that every cell receives a stable voltage. It involves creating power rings, straps, and grids to minimize IR drop and maintain uniform power delivery.

#### <ins>Problem with having a single power supply:</ins>
A single power supply can cause uneven voltage distribution, leading to IR drops, noise coupling, and poor performance, especially in large chips with high current demands.

<img width="2697" height="1833" alt="Screenshot 2025-10-26 215358" src="https://github.com/user-attachments/assets/bc390448-66a8-4a43-8184-cc7c2178f6d3" />

**Problem 1:** Ground bounce occurs when a sudden switching current through the package inductance causes a temporary rise in ground potential, leading to noise and logic errors. It’s common in high-speed circuits with many simultaneous switching outputs.

<img width="2890" height="1726" alt="Screenshot 2025-10-26 215126" src="https://github.com/user-attachments/assets/28faaef8-2d55-496c-9f8c-e6119a444028" />


**Problem 2:** Voltage droop is the temporary reduction in supply voltage due to high current demand and resistance in power lines. It can slow down or even malfunction logic circuits if the voltage drops below threshold levels.

<img width="2932" height="1802" alt="Screenshot 2025-10-26 215143" src="https://github.com/user-attachments/assets/f8c4d75d-c29b-4258-87aa-39d928700356" />



