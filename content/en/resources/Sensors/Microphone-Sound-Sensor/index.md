---
id: microphone_sens_small
title: Microphone Sound Sensor
type: sensor
desc: This sensor emits a signal if the microphone of the sensor detects a noise. The sensitivity of the sensor can be adjusted by means of a controller.
color: "#e6e6e6"
tags:
    - Hardware
    - Sensor
    - City
    - Industry
---

# Introduction

The KY-038 Microphone Sound Sensor is designed for threshold value measurement. It emits a digital high signal when the sound level exceeds a user-defined threshold, set via a rotary potentiometer. The LM393 comparator on the board compares this threshold value with the sensor's measured value to determine the output. The potentiometer setting defines the threshold for the digital high signal.

![microphone-small](img/microphone-small.png#width=300)

## FUNCTIONALITY OF THE SENSOR

This sensor's circuit board features two main components: the front sensor unit, which measures the environment and outputs an analog signal, and the comparator. The comparator compares the sensor's measured value with the threshold set on the rotary potentiometer. If the measured value exceeds the set threshold, the comparator outputs a logical high signal on the digital pin and activates LED L1.

<alert type="warning">The signal is inverted. If a high value is measured, this results in a lower voltage value at the analog output.</alert>


# Connecting to Arduino

![microphone-small--arduino](img/arduino-connection.svg#width=500)

# Code example

The program reads the current voltage value, which can be measured at the analog output, and displays it on the serial port.

Additionally, the console shows the status of the digital pin, indicating whether the threshold has been exceeded.

``` c
// Declaration and initialization of input pins
int Analog_Input = A0; // Analog output of the sensor
int Digital_Input = 3; // Digital output of the sensor
  
void setup  ( )
{
  pinMode (Analog_In, INPUT);
  pinMode (Digital_Input, INPUT);
       
  Serial.begin (9600) ;  //  Serial output with 9600 bps
}
  
//  The program reads the current values of the input pins
// and outputs it on the serial output
void loop  ( )
{
  float  Analogous;
  int Digital;
    
  //Current values are read out, converted to the voltage value...
  Analog =  analogRead (Analog_In)   *  (5.0 / 1023.0); 
  Digital = digitalRead (Digital_Input) ;
    
  //...  and issued at this point
  Serial.print  ("Analog voltage value:");  Serial.print (Analog,  4) ;   Serial.print  ("V, ");
  Serial.print ("Limit value:") ;
  
  if  (Digital==1) 
  {
      Serial.println (“reached”);
  }
  else
  {
      Serial.println (" not yet reached");
  }
  Serial.println  ( " ----------------------------------------------------------------") ;
  delay (200) ;
}

```

# Specification

- Operating Voltage: 3.3V to 5V DC
- LM393 comparator with threshold preset
- PCB Size: 3.4cm * 1.6cm
- Induction distance: 0.5 Meter
- Operating current:  4~5 mA
- Microphone Sensitivity (1kHz): 52 to 48 dB
