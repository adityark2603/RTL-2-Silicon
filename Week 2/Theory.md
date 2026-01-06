# RISC-V SoC Tapeout Program VSD
## 🍼 BabySoC — Fundamentals of SoC Design & Functional Modelling  


### 🖥️ What is a System-on-Chip (SoC)?  
A **System-on-Chip (SoC)** is an **integrated circuit** that consolidates most or all components of a computing system onto a single chip.  

Instead of separate chips for CPU, memory, and peripherals, an SoC integrates them all into one package.  
This improves performance, lowers power, saves board area, and reduces cost.  

SoCs are widely used in **mobile devices, IoT gadgets, embedded controllers, automotive ECUs, and edge AI hardware**.  

<img width="867" height="1305" alt="image" src="https://github.com/user-attachments/assets/23edd6f7-82e4-4a4e-90c9-5cf6b8262598" />


### ⚙️ <ins>Components of a Typical SoC:</ins>

1. **CPU (Processor Core)**  
         - Executes instructions (fetch → decode → execute).  
         - May be a simple microcontroller core (RISC) or advanced out-of-order processor.  

2. **Memory**  
         - On-chip **SRAM** (stack, heap).  
         - **ROM/Flash** for boot.  
         - **Caches** in high-performance SoCs.  
         - External DRAM controllers.  

3. **Peripherals**  
         - UART, SPI, I²C, GPIO, timers, ADC/DAC, USB, Ethernet, display.  
         - Interrupt controller, DMA engines.  

4. **Interconnect / Bus / Fabric**  
         - Connects CPU ↔ Memory ↔ Peripherals.  
         - Examples: AMBA AXI/AHB/APB, crossbars, or NoCs.  

5. **Power & Clock Management**  
         - PLLs, clock gating, voltage/power domains.  

6. **Security & System-level Blocks**  
         - Crypto engines, secure boot, MPU/TrustZone.  

7. **Debug & Test**  
         - JTAG, trace ports, debug bridges.  



### 🎓 <ins>Why BabySoC?</ins> 
BabySoC is a **simplified SoC model** that keeps only the essential blocks:  
      - Tiny CPU core  
      - Small memory block  
      - A few peripherals (UART/GPIO/timer)  
      - Simple interconnect  <br>


**Benefits:**  
            - Easier to understand SoC design end-to-end.  
            - Learn **integration** (address map, interrupts, bus arbitration) without advanced complexity.  
            - Quick to model, simulate & debug using open-source tools.  <br>


### 🧩 <ins>Role of Functional Modelling</ins>

Functional modelling = validating system behaviour **before** RTL coding & physical design.  

**Importance:**  
            - Catch design issues early (wrong address maps, missed protocols).  
            - Faster iterations vs RTL.  
            - Provides **golden reference** (trusted baseline implementation of a system's functionality) for RTL.  
            - Enables early software bring-up.  <br>



### 🛠️ <ins>Tools for BabySoC</ins>
1. **Icarus Verilog (iverilog)** — simulate Verilog behavioural & RTL models.  
2. **GTKWave** — waveform viewer to debug signals visually.  
3. **Testbenches** — clock/reset generators, ROM loaders, peripheral drivers.  
4. **Assertions** — check bus protocols, ready/valid handshakes.  <br>


### 🧮 <ins>Short Note on VSD's BabySoC:</ins>
The VSDBabySoC is a simple SoC (System-on-Chip) design incorporating a RISC-V processor (rvmyth), a PLL (Phase-Locked Loop) module (pll), and a DAC (Digital-to-Analog Converter) module (dac).

- RVMYTH microprocessor – executes instructions and cycles values through register r17.
- Phase-Locked Loop (PLL) – generates a stable, synchronized clock for all components.
- 10-bit DAC – converts digital values into analog signals.

<img width="2270" height="1260" alt="image" src="https://github.com/user-attachments/assets/5d994e21-dc88-4850-a40c-8b043dbfc5cc" />

