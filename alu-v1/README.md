# ALU-v1

This project contains the first version (`alu-v1`) of an 8-bit Arithmetic Logic Unit (ALU) built from the ground up using basic logic gate constructs.
This design prioritizes clarity and modularity, with each logic gate, mux, and adder constructed manually.

## Design Overview

The core of the ALU is a custom-built 1-bit ALU module that performs both addition and subtraction.
It is scaled up to 8 bits by chaining the 1-bit units together,
with carry propagation from least significant bit (LSB) to most significant bit (MSB).

### Operations Implemented:
- **Addition** (`A + B`)
- **Subtraction** (`A - B`)

### 1-Bit ALU Components:
- **NOT gate**
- **2-to-1 MUX**
- **Full Adder**

### 2-to-1 MUX Components:
- **1 * NOT**
- **1 * AND**
- **1 * OR**

### Full Adder Components
- **2 * Half Adder**
- **1 * AND Gate**

### Half Adder Components
- **1 * XOR**
- **1 * AND**

### Subtraction Method:
Subtraction is implemented via two's complement:
- The second operand `B` is inverted (`~B`) and a `1` is added if `Cin = 1`.
- This is controlled via a `Sub` input line.
- B is conditionally inverted using a MUX.

## Files

Each component is defined in a separate file for clarity and modular testing:
- `mux` – 2-to-1 multiplexer
- `half_adder` – Half adder module
- `full_adder` – Full adder module using two half adders
- `alu_1bit` – 1-bit ALU combining the above elements
- `alu_8bit` – 8-bit ALU built from 1-bit ALUs

## Status

- Addition: Verified correct
- Subtraction: Verified correct
- Carry propagation: Verified across all 8 bits

## Next Steps

- Optimize the 1-bit ALU to reduce total gate count.
- Add Logical operations (AND/OR/XOR/NOT)
- Add flags for status monitoring.
- Add Clock integration


---
