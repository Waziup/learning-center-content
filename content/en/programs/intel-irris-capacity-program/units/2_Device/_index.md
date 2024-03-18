---
id: intel-irris_device
title: Intel-IrriS Device
description: In this course, we will introduce the devices of Intel-IrriS and how to set them up and use them.
difficulty: intermediary
duration: 5h
---


The Intel-IrriS Device is, among the two main components of the system, the most specific of the project. 

Installed in the field, it periodically gathers the measurements from the ground sensors and transmits the values to the gateway using LoRa radio frames. 

The casing is waterproof and shelters the core microprocessor, on an Arduino board, the radio chip, the batteries (two AA alkaline, or 3 AAA NiMh, with or without a solar panel), all the connectors and the On/Off switch. 

![Intel-IrriS Device](img/Device.png)



2.i. Get the Device's components
================================
Different versions of the device exist with different hardware parts. Two developments took place during the project, the Off-the-shelf Waziup design and the DIY UPPA/IRD design. Different versions have been made available at different times of the project.

In this program, we will mainly focus on the most recently updated DIY PCB: the IRD PCBA v4.1. The development approach has been tackling every encountered obstacle both regarding the needed features and the technical challenges. We have simplified the assembly work, and we have included the possibility to autonomously work with a solar panel.

Let's focus on PCBs, radio chipsets, antennas, sensors solar panels, and the other chosen components.

