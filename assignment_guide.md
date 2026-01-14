# Assignment Guide

## Overview
Just as the spinal cord in a human's body handles immediate reflexes, your Pico is responsible for the low-level hardware: reading the "secrets" of your sensors and driving the actuators. 
However, the Computer (the "brain") needs to hear those stories to make high-level decisions.

Without a communication line, the "brain" is isolated from the "body". 
In this assignment, you will build that nervous system for your robot by setting up serial communication between a Pico and a computer.

- Build a circuit around the Pico to work with an LED and an SR-HC04 ultrasonic distance sensor.
- Establish physical communication paths between the Pico and the computer.
- Develope a MicroPython script on Pico to transmit data to and receive data from the computer.
- Develop a Python script on your computer to transmit data to and receive data from Pico.

## Get Started

### 1. List of Hardware:
| Item | Quantity | Description |
| :--- | :---: | :--- |
| **Computer** | 1 | Desktop/Laptop/SBC (the brain) |
| **Raspberry Pi Pico** | 1 | Microcontroller dev board (the spinal cord) |
| **HC-SR04 Module** | 1 | Ultrasonic distance sensor |
| **(Optional) LED** | 1 | 5mm LED |
| **(Optional) Resistor** | Sevral | limit current, divide voltage |
| **(Optional) Jumper Wires** | Several |  |
| **(Optional) USB Cable** | 1 | Micro-USB to USB-A (Data capable) |
| **(Optional) Breadboard** | 1 | Host the circuit |

### 2. Prepare the Software
- Python3: install it on your computer (The linux laptop and Raspberry Pi 5 came with it).
- [Thonny IDE](https://thonny.org/) or [VS Code](https://code.visualstudio.com/): Python coding environment on the computer.
- [MicroPython firmware](https://micropython.org/download/RPI_PICO2/): on Pico(2).
- [picozero](https://picozero.readthedocs.io/en/latest/) library or [`distance_sensor`](https://github.com/linzhangUCA/r1b_control/blob/main/ultrasonic_sense/distance_sensor.py) module: on Pico(2)
- [pyserial](https://pypi.org/project/pyserial/) library: on the computer.

> [!TIP]
> - [MicroPico](https://marketplace.visualstudio.com/items?itemName=paulober.pico-w-go) is a handy extension if you pick VS Code as your coding environment.
> - Be aware which device your code is running on.
For examples, if you get an error message like "_`machine`_ is not found". You may try to run a MicroPython script on your computer.
In another case, if "_`serial` is not found_" prompted, then you are very likely running a Python script on the Pico.   
> - If your Linux machine (the laptop or the RPi) refuse to talk to the Pico, try following command in the terminal then reboot.
```console
sudo usermod -aG dialout $USER
```

### 3. Plan Communication Speed
Please read the following requirements to figure out speed of the communication and plan the schedule accordingly.

## Requirements
### Circuit
Wire up the distance sensor and the LED with the Pico. 
Make sure these components are functional.

- Build the circuit around the Pico and display your wiring diagram in [README](README.md).
> [!IMPORTANT]
> The HC-SR04 module spits out 5V logic, make sure the signal out of the `ECHO` pin lowered to a safe range before the Pico can read it.

- Take a **clear** picture of your actual circuit and display it in [README](README.md).
> [!IMPORTANT]
> All the components need to match the ones in your wiring diagram.

> [!TIP]
> If wires are tangled in your mind, please review previous [slides](https://linzhanguca.github.io/robotics1-2025).

### Pico Messenger
- Send the latest detected distance to the computer at a frequency of 50Hz.
- Receive message from the computer.
- Light up the LED if and only if 9 is the command given by the computer.
Turn off the LED if and only if 0 is the command given by the computer. 

### Pico Messenger
- Send the latest detected distance to the computer at a frequency of 50Hz.
- Receive message from the computer.
- Light up the LED if and only if 9 is the command given by the computer.
Turn off the LED if and only if 0 is the command given by the computer. 

## AI Policies

Please acknowledge AI's contributions according to the policies in the syllabus.
