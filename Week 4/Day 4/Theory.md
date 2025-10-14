# 🌍 RISC-V SoC Tapeout Program VSD
## 🤖 CMOS Noise Margin Robustness Evaluation


### ✨ <ins> CMOS Inverter Robustness: Noise Margin</ins>



**<ins>Ideal Input-Output characteristics of an Inverter:</ins>**

<img width="877" height="683" alt="image" src="https://github.com/user-attachments/assets/3ce81861-b05d-4d44-b75c-6ccc0cc21903" /> <br>


**<ins>Actual Input-Output characteristics of an Inverter with finite slope:</ins>** 

![4-1T](https://github.com/user-attachments/assets/0d1a17c6-bdc0-45ad-800a-fc96dbdf4d31) <br>



### <ins>Important Terminology:</ins>
1. **<ins>V<sub>IL</sub></ins>:**
    - Input Low Voltage (Vil could be Vdd/4)
    - Any input voltage level between 0 and Vil will be treated as logic '0'
2. **<ins>V<sub>OH</sub></ins>:**
    - Output High Voltage (Vih < Voh <= Vdd)
    - Any output voltage level between Voh and Vdd will be treated as logic '1'
3. **<ins>V<sub>IH</sub></ins>:**
    - Input High Voltage (Vih could be 3Vdd/4)
    - Any input voltage level between Vih and Vdd will be treated as logic '1'
4. **<ins>V<sub>OL</sub></ins>:**
    - Output Low Voltage (0 <= Vol < Vil)
    - Any output voltage level between 0 and Vol will be treated as logic '0'

### Actual Characteristics and Noise Margins:
![4-1T -finite slope](https://github.com/user-attachments/assets/203a0ff6-5f27-4c7b-877c-1547d8c22981)



### Noise Margin Definitions:
- **NMh** - Noise Margin High
  - Any voltage level in "NMh" range will be detected as logic '1'
- **NMl** - Noise Margin Low
  - Any voltage level in "NMl" range will be detected as logic '0'
- **Undefined region** - Any signal in this region will be an indefinite logic level
- **Noise Margins** are the tolerance levels of the noise

### Noise Margin Equations:
