---
module: 1
lecture: 2
title: Architecture and communication protocols
description: The second course in this module will introduce the various architectures and communication protocols of IoT. In particular, we will introduce the sensor nodes, gateways, communications and cloud architectures.
---

IoT Architecture
================

There is no single consensus on an architecture for IoT, which is agreed on universally.
However, different architectures have been proposed by different researchers.

The 3 and 5 layer architectures are the most widely used. However the 3 layer is the most commonly used so in this lecture we will look at the 3 layer architecture.

3 Layer Architecture
The perception layer: has sensors for sensing and gathering information about the environment.
The network layer: connects to other smart things, network devices, and servers. It also transmits and processes sensor data.
The application layer: delivers application specific services to the user. It defines various applications in which the Internet of Things can be deployed.

5 Layer Architecture
Business layer : manages the whole IoT system, including applications, business and profit models, and users’ privacy.
Processing layer: also known as the middleware layer,  processes, stores and analyzes sensor data.
Transport layer: transfers the sensor data from the perception layer to the processing layer and vice versa through networks such as wireless, 3G/4G, LAN, Bluetooth, RFID, NFC etc.

Protocols
=========

A system of rules/procedures that allow two or more entities of a communications system to transmit information between themselves.

The TCP/IP protocol stack is at the heart of the Internet, with regards to the “I” in IoT.
It can be represented using the OSI seven-layer reference model.

Here are few protocols used with IoT:

IoT Protocols
HTTP is the foundation of the client-server model used for the Web. The more secure method to implement HTTP is to include only a client in your IoT device, not a server

WebSocket is a protocol that provides full-duplex communication over a single TCP connection between client and server.

XMPP
Expanded into signaling for VoIP, collaboration, lightweight middleware, content syndication, and generalized routing of XML data

CoAP
Designed by the IETF for use with low-power and constrained networks. CoAP is a RESTful protocol.

MQTT
It's an open source protocol for constrained devices and low-bandwidth, high-latency networks. 
It is a publish/subscribe messaging transport that is extremely lightweight and ideal for connecting small devices to constrained networks.

