Project: 3-Bit S-Box Encryption Circuit (TTL Implementation)
The purpose of this circuit is to demonstrate a simple, hardware-based encryption and substitution process using combinational logic. The system implements a custom 3-bit nonlinear substitution box (S-Box) built entirely from TTL logic gates, DIP switches, and LED indicators. The circuit translates a 3-bit binary input into a unique 3-bit binary output according to a predefined mapping table (substitution table). This operation models the transformation step used in many modern block ciphers, such as the Serpent or AES encryption algorithms. 

An additional circuit (the S-Inverter) can be built to perform the reverse transformation.
It uses the same gate structure but implements the inverse mapping of the S-Box. A selector switch can toggle between both circuits operating side-by-side to demonstrate forward and reverse substitution.



![IMG_1805_compressed](https://github.com/user-attachments/assets/0f58762e-e1a4-4288-8142-54bf3cb0cd2d)

PARTS LIST

DIP switches (for binary inputs A, B, C)

Pull-down resistors (10 kΩ)

74LS04 Hex Inverter

74LS08 Quad 2-Input AND Gate

74LS32 Quad 2-Input OR Gate

LEDs (for outputs y₂, y₁, y₀)

220 Ω resistors (for LEDs)

Jumper wires (male-to-male)

74LS86 Quad 2-Input XOR Gate 


K-Maps 

[Serpent s0.pdf](https://github.com/user-attachments/files/22971414/Serpent.s0.pdf)
