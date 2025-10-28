# 3×3 S-Box (Forward/Inverse)
TTL Implementation 

---

### Description
This 3×3 S-Box performs a nonlinear bit substitution, producing unique 3-bit outputs for each 3-bit input.  
It forms the encryption stage of the system.  
Outputs (Y₂, Y₁, Y₀) feed LEDs, and into the inverse S-Box (Circuit 2 input).

---
<img width="1206" height="2622" alt="IMG_1894" src="https://github.com/user-attachments/assets/0170e568-8876-4184-9769-be6e6e3d9b1b" />

---

<img width="606" height="417" alt="Screenshot 2025-10-28 at 6 22 49 PM" src="https://github.com/user-attachments/assets/c8801a54-028f-4e23-93c7-314f8eafe4db" />

---
Kmap

<img width="658" height="349" alt="Screenshot 2025-10-28 at 6 25 18 PM" src="https://github.com/user-attachments/assets/71325d15-5a7d-4510-83b2-97507ac1a53e" />

---

## Forward 3×3 S-Box

### Truth Table
| A | B | C | Decimal In | Y₂ | Y₁ | Y₀ | Decimal Out |
|:-:|:-:|:-:|:-----------:|:--:|:--:|:--:|:------------:|
| 0 | 0 | 0 | 0 | 1 | 1 | 1 | 7 |
| 0 | 0 | 1 | 1 | 0 | 1 | 1 | 3 |
| 0 | 1 | 0 | 2 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 3 | 1 | 0 | 1 | 5 |
| 1 | 0 | 0 | 4 | 1 | 1 | 0 | 6 |
| 1 | 0 | 1 | 5 | 0 | 1 | 0 | 2 |
| 1 | 1 | 0 | 6 | 1 | 0 | 0 | 4 |
| 1 | 1 | 1 | 7 | 0 | 0 | 1 | 1 |

S(A,B,C) = (Y₂,Y₁,Y₀)

---

### Boolean Equations (Forward S-Box)
Y₂ = A·C′ + B′·C′ + A′·B·C  
Y₁ = B′  
Y₀ = A′·B′ + B·C  

---

## Inverse 3×3 S-Box

### Truth Table
| Y₂ | Y₁ | Y₀ | Decimal In | Z₂ | Z₁ | Z₀ | Decimal Out |
|:--:|:--:|:--:|:-----------:|:--:|:--:|:--:|:------------:|
| 0 | 0 | 0 | 0 | 0 | 1 | 0 | 2 |
| 0 | 0 | 1 | 1 | 1 | 1 | 1 | 7 |
| 0 | 1 | 0 | 2 | 1 | 0 | 1 | 5 |
| 0 | 1 | 1 | 3 | 0 | 0 | 1 | 1 |
| 1 | 0 | 0 | 4 | 1 | 1 | 0 | 6 |
| 1 | 0 | 1 | 5 | 0 | 1 | 1 | 3 |
| 1 | 1 | 0 | 6 | 1 | 0 | 0 | 4 |
| 1 | 1 | 1 | 7 | 0 | 0 | 0 | 0 |

InvS(Y₂,Y₁,Y₀) = (Z₂,Z₁,Z₀)

---

### Boolean Equations (Inverse S-Box)
Z₂ = A·C′ + B·C′ + A′·B′·C  
Z₁ = B′  
Z₀ = B′·C + A′·B

---

### ICs Used
| Function | IC Part # | Logic Type |
|:----------|:-----------|:------------|
| Inverter | 74LS04 | NOT |
| AND | 74LS08 | 2-Input AND |
| OR | 74LS32 | 2-Input OR |



---
# IC List and Components  

| Component | Part Number | Description | Quantity | Function / Usage |
|:-----------|:-------------|:-------------|:----------:|:-----------------|
| 74LS04 | Hex Inverter | Six NOT gates per chip | 1 | Used to invert input signals (A′, B′, C′) for Boolean terms |
| 74LS08 | Quad 2-Input AND | Four AND gates per chip | 2 | Implements product terms in the S-Box and Inverse equations |
| 74LS32 | Quad 2-Input OR | Four OR gates per chip | 2 | Combines AND outputs to form final S-Box outputs (Y₂,Y₁,Y₀) |
| 74LS47 *(optional)* | BCD to 7-Segment Decoder | Drives 7-segment display | 1 | Converts 3-bit outputs (plus grounded MSB) to visual numeric output |
| Common Anode 7-Segment Display | — | Visual output display | 1 | Displays substituted output value |
| LEDs (Green, Yellow) | — | Standard 5 mm LEDs | 3–6 | Forward (green) and inverse (yellow) output indication |
| Resistors | 1 kΩ | Current limiting for LEDs / 7-seg | 6–10 | Prevents overcurrent damage |
| Breadboard | — | Prototyping board | 1 | Physical layout for TTL logic |
| Jumper Wires | — | Male-to-male | — | Logic interconnections |
| 5V Power Supply | — | +5V DC Regulated | 1 | Powers TTL ICs and LEDs |

---


