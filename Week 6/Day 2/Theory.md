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

The core is **square-shaped**.

<img width="348" height="327" alt="image" src="https://github.com/user-attachments/assets/a8840384-85fe-4488-a7fe-ac958efe10e6" /> 


<ins>**Case 2**</ins>:
Core area = 8 sq. units (2 × 4)

$$\[
\text{Utilization Factor} = \frac{4}{8} = 0.5
\]  
\[
\text{Aspect Ratio} = \frac{2}{4} = 0.5
\]$$

The core is **rectangular-shaped**.

<img width="348" height="327" alt="image" src="https://github.com/user-attachments/assets/0cadd262-2e8c-4997-8e33-0bb5b119ce0d" />


