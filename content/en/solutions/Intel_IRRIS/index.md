---
id: IntelIrris_solution
title: INTEL Irris
desc: This solution is part of the INTEL Irris project
architecture:
  resources:
    - id: 1
      type: waziup/solar-panel
      steps: [1, 2, 3, 4]
      rot: 0
      x: 85
      y: 98
      params: {}
    - id: 2
      type: waziup/li-po-battery
      steps: [1, 2, 3, 4]
      rot: 0
      x: 585
      y: 90
      params: {}
    - id: 3
      type: waziup/arduino-pro-mini
      steps: [1, 2, 3, 4]
      rot: 0
      x: 555
      y: 435
      params: {}
    - id: 4
      type: waziup/ird-pcb-v4-1
      steps: [1, 2, 3, 4]
      rot: 0
      x: 915
      y: 90
      params: {}
    - id: 5
      type: waziup/digital-temperature-sensor
      steps: [1, 2, 3, 4]
      rot: 0
      x: 1440
      y: 300
      params: {}
    - id: 6
      type: waziup/watermark-sensor
      steps: [1, 2, 3, 4]
      rot: 0
      x: 1605
      y: 165
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
    - from: 4
      to: 6
      color: "#0066FF"
      x: 1311
      y: 202
      l: [291]
---


Overview
-------

According to the Food and Agriculture Organization (FAO), small-scale farming significantly contributes to food security and rural economies. However, smallholders face challenges that hinder their productivity, profitability, and economic growth, with water resources being a major constraint. Water scarcity, exacerbated by excessive use and climate change, necessitates improved irrigation methods. INTEL-IRRIS aims to provide smallholder farmers with an efficient water management system using an open, low-cost, autonomous irrigation control system based on IoT and smart technologies. This system optimizes water usage for specific crops, times, and soil conditions using predictive algorithms.
 
This solution is part of the [INTEL Irris](http://lab.staging.waziup.io/programs/gDE2tfzuq7Y) program. Altghough different versions of PCB's were developeed during the project, we will mainly focus on the most recently updated `DIY PCB: the IRD PCBA v4.1` in this program. To complete this prototype you have order this version of PCB. You can get help from this [video tutorial](https://www.youtube.com/watch?v=ueNRfBzCXiU) or this [PDF tutorial](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials/Intel-Irris-PCB-update-PCBA.pdf).

However if you want to have a look at all the developped PCB's, [click here.](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/PCBs/README.md#pcba-ird-v41)



What parts do we need?
-----

To follow this user manual and complete this solution the first thing you need to dk is gather all the required hardwares and softwares. 

Hardware
- Microcontroller
  - IRD PCB v4.1
  - Arduino ProMini, 3.3 V 8 MHz with 1 6-pin 90° and 2 12-pin male headers

- Sensors
  - DS18B20 temperature sensor for soil temperature
  - SEN0308 capacitive soil sensor
  - WM200 Irrometer Watermark water tension sensor

- Power management
  - 2-AA battery holder you can equivalently use a non rechargeable 3.6V lithium battery with a 1-AA battery holder.
  - 2 AA Alkaline heavy duty batteries 1.5 V you can equivalently use a non rechargeable 3.6V lithium battery with a 1-AA battery holder.
  - 3 AAA NiMh 1.2 V rechargeable batteries (For solar PCBA)
  - Mini solar panel 6 V 0.6 W 100 mA 60x90 mm (For solar PCBA)

- Casing:
  - ABS waterproof enclosure with screws and joint

- Antenna
  - 3 dBi 868 MHz or 3 dBi 433 MHz antenna

- Wires & Connectors
  - 15 cm chunks of 2-joint-wire for irometer tensiometer
  - Pack of minimum 5 2.54 mm male pin headers (1 3-pin, 1 2-pin)
  - Female (F) or male (M) tipped breadboard/Dupont cables For solar PCBA devices, 2 jumper junctions can be used instead of the 2 FF jumper wires.
  - Switch with pre-soldered wires
  - Waterproof cap for the switch
  - Cable gland PG7 with nylon joint
  - Flat-face seal for outer antenna junction (6x11x0.8 mm)
  - Two-paired screw terminals (dominos)

- Others
  - 1 USB Serial FTDI breakout 3.3 V (with 6-pin Female connector and an USB cable to laptop);
  - A solder station / soldering iron with thin solder wire;
  - A tiny slotted (flat) screwdriver for the screw terminal blocks;
  - A common cruciform screwdriver;
  - A drill for the plastic casing, with 7 mm and 13 mm bits for metal, and a step bit could ease
  - A flat cutter, a wire stripper/cutter, a needle-nose plier, etc


![components
](media/components.png)

Software
  - Please install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - Download the [Arduino folder](https://github.com/CongducPham/PRIMA-Intel-IrriS/tree/main/Arduino) from PRIMA-Intel-Irris