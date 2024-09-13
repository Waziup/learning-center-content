---
id: livlab_waziup_tech_dve_unit
name: Waziup Technologies
desc: This unit introduces participants to Waziup technologies, covering the Waziup IoT platform, hardware, software, architecture, components, and APIs.
courses:
  - id: WaziDev_course
  - id: wazigate_course
  - id: wazicloud_course
  - id: waziup_api_course
---

This unit will cover the basics of Waziup technologies. 
The Waziup platform is an end-to-end solution to develop IoT prototypes.
It allows Long range communications with the LoRaWAN network, and can run your applications at the Edge.

![archi](../../../../courses/1.Fundamentals/1.Intro/img/waziup-ecosystem.png#width=700)

You should find all the components in your Solution Box. **TODO: describe Solution Box and give a link to the corresponding page.**

## The WaziDev series

WaziDev, WaziSense and WaziAct are Sensing and Actuation development board for IoT applications. They transmits data up to 7Km using LoRaWAN. It is easily programmable and customizable, using Arduino technology.

Please go through the course on **WaziDev board series** below.

You can also find the documentation for the boards in the Lab.

<alert type='success'><b>Task 1:</b> Go through all the [WaziDev](https://lab.waziup.io/resources/waziup/wazidev) tutorial and do the "Blink a LED" and "Temperature and humidity sensor" exercises.</alert>


When done, please take a picture of the device with sensor, and a screenshot showing the sensor data on a Serial Monitor; and upload it in the Drive folder.


## The WaziGate

WaziGate is an IoT LoRaWAN Gateway, ideal for all your remote IoT applications. The Gateway can cover up to 100 IoT Sensors and actuator nodes.

Please go through the course on **WaziGate** course, and also the [WaziGate documentation](https://lab.waziup.io/resources/waziup/wazigate) in the Lab.

<alert type='success'><b>Task 2:</b> Your University should have a WaziGate that has been setup. Please work with your University technical mentor so that they can setup a LoRaWAN device for you on the WaziGate and guide you on how to send LoRaWAN data from a WaziDev/WaziSense to a WaziGate.</alert>

## The WaziCloud

Please follow the **WaziCloud** course and execute all the steps.

<alert type='success'><b>Task 3:</b> Make sure that the University's WaziGate is connected to a WaziCloud account. Please take a photo of your WaziCloud dashboard showing a device and sensor values; and upload it to the Drive folder.</alert>

Optionally, you can follow the WaziCloud API course.

## End to end application

When you have done all the courses, you should be able to build your first end-to-end prototype with Waziup!

<alert type='success'><b>Task 4:</b> Measure temperature using the DHT11 sensor, and send it to the WaziCloud dashboard using a WaziGate. Please take a photo and upload it.</alert>



