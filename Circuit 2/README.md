---

## Description  
The parity verification circuit compares the parity of the **input** bits (A, B, C) from the forward S-Box with the parity of the **output** bits (Z₂, Z₁, Z₀) from the inverse S-Box.  
If both parities are identical, the data path is verified as correct. If they differ, the circuit outputs a logic 1 on the **ERROR** line, signaling a transmission or logic fault.  

This design is fully combinational and uses only basic TTL logic gates.  
It functions as an integrity checker complementing the encryption and decryption stages implemented in Circuit 1.


---

## Truth Table — Input Parity (P_out)

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

---

## Truth Table — Output Parity (P_back)

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

---

## Truth Table — Error Comparison (P_out vs P_back)

| P_out | P_back | ERROR = P_out ⊕ P_back |
|:-----:|:------:|:----------------------:|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |
