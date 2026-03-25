# LED Control Panel

Arduino Mega 2560 firmware project demonstrating interrupt-driven input handling, non-blocking timing, PWM output control, and state-machine-based behavior.

## Overview

This project implements an interactive LED control system using an Arduino Mega 2560, a push button, a potentiometer, and an RGB LED. The firmware is designed to demonstrate core embedded systems concepts including digital and analog I/O, hardware interrupts, PWM control, and mode-based state logic.

The system uses a push button to switch between operating modes, while a potentiometer provides real-time control over LED behavior. The firmware emphasizes deterministic input handling, non-blocking execution, and clean separation between state management and hardware behavior.

## Hardware Used

- Arduino Mega 2560
- Push button
- Potentiometer
- RGB LED
- 220Ω resistors
- Breadboard and jumper wires

## Circuit Connections

| Component | Arduino Pin |
|---|---|
| Button | Pin 2 (interrupt-capable) |
| Potentiometer | A0 |
| RGB Red Pin | 9 (PWM) |
| RGB Green Pin | 10 (PWM, unused) |
| RGB Blue Pin | 11 (PWM, unused) |

## Firmware Architecture

- Mode-based state machine for LED behavior
- Interrupt-driven mode switching
- Main loop handles analog input and LED updates
- Non-blocking timing using `millis()`
- ISR-safe communication using `volatile`

## Operating Modes

### Mode 0 – Blink Interval Control
- Potentiometer controls LED blink interval
- Interval range: 100 ms to 1000 ms
- Timing implemented using `millis()`

### Mode 1 – PWM Brightness Control
- Potentiometer maps directly to PWM duty cycle
- LED brightness adjusts continuously

### Mode 2 – Analog Output Mapping
- Potentiometer controls red channel intensity of the RGB LED
- Demonstrates analog-to-PWM mapping

## System Behavior

The firmware uses an interrupt-driven input model for mode switching, while the main loop handles analog sampling and LED updates without blocking execution.

- Button presses trigger mode changes through ISR-safe flag updates
- Potentiometer input is sampled continuously in the main loop
- LED behavior changes based on the active state
- Timing-sensitive behavior is handled without blocking delays

This structure keeps the system responsive while separating asynchronous events from deterministic application behavior.

## Key Embedded Concepts

- Interrupt-driven input handling
- ISR-safe communication using `volatile`
- Non-blocking timing with `millis()`
- Analog input processing
- PWM-based output control
- Mode-based state machine design
- Separation of hardware logic and application behavior

## Repository Structure

```text
include/   header files
lib/       reusable modules
src/       application source
test/      test scaffolding
platformio.ini
```
## Future Improvements
- Add configurable software debouncing
- Expand support for full RGB channel control
- Add threshold-based actuator behavior from sensor inputs
- Extend the mode logic into a more formal finite-state machine
