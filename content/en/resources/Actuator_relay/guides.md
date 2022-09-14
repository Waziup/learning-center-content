---
date: 2022-09-14T9:14:00+00:00
title: 5V Single Channel Relay
---

# Introduction

You may occasionally wish your Arduino to manage appliances with AC power, such as lamps, fans, and other home appliances. The Arduino, however, cannot directly control these higher voltage devices because it runs on 5 volts.

This is where the relay comes into play. You can use an Arduino to control the relay and the relay module to control the AC mains.
                    
![relay](img/relay.jpg)


                 
# Connecting to Arduino

![relaywire](img/relaywire.jpg)

Module interface:
1. VCC: Connect to the positive pole of the power supply (voltage is 5V)
2. GND: Connect to the negative pole of the power supply
3. IN: Connect to Arduino control pin


Relay output:
1. NO: Relay normally open interface, it will be shorted to COM after relay is closed
2. COM: Relay Common Interface(power source to be controlled is connected here)
3. NC: Normally closed relay interface. Before the relay is closed, it is short-circuited with COM.
                    
# Code example

``` arduino
/********************
 *  Program:  PIR sensor tester
 ********************/
    
int RelayPin = 10; Declaring pin 10 as the control pin

void setup() {
	// Set RelayPin as an output pin
	pinMode(RelayPin, OUTPUT);
}

void loop() {
	// Let's turn on the relay...
	digitalWrite(RelayPin, LOW);

  //Lets wait for 5 seconds
	delay(5000);
	
	// Let's turn off the relay...
	digitalWrite(RelayPin, HIGH);

  //Lets wait for another 5 seconds
	delay(5000);
}
```

# Further documentation

Documentation for this sensor is available [here](https://lastminuteengineers.com/one-channel-relay-module-arduino-tutorial/).

