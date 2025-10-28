---

## Description  
The parity verification circuit compares the parity of the **input** bits (A, B, C) from the forward S-Box with the parity of the **output** bits (Z₂, Z₁, Z₀) from the inverse S-Box.  
If both parities are identical, the data path is verified as correct. If they differ, the circuit outputs a logic 1 on the **ERROR** line, signaling a transmission or logic fault.  

This design is fully combinational and uses only basic TTL logic gates.  
It functions as an integrity checker complementing the encryption and decryption stages implemented in Circuit 1.

----

