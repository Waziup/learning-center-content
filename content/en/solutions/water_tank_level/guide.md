![Water Spillage](./media/tanks.jpg)

Overview
========

Its very common to see water storage tanks overflowing in most places where a pump is used. These overflows lead to wastage of water and higher electricity bills due to the water pumps running longer than necessary.

Luckily, we are in a digital age in which certain basic aspects of our daily lives can be automatated.

In this guide, we will look at how to automatically control the water level in a tank by switching the water pump ON, when the water level goes below a predetermined level. The circuit automatically switches the water pump OFF when the tank is full as well.


Here's what we will be learning:
- What parts are needed
- How to wire up and read sensor values
- How to trigger an actuator
- How to communicate to the cloud over LoRa

What parts do we need?
======================

To follow this user manual, one will need the following:

Hardware
  - WaziACT
  - FTDI FT232
  - Mini USB Cable
  - Wazigate
  - SR04 Ultrasonic Sensor
  - Some Jumper Wires
  - Lora 868Mhz Antenna

![Parts One](./media/autowater.png)

Software
  - Install the [Arduino IDE](https://www.arduino.cc/en/Main/Software) for the programming aspects.
  - Install the [WaziDev](https://github.com/Waziup/WaziDev/archive/master.zip) libraries for LoRa communication. Follow the guide [here](https://waziup.io/documentation/wazidev/user-manual/#install-the-wazidev-sketchbook)

**Step \#1:** Wiring and Reading Sensor Values
============================================

To be able to detect the current water level in the tank, we need to use the waterproof ultrasonic distance sensor.

The sensor head emits an ultrasonic wave and receives the wave reflected back from the target. The ultrasonic Sensor measures the distance to the target by measuring the time between the emission and reception of the ultrasonic signal.

![Ultrasonic Working](./media/ultrasonicworking.png)

Schematic
---------

![Water Level Wiring](./media/waterwire.jpg)

**NOTE:** we used the digital pin d4 as the VCC/power source for the ultrasonic sensor. This is to enable us to switch off the sensor completely if need be in the future. Because each digital pin can handle 40mA max current draw, the 30mA operating current of the sensor wont be an issue. we can see this from the manufactureres data sheet.

Lets also note that the waterproof ultrasonic sensor we are using has a minimum range of 25cm. This means that below 25cm the sensor reading might not be accurate. However we can read up to 5 meters max. This may good enough for most use cases.

![Sensor Specs](./media/specs.png)

Code Sample
-----------

````c
//sensor pins
#define trigPin  9
#define echoPin  5

//sensor power pin
#define powerPin  4

void setup() {
  Serial.begin(9600);
  
  //turning sensor on
  pinMode(powerPin, OUTPUT);
  delay(500);
  digitalWrite(powerPin, HIGH);
  
  //declaring sensor pin modes
  pinMode(trigPin, OUTPUT);
  //inputpull up to prevent noise on echo pin
  pinMode(echoPin,INPUT_PULLUP);

}

void loop() {

  //reading sensor values
  unsigned long duration = 0;
  int distance = 0;
  int average = 0;

  //taking 100 distance samples
  while (average <= 100) {
    digitalWrite(trigPin, LOW);
    delayMicroseconds(5);
    digitalWrite(trigPin, HIGH);
    delayMicroseconds(10);
    digitalWrite(trigPin, LOW);

    duration = pulseIn(echoPin, HIGH);
    distance += duration*0.034/2;
    average += 1;
    delay(30);
  }

  //finding the average of 100 samples
  distance = distance/average;

  //checking to be sure the current distance value is a number and greater than 0
  if(!(isnan(distance) || distance < 0)){
    Serial.print("Distance: ");
    Serial.print(distance); 
    Serial.println(" cm");
  }
  
  delay(10);
}
````

**Step \#2:** Triggering an Actuator with Sensor Data
=====================================================

In our previous code snample, we were able to read sensor values. Lets now use those values to trigger the relay when the water level falls to say 100cm. We will also stop or turn off the pump when the water level rises to 30cm.

NOTE: Since AC power is involved, please make sure you're wearing protective clothing. Make sure you're qualified/certified to handle the task at hand. You are 100% responsible for your safety and well being.

Schematics
----------

![Sensor Wiring](./media/waterwirev2.jpg)

Module interface:
1. VCC: Connect to the VCC pin of the WaziDev
2. GND: Connect to the GND pin of the WaziDev
3. IN: Connect to the WaziDev analog pin A0

Code Sample
-----------
```c
#include "Adafruit_Si7021.h"

Adafruit_Si7021 sensor = Adafruit_Si7021();

//MQ5 sensor pin
int smokePin = A0;

void setup() {
  Serial.begin(38400);

  Serial.println("Si7021 test!");
  
  //Activate sensor reading
  if (!sensor.begin()) {
    Serial.println("Did not find Si7021 sensor!");
    while (true)
      ;
  }
}

void loop() {
  //Read and Print Smoke Values
  int smokeVal = analogRead(smokePin);
  Serial.print("Smoke: ");
  Serial.print(smokeVal);

  //Read and Print Temp and Humidity Values
  Serial.print(" Humidity: ");
  Serial.print(sensor.readHumidity(), 2);
  Serial.print(" Temperature: ");
  Serial.println(sensor.readTemperature(), 2);

  //Wait 1 second between reads
  delay(1000);
}
```

**Step \#3:** Triggering a Buzzer when Smoke, Gas or Fire is Detected
===============================================================

Users may occasionally be away from their mobile devices, this means they may not see notifications come in from the cloud regarding smoke, gas or fire detection. It is therefore useful to add a buzzer to alert the user.

Lets take a look at how to add a buzzer and add a few more lines of code to manage it.

Schematic
---------

![Sensor Wiring](./media/firewirev2.jpg)

Code Sample
-----------
```c
#include "Adafruit_Si7021.h"

Adafruit_Si7021 sensor = Adafruit_Si7021();

//MQ5 sensor pin
int smokePin = A0;

//Buzzer pin
int buzzer = 13;

//Setting temperature and smoke threshold values
int temp_thresh = 33;
int smoke_thresh = 200;

void setup() {
  //Declaring buzzer pin mode
  pinMode(buzzer, OUTPUT);

  Serial.begin(38400);

  Serial.println("Si7021 test!");

  //Activate sensor reading
  if (!sensor.begin()) {
    Serial.println("Did not find Si7021 sensor!");
    while (true)
      ;
  }
}

void loop() {
  //Read and Print Smoke Values
  int smokeVal = analogRead(smokePin);
  Serial.print("Smoke: ");
  Serial.print(smokeVal);

  //Read and Print Temp and Humidity Values
  float hum = sensor.readHumidity();
  float temp_deg = sensor.readTemperature();

  Serial.print(" Humidity: ");
  Serial.print(hum, 2);
  Serial.print(" Temperature: ");
  Serial.println(temp_deg, 2);

  //Triggering the buzzer if the room is warm, smoke or gas is detected
  if (smokeVal > smoke_thresh || temp_deg > temp_thresh) {
    digitalWrite(buzzer, HIGH);
    delay(1000);
    digitalWrite(buzzer, LOW);
    delay(500);
  }
  //Wait 1 second between reads
  delay(500);
}
```
**Step \#4:** Combining Sensing, Alarm and Lora Communication
=============================================================

At this point, we want the WaziDev to constantly update Wazicloud with the current state of the Sensors through Wazigate.

**NOTE:** Make sure to have a configured gateway up and running before uploading this next code. Kindly see the lectures under **Module 5 Lecture 2** for how to setup a Waziup Gateway.

In order to make our project mobile, we can add a battery to power the sensor and the Wazidev as shown below.

Schematics
----------
![Final Schematic](./media/firewirev3.jpg)

Code Sample
-----------
```c
#include <WaziDev.h>
#include <xlpp.h>
#include <Base64.h>
#include "Adafruit_Si7021.h"

Adafruit_Si7021 sensor = Adafruit_Si7021();

//MQ5 sensor pin
int smokePin = A0;

//Buzzer pin
int buzzer = 13;

//Setting temperature and smoke threshold values
int temp_thresh = 33;
int smoke_thresh = 200;
// NwkSKey (Network Session Key) and Appkey (AppKey) are used for securing LoRaWAN transmissions.
// You need to copy them from/to your LoRaWAN server or gateway.
// You need to configure also the devAddr. DevAddr need to be different for each devices!!
// Copy'n'paste the DevAddr (Device Address): 26011D00
unsigned char devAddr[4] = {0x26, 0x01, 0x1D, 0x00};

// Copy'n'paste the key to your Wazigate: 23158D3BBC31E6AF670D195B5AED5525
unsigned char appSkey[16] = {0x23, 0x15, 0x8D, 0x3B, 0xBC, 0x31, 0xE6, 0xAF, 0x67, 0x0D, 0x19, 0x5B, 0x5A, 0xED, 0x55, 0x25};

// Copy'n'paste the key to your Wazigate: 23158D3BBC31E6AF670D195B5AED5525
unsigned char nwkSkey[16] = {0x23, 0x15, 0x8D, 0x3B, 0xBC, 0x31, 0xE6, 0xAF, 0x67, 0x0D, 0x19, 0x5B, 0x5A, 0xED, 0x55, 0x25};

WaziDev wazidev;

void setup()
{
  Serial.begin(38400);
  wazidev.setupLoRaWAN(devAddr, appSkey, nwkSkey);
  
  //Declaring buzzer pin mode
  pinMode(buzzer, OUTPUT);

  Serial.println("Si7021 test!");

  //Activate sensor reading
  if (!sensor.begin()) {
    Serial.println("Did not find Si7021 sensor!");
    while (true)
      ;
  }
  
}

XLPP xlpp(120);

void loop(void)
{
  //Read and Print Smoke Values
  int smokeVal = analogRead(smokePin);
  Serial.print("Smoke: ");
  Serial.print(smokeVal);

  //Read and Print Temp and Humidity Values
  float hum = sensor.readHumidity();
  float temp_deg = sensor.readTemperature();

  Serial.print(" Humidity: ");
  Serial.print(hum, 2);
  Serial.print(" Temperature: ");
  Serial.println(temp_deg, 2);

  //Triggering the buzzer if the room is warm, smoke or gas is detected
  if (smokeVal > smoke_thresh || temp_deg > temp_thresh) {
    digitalWrite(buzzer, HIGH);
    delay(1000);
    digitalWrite(buzzer, LOW);
    delay(500);
  }
  
  // 1
  // Create xlpp payload.
  
  xlpp.reset();
  
  xlpp.addTemperature(1,temp_deg);
  xlpp.addRelativeHumidity(1, hum);
  xlpp.addTemperature(2, smokeVal); //rename this temperature sensor on wazigate as smoke or to what you prefer
  
  // 2.
  // Send paload with LoRaWAN.
  serialPrintf("LoRaWAN send ... ");
  uint8_t e = wazidev.sendLoRaWAN(xlpp.buf, xlpp.len);
  if (e != 0)
  {
    serialPrintf("Err %d\n", e);
    delay(60000);
    return;
  }
  serialPrintf("OK\n");
  
  // 3.
  // Receive LoRaWAN message (waiting for 6 seconds only).
  serialPrintf("LoRa receive ... ");
  uint8_t offs = 0;
  long startSend = millis();
  e = wazidev.receiveLoRaWAN(xlpp.buf, &xlpp.offset, &xlpp.len, 6000);
  long endSend = millis();
  if (e != 0)
  {
    if (e == ERR_LORA_TIMEOUT){
      serialPrintf("nothing received\n");
    }
    else
    {
      serialPrintf("Err %d\n", e);
    }
    delay(60000);
    return;
  }
  serialPrintf("OK\n");
  
  serialPrintf("Time On Air: %d ms\n", endSend-startSend);
  serialPrintf("LoRa SNR: %d\n", wazidev.loRaSNR);
  serialPrintf("LoRa RSSI: %d\n", wazidev.loRaRSSI);
  serialPrintf("LoRaWAN frame size: %d\n", xlpp.offset+xlpp.len);
  serialPrintf("LoRaWAN payload len: %d\n", xlpp.len);
  serialPrintf("Payload: ");
  char payload[100];
  base64_decode(payload, xlpp.getBuffer(), xlpp.len); 
  serialPrintf(payload);
  serialPrintf("\n");
  
  delay(5000);
}
```

At this point, all we need to do is flash the above code to the Wazidev and place the entire unit in our desired room/space for sensing.

Since we used ```xlpp.addTemperature(2, smokeVal);``` for the smoke or gas values, we have to rename the sensor on the wazigate for clarity as shown below.

![Remaning Smoke Sensor](./media/smoke_val.png)

After renaming all our sensors and assigning them the appropriate units of measurement, we have:

![Gateway Sensors Display](./media/gateway_val.png)

We can also see the corresponding sensor data on the Wazicloud platform

![Wazicloud Sensors Display](./media/wazicloudv2.png)

we can also setup notifications on WaziCloud, for when the temperature, smoke or gas threshold conditions are met. Kindly see the lectures under **Module 5 Lecture 3** for how to setup a Notifications on Wazicloud.

![Final Schematic](./media/notification.png)