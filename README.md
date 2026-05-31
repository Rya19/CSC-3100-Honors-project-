# CSC-3100-Honors-project-
# Booth's Algorithm Logic Circuit

This project is a computer architecture honors project that implements a partially working version of Booth's Multiplication Algorithm using digital logic components in Logicly.

The goal of the project was to understand how signed binary multiplication can be represented at the hardware level using registers, multiplexers, shifters, add/subtract logic, and control signals.

## Overview

Booth's Algorithm is a multiplication algorithm used for signed binary numbers in two's complement form. Instead of performing repeated addition for every `1` bit in the multiplier, Booth's Algorithm looks at pairs of bits to decide whether to add, subtract, or simply shift.

This makes it useful for multiplying signed numbers efficiently in computer architecture.

## How Booth's Algorithm Works

Booth's Algorithm uses:

- A multiplicand
- A multiplier
- An accumulator/product register
- An extra bit often called the Booth bit or `Q-1`

At each step, the algorithm checks the current least significant bit of the multiplier and the Booth bit:

```text
00 -> No operation
01 -> Add the multiplicand
10 -> Subtract the multiplicand
11 -> No operation
```

After the add/subtract decision, the combined registers are shifted right. This process repeats for the number of bits being multiplied.

At the end, the combined register values represent the final signed product.

## Circuit Implementation

This project was built in Logicly using digital logic components to represent parts of Booth's Algorithm at the circuit level.

The design includes:

- Input switches for binary values
- Multiplexers for selecting between operation paths
- Two's complement logic for subtraction
- ALU/addition logic for arithmetic operations
- Parallel-in serial-out shift registers
- A 1-bit register for the Booth bit
- D flip-flops for stored state
- Clock, reset, read, write, and shift controls
- Output lamps to display register values and circuit state
- Logic gates for control signal routing

## Major Components

### Multiplexer

The multiplexer is used to choose which value should be passed into the arithmetic circuit. In Booth's Algorithm, this is important because the circuit must decide whether to use the original value, its two's complement, or no arithmetic operation.

### Two's Complement Logic

Two's complement is used to represent negative binary numbers. This allows the circuit to perform subtraction by adding the two's complement version of a value.

### ALU / Multi-Bit Adder

The arithmetic portion of the circuit performs the add/subtract operation required by Booth's Algorithm. Depending on the control signal, the circuit can add the selected value into the product/accumulator path.

### PISO Shift Registers

Parallel-in serial-out shift registers are used to load multiple bits at once and then shift them one bit at a time. This supports the shifting step that happens after each Booth Algorithm cycle.

### Booth Bit Register

A 1-bit register stores the previous least significant bit of the multiplier. This bit is compared with the current least significant bit to determine whether the circuit should add, subtract, or do nothing.

### Control Signals

The circuit includes manual controls for:

- Read
- Write
- Clock
- Reset
- Shift/load toggle

These controls allow the circuit to be stepped through manually while observing the behavior of the registers and outputs.

## Screenshots

### Shift Register / PISO Design

<img width="1212" height="663" alt="Screenshot 2026-05-28 at 2 23 25 PM" src="https://github.com/user-attachments/assets/2cfc0bf8-473c-4c3c-b15a-1e048f88a584" />


### Booth's Algorithm Circuit

<img width="675" height="715" alt="Screenshot 2026-05-28 at 2 23 47 PM" src="https://github.com/user-attachments/assets/915b258d-7ab4-4182-89d8-dfc9ffba0361" />


## Files

```text
HONORS.logicly                 # Logicly circuit file
Comp Architecturehonors.pdf    # Project notes and Booth's Algorithm planning
images/                        # Screenshots of the circuit design
```

## Skills Demonstrated

- Computer architecture fundamentals
- Signed binary multiplication
- Two's complement arithmetic
- Digital logic design
- Register-level circuit design
- Multiplexer-based control flow
- Shift register behavior
- Manual clock/control signal testing
- Translating an algorithm into hardware logic

## Project Status

This is a partially working hardware-level simulation of Booth's Algorithm. The project focuses on demonstrating the main components and control flow needed for Booth multiplication rather than building a fully optimized processor-level implementation.

## Future Improvements

- Fully automate the control sequence
- Add clearer labels for each register and control path
- Expand support for larger bit-width multiplication
- Improve circuit layout and wire organization
- Add a timing diagram for each Booth cycle
- Add a table showing each algorithm step for a sample multiplication problem

## Author

Created as a computer architecture honors project focused on Booth's Algorithm, signed binary multiplication, and digital logic circuit design.
