---
id: cattle_solution
title: Cattle Rustling
desc: |
  Cattle rustlings is increasingly becoming a major problem in many parts of Africa in recent years.
  Despite the growing level of cattle theft and its consequences for society, the situation has yet to receive an effective intervention.
architecture:
  resources:
    - id: 1
      type: waziup/wazidev
      steps: [1]
      rot: 0
      x: 645
      y: 15
      params: {}
    - id: 2
      type: waziup/gps
      steps: [1, 2, 3, 4, 5]
      rot: 0
      x: 30
      y: 120
      params: {}
  lines:
    - from: 1
      to: 2
      color: "#99C2FF"
      x: 448
      y: 221
      l: [183]
---

Overview
-----
Cattle rustlings is increasingly becoming a major problem in many parts of Africa in recent years. Despite the growing level of cattle theft and its consequences for society, the situation has yet to receive an effective intervention.

In this guided article we will look at how to build a simple tracking solutions for livestock using a method known as **Geofencing**.

Here's what we will be learning:
- What Geofencing means and how it works
- What parts are needed
- How to read and process GPS data
- How to track objects with Geofencing
- How to transmit data collected using LoRa


What parts do we need?
----

To follow this user manual, one will need the following hardware:

Hardware
  - Wazidev with USB Mirco Cable
  - Neo M8/7/6 GPS Breakout Board
  - Active Ceramic GPS Antenna
  - LoRa Gateway with Internet
  - Some Jumper Wires
  - LiPo/Li-ion Battery with Holder
  
![Parts One](./media/parts_one.png)

Software
  - Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - Install [TinyGPSPlus](https://github.com/mikalhart/TinyGPSPlus) library by **Mikal Hart**
  - Install the [WaziDev](https://github.com/Waziup/WaziDev/archive/master.zip) libraries for LoRa communication. Follow the guide [here](https://waziup.io/documentation/wazidev/user-manual/#install-the-wazidev-sketchbook)
