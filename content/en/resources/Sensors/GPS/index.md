---
id: gps_res
title: GPS 
type: sensor
desc: A Global Positioning System module for getting your position using satellite data.
color: "#bad8ff"
tags:
    - Hardware
    - Sensor
    - City
    - Agriculture
    - Industry
---

# Introduction

![gps](img/gps.png)

GPS modules usually use serial communication to transfer information back to the Arduino board. These information are text NMEA messages that are normalized text providing geolocalization information. More details on NMEA message format can be found  [here](http://aprs.gids.nl/nmea/).

For instance, the GPGGA message (Global Positioning System Fix Data) had the following format: 

	GPGGA,hhmmss.ss,llll.ll,a,yyyyy.yy,a,x,xx,x.x,x.x,M,x.x,M,x.x,xxxx*hh</tt>

where `llll.ll` is the latitude and `yyyyy.yy` is the longitude.

A GPS module is quite autonomous: once powered on it will try to perform a GPS fix and usually 
when the fix is obtained a green led on the module will blink. A successful fix means that all 
the fields of the GPGGA message are valid. In the provided example, the GPS module is connected to the Arduino using a software serial communication. 

Software serial means that general purpose digital pins are used for the serial TX/RX. This is useful for boards that has only 1 serial interface, e.g. mostly those based on the ATMega328P microcontroller such as the Arduino Uno/ProMini/Nano family, that is already used by the Arduino IDE to program the board. 

Here, the program constantly reads data from the GPS serial (gps_serial) and will try to decode GPGGA messages. Once a fix is obtained, the GPGGA message will provide localization data and the program will convert the latitude and longitude into decimal degree that can directly be copied/pasted into GoogleMap for instance.

There are many comments in the code for you to get more detailed information and better understand how to work with GPS sensor modules.

# Connecting to Arduino

Note how we use pins 3 and 4 for serial TX/RX from the microcontroller board. So we have `GPS_TX <> 4` and `GPS_RX <> 3`.

![gps_connection](img/gps_connection.png)

# Code example

``` c
//////////////////////////////////////////////////////////////////////
// Simple GPS Sensor : parsing GGA NMEA sentence (GPGGA or GNGGA) 
// On the Ublox 8 series GPGGA is replaced by GNGGA by default
// 
// $GNGGA,123519,4807.038,N,01131.000,E,1,08,0.9,545.4,M,46.9,M,,*47
//
// Copyright (C) 2018 Mamour Diop & Congduc Pham, University of Pau, France
/////////////////////////////////////////////////////////////////////

// #define HARDWARE_SERIAL_GPS
#define SOFTWARE_SERIAL_GPS
#ifdef HARDWARE_SERIAL_GPS

///////////////////////////////
// USING HARDWARE SERIAL
//
// On Arduino with only 1 serial port (TX/RX), it is necessary to perform the following actions 
// as the serial port is use for both the GPS and the programming. To see GPS message:

// be sure that serial monitor is not open
// connect only GPS_GND<->GND and GPS_TX<>RX
// after uploading the sketch, connect GPS_VCC<>3.3V
// then open Serial Monitor (set baud rate to 9600)
// do not connect GPS_TX
// 
// you should see NMEA messages from the GPS module
// to understand NMEA message: http://aprs.gids.nl/nmea/

// if you are using an Arduino board with several serial port (such as the MEGA)
// then define here the one that is connected to the GPS module

//#define gps_serial Serial3
#define gps_serial Serial
#endif
#ifdef SOFTWARE_SERIAL_GPS

#include < SoftwareSerial.h> 
// connect GPS_TX <> 4 and GPS_RX <> 3
SoftwareSerial gps_serial(4,3); // rx,tx 
#endif

char GPSBuffer[150];
byte GPSIndex=0;
double gps_latitude = 0.0;
double gps_longitude = 0.0;
char lat_direction, lgt_direction;

void parseNMEA(){
char inByte;
bool detect_new_line=false;
  
  while (!detect_new_line)
  {
    if (gps_serial.available()) {
      inByte = gps_serial.read();
    
      // Serial.print(inByte); // Output exactly what we read from the GPS to debug    
      if ((inByte =='$') || (GPSIndex >= 150)){
        GPSIndex = 0;
      }      
      if (inByte != '\r' && inByte != '\n'){
        GPSBuffer[GPSIndex++] = inByte;
      }   
      if (inByte == '\n'){
        GPSBuffer[GPSIndex++] = '\0';
        detect_new_line=true;
      }
    }
  } 
```

This is repeated until the GPS module gets a GPS fix. When this is done, the output looks like the one below. This
too will continue to repeat itself, without interruption.

```
==============
Location: 43.31425, -0.36474
==============

# Specifications

- Accuracy: Velocity accuracy 0.05 m/s, Heading accuracy 0.3 degrees, Horizontal position accuracy 2.5m
- CommunicationCommunication Protocol : NMEA ( default ) / UBX Binary
- Current: 35mA
- Operating voltage: 3.3 - 5V
- Interfaces: TTL level compatible with 3.3V/ 5V systems
- Length x Width x Height: Antenna Size is approx. 25mm x 25mm , Module Size is approx. 25mm x 36mm x 6mm
- Response Time: Cold start 26s, Hot start 1s
- Sensitivity: Tracking & Navigation –167 dBm
- Temperature Range: -40 C ~ 85 C
- Weight: 17 g
