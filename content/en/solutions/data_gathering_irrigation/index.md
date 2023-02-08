---
title: Auto Irrigation
desc: With the help of this guide you will be able to build a device to track moisture and soil temperature.
architecture:
  resources:
    - id: 1
      type: Power_Solar_Panel
      steps: [1, 2, 3, 4]
      rot: 0
      x: 85
      y: 98
      params: {}
    - id: 2
      type: Power_LiPo
      steps: [1, 2, 3, 4]
      rot: 0
      x: 585
      y: 90
      params: {}
    - id: 3
      type: Power_Solar_Panel_Regular
      steps: [1, 2, 3, 4]
      rot: 0
      x: 555
      y: 435
      params: {}
    - id: 4
      type: Board_WaziAct
      steps: [1, 2, 3, 4]
      rot: 0
      x: 915
      y: 90
      params: {}
    - id: 5
      type: Sensor_Temperature_DS18B20
      steps: [1, 2, 3, 4]
      rot: 0
      x: 1440
      y: 300
      params: {}
    - id: 6
      type: Sensor_Watermark
      steps: [1, 2, 3, 4]
      rot: 0
      x: 1605
      y: 165
      params: {}
  lines:
    - from: 1
      to: 4
      color: "#0066FF"
      x: 435
      y: 500
      l: [525]
    - from: 2
      to: 3
      color: "#0066FF"
      x: 690
      y: 355
      l: [0, 140]
    - from: 4
      to: 5
      color: "#0066FF"
      x: 1270
      y: 360
      l: [190]
    - from: 4
      to: 6
      color: "#0066FF"
      x: 1270
      y: 200
      l: [390]
---

Overview
========

With the help of this guide you will be able to build a device to track moisture and soil temperature. We use it to collect data for different purposes. [Congduc Pham](https://cpham.perso.univ-pau.fr) created similar devices for the [Intel-Irris Project](https://intel-irris.eu), they also got a [github repository](https://github.com/CongducPham/PRIMA-Intel-IrriS). In the OSIRRIS we want to create a dataset, to automate irrigation for a farm. Therefore we use a slightly different configuration to meet the requirements. 

Here's what we will be learning:
- What parts are required
- How to wire up and read sensor values
- How to connect to WaziGate
- How to communicate to the cloud over LoRa
- 

What parts are required?
======================

The following hardware and software is required in order to follow this user guide:

**Hardware:**
- Waziact Board
- Antenna
- Wires and jumpers
- Watermark Sensor (Irrometer)
- DS18B20 temperature sensor 
- 10kOhm resistor, for the Watermark
- 4.7kOhm resistor, for the DS18B20
- (OLED screen)
- Waterproof casings (minimum: IP 55)
- FTDI connector + USB cable
- Ordinary 2-way switch 
- Powering:
  1) Option:
      - 4x AA battery holder 
      - 4x 1,5V AA battery 
  2) Option:
      - MPPT solar charge controller
      - Solar panel 5V, 0,3W 
      - 3,7V LiPo battery with 2500mAh


![Parts One](./media/combined.png)


**Software:**
  - Please install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - clone this [git repository](https://github.com/Waziup/OSIRRIS) to get all the dependencies and start right away
  - Follow the guide [here](https://waziup.io/documentation/wazidev/user-manual/#install-the-wazidev-sketchbook) to setup the Arduino IDE with the projects dependencies.
