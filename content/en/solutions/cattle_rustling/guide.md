![Cattle with Tag](./media/cattle.jpg)

Overview
========
Cattle rustlings is increasingly becoming a major problem in many parts of Africa in recent years. Despite the growing level of cattle theft and its consequences for society, the situation has yet to receive an effective intervention.

In this guided article we will look at how to build a simple tracking solutions for livestock using a method known as **Geofencing**.

Here's what we will be learning:
- What Geofencing means and how it works
- What parts are needed
- How to read and process GPS data
- How to track objects with Geofencing
- How to transmit data collected using LoRa

What parts do we need?
=====================

To follow this user manual, one will need the following hardware:

Hardware
  - Wazidev with USB Mirco Cable
  - Neo M8/7/6 GPS Breakout Board
  - Active Ceramic GPS Antenna
  - LoRa Gateway with Internet
  - Some Jumper Wires
  - LiPo/Li-ion Battery with Holder
  
![Parts One](./media/parts_one.png)

Software
  - Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - Install [TinyGPSPlus](https://github.com/mikalhart/TinyGPSPlus) library by **Mikal Hart**
  - Install the [WaziDev](https://github.com/Waziup/WaziDev/archive/master.zip) libraries for LoRa communication. Follow the guide [here](https://waziup.io/documentation/wazidev/user-manual/#install-the-wazidev-sketchbook)

**Step \#1:** Installing TinyGPS Plus Library
=============================================
Under the **Sketch** menu in the Arduino IDE, locate **Include Libraries** and navigate to **Manage Libraries..** and click to open the libraries manager.

![Installing TinyGPSPlus](./media/lib1.png)

Search for **"tinygpsplus"** in the search box and install the version by **Mikal Hart** as shown below

![Install TinyGPSPlus](./media/lib2.png)

After installing we should see the label **INSTALLED** as shown below.

![Install TinyGPSPlus](./media/lib3.png)

We can now close the library manager.

**Step \#2:** Reading and Processing GPS Coordinates
====================================================
In order to be sure our GPS sensor works, we need to atleast see some raw GPS data containing latitute, longitude, altitude etc...
To do that we need to wire up our GPS breakout board to the Wazidev UART pins and run some basic GPS code.

We will have to use **Software Serial** to define a diffent set of pins for UART to interface the GPS with the wazidev
  
Schematics
----------
![GPS Wiring](./media/sch1.png)

Module interface:
1. VCC: Connect to the 3.3V(VCC) pin of the wazidev
2. GND: Connect to the GND pin of the wazidev
3. TX: Connect to Analog pin AO of the wazidev
4. RX: No need to connect to pin 11 as we wont be sending any commands to the GPS board

Code Sample
-----------

````c
#include <TinyGPS++.h>
#include <SoftwareSerial.h>

//Declaring pin A0 as recieve and A1 as Transmit
static const int RXPin = A0, TXPin = A1;

//Setting GPS communication Speed to default of NEO-M8 board
static const uint32_t GPSBaud = 9600;

//Creating GPS Object
TinyGPSPlus gps;

//Activating serial communication
SoftwareSerial ss(RXPin, TXPin);

void setup() {
  Serial.begin(38400);

  //Start listening for GPS Data
  ss.begin(GPSBaud);
}

void loop() {
  //When GPS data is available.
  while (ss.available() > 0)
    if (gps.encode(ss.read()))
      displayInfo();

  //If there's an error
  if (millis() > 5000 && gps.charsProcessed() < 10)
  {
    Serial.println("No GPS detected: check wiring.");
    while(true);
  }
}

void displayInfo() {
  //Checking number of satelites in sight
  if (gps.satellites.isValid()) {
    Serial.print("Sats: ");
    Serial.print(gps.satellites.value());
  } else {
    Serial.println(" INVALID SATELITE");
  }

  //Checking GPS location coordinates
  if (gps.location.isValid()) {
    Serial.print(" Location: ");
    Serial.print(gps.location.lat(), 6);
    Serial.print(" ");
    Serial.print(gps.location.lng(), 6);
  } else {
    Serial.println(" INVALID LOCATION");
  }

  //Checking Altitude/Elivation above sea level
  if (gps.altitude.isValid() ) {
    Serial.print(" Altitude: ");
    Serial.println(gps.altitude.meters());
  } else {
    Serial.println(" INVALID ALTITUDE");
  }

  //wait 1 second between checks
  delay(1000);
}
````

**NOTE:** It takes a while to obtain an accurate GPS lock on the location of the board. This Could take anywhere from seconds to several minutes for values to begin showing up in the serial monitor in this form

**Sats:** vvvvv **Location:** xxxxx yyyyy **Altitude:** zzzzz

where:
- vvvvv is the number of satelites the tracker sees
- xxxxx is the longitude
- yyyyy is the latitude

**Step \#3:** Tracking Using Geofencing
=======================================

Now that we are able to see the GPS coordinates, the next thing is to set a fixed coordinate and determine how far new coordinates received are from fixed coordinate.
We can do this calculation using the Haversine Formular. The haversine formula determines the great-circle distance between two points on a sphere given their longitudes and latitudes.

![Haversine Formular](./media/haversine.png)

Lets take a look at how to implement the Haversine Formular in our previous GPS code.

Code Sample
-----------
`````c
//Adding GPS and Software Serial Library
#include <TinyGPS++.h>
#include <SoftwareSerial.h>

//Declaring pin A0 as recieve and A1 as Transmit
static const int RXPin = A0, TXPin = A1;

//Setting GPS communication Speed to default of NEO-M8 board
static const uint32_t GPSBaud = 9600;

//This is the fixed location's GPS Coordinates(this can be the cattle owners land)
const float fixedlat = xxxxx; // insert your latitude
const float fixedlon = yyyyy; // insert your longitude

//Creating GPS Object
TinyGPSPlus gps;

//Activating serial communication
SoftwareSerial ss(RXPin, TXPin);

void setup() {
  Serial.begin(38400);

  //Start listening for GPS Data
  ss.begin(GPSBaud);
}

void loop() {
  //When GPS data is available.
  while (ss.available() > 0)
    if (gps.encode(ss.read()))
      displayInfo();

  //If there's an error
  if (millis() > 5000 && gps.charsProcessed() < 10)
  {
    Serial.println(F("No GPS detected: check wiring."));
    while (true);
  }
}

void displayInfo() {
  //Checking for number of Valid Satelites in sight
  if (gps.satellites.isValid()) {
    Serial.print("Sats: ");
    Serial.print(gps.satellites.value());
  } else {
    Serial.println(" INVALID SATELITE");
  }

  //Checking GPS location coordinates
  if (gps.location.isValid()) {
    Serial.print(" Location: ");
    float newlat = gps.location.lat();
    float newlon = gps.location.lng();
    float distance = calcDistance(fixedlat, fixedlon, newlat, newlon);
    Serial.print(newlat, 6);
    Serial.print(" ");
    Serial.print(newlon, 6);
    Serial.print(" ");
    Serial.print(distance);
    Serial.print("m");
  } else {
    Serial.println(" INVALID LOCATION");
  }

  //Checking Altitude/Elivation above sea level
  if (gps.altitude.isValid() ) {
    Serial.print(" Altitude: ");
    Serial.println(gps.altitude.meters());
  } else {
    Serial.println(" INVALID ALTITUDE");
  }

  //wait 1 second between checks
  delay(1000);
}

//Calculating distance between fixed coordinates and new coordinates
float calcDistance(float lat1, float lon1, float lat2, float lon2) {
  float dlon, dlat, a, c;
  float dist = 0.0;
  dlon = dtor(lon2 - lon1);
  dlat = dtor(lat2 - lat1);
  a = pow(sin(dlat / 2), 2) + cos(dtor(lat1)) * cos(dtor(lat2)) * pow(sin(dlon / 2), 2);
  c = 2 * atan2(sqrt(a), sqrt(1 - a));

  dist = 6378140.0f * c;  //radius of the earth (6378140 meters) in feet 20925656.2
  return (dist + 0.5);
}

//Convert degrees to radians
float dtor(float fdegrees) {
  return (fdegrees * PI / 180);
}
`````
The data from the serial monitor this time would look like this.
**Sats:** vvvvv **Location:** xxxxx yyyyy ddddd **Altitude:** zzzzz

where:
- vvvvv is the number of satelites the tracker sees
- xxxxx is the longitude
- yyyyy is the latitude
- ddddd is the distance between coordinates in meters
- zzzzz is the altitude

**Step \#4:** Transmitting Data using LoRa 
=======================================

To transmit the data collected over LoRa to the cloud, we need a gateway.

NOTE: the Gateway must already be configured and have internet access. For how to setup the Wazidev to communicate with the gateway, be sure to see Module 5 Lecture 1.

At this point we just need to pass on the distance between coordinates to **xlpp.addAnalogInput()** and gps coordinates to **xlpp.addGPS()** functions for transmission to the gateway.

**Step \#5:** Final Touches
===========================
Putting the 