---
id: wazigate_course
title: WaziGate
description: The second course will take us through the WaziGate parts and features.
difficulty: beginner
duration: 4h
---

WaziGate Overview
================

<!-- Let's start this lesson on the WaziGate with a tour of its parts and features. -->

<youtube>QCZssYIdKss</youtube>

WaziGate is a IoT LoRa Gateway, ideal for all your remote IoT applications. The Gateway can cover up to 100 IoT Sensors and actuator nodes using LoRa radio network: Weather stations, soil monitoring, GPS applications... The possibilities are endless! The Gateway can also control your actuators, such as electro-valves. You can host your own applications directly in the gateway, and connect to it through WiFi. The gateway can easily work without Internet connectivity and still provides data to end-users through its embedded database and web-based visualization module.

### Resources
- download [Gateway ISO Image](https://downloads.waziup.io/)
- download [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
- browse [Raspberry Pi 5](http://lab.waziup.io/resources/waziup/raspberry-pi)
- browse [WaziHat Pro Signle](http://lab.waziup.io/resources/waziup/wazihat-pro-single)


OS Installation
===============
From here and onward you will be guided through the steps to assemble your Wazigate and configure it in order to connect to the Waziup Cloud. 

<youtube>NUv9xwDRtUc</youtube>

## What do you need to start?
- Raspberry Pi
- SD card (minimum 8 GB)
- Gateway ISO Image (link provided in resource section)
- Raspberry Pi Imager (link provided in resource section)

## Assemble the WaziGate
There are only two simple steps to assemble your WaziGate:

**Step #1:** Attach the heat sinks.
![heat sink](img/heat-sink.png)


**Step #2:** Mount a WaziHat on the Raspberry PI.
![heat sink](img/wazihat-mount.png)


## Installation

Nice! Now that you have all the required resources you are ready to go. First, start with flashing the WaziGate as shown in the video tutorial earlier.

<alert severity='warning'>Your Micro SD card must be at least <b>8 GB</b> but <b>16 GB</b> is better.</alert>  


### Resources
- download [Gateway ISO Image](https://downloads.waziup.io/)
- download [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
          

Connect to the WaziGate
=======================

Once the WaziGate OS is installed, we need to connect to it. The following tutorial demonstrates the whole process.

<youtube>ZsFFwagjE5E</youtube>

### Resources
- download [Advance IP Scanner](https://www.advanced-ip-scanner.com/)
- browse [WaziGate](http://lab.waziup.io/resources/waziup/wazigate)


UI Overview
===========

Congratulations! You have it running! 

In this part you will get to know about WaziGate UI and its features.

<youtube>SAwH-iR18hc</youtube>

<alert severity='info'> Soon we will launch a newer version of WaziGate UI with some killer features. stay connected for update!</alert>

### Resources
- browse [WaziGate](http://lab.waziup.io/resources/waziup/wazigate)

Configuring Internet
====================

<youtube>aucdo0knjh4</youtube>

Let's now configure the internet on your WaziGate following two steps:

**Step # 1:** Select menu Settings/Wifi.

Once Wazigate found all the available WiFi networks in range, click on the network that you want to connect to.

**Step #2:** Enter the password for that network and click on "connect".

<alert severity='warning'> <li>Once you setup your WaziGate to connect to a WiFi network, you will lose the Hotspot connection.</li>
<li>**Note:** If Wazigate does not manage to connect to your WiFi due to wrong credentials or not being in the range of the WiFi router, it will rollback to the hotspot mode and you need to connect to it again and start over. This might take a few minutes depending on the router.</li>
</alert>

Configuring the Gateway
======================

<youtube>YeDg1wnJhQY</youtube>

### Resources
- browse [Waziup Dashboard](https://dashboard.waziup.io)
- browse [WaziGate](http://lab.waziup.io/resources/waziup/wazigate)

Let's now configure the rest of your WaziGate.

Waziup account enables you to receive all your sensor data in your dashboard and manage your Wazigate remotely. If you do not have an account on [Waziup dashboard](https://login.waziup.io/auth/realms/waziup/protocol/openid-connect/auth?client_id=dashboard&redirect_uri=https%3A%2F%2Fdashboard.waziup.io%2F&state=7c9547dd-c0bf-4b2a-8642-bdc13a3949a3&response_mode=fragment&response_type=code&scope=openid&nonce=1a520f4b-4814-4607-8472-aaeba34f5b6b), you need to create one first. Then follow the steps:

**Step #1:** Clik on the Sync menu. 
**Step #2:** Enter you Cloud Username and Password and click Save.
<alert severity='warning'> You need to enter your CLOUD login/password, collected on https://dashboard.waziup.io/. Do not enter your gateway password here.</alert>
**Step #3:** Flip the Active Sync ON.

LoRaWAN Sensing and Actuating
=============================

Congratulations on reaching this point! Now, it's time to dive into the exciting world of LoRaWAN sensing and actuating — the real deal awaits you!

<youtube>G_cQ_UaOvq4</youtube>

### Resources
- browse [WaziDev](http://lab.waziup.io/resources/waziup/wazidev)
- browse [WaziAct](http://lab.waziup.io/resources/waziup/waziact)
- browse [WaziSense](http://lab.waziup.io/resources/waziup/wazisense)