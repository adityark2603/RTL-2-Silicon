# RISC-V SoC Tapeout Program VSD
## 🍼 BabySoC — Fundamentals of SoC Design & Functional Modelling  


## 🖥️ What is a System-on-Chip (SoC)?  
A **System-on-Chip (SoC)** is an **integrated circuit** that consolidates most or all components of a computing system onto a single chip.  

Instead of separate chips for CPU, memory, and peripherals, an SoC integrates them all into one package.  
This improves performance, lowers power, saves board area, and reduces cost.  

SoCs are widely used in **mobile devices, IoT gadgets, embedded controllers, automotive ECUs, and edge AI hardware**.  


---


## ⚙️ Components of a Typical SoC:  

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

---

## 🎓 Why BabySoC?  
BabySoC is a **simplified SoC model** that keeps only the essential blocks:  
- Tiny CPU core  
- Small memory block  
- A few peripherals (UART/GPIO/timer)  
- Simple interconnect  

### Benefits:  
- Easier to understand SoC design end-to-end.  
- Learn **integration** (address map, interrupts, bus arbitration) without advanced complexity.  
- Quick to model, simulate & debug using open-source tools.  

---

## 🧩 Role of Functional Modelling  

Functional modelling = validating system behaviour **before** RTL coding & physical design.  

### Importance:  
- Catch design issues early (wrong address maps, missed protocols).  
- Faster iterations vs RTL.  
- Provides **golden reference** (trusted baseline implementation of a system's functionality) for RTL.  
- Enables early software bring-up.  


---

## 🛠️ Tools for BabySoC  

- **Icarus Verilog (iverilog)** — simulate Verilog behavioural & RTL models.  
- **GTKWave** — waveform viewer to debug signals visually.  
- **Testbenches** — clock/reset generators, ROM loaders, peripheral drivers.  
- **Assertions** — check bus protocols, ready/valid handshakes.  


