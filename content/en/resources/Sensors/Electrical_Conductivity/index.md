---
id: conductivity_res
title: Electrical Conductivity
type: sensor
desc: Measures the amount of electrolytes in a liquid 
color: "#BEFFE6"
tags:
    - Hardware
    - Sensor
    - Agriculture
    - City
    - Industry
    - Health
---

# Introduction

Conductivity is the reciprocal of the resistance, which is related to the ability of the material to carry the current. In the liquid, the reciprocal of the resistance, the conductivity, is the measure of its ability to conduct electricity. Conductivity is an important parameter of water quality. It can reflect the extent of electrolytes present in water.

![picxxyyzz](img/pic1.png)

# Wiring

![picxxyyzz](img/pic2.jpg)

1. VCC:	5v of Arduino
2. GND:	GND of Arduino
3. A  :	A1 of Arduino

# Installing EC Library

Download the zip library [here](https://github.com/DFRobot/DFRobot_EC/archive/master.zip).

Next, install the library by navigating to Sketch > Include Library > Add Zip Library

![picxxyyzz](img/pic3.png)

Inside the add zip library window, locate the downloaded zip file and click Open to install it.

![picxxyyzz](img/pic4.png)

From here, we can restart our Arduino IDE to load the new library up.

# Code example

```c
/*
 * file DFRobot_EC.ino
 * @ https://github.com/DFRobot/DFRobot_EC
 *
 * This is the sample code for Gravity: Analog Electrical Conductivity Sensor / Meter Kit V2 (K=1.0), SKU: DFR0300.
 * In order to guarantee precision, a temperature sensor such as DS18B20 is needed, to execute automatic temperature compensation.
 * You can send commands in the serial monitor to execute the calibration.
 * Serial Commands:
 *   enterec -> enter the calibration mode
 *   calec -> calibrate with the standard buffer solution, two buffer solutions(1413us/cm and 12.88ms/cm) will be automaticlly recognized
 *   exitec -> save the calibrated parameters and exit from calibration mode
 *
 * Copyright   [DFRobot](http://www.dfrobot.com), 2018
 * Copyright   GNU Lesser General Public License
 *
 * version  V1.0
 * date  2018-03-21
 */

#include "DFRobot_EC.h"
#include <EEPROM.h>

#define EC_PIN A1
float voltage,ecValue,temperature = 25;
DFRobot_EC ec;

void setup()
{
  Serial.begin(115200);  
  ec.begin();
}

void loop()
{
    static unsigned long timepoint = millis();
    if(millis()-timepoint>1000U)  //time interval: 1s
    {
      timepoint = millis();
      voltage = analogRead(EC_PIN)/1024.0*5000;   // read the voltage
      //temperature = readTemperature();          // read your temperature sensor to execute temperature compensation
      ecValue =  ec.readEC(voltage,temperature);  // convert voltage to EC with temperature compensation
      Serial.print("temperature:");
      Serial.print(temperature,1);
      Serial.print("^C  EC:");
      Serial.print(ecValue,2);
      Serial.println("ms/cm");
    }
    ec.calibration(voltage,temperature);          // calibration process by Serail CMD
}

float readTemperature()
{
  //add your code here to get the temperature from your temperature sensor
}

```

# Further Documentation and Calibration

For more information on calibration of this sensor, see here [here](https://wiki.dfrobot.com/Gravity__Analog_Electrical_Conductivity_Sensor___Meter_V2__K%3D1__SKU_DFR0300).

# Specifications

Signal Conversion Board (Transmitter) V2
- Supply Voltage: 3.0~5.0V
- Output Voltage: 0~3.4V
- Probe Connector: BNC
- Signal Connector: PH2.0-3Pin
- Measurement Accuracy: ±5% F.S.
- Board size: 42mm*32mm/1.65in*1.26in

Electrical Conductivity Probe
- Probe Type: Laboratory Grade
- Cell Constant: 1.0
- Support Detection Range: 0~20ms/cm
- Recommended Detection Range: 1~15ms/cm
- Temperature Range: 0~40°C
- Probe Life: >0.5 years (depending on the frequency of use)
- Cable Length: 100cm

# Features

- 3.0~5.0V wide voltage input
- Hardware filtered output signal, low jitter
- AC excitation source, effectively reduce polarization
- Gravity connector and BNC connector, plug and play, no welding
- Software library supports two-point calibration and automatically identifies standard buffer solution, integrates temperature compensation algorithm
- Uniform size and connector, convenient for the design of mechanical structures
