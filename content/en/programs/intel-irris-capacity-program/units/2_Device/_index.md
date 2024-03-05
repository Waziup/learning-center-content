---
id: intel-irris_device
title: Intel-IrriS Device
description: In this course, we will introduce the devices of Intel-IrriS and how to set them up and use them.
difficulty: intermediary
duration: 5h
---


The Intel-IrriS Device is, among the two main components of the system, the most specific of the project. 

Installed in the field, it periodically gathers the measurements from the ground sensors and transmits the values to the gateway using LoRa radio frames. 

The casing is waterproof and shelters the core microprocessor, on an Arduino board, the radio chip, the batteries (two AA alkaline, or 3 AAA NiMh, with or without a solar pannel), all the connectors and the On/Off switch. 

![Intel-IrriS Device](img/Device.png)


2.i. Device's hardware
======================
Different versions of the device exist with different hardware parts. Two development took place during the project, the Off-the-shelf Waziup design and the DIY UPPA/IRD design. And different versions have been made available at different times of the project.

Let's focus on PCBs, radio chipsets, antennas, solar panels, and other chosen components.

## 1. The PCBs
### a. WaziSense v2.0, Waziup design
![WaziSense Board](img/WaziSense-v2.png)

More info:
[WaziSense Intro](../../../../resources/Boards/WaziSense/index.md); 
[WaziSense User Manual](../../../../resources/Boards/WaziSense/user_manual.md)

### b. UPPA PCB v2, UPPA's design
![PCBv2 UPPA](img/PCB-v2.png)

More info:
[UPPA PCB v2](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/PCBs/README.md#pcb-v2)

### c. UPPA PCB RAK3172 v1, UPPA's design
![PCB Rak](img/PCB-rak-v1.png)
More info:
[UPPA PCB RAK3172 v1](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/PCBs/README.md#pcb-rak3172-v1)

### d. IRD PCBA v4.1, IRD/UPPA's design
![PCBA](img/PCBA.png)
More info:
[IRD PCBA v4.1](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/PCBs/README.md#pcba-ird-v41)

## 2. The radio chipsets and antennas
The take-away message here is that the allowed frequency band for the LoRa radio communications differs according to local regulations. The band is centered around: 
   1. In Europe: 868 MHz;
   2. In most of the African Countries, e.g. Algeria: 433 Mhz; 
   3. In other regions: 915MHz;
   4. Traffic is usually allowed on the Wi-Fi band: 2.4 GHz.

### a. Radio chipsets
In Intel-IrriS, we chose two radio modules that are common and easy to find on the market:
- The RFM95W (868MHz);
![rfm95w](img/rfm95w.png)
- The RFM96W (433MHz).
![rfm96w](img/rfm96w.png)

Different versions are available on the market, with different features, most are compatible with the PCBs.
Note that in this pictures, the same type of Integrated Circuit (IC) is used: RF96. 
I took from the datasheets the following tables summarizing frequency compatibilities:
- for ICs:
| IC Number | Frequency Range | Spreading Factor | Bandwidth | Effective Bitrate | Estimated Sensitivity |
| --------- | --------------- | --- |--------------- |--------------- |--------------- |
| RF96 | 137 - 1020 MHz | 6 - 12 | 7.8 - 500 kHz | .018 - 37.5 kbps | -111 to -148 dBm |
| RF97 | 137 - 1020 MHz | 6 - 9 | 7.8 - 500 kHz | 0.11 - 37.5 kbps | -111 to -139 dBm |
| RF98 | 137 - 525 MHz | 6- 12 | 7.8 - 500 kHz | .018 - 37.5 kbps | -111 to -148 dBm |

- for LoRa chipsets:
| Chipset Number | Frequency Band | Spreading Factor | Bandwidth | Effective Bitrate | Estimated Sensitivity |
| --------- | --------------- | --- |--------------- |--------------- |--------------- |
| RFM95W | 868\915 MHz | 6 - 12 | 125 - 500 kHz | .293 - 37.5 kbps | -111 to -136 dBm |
| RFM96W/98W | 433\470 MHz | 6 - 12 | 62.5 - 500 kHz | .1465 - 37.5 kbps | -112 to -140 dBm |
| RFM98W | 169MHz | 6 - 12 | 31.25 - 125 kHz | 73.24- 9375 bps | -118 to -143 dBm |

### b. LoRa antennae
The antenna model will also depend on the frequency band. The default type for Intel-IrriS devices are simple whip (monopole) antennae. We adopted the following color convention: white antennae for 433 MHz; black antennae for 868 MHz.
![antennae](img/antennae.png)

The market provides other models, a tradeoff price vs range&sensitivity has to be chosen.
We made some comparisons tests:
[antenna-tests](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials/Intel-Irris-antenna-test.pdf)

More info, more models, and market references for both chipsets and antennae here:
[hardware-parts](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials/Intel-IrriS-low-cost-sensor-hardware-parts.pdf)


## 3. The solar panels

## 4. The other components

2.ii. Sensors
=============
bla

2.iii. Order it
===============
bla

2.iv. Build it
==============
bla

2.v. Device's software
======================
bla

2.vi. Device's debug
====================

bla

![ex im](img/II-mini.png)

<youtube>wgfhedtyjhdt</youtube>


<quiz id="0261c201-7AAAAAAAAAAA171-60158676498c" type="single-choice" title="What is 4x4?">
	<answer feedback="Thats wrong!">It's 17.</answer>
	<answer feedback="Nope.">Something like 123.</answer>
	<answer feedback="You got it!" right>It's an all-wheel drive car.</answer>
</quiz>