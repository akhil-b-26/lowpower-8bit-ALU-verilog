# Low Power 8-bit ALU with Clock Gating and Operand Isolation

## Overview

This project implements an 8-bit Arithmetic Logic Unit (ALU) in Verilog, designed with low-power techniques suitable for modern digital systems. The ALU supports a complete set of arithmetic, logical, shift, and rotate operations, controlled via a 4-bit operation selector.

To reduce dynamic power consumption, the design includes:

- **Clock Gating**: Disables the output register’s clock when the ALU is not enabled.
- **Operand Isolation**: Prevents unnecessary switching on unused operands during single-operand operations (e.g., NOT, INC, DEC).

The design is fully synthesizable and was developed and verified using **Xilinx Vivado WebPACK**. A simulation testbench demonstrates the functional correctness of all operations and the effectiveness of the low-power mechanisms.

---

## Features

- **Supported Operations (via 4-bit `op` input):**
  - `0000` → ADD
  - `0001` → SUB
  - `0010` → AND
  - `0011` → OR
  - `0100` → XOR
  - `0101` → NOT
  - `0110` → INC
  - `0111` → DEC
  - `1000` → SHL (Shift Left Logical)
  - `1001` → SHR (Shift Right Logical)
  - `1010` → ROL (Rotate Left)
  - `1011` → ROR (Rotate Right)

- **Power Optimization Techniques:**
  - Clock gating of output register
  - Operand isolation for one-operand instructions

- **Clean modular structure** using reusable Verilog components

---

## Files

| File              | Description                                      |
|-------------------|--------------------------------------------------|
| `alu.v`           | Main ALU module with operation logic and output register |
| `clock_gating.v`  | Clock gating logic using `clk & en`             |
| `testbench.v`     | Verifies all operations and clock gating behavior |
| `alu_wave.vcd`    | Waveform dump for viewing in Vivado or GTKWave  |
| `waveform.png`    | Screenshot of simulation waveform showing ALU behavior and clock gating |

---

## Tools Used

- **Xilinx Vivado WebPACK** (Design, Synthesis, Simulation)
- Icarus Verilog + GTKWave (for open-source simulation)

---

## How to Simulate (Vivado Users)

1. Create a new project in Vivado.
2. Add `alu.v`, `clock_gating.v`, and `testbench.v`.
3. Run behavioral simulation to view output waveforms.
4. Use **Simulation > Run Simulation > Run Behavioral Simulation** to generate and inspect signal transitions.

---

## Waveforms

Below is a waveform captured from the simulation demonstrating the clock gating behavior and ALU outputs during various operations:

![ALU Waveform](waveform.png)

---

## License

This project is licensed under the [MIT License](LICENSE).

---

Feel free to fork or contribute.
