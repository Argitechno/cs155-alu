# ALU-v2

This is the **second version** (`alu-v2`) of the 8-bit Arithmetic Logic Unit (ALU) project,
focused entirely on minimizing **total gate count** while maintaining correct functionality.
Unlike `alu-v1`, this version eliminates modular layers in favor of **fully flattened** logic.

## Overview

- **Focus:** Gate count minimization
- **Design:** Flattened logic only (no submodules)
- **Subtraction:** Performed via two’s complement
- All expressions built using primitive logic gates: AND, OR, XOR

## Files

- `alu_8bit` – Final 8-bit ALU with minimal gate count
- `alu_1bit` – Optimized 1-bit ALU logic (for reference)
- `full_adder` – Flattened full adder logic (for reference)

> `alu_1bit` and `full_adder` are retained to show progression and are not used in `alu_8bit`.
> `alu_1bit` in particular is different, as the not and MUX was removed in favor of a XOR gate for simplified logic.

## Supported Operations

- **Addition:** `A + B`
- **Subtraction:** `A - B`, using:
  - `B xor Sub` for bitwise inversion when `Sub = 1`
  - `Cin` to add 1 for two’s complement

## Gate Usage Summary (8-bit ALU)

| Gate | Inputs | Total Used |
|------|--------|------------|
| AND  | 2      | 16         |
| OR   | 2      | 8          |
| XOR  | 2      | 24         |

## Testing

- All 16 input combinations for the 1-bit ALU verified
- Addition and subtraction confirmed correct across all 8 bits
- Carry propagation verified

## Goals for v3

- Add **logical operations**: AND, OR, XOR, NOT
- Add **operation selector** input
- Reintroduce **modularity** only if it does **not increase gate count**
