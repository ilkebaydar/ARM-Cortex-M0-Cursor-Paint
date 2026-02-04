# ARM Cortex-M0+ Cursor-Based Paint Application

This repository contains an ARM assembly program that simulates a cursor-based drawing application on a memory-mapped virtual screen. The project utilizes **SysTick Timer Interrupts** to process predefined user inputs at regular intervals.

---

## Project Overview

The application reads a sequence of 8-bit instructions from a data array and updates a virtual canvas starting at memory address `0x20001000`. The system simulates a joystick-like input device where the cursor moves and paints based on timer triggers.

### Key Features
* **Timer-Driven Logic**: Uses the SysTick timer configured for a 10 MHz clock to trigger an interrupt every **1 second**.
* **Memory-Mapped Canvas**: Draws on a **32x8 pixel** grid, where each pixel is represented in memory.
* **Instruction Decoding**:
    * **Color Change**: Commands starting with `0xA` update the brush color.
    * **Movement & Paint**: Directions (0: Up, 1: Right, 2: Down, 3: Left) with specified stroke lengths.
* **Boundary Control**: Includes logic to prevent the cursor from moving outside the canvas limits.

---

## Technical Specifications

| Feature | Details |
| :--- | :--- |
| **Architecture** | ARM Cortex-M0+ |
| **System Clock** | 10 MHz |
| **Interrupt Frequency** | 1 Hz (Reload Value: `0x0098967F`)  |
| **Canvas Base Address** |`0x20001000`  |
| **Register Constraint** | Implemented using a limited number of registers (R0-R1 focus)  |

---

## Project Structure

* **`paint_app.s`**: The core assembly source code containing the `SysTick_Handler`, `Process`, and movement subroutines.
* **`Technical_Report.pdf`**: Detailed design documentation, including reload value calculations and memory visualizations.

---

## How to Run

1. Open the project in **Keil µVision v5**.
2. Ensure the target is set to an **ARM Cortex-M0+** device.
3. Use the **Debugger** and open a **Memory Window** at address `0x20001000`.
4. Adjust the Memory Window size (32 columns) to visualize the drawing process in real-time as the timer interrupts trigger.

---

> **Academic Note**: This project was developed as part of the BLG212E Microprocessor Systems course at Istanbul Technical University (ITU).
