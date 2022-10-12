![Cattle with Tag](./media/cattle.jpg)

Overview
========
Cattle rustlings is increasingly becoming a major problem in many parts of Africa in recent years. Despite the growing level of cattle theft and its consequences for society, the situation has yet to receive an effective intervention.

In this guided article we will look at how to build a simple tracking solutions for livestock using a method known as **Geofencing**.

Here's what we will be learning:
- What Geofencing means and how it works
- What parts are needed
- How to read and process GPS data
- How to track objects with Geofencing
- How to transmit data collected using LoRa

What parts do we need?
=====================

To follow this user manual, one will need the following hardware:

Hardware
  - Wazidev with USB Mirco Cable
  - Neo 6/7M GPS Breakout Board
  - Active Ceramic GPS Antenna
  - LoRa Gateway with Internet
  - Some Jumper Wires
  - LiPo/Li-ion Battery with Holder
  
![Parts One](./media/parts_one.png)

Software
  - Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - Install [TinyGPSPlus](https://github.com/mikalhart/TinyGPSPlus) library by **Mikal Hart**
  - Install the [WaziDev](https://github.com/Waziup/WaziDev/archive/master.zip) libraries for LoRa communication. Follow the guide [here](https://waziup.io/documentation/wazidev/user-manual/#install-the-wazidev-sketchbook)

**Step \#1:** Installing TinyGPS Plus Library
=============================================
Under the **Sketch** menu in the Arduino IDE, locate **Include Libraries** and navigate to **Manage Libraries..** and click to open the libraries manager.

![Installing TinyGPSPlus](./media/lib1.png)

Search for **"tinygpsplus"** in the search box and install the version by **Mikal Hart** as shown below

![Install TinyGPSPlus](./media/lib2.png)

After installing we should see the label <span style="color: #00979C;">INSTALLED</span> **INSTALLED** as shown below.

![Install TinyGPSPlus](./media/lib3.png)

We can now close the library manager.

**Step \#2:** Reading and Processing GPS Coordinates
====================================================

**Step \#3:** Tracking Using Geofencing
===============================================

**Step \#4:** Transmitting Data of LoRa 
===================================

**Step \#5:** Final Touches
===========================