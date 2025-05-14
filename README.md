# ALU-v3

This is the **fourth version** (`alu-v4`) of the 8-bit Arithmetic Logic Unit (ALU) project.
Version 3 builds on v3 by adding functions to pass through a or b, or set the result to 0 or 1.
This then allows us to use a 4 bit opcode in order to control the alu using a lookup table for demonstration.

---

## Files

- `alu_8bit` - Top-level 8-bit ALU (chains eight 1-bit slices)
- `alu_1bit` - Modular 1-bit ALU slice (with adder + logic + inverter controls)
- `3to8_mux` - Modular 3 to 8 mux that takes a 3 bit opcode and picks between 8 inputs.

---

## Possible Operations
- OP 0 AND
- OP 1 OR
- OP 2 XOR
- OP 3 ADD
- OP 4 SUB
- OP 5 RSUB
- OP 6 NOTA
- OP 7 NOTB
- OP 8 PASSA
- OP 9 PASSB
- OP 10 CLEAR
- OP 11 SET
---

> All of the above are realized by appropriate settings of **InvertA**, **InvertB**, **Cin**, and selecting the correct gate output via the 3-bit opcode.

---

## Gate Resources per 1-Bit Slice

- **Adder/Subtractor** (full adder + inverter control)
- **Inverter** XOR Gate with invert input and normal input
- **AND**, **OR**, **XOR** gates
- **1 3-to-8 MUX** driven by 3 bit Opcode


Running: cd to the digital folder (I included here, it's source is located at https://github.com/hneemann/Digital, was used to compose this project), and run ./Digital.sh, then go to file on top left, and open the alu-v4 folder, then open alu_8bit_full.
