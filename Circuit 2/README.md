---

## Description  
The parity verification circuit compares the parity of the **input** bits (A, B, C) from the forward S-Box with the parity of the **output** bits (Z₂, Z₁, Z₀) from the inverse S-Box.  
If both parities are identical, the data path is verified as correct. If they differ, the circuit outputs a logic 1 on the **ERROR** line, signaling a transmission or logic fault.  

This design is fully combinational and uses only basic TTL logic gates.  
It functions as an integrity checker complementing the encryption and decryption stages implemented in Circuit 1.

---
## Simulation

<img width="1021" height="417" alt="Screenshot 2025-10-28 at 6 27 12 PM" src="https://github.com/user-attachments/assets/82f1a6a4-d97f-443a-ab0e-d9b32676a651" />

---

## Truth Table — Input Parity (P_out)
<img width="614" height="417" alt="Screenshot 2025-10-28 at 6 26 35 PM" src="https://github.com/user-attachments/assets/6dcd2df5-6f79-4877-b666-9ae45f9d42eb" />

| A | B | C | Decimal In | P_out = A ⊕ B ⊕ C |
|:-:|:-:|:-:|:-----------:|:----------------:|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 2 | 1 |
| 0 | 1 | 1 | 3 | 0 |
| 1 | 0 | 0 | 4 | 1 |
| 1 | 0 | 1 | 5 | 0 |
| 1 | 1 | 0 | 6 | 0 |
| 1 | 1 | 1 | 7 | 1 |

P_out  = A′B′C + A′BC′ + AB′C′ + ABC

---

## Truth Table — Output Parity (P_back)
<img width="614" height="417" alt="Screenshot 2025-10-28 at 6 26 44 PM" src="https://github.com/user-attachments/assets/fdf81655-8ec3-4929-8ef9-8b11b3d137b2" />

| Z₂ | Z₁ | Z₀ | Decimal In | P_back = Z₂ ⊕ Z₁ ⊕ Z₀ |
|:-:|:-:|:-:|:-----------:|:----------------:|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 1 |
| 0 | 1 | 0 | 2 | 1 |
| 0 | 1 | 1 | 3 | 0 |
| 1 | 0 | 0 | 4 | 1 |
| 1 | 0 | 1 | 5 | 0 |
| 1 | 1 | 0 | 6 | 0 |
| 1 | 1 | 1 | 7 | 1 |


P_back = Z₂′Z₁′Z₀ + Z₂′Z₁Z₀′ + Z₂Z₁′Z₀′ + Z₂Z₁Z₀

---

## Truth Table — Error Comparison (P_out vs P_back)

| P_out | P_back | ERROR = P_out ⊕ P_back |
|:-----:|:------:|:----------------------:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

ERROR  = P_out′P_back + P_outP_back′

---
# IC List and Components   

| Component | Part Number | Description | Quantity | Function / Usage |
|:-----------|:-------------|:-------------|:----------:|:-----------------|
| 74LS04 | Hex Inverter | Six NOT gates per chip | 1 | Generates complemented signals for XOR formation |
| 74LS08 | Quad 2-Input AND | Four AND gates per chip | 1 | Forms partial XOR products and ERROR term |
| 74LS32 | Quad 2-Input OR | Four OR gates per chip | 1 | Combines AND gate outputs to form XOR results |
| LEDs (Red, Green, Yellow) | — | Status indicators | 3 | Green = input parity (P_out), Yellow = output parity (P_back), Red = error |
| Resistors | 220 Ω | Current limiting for LEDs | 3 | LED current protection |
| Breadboard | — | Prototyping board | 1 | Circuit assembly base |
| Jumper Wires | — | Male-to-male | — | Signal routing between outputs |
| 5V Power Supply | — | +5V DC Regulated | 1 | TTL power input |

---
## Reflection

Developing the parity verification circuit highlighted the importance of validation and fault detection in digital design.  
By implementing XOR-based parity comparison using only AND, OR, and NOT gates, I gained a practical understanding of how simple logic can ensure data integrity.  
Debugging the LED indicators and verifying the ERROR signal deepened my grasp of logical equivalence, complementarity, and how to visualize binary relationships.  
This circuit complemented the S-Box system by demonstrating that even a minimal set of gates can provide robust error checking and clear visual feedback in real-time hardware.

