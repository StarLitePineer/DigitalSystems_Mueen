# 3×3 S-Box (Forward/Inverse)
TTL Implementation 

---

### Description
This 3×3 S-Box performs a nonlinear bit substitution, producing unique 3-bit outputs for each 3-bit input.  
It forms the encryption stage of the system.  
Outputs (Y₂, Y₁, Y₀) feed LEDs, and into the inverse S-Box (Circuit 2 input).

---
<img width="1206" height="2622" alt="IMG_1894" src="https://github.com/user-attachments/assets/0170e568-8876-4184-9769-be6e6e3d9b1b" />


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


