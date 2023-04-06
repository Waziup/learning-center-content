---
title: Automatic Irrigation
desc: As you may already know, plants require water, light (usually sunlight), nutrients etc, ... to grow healthy.
architecture:
  resources:
    - id: 1
      type: Sensor_soilMoisture
      steps: [1]
      rot: 0
      x: 360
      y: 225
      params: {}
    - id: 2
      type: Board_WaziAct
      steps: [1, 2, 3]
      rot: 0
      x: 570
      y: 45
      params: {}
    - id: 3 
      type: Other_water_pump
      steps: [2]
      rot: 0
      x: 60
      y: 75
      params: {}
  lines:
    - from: 3
      to: 2
      color: "#99C2FF"
      # x and y are the starting point of the line
      x: 300
      y: 132
      # l is the path of the line: horiz., vertic., ...
      l: [270]
    - from: 1
      to: 2
      color: "#99C2FF"
      x: 495
      y: 307
      l: [75]
---

Overview
========

As you may already know, plants require water, light (usually sunlight), nutrients etc, ... to grow healthy. While these factors can be easily provided, the problem is usually forgetfulness.

Luckily for us, we can use smart electronic devices to automate some of the above mentioned entities required for plant growth, specifically watering.

Here's what we will be learning:
- What parts are needed
- How to wire up and read sensor values
- How to trigger an actuator
- How to use the actuator to control a water pump
- How to communicate to the cloud over LoRa


What parts do we need?
======================

To follow this user manual, one will need the following hardware:

Hardware
  - WaziAct
  - FT232 FTDI module with Mini USB Cable
  - Wazigate
  - Soil Moisture Sensor
  - Submersible Water Pump
  - Some Jumper Wires
  - Power Supply

![Parts One](./media/parts_one.png)

Software
  - Please install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - Install the [WaziDev](https://github.com/Waziup/WaziDev/archive/master.zip) libraries for LoRa communication. Follow the guide [here](https://waziup.io/documentation/wazidev/user-manual/#install-the-wazidev-sketchbook)