---
id: sensing_temperature_solution
title: Sensing Temperature with DHT11
desc: Measure the room temperature and humidity with WaziDev and DHT11.
architecture:
  resources:
    - id: 1
      type: waziup/dht22-temperature-humidity-sensor
      steps: [2]
      rot: 0
      x: 20
      y: 150
      params: {}
    - id: 2
      type: waziup/wazidev
      steps: [1, 2]
      rot: 0
      x: 380
      y: 150
      params: {}
  lines:
    - from: 1
      to: 2
      color: "#99C2FF"
      # x and y are the starting point of the line
      x: 200
      y: 220
      # l is the path of the line: horiz., vertic., ...
      l: [120]
---

In an increasingly connected world, the need for reliable and efficient environmental monitoring systems has never been greater. Whether it's for smart homes, agricultural monitoring, industrial applications, or scientific research, understanding and controlling temperature is crucial. With the advent of IoT (Internet of Things) technologies, creating cost-effective and efficient temperature sensing solutions has become accessible to hobbyists, students, and professionals alike.

Overview
------------
This guide provides a step-by-step process to build a temperature sensing solution using the WaziDev board, a Micro USB cable, and a DHT11 sensor. The WaziDev board is an open-source, low-power microcontroller designed for IoT applications. It is equipped with LoRaWAN capabilities, making it ideal for long-range wireless communication. The DHT11 sensor is a simple, digital temperature and humidity sensor that is easy to use and widely available.

Key Components
------------
Hardware

  - **WaziDev Board:** This microcontroller is the heart of this solution. It will read the temperature data from the DHT11 sensor and can be configured to send this data to a remote server using LoRaWAN technology.
  - **Micro USB Cable:** This will be used to connect the WaziDev board to a computer for programming and power.
  - **DHT11 Sensor:** A digital sensor that provides calibrated digital output for temperature and humidity.

![WaziDev board](../../resources/Boards/WaziDev/media/image9.png)
![Micro USB cable](../../resources/Boards/WaziDev/media/image8.png)
![DHT11 sensor](../../resources/Boards/WaziDev/media/image13.png)

<alert type='warning'> **N.B:** Micro USB cable must be a "data" cable. Some cable sold on the market are just for power, and they won't work for the WaziDev.</alert>

Software
  - install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - install the [WaziDev](https://github.com/Waziup/WaziDev/archive/master.zip) libraries for LoRa communication.

Solution Overview
-----------------
The goal of this project is to create a temperature sensing device that can:

  - **Read Temperature Data:** Use the DHT11 sensor to measure the ambient temperature.
  - **Process Data:** Interface the DHT11 sensor with the WaziDev board to capture the temperature data.
  - **Transmit Data:** Send the captured temperature data wirelessly to a remote server or cloud platform using the LoRaWAN capabilities of the WaziDev board.
