---
id: micropython_course
title: "Micropython"
description: "Micropython is an implementation of Python 3 for embedded systems and microcontrollers"
difficulty: advanced
duration: 3h
---

# Overview
Are you interested with learning IoT, and building connected devices? If so, you're in luck Micropython can help you build all these fun stuff and a lot more. In this course you will learn:
- Differences between MicroPython and other programming languages
- Advantages
- Basics of Micropython
- GPIO Programming with Micropython
- Micropython use cases

# What is Micropython

Python has been growing its popularity in the developer community, being used from DevOps, statistical analysis and also desktop services. With the need to elevate python use to be used in microcontrollers, the MicroPython language was introduced.

Therefore, MicroPython is an efficient implementation of Python 3, but specifically used in embedded systems and microcontrollers. MicroPython brings simplicity into Python programming to resource-constrained devices. For this reason, MicroPython becomes and fit language to be used in IoT, Robotics and other embedded systems.

**MicroPython features** 
- **Lightweight and compact** <br>
    - Micropython is  designed to run on microcontrollers with limited resources, therefore, providing minimal and powerful subset of Python
- **Compatibility** <br>
    - Micropython is compatible with the syntax used in Python3. Developers with existing skills in Python3 can leverage the skills to program microcontrollers.
- **Cross platform support** <br>
    - Micropython can be used to program a varieties of microcontrollers like ESP32, ESP8266, STM32, Raspberry pi Pico among others. This feature offers reusability of code with minimal modification when transitioning between different microcontrollers.
- **Extensivity** <br>
    - This feature allows libraries to be used to intergrate platform-oriented functionalities offering flexibility to the language

**How is MicroPython different from standard Python?**
The two languages share the same syntax but differ in their implementation, use cases anf the target platforms. The notable difference are:
- **Target audience & platform** <br>
    - Micropython is essentially designed for microcontrollers and other resource contrained devices, while python (CPython) designed for large memory footprint with abundant resources
- **Execution environment** <br>
    - Micropython runs on bare metal or its the microcontroller's OS, while python runs on top of other OS like Windows, macOS and abstracts the hardware details
- **Interactive development** <br>
    - Micropython emphasizes on Read-Eval-Print-Loop (REPL) in development. This feature offers developers with ability to rest code interactively. CPython offers the interactive feature, but emphasis on this is used in writing scripts.

# Basics of Micropython

**Installation**

To get started with Micropython, you will need a microcontroller boad. Most common microcontrollers are, ESP32, ESP8266, STM32, Raspberry pi Pico.

Micropython supports REPL which allows you to enter python commands directly. This is a great tool to test small code snippets and experiment. You can access REPL through the serial connection in your microcontroller or by using applications like [PuTTY]() or [Thonny]()

**Hello world with Micropython**
All micropython scripts end with .py extension just like in standard python. An example of filename can be _hello.py_
Create a file named **hello.py**. In the script, add the print function which will output/display text
```
print("Hello world")
```
Run the code, and it should output _Hello world_ from the serial monitor.

**Varables and data types**

Micropython supports common data types, like in standard python:
- Integers: ```delay_seconds = 5```
- Floats: ```temperature = 17.1```
- Strings: ```led_status = "ON"```
- Lists ```my_boards = ['STM32','ESP8266','ESP32']```
- Tuple ```board_elements = ('Actuators','Sensors','LEDs')```
- Dictionary ```sensor_data = {'temperature':23.1, 'timestamp':'23:44:00PM'}```

**Control flow**
Micropython supports control flow statements like:
- if
- else
- elif
- while
- for
```
if x > 0:
    print("Positive number")
else:
    print("Non-positive number")
```

**Functions**
Functions in micropython are defined using the `def` keyword. For instance, the function below takes an argument of LED status and prints it as output.

```
def print_led_status(status):
    print(f"led is {status}") // output: led is ON

led_status = 'ON'
print_led_status(led_status)
```

# GPIO Programming with micropython
Required hardware

1. LED x1
2. Resistor x1 (1k)
3. Microcontroller
4. Jumper cables

Youl will learn how to blink an LED using micropython. This will give you an understanding on how to interact with General-Purpose Input/Output (GPIO) to control other external devices like LEDs.
```
from machine import Pin
import time

led = Pin(2, Pin.OUT)  # GPIO Pin 2 as an output
led.value(1)           # Turn on the LED
time.sleep(1)          # Pause for 1 second
led.value(0)           # Turn off the LED

```

# Micropython use cases

1. **Devices for the Internet of Things (IoT)**

Micropython is a great option for creating networked and intelligent devices because to its ease of use and interoperability with a wide range of microcontroller platforms.

2. **Learning and Education**

Because of its ease of use and Python syntax, MicroPython is well-liked in educational environments. It offers learners and novices an approachable starting place for learning hardware interface and programming.

3. **Robotics and Embedded Systems**

MicroPython's lightweight design makes it a good choice for robotic application and embedded system programming. It makes it simple for developers to manage and control physical components.

4. **Smart Home**

Home automation projects that utilize microcontrollers to operate lights, sensors, and other smart devices in the home environment use MicroPython.

5. **Industrial automation**

MicroPython is a versatile and accessible scripting language that may be used in industrial settings for automation and control systems. It is useful for managing machinery and processes.





































