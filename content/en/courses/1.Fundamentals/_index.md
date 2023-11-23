---
id: intro_iot_mod
title: Introduction to IoT
description: The main fundamentals of IoT
---


Introduction to IoT
===================

The Internet of things (IoT) is a system of interrelated computing devices, mechanical and digital machines provided with unique identifiers (UIDs) and the ability to transfer data over a network without requiring human-to-human or human-to-computer interaction.

The definition of the Internet of things has evolved due to the convergence of multiple technologies, real-time analytics, machine learning, commodity sensors, and embedded systems. Traditional fields of embedded systems, wireless sensor networks, control systems, automation (including home and building automation), and others all contribute to enabling the Internet of things. In the consumer market, IoT technology is most synonymous with products pertaining to the concept of the "smart home", including devices and appliances (such as lighting fixtures, thermostats, home security systems and cameras, and other home appliances) that support one or more common ecosystems, and can be controlled via devices associated with that ecosystem, such as smartphones and smart speakers.

IoT system architecture, in its simplistic view, consists of three parts:

- Device
- Edge Gateway
- Cloud

Devices include networked things, such as the sensors and actuators found in IIoT equipment,The Edge Gateway consists of sensor data aggregation systems that provide functionality, such as pre-processing of the data, securing connectivity to cloud, using systems such as WebSockets, the event hub, and, even in some cases, edge analytics or fog computing.The final part includes the cloud application built for IIoT using the microservices architecture it also includes various database systems that store sensor data, such as time series databases or asset stores using backend data storage systems.


<youtube>LlhmzVL5bm8</youtube>



<!-- {{< youtube id="LlhmzVL5bm8">}} -->

______

WAZIUP and IoT
-------------------------

{{< youtube id="sf7SRVEChbY">}}

The WAZIUP project uses cutting edge technology from IoT and Big Data to improve the working conditions in the rural ecosystem of Sub-Saharan Africa. First, WAZIUP involves end users of IoT and Big Data in order to define focused validation cases. Secondly, it engages the ICT ecosystem by fostering new tools and good practices amongst entrepreneurs and start-ups.


The technology we use to do this is:

- **WAZIDEV**: WaziDev is a Sensing and Actuation platform for your applications! It can send your data up to 7 Km using the LoRa technology. It is easily programmable and customizable, using Arduino technology. It is an ideal solution for start-ups and entrepreneurs who want to rapid prototype a IoT applications.
- **WAZIGATE** : WaziGate is a IoT LoRa Gateway, ideal for all your remote IoT applications. The Gateway can cover up to 100 IoT Sensors and actuator nodes using LoRa radio network: Weather stations, soil monitoring, GPS applications... The possibilities are endless! The Gateway can also control your actuators, such as electro-valves. You can host your own applications directly in the gateway, and connect to it through WiFi. The gateway can easily work without Internet connectivity and still provides data to end-users through its embedded database and web-based visualization module.
- **WAZICLOUD** : The WAZIUP Cloud platform allows you to manage your sensors, actuators and IoT data. WAZIUP Cloud platform offers everything that you need for your application:


{{< youtube id="Ro4f69a8ufo" >}}

______



Sensors
------

