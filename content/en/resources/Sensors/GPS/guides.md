---
date: 2020-07-24T09:00:00+00:00
title: NEO-8M GPS Module
type: guide
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
  Serial.print("---->");
  Serial.println(GPSBuffer);
  // Serial.flush();
}

bool isGGA(){
  return (GPSBuffer[1] == 'G' && (GPSBuffer[2] == 'P' || GPSBuffer[2] == 'N') && GPSBuffer[3] == 'G' && GPSBuffer[4] == 'G' && GPSBuffer[5] == 'A');
}
// GPGGA and GNGGA for the Ublox 8 series. Ex:
// no fix -> $GPGGA,,,,,,0,00,99.99,,,,,,*63
// fix    -> $GPGGA,171958.00,4903.61140,N,00203.95016,E,1,07,1.26,55.1,M,46.0,M,,*68 

void decodeGGA(){
int i, j;
char latitude[30], longitude[30];
byte latIndex=0, lgtIndex=0;
  
  for (i=7, j=0; (i < GPSIndex) && (j<9); i++) { // We start at 7 so we ignore the '$GNGGA,'
    
    if (GPSBuffer[i] == ','){
      j++;    // Segment index
    }
    else{
      if (j == 1){   // Latitude
        latitude[latIndex++]= GPSBuffer[i];
      }
      else if (j == 2){   // Latitude Direction: N=North, S=South
        lat_direction = GPSBuffer[i];
      }      
      else if (j == 3){    // Longitude
        longitude[lgtIndex++]= GPSBuffer[i];
      }
      else if (j == 4){   // Longitude Direction: E=East, W=West
        lgt_direction = GPSBuffer[i];
      }
    }
  }
  // Serial.print("Lat Direction: "); Serial.println(lat_direction);
  //Serial.print("Lgt Direction: "); Serial.println(lgt_direction);
  gps_latitude = degree_location(atof(latitude), lat_direction);
  gps_longitude = degree_location(atof(longitude), lgt_direction);
}

bool isValidLocation(){
  return (gps_latitude != 0.0 && gps_longitude != 0.0 && (lat_direction == 'N' || lat_direction=='S') && (lgt_direction=='E'|| lgt_direction=='W'));
}

void display_location(){
  Serial.println("==============");
  Serial.print("Location: ");
  Serial.print(gps_latitude, 5);
  Serial.print(",");
  Serial.println(gps_longitude, 5);
  Serial.println("=============="); 
}

//////////////////////////////////////////////////////////////////////////////////
//Convert NMEA latitude & longitude to decimal (Degrees)
//  Notice that for latitude of 0302.78469,
//              03 ==> degrees. counted as is
//              02.78469 ==> minutes. divide by 60 before adding to degrees above
//              Hence, the decimal equivalent is: 03 + (02.78469/60) = 3.046412
//  For longitude of 10601.6986,
//              ==> 106+1.6986/60 = 106.02831 degrees
//  Location is latitude or longitude
//  In Southern hemisphere latitude should be negative
//  In Western Hemisphere, longitude degrees should be negative
//////////////////////////////////////////////////////////////////////////////////

double degree_location(double loc, char loc_direction){
  double degLoc = 0.0;
  double degWhole= loc/100; // gives the whole degree part of latitude
  double degDec = (degWhole - ((int)degWhole)) * 100 / 60; // gives fractional part of location
  degLoc = (int)degWhole + degDec; // gives complete correct decimal form of location degrees
  
  if (loc_direction =='S' || loc_direction =='W') {  
    degLoc = (-1)*degLoc;
  }
  return degLoc;  
}

void setup(){
  Serial.begin(9600);
  // if only 1 serial port then gps_serial is equivalent to Serial  
  gps_serial.begin(9600);
 
  Serial.println("GPS basic program");
}

void loop(){
  bool get_fix = false;
  while (!get_fix){
    parseNMEA();
    if (isGGA()){
      decodeGGA();
      if (isValidLocation()){
        display_location();
        get_fix = true;
      }
    }
  }
}
```

{{< alert >}}
The raw source of the sketch example is visible [here](src/sketch/Arduino_GPS_Parser_GGA/Arduino_GPS_Parser_GGA.ino).
{{< /alert >}}

## GPS output 

First output when GPS module is trying to get a fix.

```
---->$GPGGA,,,,,,0,00,99.99,,,,,,*48
---->$GPGSA,A,1,,,,,,,,,,,,,99.99,99.99,99.99*30
---->$GPGLL,,,,,,V,N*64
---->$GPRMC,,V,,,,,,,,,,N*53
---->$GPVTG,,,,,,,,,N*30
```

This is repeated until the GPS module gets a GPS fix. When this is done, the output looks like the one below. This
too will continue to repeat itself, without interruption.

```
---->$GPGGA,100428.00,4318.85527,N,00021.88426,W,1,06,4.89,203.0,M,49.1,M,,*4F
==============
Location: 43.31425, -0.36474
==============
---->$GPGSA,A,3,01,18,11,31,22,32,,,,,,,6.57,4.89,4.38*07
---->$GPGSV,2,1,08,01,75,061,10,08,16,164,11,11,64,137,13,14,31,052,*7E
---->$GPGSV,2,2,08,18,48,102,19,22,81,019,11,31,06,087,12,32,14,039,19*70
---->$GPGLL,4318.85527,N,00021.88426,W,100428.00,A,A*74
---->$GPRMC,100429.00,A,4318.85531,N,00021.88413,W,0.636,,061118,,,A*61
---->$GPVTG,,T,,M,0.636,N,1.179,K,A*2E
---->$GPGGA,100429.00,4318.85531,N,00021.88413,W,1,05,5.24,203.2,M,49.1,M,,*48
==============
Location: 43.31425, -0.36474
==============
---->$GPGSA,A,3,18,11,31,22,32,,,,,,,,7.19,5.24,4.92*0B
---->$GPGSV,2,1,08,01,75,061,09,08,16,164,11,11,64,137,12,14,31,052,*77
---->$GPGSV,2,2,08,18,48,102,18,22,81,019,12,31,06,087,12,32,14,039,20*78
---->$GPGLL,4318.85531,N,00021.88413,W,100429.00,A,A*74
---->$GPRMC,100430.00,A,4318.85457,N,00021.88406,W,0.602,,061118,,,A*6B
---->$GPVTG,,T,,M,0.602,N,1.115,K,A*23
---->$GPGGA,100430.00,4318.85457,N,00021.88406,W,1,06,2.08,203.3,M,49.1,M,,*4E
==============
Location: 43.31425, -0.36473
==============
```

