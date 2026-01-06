# Interactive LED Control Panel

## Overview

The **Interactive LED Control Panel** is an embedded firmware project built on the Arduino Mega 2560 that demonstrates core microcontroller concepts including digital and analog I/O, PWM, interrupts, non-blocking timing, and state-based control logic.

The system uses a push button (interrupt-driven) to switch between operating modes, while a potentiometer provides continuous analog control over LED behavior. This project focuses on deterministic input handling and responsive firmware design.

## Hardware Used

| Component            | Description                       |
| -------------------- | --------------------------------- |
| Arduino Mega 2560    | Main microcontroller              |
| Push button          | Mode switching (interrupt-driven) |
| Potentiometer        | Analog input control              |
| RGB LED              | Output device (red channel used)  |
| 220Ω resistors       | LED current limiting              |
| Breadboard & jumpers | Prototyping setup                 |


## Circuit Connections

| Component    | Arduino Pin |
|--------------|-------------|
| Button       | Pin 2 (interrupt-capable) |
| Potentiometer | A0          |
| RGB Red      | Pin 9 (PWM)      |
| RGB Green    | Pin 10 (PWM, unused) |
| RGB Blue     | Pin 11 (PWM, unused) |

## Firmware Architecture

* Structured around a mode-based state machine
* Each mode defines a distinct LED behavior
* A hardware interrupt is used to switch between modes
* Ensures immediate responsiveness without blocking the main execution loop

## Operating Modes

### Mode 0 - Blink Control

* Potentiometer controls LED blink interval
* Interval range: 100 ms – 1000 ms
* Timing implemented using millis() (non-blocking)

### Mode 1 - Blink Control

* Potentiometer maps directly to PWM duty cycle
* LED brightness adjusted smoothly via hardware PWM

### Mode 2 - Blink Control

* Potentiometer controls red channel intensity of RGB LED
* Demonstrates analog-to-PWM mapping fgor output control


## Key Concepts

* Interrupt-driven input handling
* Non-blocking timing using millis()
* Analog-to-digital input processing
* PWM-based output control
* State-based firmware design
* Safe ISR communication using volatile
