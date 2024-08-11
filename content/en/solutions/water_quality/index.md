---
id: waterquality_solution
title: Automatic Water quality monitoring
desc:
   Its very common to see water storage tanks overflowing in most places where a pump is used.
   These overflows lead to wastage of water and higher electricity bills due to the water pumps running longer than necessary.
architecture:
  resources:
    - id: 1
      type: waziup/waziup/total-dissolved-solids-sensor
      steps: [1, 2, 3, 4]
      rot: 0
      x: 20
      y: 80
      params: {}
    - id: 2
      type: waziup/digital-temperature-sensor
      steps: [1, 2, 3, 4]
      rot: 0
      x: 300
      y: 200
      params: {}
    - id: 3
      type: waziup/oled-display
      steps: [1, 2, 3, 4]
      rot: 0
      x: 500
      y: 435
      params: {}
    - id: 4
      type: waziup/wazidev
      steps: [1, 2, 3, 4]
      rot: 0
      x: 500
      y: 75
      params: {}
  lines:
    - from: 1
      to: 3
      color: "#0066FF"
      x: 491
      y: 513
      l: [67]
    - from: 3
      to: 4
      color: "#0066FF"
      x: 841
      y: 513
      l: [69]
    - from: 2
      to: 3
      color: "#0066FF"
      x: 690
      y: 387
      l: [0, 43]
    - from: 4
      to: 5
      color: "#0066FF"
      x: 1311
      y: 355
      l: [116]
---

Overview
----

It is not rare to find dissolved solids in the water. The materials that constitute dissolved solids in water include materials such as minerals, salts, anionic and cationic substances. They can also include pollutants such as heavy metals, and other substances such as organic materials that may have leaked into the water supply system and reduce the purity of water which isn't visible to the open eyes.

With the help of our advanced technology we can now monitor the quality of water.



In this guide, we will look at how to monitor water quality through interfacing Gravity Analog TDS Sensor with WaziDev and read the value in an OLED Display. Since TDS Value depends upon the temperature. So we will also add DS18B20 Waterproof Temperature Sensor to measure Water Temperature. 


Here's what we will be learning:
- What parts are needed
- How to wire up and read sensor values
- How to communicate to the cloud over LoRa

What parts do we need?
----

To follow this user manual, one will need the following:

Hardware
  - WaziDev
  - Mini USB Cable
  - DS18B20 Temperature Sensor
  - TDS Sensor
  - Resistor 4.7k
  - OLED display
  - Some Jumper Wires
  - wazigate
  - 2 Lora 868Mhz Antenna
  - Battery and Battery holder



Software
  - Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - Install the [WaziDev](https://github.com/Waziup/WaziDev/archive/master.zip) libraries for LoRa communication. Follow the guide [here](https://waziup.io/documentation/wazidev/user-manual/#install-the-wazidev-sketchbook)
