# ALU-v3

This is the **third version** (`alu-v3`) of the 8-bit Arithmetic Logic Unit (ALU) project.
Version 3 builds on v2’s flattened arithmetic path by modularizing the 1 bit alu again, and adding a 2:4 mux to each one, as well as an AND, OR, and XOR gate.
allowing operations—using only the existing gates plus the global `InvertA`, `InvertB`, and `Cin` control lines.

---

## Files

- `alu_8bit` - Top-level 8-bit ALU (chains eight 1-bit slices)
- `alu_1bit` - Modular 1-bit ALU slice (with adder + logic + inverter controls)
- `2to4_mux` - Modular 2 to 4 mux that takes a 2 bit opcode and picks between 4 inputs.

> Note: `alu_1bit` and `full_adder` are **not** instantiated by `alu_8bit`; they remain for documentation of the design progression.

---

## Possible Operations


```
| AND                 | bitwise A ∧ B                  | InvertA=0, InvertB=0,        OP=00   |
| OR                  | bitwise A ∨ B                  | InvertA=0, InvertB=0,        OP=01   |
| XOR                 | bitwise A ⊕ B                  | InvertA=0, InvertB=0,        OP=10   |
| NAND                | (¬A ∨ ¬B)                      | InvertA=1, InvertB=1,        OP=01   |
| NOR                 | (¬A ∧ ¬B)                      | InvertA=1, InvertB=1,        OP=10   |
| ADDITION            | A + B                          | InvertA=0, InvertB=0, Cin=0, OP=11   |
| SUBTRACTION         | A – B (two’s-complement)       | InvertA=0, InvertB=1, Cin=1, OP=11   |
| REVERSE SUBTRACTION | B – A                          | InvertA=1, InvertB=0, Cin=1, OP=11   |
| NEG                 | −(A + B)                       | InvertA=1, InvertB=1, Cin=1, OP=11   |
```
---

> All of the above are realized by appropriate settings of **InvertA**, **InvertB**, **Cin**, and selecting the correct gate output via the 2-bit opcode.

---

## Gate Resources per 1-Bit Slice

- **Adder/Subtractor** (full adder + inverter control)
- **Inverter** XOR Gate with invert input and normal input
- **AND**, **OR**, **XOR** gates
- **1 2-to-4 MUX** driven by 2 bit Opcode

---

## Next Steps for v4

- **Logical shifts & rotates** (SHL, SHR, ROL, ROR)
- **Pass-through** (MOV A, MOV B), **CLEAR**, **SET**
- **Flags** (Zero, Carry, Overflow, Parity)

---
