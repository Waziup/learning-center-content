---
id: ups_res
title: UPS_HAT
type: power-management
desc: Uninterruptible power supply module
color: "#d4e7ff"
---

# Introduction
This is a power expansion board specially designed for Raspberry Pi. It allows the Raspberry Pi to be mobile or moveable.
It's more convenient to use external 3.7V Lithium polymer battery or 3.7V 18650 series Lithium battery.

![picxxyyzz](img/pic1.jpg)

![picxxyyzz](img/pic2.jpg)

# Wiring

This UPS board is plug and play, so all you need to do is directly sit it on top of your raspberry pi(aligned and connected to all 40 GPIOs)
Next connect a li-ion or li-po battery to the battery port of the UPS.
Finally connect the Pi's power adaptor to the UPS and hold down the UPS power button for a few seconds to power it up

![picxxyyzz](img/pic3.jpg)

![picxxyyzz](img/pic4.jpg)

# Specifications

- Maximum discharge current: 2A
- Maximum charge current: 2A
- Output protection: overcurrent, short circuit, undervoltage protection
- Input protection: overvoltage, overcharge, undervoltage protection

# Features

- Built-in power path management, perfectly supports charging While discharging.
- Intelligent 3-stage charging (trickle, constant current, constant voltage), it can effectively extend the battery life.
- Supports I2S Output with Capacity & Voltage Reading Function (provide algorithms and examples)
- Support Raspberry pi or Android & Apple Phone or Pad or other electronic device charging
- Supports charging while discharging(use external heatsilk on clip)
- 4 LED power indicator
- Standard dimension of Raspberry Pi HAT
- Two power supply modes: GPIO power output and USB power out
- Removable battery, The external lithium battery requirements: 3.7V lithium battery; (The battery is not included)