## 1. Order The PCB
### IRD PCBA v4.1, IRD/UPPA's design [this is the current version]
![PCBA](img/PCBA.png)
More info:
[IRD PCBA v4.1](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/PCBs/README.md#pcba-ird-v41)

Watch our PDF tutorial, [here](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials/Intel-Irris-PCB-update-PCBA.pdf), and our video tutorial:

[comment]: # "<youtube>ueNRfBzCXiU</youtube>"
[![Video PCB order howto](img/you_order_PCB.png)](http://www.youtube.com/watch?v=ueNRfBzCXiU "Video PCB Order Howto")


## 2. Choose the radio chipsets and antennas
[comment]: # "The take-away message here is that "

Before choosing these elements, it is important to note that the allowed frequency band for the LoRa radio communications differs according to local regulations. The band is centered around: 
   1. In Europe: 868 MHz;
   2. In most of the African Countries, e.g. Algeria: 433 Mhz; 
   3. In other regions: 915MHz;
   4. Traffic is usually allowed on the Wi-Fi band: 2.4 GHz.

The radio chipset, the antenna, and the software are frequency dependent. 

### a. Radio chipsets
In Intel-IrriS, we chose two radio modules that are common and easy to find on the market:
- The RFM95W (868MHz);
![rfm95w](img/rfm95w.png)
- The RFM96W (433MHz).
![rfm96w](img/rfm96w.png)

Different versions are available on the market, with different features, most are compatible with the PCBs.
Note that in these pictures, the same type of Integrated Circuit (IC) is used: RF96. 
I took from the datasheets the following tables summarizing frequency compatibilities:
- for ICs:

| IC Number | Frequency Range | Spreading Factor | Bandwidth | Effective Bitrate | Estimated Sensitivity |
| --------- | --------------- | --- |--------------- |--------------- |--------------- |
| RF96 | 137 - 1020&thinsp;MHz | 6 - 12 | 7.8 - 500&thinsp;kHz | .018 - 37.5&thinsp;kbps | -111 to -148&thinsp;dBm |
| RF97 | 137 - 1020&thinsp;MHz | 6 - 9 | 7.8 - 500&thinsp;kHz | 0.11 - 37.5&thinsp;kbps | -111 to -139&thinsp;dBm |
| RF98 | 137 - 525&thinsp;MHz | 6- 12 | 7.8 - 500&thinsp;kHz | .018 - 37.5&thinsp;kbps | -111 to -148&thinsp;dBm |

- for LoRa chipsets:

| Chipset Number | Frequency Band | Spreading Factor | Bandwidth | Effective Bitrate | Estimated Sensitivity |
| --------- | --------------- | --- |--------------- |--------------- |--------------- |
| RFM95W | 868/915&thinsp;MHz | 6 - 12 | 125 - 500&thinsp;kHz | .293 - 37.5&thinsp;kbps | -111 to -136&thinsp;dBm |
| RFM96W/98W | 433/470&thinsp;MHz | 6 - 12 | 62.5 - 500&thinsp;kHz | .1465 - 37.5&thinsp;kbps | -112 to -140&thinsp;dBm |
| RFM98W | 169&thinsp;MHz | 6 - 12 | 31.25 - 125&thinsp;kHz | 73.24- 9375&thinsp;bps | -118 to -143&thinsp;dBm |

### b. LoRa antennae
The antenna model will also depend on the frequency band. The default type for Intel-IrriS devices are simple whip (monopole) antennae. We adopted the following color convention: white antennae for 433 MHz; black antennae for 868 MHz.
![antennae](img/antennae.png)

The market provides other models, a tradeoff price vs range&sensitivity has to be chosen.
We made some comparisons tests:
[antenna-tests](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials/Intel-Irris-antenna-test.pdf)

More info, more models, and market references for both chipsets and antennae here:
[hardware-parts](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials/Intel-IrriS-low-cost-sensor-hardware-parts.pdf)


## 3. Choose the sensors
We selected in Intel-IrriS three sensors:
- the *SEN0308 capacitive* soil sensor;
- the *WM200 Irrometer Watermark* water tension sensor;
- the *DS18B20 temperature sensor* for soil temperature.

We further detail them and why we chose them.

The three sensor types can be attached to and confirgured on the devices, in the following combinations or *device type*:

||C|W|CT|WT|2WT|
|-|-|-|-|-|-|
|SEN0308|1|-|1|-|-|
|WM200|-|1|-|1|2|
|DS18B20|-|-|1|1|1|

The most common device type are the Capacitive (C), the Watermark & Temperature (WT) and the 2 Watermarks & Temperature (2WT). 2WT is particularly helpful to obtain information at two different depths in ground, giving insights of the water movements in the soil.

![Device types](img/devtypes.png)

### a. The *SEN0308 capacitive* soil sensor
![Capacitive](img/SEN0308.jpeg)


The cost of capacitive sensors is relatively low (especially when compared to TDR, -time domain reflectometry, probes), which makes it possible to instrument field with a low budget or (if keeping the same budget) by increasing the sensor's density in a given field.
Moreover, their power consumption can be very low and some require low excitation voltages to operate (as low as 3 volts) which allows for a high autonomy with reasonable battery capacities. Finally, they are also relatively easy to install.

The disadvantage of the capacitive method is that the signal is difficult to interpret in the absence of additional information, on the sensor itself and the characteristics of the environment, i.e. soil characteristics (mainly clay content) and the concentration of dissolved minerals. This disadvantage has been compensated in Intel-IrriS by allowing the user and the system to provide contextual information, particularly on soil types, and by recommending a calibration before use. 

Two models of capacitive sensors built by the DFRobot company are commonly used at the moment: SEN0193 & SEN0308 which cost around 5 & 20 euros, respectively. Compared with the SEN0193 version, the SEN0308 sensor has increased waterproof performance; as it can still be used after being immersed in water according to DFRobot. With an increased plate length, the capacitive electrode plate has increased length (12cm approximately) to measure more accurately the soil moisture (in addition, the circuit performances are presented as optimized). Finally, the sensor has a wide input voltage (3.3&thinsp;V-5.5&thinsp;V) and is compatible with Arduino, ESP32, micro:bit, control board, Raspberry Pi and other common control boards.

A complete report about the capacitve measurement method and about this sensor model can be found here:
[Capcitive-KPIs-D3.6b](https://intel-irris.eu/wp-content/uploads/2023/09/D3.6b.pdf)

More info on this sensor can be found here:
[SEN0308-details](https://wiki.dfrobot.com/Waterproof_Capacitive_Soil_Moisture_Sensor_SKU_SEN0308)


### b. The *WM200 Irrometer Watermark* water tension sensor

Intel-IrriS chose this one because it is widespread, and relatively easy to connect to a board (e.g. Arduino). That is, it is less expensive than more sophisticated sensors using other physical processes, but the project can bring and use enough contextual information (soil temperature, soil type), and calibration before use, to overcome the variability and maintenance issues. 

A nice description and basic code example here:
[Watermark-WM200](../../../../resources/Sensors/Watermark/index.md); 

[comment]: # "you will need a resistor from 7kΩ to 14kΩ (we use 10kΩ)"

### c. The *DS18B20 temperature sensor* for soil temperature

In Intel-IrriS we use the waterproof version of this typical and effective temperature sensor. 

A nice description and basic code example here:
[DS18B20 temperature sensor](../../../../resources/Sensors/Temperature_DS18B20/index.md); 


## 4. Order all the parts

### a. The solar panels
The Solar panel must fit the casing, Intel-IrriS selected this model: Mini solar panel 6 V 0.6 W 100 mA 60x90mm.
The PCBA has a circuit designed to make the device work with this solar panel and NiMh rechargeable batteries.
The WaziSense v2 however is designed for Li-ion or Li-Po 3.7v batteries. 

Again, since the addition of a solar panel make the device's assembly more complex, costly, and slightly reduce its robustness and watertightness, it is not the default choice of implementation of Intel-IrriS.


### b. List of components
Most of the needed components are listed here:
[hardware-parts](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials/Intel-IrriS-low-cost-sensor-hardware-parts.pdf)

Here a brief table summary for the PCBA, with and without a solar panel:


||for PCBA|for solar PCBA |
|-----|--------|----------|
|Arduino ProMini, 3.3&thinsp;V 8&thinsp;MHz with 1 6-pin 90° and 2 12-pin male headers | 1 |1|
|Pack of minimum 5 2.54&thinsp;mm male pin headers (1 3-pin, 1 2-pin) | 1 | 1 |
|ABS waterproof enclosure with screws and joint| 1 | 1|
|2-AA battery holder|1|-|
|2 AA **heavy duty** batteries 1.5&thinsp;V|1|-|
|3 AAA NiMh 1.2&thinsp;V rechargeable batteries|-|1|
|Mini solar panel 6&thinsp;V 0.6&thinsp;W 100&thinsp;mA 60x90&thinsp;mm|-|1|
|Female (F) or male (M) tipped breadboard/Dupont cables^^ | 1 FF | 2 FF + 2 MM |
|Switch with pre-soldered wires|1|1|
|Waterproof cap for the switch|1|1|
|Cable gland PG7 with nylon joint|1|1|
|3&thinsp;dBi 868&thinsp;MHz or 3&thinsp;dBi 433&thinsp;MHz antenna|1|1|
|Flat-face seal for outer antenna junction (6x11x0.8&thinsp;mm)|1|1|
|DS18B20 for devices of type CT, WT, 2WT|1|1|
|SEN0308 for devices of type C, CT|1|1|
|WM200 for devices of type W, WT, 2WT|1 or 2**|1 or 2**|
|Two-paired screw terminals (dominos)| 1 or 2**|1 or 2**|
|15&thinsp;cm chunks of 2-joint-wire for irometer tensiometer| 1 or 2** |1 or 2**|

^^for solar PCBA devices, 2 jumper junctions can be used instead of the 2 FF jumper wires.\
**2 for 2WT devices, otherwise 1.


[comment]: # "|Nylon joint for pg7 (diameter 12.4)|1|1|1|"

[comment]: # "This table confirms the fact that the PCBA, as compared with the PCBv2, has reduced the complexity of the assembly, and for a start, the ΩΩΩΩΩΩΩΩΩΩΩΩ"

For the device assembly, preparation and programming, you will also need: 
- 1 USB Serial FTDI breakout 3.3&thinsp;V (and USB connector to laptop);
- a solder station / soldering iron with thin solder wire;
- a tiny slotted (flat) screwdriver for the screw terminal blocks;
- a comon cruciform screwdriver;
- a drill for the plastic casing, with 7&thinsp;mm and 13&thinsp;mm bits for metal, and a step bit could ease;
- a flat cutter, a wire stripper/cutter, a needle-nose plier, etc.


[comment]: # "8-12&thinsp;mm drill bit for old gw case"



During the project, we provided some links to online webs that had available in 2022, in Pau, France, Europe, the many other components required:
[hardware-parts](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials/Intel-IrriS-low-cost-sensor-hardware-parts.pdf)
The provided web links to some vendors are only given as example. An actor willing to order the Intel-IrriS pieces should search from other vendors, available in her region, and catalog items or packs/offer that would allow to optimize cost at the time of ordering.

You could walk the following steps:
1. Parse this components table according to the chosen quantity and types of device, power supply, and to the sensors;
2. Summarize your list of required material, including the sensors, and according to your already available stock;
3. Find the best vendors and offers for your needed quantities and region;
4. Prepare combined orders of different pieces from the same vendors to reduce travel costs and delays;
5. Make the orders :)

[comment]: # "[here](../_index.md#4-list-of-components) or "


2.ii. Build the Device
==============

Now that you have all the pieces recieved, let's detail the following steps to put all together and build the device:

[comment]: # "2. Solder a 4-pin on H2 (if not already done);"
1. Drill the case for the cable gland, the switch, the antenna, (the solar panel);  
2. Install the case waterproof joint;
3. Install the cable gland;
4. Install the switch;
5. connect the switch and the battery holder to the PCB;
6. connect the sensors' wires to the PCB;
7. (Solder 2 MM wires to the solar panel and connect them to the PCB);
8. Connect H2 pins according to battery type;
9. Connect the antenna.

The following and last three steps should be done after next section (programming the Arduino): 

10. Place the Arduino and test a transmission using a serial connection;
11. Place the batteries in the holder and test;
12. Close the case.

[comment]: # "stick an Intel-IrriS tag on the case "




A complete bunch of detailed material has been made available all along the project, for this section two items are very important:

1. the [PCBv4-PCBA.pdf](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials//Intel-Irris-IOT-platform-PCBv4-PCBA.pdf): the Tutorial slides on building the INTEL-IRRIS IoT platform. Part 1: soil sensor device. Focus on the latest IRD PCBv4.1. This tutorial has been updated to focus on the latest IRD PCBv4.1;
[![PCBv4-PCBA.pdf](img/tuto_PCBv4-PCBA.png)](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials//Intel-Irris-IOT-platform-PCBv4-PCBA.pdf)
2. the [Intel-IrriS video 2](https://youtu.be/zcazzDbXvHk): the YouTube tutorial video showing how to build the outdoor LoRa IoT soil sensor device.  
[![Video Build Device](img/you_build_dev.png)](https://youtu.be/zcazzDbXvHk?start=0&end=380 "Video Build Device Howto")

[comment]: # "[![Video Build Device](img/you_build_dev.png)](https://www.youtube.com/v/zcazzDbXvHk?start=0&end=380&autoplay=1 "

[comment]: # "=>6:20"

## 1. Drill the case for the cable gland, the switch, the antenna, (the solar panel);  
The following dimensions are given for an IP65 box which dimension is 115 x 65 x 40&thinsp;mm.

**Choose** one side of the case for the cable gland and the switch. Leave the other for the SMA connector (antenna).
Use drilling bits for metal (not for wood nor concrete).

**Measure** and prepare the following distances from the flat side of the case, since its corners are rounded.

||from left edge:|from right edge:|from outside bottom edge:|drill bit:|
|--|--|--|--|--|
|SMA connector|-|27&thinsp;mm***|11&thinsp;mm***|7&thinsp;mm|
|Switch|-|20&thinsp;mm|9&thinsp;mm|7&thinsp;mm|
|Cable gland|-|41&thinsp;mm|9&thinsp;mm|13&thinsp;mm*|
|Solar panel|-|-|-|10 to 12&thinsp;mm**|

*it is recommended to use a step drill bit to first get a 12mm hole before using the 13mm drill bit.\
**in the center of the case's cover.\
***these dimensions have been updated for the latest PCBA and enable to place three AAA batteries with their holder under the PCB. The video [Intel-IrriS video 2](https://youtu.be/zcazzDbXvHk) mentions a 28 x 9&thinsp;mm compatible with the older PCBv2.


**Remove** unwanted plastic part with a flat cutter and/or a small plier for instance, and smooth the inside part of the case to make the interface the most waterproof possible.


More info in the [PCBv4-PCBA.pdf](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/Tutorials//Intel-Irris-IOT-platform-PCBv4-PCBA.pdf) slides 35-43.

More info in the [Intel-IrriS video 2](https://youtu.be/zcazzDbXvHk):
[![Video Drill Device](img/you_drill_dev.png)](https://youtu.be/zcazzDbXvHk?start=72&end=305 "Video Drill Device Howto")

[comment]: # "1:12 - 5:05"

## 2. Install the case waterproof joint;
## 3. Install the cable gland;
44
5:05-5:43
## 4. Install the switch;
44
5:43
## 5. connect the switch and the battery holder to the PCB;
17-25
## 6. connect the sensors' wires to the PCB;
18
21
## 7. (Solder 2 MM wires to the solar panel and connect them to the PCB);
27-28-29
## 8. Connect H2 pins according to battery type;
26
## 9. Connect the antenna.
44-46
## 10. Place the Arduino and test a transmission using a serial connection;
See next section.
31
## 11. Place the batteries in the holder and test;
See next section.
## 12. Close the case.
Check that the switch, the antenna, and the cable gland are tightly screwed to the case;
Then just screw down the case cover. Make sure all the wires are inside the case so that they suffer no damage at closing the case. 


2.iii. Program the Device
======================
bla

[comment]: # "Il faut identifier les étapes que l'on va demander aux 'apprenants' de valider, et ce qu'ils faut qu'ils montrent ou vérifient. Par exemple: 'When flashing the ProMini with the INTEL-IRRIS code, what do you see in the Serial Monitor?'"

[comment]: # "déjà, qu'ils arrivent bien à récupérer le code du github, à configurer l'arduino IDE, à sélectionner le bon board, ..."




2.iv. Debug the Device
====================


2.v. Learn more info
====================

bla

## 1. PCB variants
### a. WaziSense v2.0, Waziup design
![WaziSense Board](img/WaziSense-v2.png)

More info:
[WaziSense Intro](../../../../resources/Boards/WaziSense/index.md); 
[WaziSense User Manual](../../../../resources/Boards/WaziSense/user_manual.md)

### b. UPPA PCB v2, UPPA's design [this version is outdated]
![PCBv2 UPPA](img/PCB-v2.png)

More info:
[UPPA PCB v2](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/PCBs/README.md#pcb-v2)

#### List of additional components for this PCBv2

||for PCBv2|
|--------------|----|
|12-pin screw terminal block (green)|1^ or 2|
|2-pin or 4-pin screw terminal block (green) | 1 |
|12-pin female header | 2 |
|RFM95W (868&thinsp;MHz) or RFM96W (433&thinsp;MHz)| 1 |
|SMA female PCB connector for 1.6&thinsp;mm PCB| 1 |
|1 4.7&thinsp;kΩ*, 1 or 2** 10&thinsp;kΩ resistor(s) |1|
|10 heat-shrink tubes to isolate wires***|1|

^for devices type C (with a capacitive sensor only), see [2.i.3](#3-choose-the-sensors)\
*for devices with temperature sensors, see [2.i.3](#3-choose-the-sensors)\
**for devices with 1 or 2 watermark sensors, see [2.i.3](#3-choose-the-sensors)\
***2 tubes for each resistor's end wire.

[comment]: # "|Nylon joint for pg7 (diameter 12.4)|1|1|1|"

[comment]: # "This table confirms the fact that the PCBA, as compared with the PCBv2, has reduced the complexity of the assembly, and for a start, the ΩΩΩΩΩΩΩΩΩΩΩΩ"

### c. UPPA PCB RAK3172 v1, UPPA's design [this version is not the common one]
![PCB Rak](img/PCB-rak-v1.png)
More info:
[UPPA PCB RAK3172 v1](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/PCBs/README.md#pcb-rak3172-v1)

### d. IRD PCB v4.1, IRD/UPPA's design [this is the raw (non assembled) current version]
![PCB41top](https://github.com/CongducPham/PRIMA-Intel-IrriS/raw/main/images/ird-pcb-4-1-raw-top.png)
![PCB41bottom](https://github.com/CongducPham/PRIMA-Intel-IrriS/raw/main/images/ird-pcb-4-1-raw-bottom.png)
More info:
[IRD PCBA v4.1](https://github.com/CongducPham/PRIMA-Intel-IrriS/blob/main/PCBs/README.md#pcb-ird-v41)



## 2. Power consumption studies

2.vi. Device's Quizz
=====================


[comment]: # "<youtube>wgfhedtyjhdt</youtube>"


[comment]: # ""

<quiz id="AAAAA" type="single-choice" title="What is the best tension that should be supplied to the Intel-IrriS device, assuming that enough current is supplied too?">
	<answer feedback="You got it!" right>3.3&thinsp;V</answer>
	<answer feedback="Nope.">3.6&thinsp;V</answer>
	<answer feedback="Nope... Well tried!">3.7&thinsp;V</answer>
	<answer feedback="Thats wrong!">5.0&thinsp;V</answer>
	<answer feedback="Thats wrong too!">5.1&thinsp;V</answer>
</quiz>

<quiz id="0261c201-7AAAAAAAAAAA171-60158676498c" type="single-choice" title="What frequency band is allowed for LoRa in Europe?">
	<answer feedback="Nope.">433&thinsp;Mhz</answer>
	<answer feedback="You got it!" right>868&thinsp;MHz</answer>
	<answer feedback="Thats wrong!">Both 433 and 868&thinsp;MHz</answer>
</quiz>