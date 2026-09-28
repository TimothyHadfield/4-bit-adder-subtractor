# 4-Bit Binary Adder / Subtractor

A 4-bit adder and a 4-bit **two's-complement subtractor**, each designed and simulated in NI Multisim and then built and tested on a breadboard with TTL logic chips. Lab 2 of ECE 2705 (Digital Design I Lab) at Utah Valley University, Fall 2026.

![The finished circuit on the breadboard, with the output LEDs lit](docs/photos/hero.jpg)

## How it works

- **Inputs:** an 8-position DIP switch sets two 4-bit numbers, A3–A0 and B3–B0. Each switch line has a 1 kΩ pull-down resistor, so an open switch reads as a clean 0.
- **Math:** a **74LS83** 4-bit full-adder chip adds A + B + carry-in and outputs a 4-bit sum (S3–S0) and a carry-out (Cout).
- **Outputs:** five LEDs (Cout, S3–S0) show the result in binary. Each LED is driven by a **74LS04** inverter through a 330 Ω current-limiting resistor.
- **Power:** +5 V DC bench supply.

**Adding:** the carry-in is tied to 0, so the chip computes A + B. Example: 1100 + 0011 = 0 1111.

**Subtracting (two's complement):** to compute A − B, the circuit adds A to the two's complement of B:
1. **Invert every bit of B** with 74LS04 inverters.
2. **Set the carry-in to 1**, which adds the extra +1.
3. **Ignore the carry-out.**

Example: 1001 − 0111 → 1001 + 1000 + 1 = 1 0010 → the answer is **0010** (9 − 7 = 2).

## Multisim design

| 4-bit adder | 4-bit subtractor |
|---|---|
| ![Multisim schematic of the 4-bit adder](docs/multisim/adder-1.png) | ![Multisim schematic of the 4-bit subtractor, with inverters on the B inputs](docs/multisim/subtractor-1.png) |

Each circuit was simulated with several different switch settings:

| Adder tests | | | |
|---|---|---|---|
| ![Adder simulation 1](docs/multisim/adder-1.png) | ![Adder simulation 2](docs/multisim/adder-2.png) | ![Adder simulation 3](docs/multisim/adder-3.png) | ![Adder simulation 4](docs/multisim/adder-4.png) |

| Subtractor tests | | |
|---|---|---|
| ![Subtractor simulation 1](docs/multisim/subtractor-1.png) | ![Subtractor simulation 2](docs/multisim/subtractor-2.png) | ![Subtractor simulation 3](docs/multisim/subtractor-3.png) |

## Breadboard build

| | |
|---|---|
| ![Breadboard from the side](docs/photos/breadboard-8462.jpg) | ![Breadboard wiring close-up](docs/photos/breadboard-8468.jpg) |
| ![Breadboard with outputs lit](docs/photos/breadboard-8480.jpg) | ![Breadboard with a different output](docs/photos/breadboard-8481.jpg) |

<details>
<summary>More test photos</summary>

| | | |
|---|---|---|
| ![](docs/photos/breadboard-8464.jpg) | ![](docs/photos/breadboard-8467.jpg) | ![](docs/photos/breadboard-8476.jpg) |
| ![](docs/photos/breadboard-8478.jpg) | ![](docs/photos/breadboard-8479.jpg) | |

</details>

## Parts

| Part | Job |
|---|---|
| 74LS83 | 4-bit binary full adder |
| 74LS04 | Hex inverter: inverts B for subtraction and drives the LEDs |
| 8-position DIP switch | Sets the A and B inputs |
| 1 kΩ resistors | Pull-downs on the switch inputs |
| 330 Ω resistors + 5 LEDs | Show Cout and S3–S0 |
| Breadboard, +5 V supply, multimeter | Build and test |

## Credits

The lab handout for ECE 2705 at UVU gave the adder's reference schematic and the two's-complement method. I built both circuits in Multisim, designed the subtractor's changes to the adder, and wired and tested both on the breadboard.

---
By [Timothy Hadfield](https://github.com/TimothyHadfield), Electrical Engineering @ UVU
