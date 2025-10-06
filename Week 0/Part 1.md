# RISC-V SoC Tapeout Program VSD 

## 📖 Introduction Video Summary 

### 1. Chip Modeling (Step O1)  
- Write a high-level plan of what the chip should do, usually in C language.  
- This is like a blueprint for the chip's functions before building the actual hardware.  
- Test this plan with a C program to make sure it works as expected.  

### 2. RTL Architecture (Step O2)  
- Create a hardware design using a language like Verilog that describes registers and data flow.  
- Include the processor and other hardware blocks (peripherals).  
- Turn the design into a gate-level schematic (logic gates) through synthesis.  
- Add pre-built modules and analog parts.  
- This step converts the high-level plan into a detailed design ready for hardware.  

### 3. SoC Integration (Step O3)  
- Put all pieces (processor, peripherals, pre-built modules) together into one chip design.  
- Arrange and connect these blocks physically on the chip (floorplanning, routing).  
- The result is a layout file (GDSII), which is used for making the chip.  

### Bottom Flow: From GDSII to Final Chip  
- Check design rules and verify layout correctness before sending to the chip factory.  
- Send the design to the foundry for manufacturing.  
- The end result is the final manufactured chip.  

