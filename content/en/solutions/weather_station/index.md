---
id: weather_solution
title: Weather Station
desc: |
  A weather station is a facility, either on land or sea, with instruments and equipment for measuring atmospheric conditions to provide information for weather forecasts and to study the weather and climate.
architecture:
  resources:
    - id: 1
      type: waziup/weather-station
      steps: [1, 2, 3, 4]
      rot: 0
      x: 30
      y: 15
      params: {}
    - id: 2
      type: waziup/arduino-uno
      steps: [1, 2, 3, 4]
      rot: 0
      x: 780
      y: 390
      params: {}
  lines:
    - from: 1
      to: 2
      color: "#0066FF"
      x: 548
      y: 563
      l: [273]
---

Overview
----

A weather station is a facility, either on land or sea, with instruments and equipment for measuring atmospheric conditions to provide information for weather forecasts and to study the weather and climate.

In recent years weather stations have become increasingly porpular among DIYers but the issue has always been with how to build a low-cost but functional station. In this guide, we will look at how to build a weather staion from scratch. 

We will be using The **Arduino Weather Shield** from [Sparkfun](https://learn.sparkfun.com/tutorials/arduino-weather-shield-hookup-guide-v12/all). This is an easy-to-use Arduino shield that grants you access to barometric pressure, relative humidity, luminosity, and temperature. There are also connections to optional sensors such as wind speed/direction, rain gauge, and GPS for location and super accurate timing. 

We will also use LoRa for communicating weather data to a Wazigate and then to Wazicloud.

Here's what we will be learning:
- How to read atmospheric sensor data (barometric pressure, relative humidity, luminosity, and temperature)
- How to read wind speed/direction, rain gauge, and GPS
- How to process all sensor data
- How to transmit sensor data to Wazicloud using LoRa

What parts do we need?
----

To follow this user manual, one will need the following hardware and software:

Hardware
- SparkFun Weather Shield Kit
- SparkFun Weather Meter Kit
- Arduino Uno with USB Cable
- Lora SX1276 Breakout Board
- Waziup Gateway
- Some Jumper Wires
- Power Supply

![Parts](./media/parts.png)

Things you should know about the Sparkfun Weather shield:

- It Uses the [Si7021](https://www.sparkfun.com/products/13763) sensor, [MPL3115A2 barometric pressure](https://www.sparkfun.com/products/11084?_ga=2.39980774.510170626.1666488566-160177867.1666172664) sensor, and [ALS-PT19 light](https://www.sparkfun.com/products/12566?_ga=2.39980774.510170626.1666488566-160177867.1666172664) sensor.
- Has connector for the [GP-735 compact GPS module](https://www.sparkfun.com/products/13670?_ga=2.216133586.510170626.1666488566-160177867.1666172664)
- Has optional [RJ11 connector](https://www.sparkfun.com/products/132?_ga=2.203755092.510170626.1666488566-160177867.1666172664) footprints to connect the [SparkFun weather meters](https://www.sparkfun.com/products/15901)
- Weather shield can operate from 3V to 10V and has built in voltage regulators and signal translators
- Typical humidity accuracy of ±2%
- Typical pressure accuracy of ±50Pa
- Typical temperature accuracy of ±0.3C

Software
  - Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - Install [TinyGPSPlus](https://github.com/mikalhart/TinyGPSPlus) library by **Mikal Hart**
  - Install the [WaziDev](https://github.com/Waziup/WaziDev/archive/master.zip) libraries for LoRa communication. Follow the guide [here](https://waziup.io/documentation/wazidev/user-manual/#install-the-wazidev-sketchbook)
  - Install [SparkFunMPL3115A2](https://github.com/sparkfun/MPL3115A2_Breakout/tree/master/Libraries/Arduino)library by **Sparkfun**
  - Install [SparkFun_Si7021_Breakout_Library](https://github.com/sparkfun/SparkFun_Si7021_Arduino_Library)library by **Sparkfun**
