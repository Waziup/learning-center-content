---
module: 1
lecture: 1
title: Introduction to IoT
description: The first course will touch on the fundamentals of IoT.
difficulty: beginner
duration: 2h
---

Introduction to IoT
===================

The first course will touch on the fundamentals of IoT. After a short history of the creation of IoT, the course will explain briefly what IoT is and why it is important.
It will also show some of its application use cases and domains.

<youtube>IIgDQbp2-dY</youtube>


The term “Internet of Things” was coined by Kevin Ashton in 1999. 
Ashton, who was working in supply chain optimization, wanted to attract senior management’s attention to a new exciting technology called RFID. 
Because the internet was the hottest new trend in 1999, he called his presentation “Internet of Things”.

The internet of things is an extension of the current internet, further into the physical world.
We can collect data from the physical world using sensors and also effect changes in the physical world using actuators or effectors.

![IoTdevices](img/IoTdevices.png)

IoT is increasingly becoming popular because of advances in smartphone technology, internet connectivity, wearables and its relationship with open source, big data, security and privacy and software-defined networking.

The applications of IoT are wide: wearables, smart home automation, precision agriculture, smart city...
It is pervasing both consumer industrial worlds.

![components](img/components.png)

Finally, the challenges facing IoT are the security, the lack of strong regulations, availability of skilled talent, compatibility, bandwidth and customer expectations.

IoT Architecture
================

There is no single consensus on an architecture for IoT, which is agreed on universally.
However, different architectures have been proposed by different researchers.
The 3 and 5 layer architectures are the most widely used. However the 3 layer is the most commonly used so in this lecture we will look at the 3 layer architecture. The three first layers are: 
- *The perception layer* has sensors for sensing and gathering information about the environment.
- *The transport layer* allows to connect together to the smart things, network devices, and servers. It also transmits and processes sensor data.
- *The application layer* delivers application specific services to the user. It defines various applications in which the Internet of Things can be deployed.

Additionally, we sometimes add two more layers:
- *The business layer* manages the whole IoT system, including applications, business and profit models, and users’ privacy.
- *The processing layer*, also known as the middleware or edge layer, allows to process, store and analyze sensor data.

In Waziup, we divide the architecture in three layers:

![archi](img/archi.png)

WaziDev is a development platform, capable of sending data through LoRaWAN to the WaziGate.
The WaziGate processes locally the data and forwards it to the WaziCloud, were the user applications lives.
More on this in Waziup module!


Networking & protocols
=======================

Protocols are systems of rules and procedures that allow two or more entities to communicate.
The TCP/IP protocol stack is at the heart of the Internet, which is the “I” in IoT, or course!
It can be represented using the OSI seven-layer reference model.

![OSI](img/OSI.png)

Here are few protocols used with IoT:
- *HTTP* is the foundation of the client-server model used for the Web. The more secure method to implement HTTP is to include only a client in your IoT device, not a server
- *WebSocket* is a protocol that provides full-duplex communication over a single TCP connection between client and server.
- *CoAP* is for use with low-power and constrained networks. CoAP is a RESTful protocol.
- *MQTT* is a publish/subscribe messaging transport that is extremely lightweight and ideal for connecting small devices to constrained networks.


Radio communications
====================

Radio communications are an essential part of IoT.

Our course on radio communications will introduce the basics of wireless communications: wireless transmission fundamentals including radio propagation models, antenna technologies, wireless link budget and the relationship between modulation, throughput, energy and transmission range.

Web & mobile IoT applications
=============================

A complete IoT application should always include a web or mobile application.
Our course will show you how to develop a Web interface for your IoT application. At first, we will develop a very simple Web application, based solely on HTML and Javascript. We will build on this knowledge to go to the next step: the Web frameworks. We will show the basics of three of the most popular frameworks: ReactJS, Angular and Vue.

Data analysis and AI
====================

When people think of AI, most of them think of Artificial General Intelligence (AGI). An AGI can do everything what humans do (and even better). But the sad truth is, that mankind is not even close to develop a "real AGI". Nowadays AI is very focused on some specific use cases, therefore one can speak of a Artificial Narrow Intelligence (ANI). Because you train it on a specific thing its capabilities are limited. If you try to use it for another task, it will not perform like you would expect it. AI is separated in many subfields, in this lesson we will elaborate on some of them:

    Machine Learning (ML)
    Deep Leaning (DL)
    Computer Vision (CV)
    Natural Language Processing (NLP)


Business support
================

We also provide business support for creating your IoT startup. Please checkout our courses on business, for instance how to build a business canvas.
