---
date: 2020-07-24T09:00:00+00:00
title: Analog LM35DZ
---

# Introduction

The LM35DZ is an integrated circuit analog sensor that can be used to measure temperature with an electrical output 
proportional to the temperature (this is why it is an analog sensor). It can measure temperature more accurately than a 
thermistor. The sensor circuitry is sealed and not subject to oxidation. The LM35DZ generates a higher output 
voltage than thermocouples and may not require that the output voltage be amplified. The LM35 has an output 
voltage that is proportional to the temperature.The scale factor is 10mV/°C (Celcius).

LM35DZ sensor is typical of many other analog temperature sensors. If you have another analog sensor then read 
the data sheet to know how to calculate the real temperature from the analog value read from the input analog pin.
                    
# Connecting to Arduino

![LM35DZ](img/lm35-arduino.png)


# Code example

```arduino
/********************
 *  Program:  LM35 sensor tester
 *  Description: Reads the voltage from a LM35 temperature
 *  sensor on pin A0 of the Arduino. Converts the voltage to 
 *  a temperature and sends it out of the serial port for 
 *  display on the serial monitor.
 ********************/
 
#define TEMP_PIN_READ A0 // Analog pin 0 (A0) to read the output of the sensor

void setup() {
  // to run once
  Serial.begin(38400); // Initialize the serial port
}

// Define a new function that reads and convert the raw reading to temperature 
float temperature_celcius() { 
  return analogRead(TEMP_PIN_READ) * (5.0 / 1023.0 * 100.0); 
}

void loop() {
  // to run repeatedly
  Serial.print(temperature_celcius());
  Serial.println("°C");
  //Serial.println("deg. Celsius");
  delay(250); // ms
}
```

# Further documentation

The technical information of this sensor is available [here](http://www.ti.com/lit/ds/symlink/lm35.pdf).

