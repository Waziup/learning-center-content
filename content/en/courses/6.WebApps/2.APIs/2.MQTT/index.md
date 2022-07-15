---
title: MQTT APIs
description: This course will show you how to use MQTT APIs.
---

MQTT (Message Queue Telemetry Transport) is a publish-subscribe messaging protocol designed for lightweight M2M communications.
It is very useful in IoT applications, as we will see.

<youtube>ozqQEhM5IPo</youtube>

HTTP vs MQTT
------------

There is a major difference between HTTP and MQTT: HTTP is a "request-response" protocol.
You perform a request, the server responds, and completely forgets about you.
This works fine most of the time, but for IoT applications in particular there is a small problem.
Say, that you request the value of a sensor.
However, after some seconds, that value may change! So you have to request it again. And again.

A better solution in this case is to use MQTT, which uses the "publish-subscribe".
Instead of performing regular requests, you say to the server "Look, I'm interrested in this sensor values. Could you call me back if there is any changes?"

As can be seen in the following picture, in MQTT the connection with the server is persistent (as opposed to HTTP).

![HTTPvsMQTTdiag](img/HTTPvsMQTTdiag.png)

The following picture show the HTTP methods vs the MQTT operations.

![HTTPvsMQTT](img/HTTPvsMQTT.png)

Architecture
------------

The architecture of MQTT is based on a central server, called the "broker".
All clients can publish informations to the broker, and also subscribe on informations.

![archi](img/archi.png)

In the picture above, Client A and Client B are smartphones subscribing on an topic called "human-presence" from the broker.
Client C is a presence detector, than will publish any detection on the "human-presence" topic. 
As soon as the publish is done, the server will send an update on any subscribed clients.

Topics
------

A topic is a string that the broker uses to filter messages for each connected client.
The topic consists of one or more topic levels. Each topic level is separated by a forward slash (topic level separator).

![topic](img/topic.png)

Topics supports wildcards. 
For example, subscribing on the following topic would get you update for the temperature changes in any rooms:

![topicwild](img/topicwild.png)

You can also subscribe on all sub-topics using the wildcard "#":

![topicwild2](img/topicwild2.png)


Quality of service
-------------------

MQTT supports the following Quality of Service levels:
- Fire and forget (0): Client sends message to broker. Doesn’t care what happens to it.
- Deliver at least once (1): Client only destroys copy of message when acknowledgement is received from broker.
- Deliver exactly once (2): Multiple levels of checks and balances until it is established that message has been sent exactly once.

Last Will Testament
-------------------

You can configure the broker to send message to a specified client in case the connecting client’s connection closes in an ungraceful manner.


Persistent sessions
-------------------

In the event that the client goes offline, the broker stores all messages that the client has subscribed to and notifies the client of all such messages once it comes back online.
