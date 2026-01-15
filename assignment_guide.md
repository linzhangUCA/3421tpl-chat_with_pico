# Assignment Guide

## 1. Overview
Just as the spinal cord in a human's body handles immediate reflexes, your Pico is responsible for the low-level hardware: reading the "secrets" of your sensors and driving the actuators. 
However, the Computer (the "brain") needs to hear those stories to make high-level decisions.

Without a communication line, the "brain" is isolated from the "body". 
In this assignment, you will build that nervous system for your robot by setting up serial communication between a Pico and a computer.

- Build a circuit around the Pico to work with an LED and an SR-HC04 ultrasonic distance sensor.
- Establish physical communication paths between the Pico and the computer.
- Develope a MicroPython script on Pico to transmit data to and receive data from the computer.
- Develop a Python script on your computer to transmit data to and receive data from Pico.

## Get Started

### 1.1. List of Hardware:
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

### 1.2. Prepare the Software
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

### 1.3. Plan Communication Speed
Please read the following requirements to figure out speed of the communication and plan the schedule accordingly.


## 2. Requirements
### 2.1. Circuit
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


### 2.2. Pico Messenger
- Send the latest detected distance to the computer at the frequency of 50Hz.
Please round the distance value to 4 decimal places.
- Receive message from the computer the USB line is occupied (should be receiving a message every 5 seconds).
  - Light up the LED if and only if "on" is the message.
  - Turn off the LED if and only if "off" is the message. 

> [!TIP]
> You may want to save the MicroPython script as `main.py` or the Python shell in Thonny will take over the serial line and prevent your Python script chatting with Pico.


### 2.3. Computer Messenger
- Send LED control message at the frequency of 5Hz.
Toggle the state of the LED in each outgoing message.
  - Print outgoing message with time stamp (keep 2 decimals in seconds) for debugging.
- Receive message from Pico whenever the USB line is not empty (should be receiving a message every 20 milliseconds).
  - Print each received message with the time stamp (keep 2 decimals in seconds).

> [!TIP]
> Plug in the `main.py` loaded Pico, then execute the Python script.


### 2.4. Data Transfer Limit
Let's assume the serial data transfer baudrate is set to your Bear ID number.
What would be the fastest rate/frequency you can use to repeatedly send the message below?

```text
I ♥️ UCA! Go Bears!
```

> [!NOTE]
> Please document your reasoning and calculation in [README](README.md).


## AI Policies

Please acknowledge AI's contributions according to the policies in the syllabus.
