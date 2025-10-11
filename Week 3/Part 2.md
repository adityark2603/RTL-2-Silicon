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



#### ✂️ <ins>Slack Calculations:</ins>
**Slack** measures how early or late a signal arrives compared to its required time.

**Formula:**  
  `Slack = Required Time - Arrival Time`

**Minimum Slack:**  
  `Minimum Slack = Arrival Time - Minimum Expected Time`

**Maximum Slack:**  
  `Maximum Slack = Arrival Time - Maximum Expected Time`

#### Slack Types:
- **Min Slack → Hold Slack** (Hold Timing / Hold Analysis)  
- **Max Slack → Setup Slack** (Setup Timing / Setup Analysis)



### ⌛ <ins>Types of Setup / Hold Analysis:</ins>
1. **Reg-to-Reg (reg2reg):** Timing path between two registers.  
2. **In-to-Reg (in2reg):** Timing path from an input port to a register.  
3. **Reg-to-Out (reg2out):** Timing path from a register to an output port.  
4. **In-to-Out (in2out):** Timing path from an input port to an output port.  
5. **Clock Gating:** Improves chip performance by gating clock power to reduce dynamic power consumption.

![3](https://github.com/user-attachments/assets/60f32cb8-7269-4a49-8fec-640c8459a3d0)


6. **Recovery/Removal:** Ensures the reset signal of a flip-flop arrives at the correct time relative to the clock edge.  
7. **Data-to-Data:** Timing check between two data signals.  
8. **Latch Setup/Hold Analysis:** Considers transparency windows and level-sensitive behavior of latches during analysis.

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
**Actual Arrival Time (AAT)** - Sum of all propagation delays from startpoint to endpoint.
**Required Arrival Time (RAT)** - The latest acceptable signal arrival time, ensuring setup/hold constraints are satisfied.

#### <ins>Slack and GBA-PBA Analysis:</ins>
- **Slack:** `Slack = RAT - AAT`  
- **GBA (Graph-Based Analysis):** Conservative estimation across all paths.  
- **PBA (Path-Based Analysis):** More accurate for critical paths.

![6](https://github.com/user-attachments/assets/22dee3dc-9f6c-414c-8116-27b2faf619c6)

For accurate & detailed timing analysis, DAG should be with pin node conventions.

![7](https://github.com/user-attachments/assets/72204192-481c-4674-84a9-c7656c63f640)

![8](https://github.com/user-attachments/assets/553912ee-d4bf-405b-9b10-18c580ede19a)



#### <ins>Transistor-Level Timing Elements:</ins>
#### Transistor-Level Circuit for Flops: 
A flip-flop is built from cross-coupled inverters and transmission gates, storing and transferring data on clock edges.

#### <ins>Negative & Positive Latch Operation:</ins> 
- **Positive Latch:** Transparent when clock = HIGH.

![13](https://github.com/user-attachments/assets/4a16e7b3-3bcc-44e4-9c8e-d4cb66aafec7)

![12](https://github.com/user-attachments/assets/030c0811-6328-4fa0-a5f5-82de0ffa9258)

- **Negative Latch:** Transparent when clock = LOW.

![10](https://github.com/user-attachments/assets/0c4f5715-a97d-42ca-973e-0729a50129fd)

![11](https://github.com/user-attachments/assets/454744d4-bf70-48f4-8866-cd2b63b6a67e)

Both use pass transistors and inverters for controlled data flow.


#### <ins>Setup Time Calculation:</ins>
Setup time = Minimum time data must be stable before the clock edge for correct latching, determined via transistor-level simulation.

![9](https://github.com/user-attachments/assets/be4a7188-5c1b-4bc5-90bd-397a3bcb1d45)


#### <ins>Clock-to-Q (Clk-Q) Delay Calculation:</ins>
Time between the active clock edge and the resulting output transition, representing the flip-flop’s response speed.

#### <ins>Positive Edge Triggered Flip-Flop using Master-Slave configuration:</ins>
A positive edge triggered flip-flop using master-slave configuration is a circuit composed of two latches connected in series: the master and the slave. The master latch becomes active when the clock signal is low, storing the input data, while the slave latch is triggered on the rising edge (positive edge) of the clock and updates the output.

![14](https://github.com/user-attachments/assets/042d9376-60a1-413f-971d-17d4ea8b4122)

Setup time = 3 Inverter delay + 1 Transmission gate delay
Clk-Q = 1 Transmission gate delay + 1 Inverter delay
Hold time = 0


#### <ins>Eye Diagram and Jitter Analysis:</ins>
An eye diagram is a visual tool used in digital communications and signal processing to assess the quality and integrity of a high-speed digital signal over time. It is formed by overlaying multiple cycles of a digital signal waveform on an oscilloscope, creating an image that resembles an eye.

![15](https://github.com/user-attachments/assets/e967b5a0-2f93-48b5-903c-4b3ad70588b7)


#### <ins>Jitter Extraction and Accounting:</ins> 
Jitter in a network context refers to the variation in the timing of signal transitions or packet arrivals in digital communication systems. It causes uncertainty in the timing of bits, which can degrade signal quality and increase bit error rates

![16](https://github.com/user-attachments/assets/a38f7834-8c69-4917-9269-b1ea06f9e967)

![17](https://github.com/user-attachments/assets/90a20e6a-e176-4ba0-9053-9c09b0735a1d)

![18](https://github.com/user-attachments/assets/4572e6e9-527a-469c-b719-e7daf75920c5)

![19](https://github.com/user-attachments/assets/1306c474-b959-4508-8f4d-45937cd38975)
<br>

<img width="3839" height="2090" alt="20" src="https://github.com/user-attachments/assets/cb6679ca-f242-470c-88e0-3d96229f5db0" />

<br>

![21](https://github.com/user-attachments/assets/fc5ada3c-dece-4953-aa88-ed6cba4cffc3)



![22](https://github.com/user-attachments/assets/fe24d471-783f-4712-af56-bfc739ddc60d)


#### <ins>Sources of Variation:</ins>
#### Etching:  
Fabrication-induced etching variations affect interconnect dimensions, altering resistance and delay.

![23](https://github.com/user-attachments/assets/dce35102-981b-4ce5-9301-2fd6d797a3df)

![24](https://github.com/user-attachments/assets/c0913c21-c88c-46c2-8662-1c6459a18be8)

Drain Current formula:
```
Iᴅ = (1/2) · μₙ · Cₒₓ · (W/L) · (Vᴳˢ - Vᵀᴴ)²
```

#### Oxide Thickness: 
Changes in gate oxide thickness modify transistor threshold voltages and drive currents, impacting timing performance.

![25](https://github.com/user-attachments/assets/6dcd06f7-9445-4e3d-90c1-f7ded7293043)

![26](https://github.com/user-attachments/assets/8613faf2-9772-4f0a-94b4-ca345068d1e6)


#### Relationship: Resistance, Drain Current & Delay:  
Higher resistance reduces drain current, increasing RC delay and slowing signal transitions.

```
tₚᴅ = f(R) = f(Iᴅ) = f(tₒₓ, W, L)
```
![27](https://github.com/user-attachments/assets/11bc34a6-5062-416a-8fb8-4917a701a81b)



#### <ins>On-Chip Variation (OCV) and Pessimism Removal:</ins>
#### OCV-Based Setup Timing Analysis:  
Applies derating factors to account for delay variations across the chip, ensuring conservative setup margins.

#### Setup Timing After Pessimism Removal:
Removes excessive pessimism in correlated clock paths for realistic timing results.

![28](https://github.com/user-attachments/assets/5e794b10-2df2-46d3-bb31-ef07a165ad7a)


#### OCV-Based Hold Timing Analysis: 
Applies OCV derates to handle fast data path variations and prevent early data capture.

![29](https://github.com/user-attachments/assets/b292714c-8203-4839-8379-6ec4226a220e)

#### Hold Timing After Pessimism Removal: 
Refines hold margins by eliminating unnecessary pessimism between correlated data and clock paths.

![30](https://github.com/user-attachments/assets/12f35343-1c3f-4c18-a83f-2c43c9b02a66)


### 🏅<ins>Course Completion Certificate:</ins>
![VSD-STA](https://github.com/user-attachments/assets/da5d256e-c914-4175-8135-fe4c3fa9ed26)


