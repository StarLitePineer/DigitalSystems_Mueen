# 3×3 S-Box (Forward/Inverse)
TTL Implementation 

---

## Circuit 1 — Forward 3×3 S-Box

### Inputs → Outputs
| A | B | C | Y₂ | Y₁ | Y₀ |
|:-:|:-:|:-:|:--:|:--:|:--:|
| 0 | 0 | 0 | 1 | 1 | 1 |
| 0 | 0 | 1 | 0 | 1 | 1 |
| 0 | 1 | 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 | 0 | 0 |
| 1 | 1 | 1 | 0 | 0 | 1 |

S(A,B,C) = (Y₂, Y₁, Y₀)

---

### Boolean Equations (Forward S-Box)
Y₂ = A·C′ + B′·C′ + A′·B·C  
Y₁ = B′  
Y₀ = A′·B′ + B·C  

---

### ICs Used
| Function | IC Part # | Logic Type |
|:----------|:-----------|:------------|
| Inverter | 74LS04 | NOT |
| AND | 74LS08 | 2-Input AND |
| OR | 74LS32 | 2-Input OR |

---

### Description
This 3×3 S-Box performs a nonlinear bit substitution, producing unique 3-bit outputs for each 3-bit input.  
It forms the encryption stage of the system.  
Outputs (Y₂, Y₁, Y₀) feed LEDs, and into the inverse S-Box (Circuit 2 input).
