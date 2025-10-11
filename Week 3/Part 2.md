# 🧮 RISC-V SoC Tapeout Program VSD
## ✉️ Post-Synthesis GLS & STA Fundamentals
### <ins>Static Timing Analysis:</ins>

Static Timing Analysis (STA) is a method to verify the timing performance of a digital circuit **without applying input vectors**. It checks whether all timing constraints are met under all possible paths in the design.



#### <ins>Timing Path: </ins>
A **timing path** is the path between a **start point** and an **end point**:
- **Start point:** Flip-flop clock pin or input port  
- **End point:** Flip-flop D pin or output port

![1](https://github.com/user-attachments/assets/04078669-3119-447a-afc5-7c905a250a16)


A timing path represents the signal flow through combinational logic and interconnects. The **arrival time** at the endpoint determines whether the signal meets timing constraints.



#### <ins>Arrival Time:</ins>

**Arrival Time** is the time required for a signal to travel from the **start point** to the **end point**. It is calculated by summing the propagation delays through each gate and interconnect along the path.

![2](https://github.com/user-attachments/assets/b5e07bc9-1b8a-468d-9636-4bc3921b8fe5)



#### <ins>Required Time:</ins>

**Required Time** is the latest time by which a signal must arrive to ensure proper synchronization. It is derived by back-propagating constraints from the endpoint toward the startpoint.

For example:
A signal must arrive **after 0.5 ns** but **before 3 ns**.
  - **Minimum expected time:** 0.5 ns  
  - **Maximum expected time:** 3 ns



#### ✂️<ins>Slack Calculations:</ins>
**Slack** measures how early or late a signal arrives compared to its required time.

**Formula:**  
  `Slack = Required Time - Arrival Time`

**Minimum Slack:**  
  `Minimum Slack = Arrival Time - Minimum Expected Time`

**Maximum Slack:**  
  `Maximum Slack = Arrival Time - Maximum Expected Time`

##### Slack Types
- **Min Slack → Hold Slack** (Hold Timing / Hold Analysis)  
- **Max Slack → Setup Slack** (Setup Timing / Setup Analysis)



### ⌛ <ins>Types of Setup/Hold Analysis:</ins>
1. **Reg-to-Reg (reg2reg):** Timing path between two registers.  
2. **In-to-Reg (in2reg):** Timing path from an input port to a register.  
3. **Reg-to-Out (reg2out):** Timing path from a register to an output port.  
4. **In-to-Out (in2out):** Timing path from an input port to an output port.  
5. **Clock Gating:**  
   Improves chip performance by gating clock power to reduce dynamic power consumption.

![3](https://github.com/user-attachments/assets/60f32cb8-7269-4a49-8fec-640c8459a3d0)


6. **Recovery/Removal:**  
   Ensures the reset signal of a flip-flop arrives at the correct time relative to the clock edge.  
7. **Data-to-Data:**  
   Timing check between two data signals.  
8. **Latch Setup/Hold Analysis:**  
   Considers transparency windows and level-sensitive behavior of latches during analysis.

![4](https://github.com/user-attachments/assets/40d887e1-869a-46b6-9b14-e0f405260ac9)


#### <ins>Slew/Transition Time:</ins>  
**Slew** is the rate of change of a signal (rise or fall time).  
- **Data Path:** Check **max/min slew** at different points.  
- **Clock Path:** Usually has tighter slew constraints.

#### <ins>Load Analysis:</ins>
- **Fanout Analysis:** Ensures each node drives a safe number of loads.  
- **Capacitance Analysis:** Keeps node capacitance within allowable limits.

#### <ins>Clock Analysis:</ins>  
- **Clock Skew:**  
  Difference in clock latency across the circuit.  
  `Skew = Max(L1, L2, L3, L4) - Min(L1, L2, L3, L4)`  
- **Clock Pulse:**  
  Evaluates pulse width degradation due to parasitics.



#### <ins>Conversion of Circuitry diagram to Directed Acyclic graph (DAG):</ins>
DAG representation helps in detecting redundant computations and optimizing the design by clarifying dependencies among components.​

![5](https://github.com/user-attachments/assets/a8504ce9-96b4-4659-b851-3747011a4d1f)


#### <ins>Computing Key Parameters:</ins>
##### Actual Arrival Time (AAT)  
Sum of all propagation delays from startpoint to endpoint.

##### Required Arrival Time (RAT)  
The latest acceptable signal arrival time, ensuring setup/hold constraints are satisfied.

##### Slack and GBA-PBA Analysis  
- **Slack:** `Slack = RAT - AAT`  
- **GBA (Graph-Based Analysis):** Conservative estimation across all paths.  
- **PBA (Path-Based Analysis):** More accurate for critical paths.

![6](https://github.com/user-attachments/assets/22dee3dc-9f6c-414c-8116-27b2faf619c6)


## Transistor-Level Timing Elements

### Transistor-Level Circuit for Flops  
A flip-flop is built from cross-coupled inverters and transmission gates, storing and transferring data on clock edges.

### Negative & Positive Latch Operation  
- **Positive Latch:** Transparent when clock = HIGH.  
- **Negative Latch:** Transparent when clock = LOW.  
Both use pass transistors and inverters for controlled data flow.

---

## Library Characterization

### Library Setup Time Calculation  
Setup time = Minimum time data must be stable before the clock edge for correct latching, determined via transistor-level simulation.

### Clock-to-Q (Clk-Q) Delay Calculation  
Time between the active clock edge and the resulting output transition, representing the flip-flop’s response speed.

---

## Eye Diagram and Jitter Analysis

### Steps to Create Eye Diagram  
Overlay multiple signal cycles to visualize timing noise, jitter, and voltage margins—used to evaluate signal integrity.

### Jitter Extraction and Accounting  
Clock jitter variations are extracted and included in setup analysis to ensure realistic timing under uncertainty.

---

## Setup and Hold Analysis Representations

### Setup Analysis – Graphical to Textual  
Graphical timing paths are converted to tabular reports listing delays, arrival/required times, and slack for verification.

### Hold Analysis with Real Clocks  
Considers actual clock delays and skews to ensure post-clock data stability.

### Hold Analysis – Graphical to Textual  
Converts visual hold timing diagrams into detailed textual timing reports.

---

## Sources of Variation

### Etching  
Fabrication-induced etching variations affect interconnect dimensions, altering resistance and delay.

### Oxide Thickness  
Changes in gate oxide thickness modify transistor threshold voltages and drive currents, impacting timing performance.

### Relationship: Resistance, Drain Current & Delay  
Higher resistance reduces drain current, increasing RC delay and slowing signal transitions.

---

## On-Chip Variation (OCV) and Pessimism Removal

### OCV-Based Setup Timing Analysis  
Applies derating factors to account for delay variations across the chip, ensuring conservative setup margins.

### Setup Timing After Pessimism Removal  
Removes excessive pessimism in correlated clock paths for realistic timing results.

### OCV-Based Hold Timing Analysis  
Applies OCV derates to handle fast data path variations and prevent early data capture.

### Hold Timing After Pessimism Removal  
Refines hold margins by eliminating unnecessary pessimism between correlated data and clock paths.

---

## Summary

Static Timing Analysis ensures all signal paths meet setup and hold requirements under worst- and best-case conditions.  
It provides confidence in **timing closure**, **signal integrity**, and **reliability** across **process, voltage, and temperature** variations.

---

**Author:** Your Name  
**Last Updated:** October 2025  
**Tags:** `Static Timing Analysis`, `Digital Design`, `VLSI`, `Timing Closure`, `OCV`
