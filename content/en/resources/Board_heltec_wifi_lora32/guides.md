---
date: 2022-09-14T9:14:00+00:00
title: Analog pH Sensor
---

# Introduction

WiFi LoRa 32 is a classic IoT dev-board based on ESP32 + SX127x, it has Wi-Fi, BLE, LoRa functions. It also comes with a Li-Po battery management system and 0.96″ OLED. This makes the heltec WiFi LoRA 32 suitable for smart cities, smart farms, smart home, and IoT applications.

![heltec](img/heltec.png)
                 
# Connecting to Arduino

![phw](img/phw.jpg)

Module interface:
1. VCC(+): Connect to the positive pole of the power supply (voltage is 5V)
2. GND(-): Connect to the negative pole of the power supply
3. OUT(A): Connect to any Arduino analog pin(A1 in this case)
                    
# Code example

``` Arduino
/********************
 *  Program:  Analog pH Sample Code
 ********************/

#include "DFRobot_PH.h"
#include <EEPROM.h>

#define PH_PIN A1
float voltage,phValue,temperature = 25;
DFRobot_PH ph;

void setup()
{
    Serial.begin(115200);  
    ph.begin();
}

void loop()
{
    static unsigned long timepoint = millis();
    if(millis()-timepoint>1000U){                  //time interval: 1s
        timepoint = millis();
        //temperature = readTemperature();         // read your temperature sensor to execute temperature compensation
        voltage = analogRead(PH_PIN)/1024.0*5000;  // read the voltage
        phValue = ph.readPH(voltage,temperature);  // convert voltage to pH with temperature compensation
        Serial.print("temperature:");
        Serial.print(temperature,1);
        Serial.print("^C  pH:");
        Serial.println(phValue,2);
    }
    ph.calibration(voltage,temperature);           // calibration process by Serail CMD
}

float readTemperature()
{
  //add your code here to get the temperature from your temperature sensor
}
```

# Further documentation

Documentation for this sensor is available [here](https://wiki.dfrobot.com/Gravity__Analog_pH_Sensor_Meter_Kit_V2_SKU_SEN0161-V2).

See [here](https://www.youtube.com/watch?v=9EIbTbh80gA&ab_channel=DavyWybiral) for details on calibration