We have already created a section within the documentation, we invite you to look at it to find out more about the main sensors.
You can find it by clicking on this [link](https://www.waziup.io/documentation/wazidev/sensors/#overview).

Below we leave you a short video where we will talk about some sensors

{{< youtube id="okqQ0M1ulv4" >}}


IoT Devices, Architecture & Ecosystem
=====================================

IoT Ecosystem
-------------

The IoT ecosystem includes all those technologies that enable consumers, businesses, and governments to connect, control and derive value from their connected objects in diverse environments, including manufacturing, agriculture, transportation, smart cities, construction, oil, and gas. The ecosystem includes remotes, dashboards, networks, gateways, analytics, data storage, and security.

It is clear then that the IoT market is a huge and expanding space which offers opportunities but threatens confusion, as the number of IoT products proliferates and it becomes less clear what distinguishes them.

IoT Device
----------

IoT devices are the nonstandard computing devices that connect wirelessly to a network and have the ability to transmit data.

Connected devices are part of an ecosystem in which every device talks to other related devices in an environment to automate home and industry tasks. They can communicate usable sensor data to users, businesses and other intended parties. The devices can be categorized into three main groups: consumer, enterprise and industrial.

Consumer connected devices include smart TVs, smart speakers, toys, wearables and smart appliances. Smart meters, commercial security systems and smart city technologies -- such as those used to monitor traffic and weather conditions -- are examples of industrial and enterprise IoT devices. Other technologies, including smart air conditioning, smart thermostats, smart lighting and smart security, span home, enterprise and industrial uses

**connectivity and networking**

The networking, the communication and connectivity protocols used with internet-enabled devices largely depend on the specific IoT application deployed. Just as there are many different IoT applications, there are many different connectivity and communication options.

Communications protocols include CoAP, DTLS and MQTT, among others. Wireless protocols include IPv6, LPWAN, Zigbee, Bluetooth Low Energy, Z-Wave, RFID and NFC. Cellular, satellite, Wi-Fi and Ethernet can also be used.

Each option has its tradeoffs in terms of power consumption, range and bandwidth, all of which must be considered when choosing connected devices and protocols for a particular IoT application.

To share the sensor data they collect, IoT devices connect to an IoT gateway or another edge device where data can either be analyzed locally or sent to the cloud for analysis.


IoT architecture
----------------

The term Internet of Things (IoT) refers to a heterogeneous network of physical and virtual objects
embedded with electronics, software, sensors and connectivity to enable objects to achieve greater value
and service by exchanging data with other connected objects via the internet 

An example of IoT-enabled environment is an integrated transport system that can be dynamically
routed and reorganized in response to changing traffic needs and conditions.

![architecture-layer](./media/architectures.png)

The physical/perception layer contains embedded devices that make use of sensors to gather real world data. The network layer provides the mechanism The middle-ware layer facilitates and manages the communication between the real world sensed activities
and the application layer. The application layer maps onto applications that can be used by the consumer to send commands to real word objects over the Internet via mobile applications, webapps, etc.

IoT software
============
The software and the programming languages on which IoT works uses very common programming languages that programmers use and already know.
So which language should be chosen?
Firstly, because embedded systems have less storage and processing power, their language needs are different.
The most commonly used operating systems for such embedded systems are Linux or UNIX-like OSs like Ubuntu Core or Android.
IoT software encompasses a wide range of software and programming languages from general-purpose languages like C++ and Java to embedded-specific choices like Google’s Go language.
Here’s a quick overview of each one of IoT Software:

- **C & C++**: The C programming language has its roots in embedded systems—it even got its start for programming telephone switches. It’s pretty ubiquitous, that is, it can be used almost everywhere and many programmers already know it. C++ is the object-oriented version of C, which is a language popular for both the Linux OS and Arduino embedded IoT software systems. These languages were basically written for the hardware systems which makes them so easy to use.
- **Java**: While C and C++ are hardware specific, the code in JAVA is more portable. It is more like a write once and read anywhere language, where you install libraries, invests time in writing codes once and you are good to go.
- **Python**: There has been a recent surge in the number of python users and has now become one of the “go-to” languages in Web development. Its use is slowly spreading to the embedded control and IoT world—specially the Raspberry Pi processor. Python is an interpreted language, which is, easy to read, quick to learn and quick to write. Also, it’s a powerhouse for serving data-heavy applications.

Arduino IDE
===========

Introduction to Arduino IDE
---------------------------

The Arduino Integrated Development Environment (IDE) is a cross-platform application (for Windows, macOS, Linux) that is written in functions from C and C++. It is used to write and upload programs to Arduino compatible boards, but also, with the help of third-party cores, other vendor development boards.

The Arduino Integrated Development Environment - or Arduino Software (IDE) - contains a text editor for writing code, a message area, a text console, a toolbar with buttons for common functions and a series of menus. It connects to the Arduino and Genuino hardware to upload programs and communicate with them.

Programs written using Arduino Software (IDE) are called sketches. These sketches are written in the text editor and are saved with the file extension .ino. The editor has features for cutting/pasting and for searching/replacing text. The message area gives feedback while saving and exporting and also displays errors. The console displays text output by the Arduino Software (IDE), including complete error messages and other information. The bottom righthand corner of the window displays the configured board and serial port. The toolbar buttons allow you to verify and upload programs, create, open, and save sketches, and open the serial monitor.

The Arduino Software (IDE) uses the concept of a sketchbook: a standard place to store your programs (or sketches). The sketches in your sketchbook can be opened from the File > Sketchbook menu or from the Open button on the toolbar. The first time you run the Arduino software, it will automatically create a directory for your sketchbook. You can view or change the location of the sketchbook location from with the Preferences dialog.

Libraries provide extra functionality for use in sketches, e.g. working with hardware or manipulating data. To use a library in a sketch, select it from the Sketch > Import Library menu. This will insert one or more #include statements at the top of the sketch and compile the library with your sketch. Because libraries are uploaded to the board with your sketch, they increase the amount of space it takes up. If a sketch no longer needs a library, simply delete its #include statements from the top of your code.

{{< youtube id="nbD_V4QtNvY">}}


To know how to download and set up Arduino IDE for WAZIUP click on this [link](https://www.waziup.io/documentation/wazidev/user-manual/#install-arduino-ide) to be directed to the dedicated section
