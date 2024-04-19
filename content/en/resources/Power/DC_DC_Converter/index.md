---
id: dc_dc_conv_res
title: DC-DC Converter
type: power-management
desc: DC to DC converter
tags:
    - Hardware
    - Power Management
---

# Introduction

The S9V11MACMA switching step-up/step-down regulator efficiently produces a finely adjustable output between 2.5 V and 9 V whether it is higher or lower than the input voltage, which can range from 3 V to 16 V. The regulator also has a precision-adjustable low-voltage cutoff with hysteresis that can be used to prevent battery over-discharge.

![picxxyyzz](img/pic1.jpg)

![picxxyyzz](img/pic2.jpg)

To use this dc-dc converter, you have to hook up your power source to the VIN and VOUT to the sensor node or device to be powered.

**Note:** you need to set the output and cut off voltage of the converter by means of the potentiometers and a multimeter before connecting your sensor.

![picxxyyzz](img/pic3.jpg)

![picxxyyzz](img/pic4.jpg)

The regulator features an enable pin, EN, that can be used as a precision low-voltage cutoff thanks to its tight activation and deactivation thresholds (voltages below 0.7 V trigger a low-power sleep state, and voltages above 0.8 V re-enable the regulator). On this regulator version, EN is connected to VIN through a 12-turn potentiometer to provide a user-adjustable cutoff threshold, which is useful for battery powered applications where draining the battery below a particular voltage threshold could permanently damage it. The quiescent current draw in this sleep mode is dominated by the current in the resistor network from ENABLE to VIN, which is approximately 7 µA per volt on VIN (e.g. approximately 20 µA with 3 V in). See the Setting the cutoff voltage section below for details on how to use the built-in potentiometer to set the cutoff threshold.

# Further documentation
Documentation for this Converter is available [here](https://www.pololu.com/product/2868/specs).

# Specifications

- Minimum operating voltage:	2 V
- Maximum operating voltage:	16 V
- Maximum output current:	1.5 A3
- Minimum output voltage:	2.5 V4
- Maximum output voltage:	9 V4
- Reverse voltage protection?:	None (you have to place your own diode)
- Maximum quiescent current:	1 mA
- Low-voltage cutoff:	adjustable

# Features

- Input voltage: 2 V to 16 V (note: this regulator requires 3 V to start, but it can operate down to 2 V after startup)
- Output voltage: 2.5 V to 9 V (precision-adjustable using built-in 12-turn potentiometer)
- Typical maximum continuous output current: 1.5 A
- Precision-adjustable low-voltage cutoff with hysteresis can be used to protect batteries from over-discharging
- Power-good indicator can be used to tell when the regulator has reached and is maintaining its target output voltage
- Power-saving feature maintains high efficiency at low currents (quiescent current is less than 1 mA while enabled)
- Integrated over-temperature and short-circuit protection
- Small size: 0.5″ × 0.6″ × 0.25″ (12.7 × 15.3 × 6.4 mm)
- Enable pin for activating/deactivating the converter output
