---
id: fire_solution
title: Fire Smoke Detection
desc: |
  When a fire breaks out, time is of the essence. Prompt measures need to be taken to evacuate the trapped people and contain the fire before it spreads out of hand.
architecture:
  resources:
    # ids are generated
    - id: 1
      type: waziup/mq5-gas-sensor
      steps: [2, 4]
      # rotation: 0, 90, 180 or 270
      rot: 0
      x: 225
      y: 60
      params: {}
    - id: 2
      type: waziup/buzzer
      steps: [3, 4]
      rot: 0
      x: 240
      y: 240
      params: {}
    - id: 3
      type: waziup/wazidev
      steps: [1, 2, 3, 4]
      rot: 0
      x: 540
      y: 30
      params: {}
  lines:
    - from: 1
      to: 3
      color: "#0066FF"
      # x and y are the starting point of the line
      x: 412
      y: 120
      # l is the path of the line: horiz., vertic., ...
      l: [113]
    - from: 2
      to: 3
      color: "#0066FF"
      x: 383
      y: 293
      l: [142]
---

Overview
----

When a fire breaks out, time is of the essence. Prompt measures need to be taken to evacuate the trapped people and contain the fire before it spreads out of hand. However, to accomplish this we need a system that can detect fires before it is too late.

This fully automated fire detection and alarm system is equipped with a temperature, humidity and smoke sensor.

Here's what we will be learning:
- What parts are needed
- How to wire up and read sensor values
- How to trigger an effector(buzzer)
- How to communicate to the cloud over LoRa


What parts do we need?
----

To follow this user manual, one will need the following hardware:

Hardware
  - WaziDev
  - Micro USB Cable
  - Wazigate
  - MQ5 Gas and Smoke Sensor
  - Some Jumper Wires

![Parts One](./media/firedetection.png)

Software
  - Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - Install the [WaziDev](https://github.com/Waziup/WaziDev/archive/master.zip) libraries for LoRa communication. Follow the guide [here](https://waziup.io/documentation/wazidev/user-manual/#install-the-wazidev-sketchbook)
  - Install the [Si7021](https://github.com/adafruit/Adafruit_Si7021) digital humidity and temperature sensor 
