---
id: pir_motion_res
title: PIR Motion Sensor
type: sensor
desc: A passive infrared sensor is an electronic sensor that measures infrared light radiating from objects in its field of view.
color: "#c0dfe9"
tags:
    - City
    - Agriculture
---

# Introduction

PIR sensors allow you to sense motion, almost always used to detect whether a human has moved in or out of 
the sensors range. They are small, inexpensive, low-power, easy to use and don't wear out. For that reason they 
are commonly found in appliances and gadgets used in homes or businesses. They are often referred to as PIR, 
"Passive Infrared", "Pyroelectric", or "IR motion" sensors.
                    
![pir2](img/pir2.jpg)
                 
# Connecting to Arduino

![pir-arduino](img/pic1.png)

**Note:** You can tweak the potentiometers on the PIR motion sensor to increase its sensitivity or reaction time.

![pir-arduino](img/pir-arduino.gif)
                    
# Code example

```c
/********************
 *  Program:  PIR sensor tester
 ********************/
    
int ledPin = 13;               // choose the pin for the LED
int inputPin = 2;               // choose the input pin (for PIR sensor)
int pirState = LOW;             // we start, assuming no motion detected
int val = 0;                    // variable for reading the pin status

void setup(){
  pinMode(ledPin, OUTPUT);      // declare LED as output
  pinMode(inputPin, INPUT);     // declare sensor as input

  Serial.begin(38400);
}

void loop(){
  val = digitalRead(inputPin);  // read input value
  if (val == HIGH) {            // check if the input is HIGH
    digitalWrite(ledPin, HIGH);  // turn LED ON
    if (pirState ==  LOW){
      // we have just turned on
      Serial.println("Motion detected!");
      // We only want to print on the output change, not state
      pirState = HIGH;
   }
  } else {
    digitalWrite(ledPin,LOW); // turn LED OFF
    if (pirState == HIGH){
      // we have just turned of
      Serial.println("Motion ended!");
      // We only want to print on the output change, not state
      pirState = LOW;
    }
  }
}
```

# Further documentation

Documentation for this sensor is available [here](https://learn.adafruit.com/pir-passive-infrared-proximity-motion-sensor/how-pirs-work).


# Specifications

- Operating Voltage (VDC): 4.5 ~ 20v
- Idle Current Consumption (mA): 0.06
- Distance Measuring Range (CM): 300 ~ 700
- Output Type: (High/ Low-level Signal) 3.3V TTL output
- Dimensions (mm)LxWxH: 32 x 24 x 18
- Weight (gm): 10
- Working Temperature Range (°C): -20 to 80
- Detection Angle: <140°
- Delay Time: 5 to 200s (Can be Adjusted, Default 5s +/- 3%)

# Features

- Infrared Sensor with Control Circuit Board
- The Sensitivity and Holding Time are adjustable.
- Blockade time: 2.5s (Default)
- Sensitive Setting: Turn to Right, Distance Increases (About 7M); Turn to Left, Distance Reduce (About 3M)
- Time Setting: Turn to Right, Time Increases (About 200S); Turn to Left, Time Reduce (About 5S).
