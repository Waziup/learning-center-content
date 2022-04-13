---
title: Introduction to Electronics
---


Basic knowledge of electronics is crucial to design your IoT solutions, but more importantly, it keeps yourself and your users safe from electric shock or unpredictable hazards.

Before we get into more exciting electronic components in details, let’s understand why there is a need for the ground.
In the light bulb example, everything works just fine without the ground.
However, the reason we need the ground is that of the safety issue, and electronic components can be damaged easily by the extra unwanted energy on the circuit.
The ground is not a specific component or a place.  The ground is like a buffer that can accept extra electrons or negative charges.
If you are working on a low voltage device, the ground can be the big metal table since it can accept some extra electrons without giving off charges or discharging to other things.
If you are working on a high voltage device, the best ground is the soil under a few feet below.
However, if the ground contains more sand than soil, it is not a good buffer since it does not conduct electricity well.
As a result, the ground acts like a buffer that neutralizes extra negative charges.
The circuit board does not like extra charges running around, and it can cause significant damages to the electronic components easily.

Electronics is always an exciting field of discovery and innovation.  We cannot cover all of them in detail as they are an enormous subject.
However, we hope that you will have a good overview of what small electronic component can do and how it relates to the design of your IoT solutions and learn some basics on the wonder of what electric power can do.

Tools
-----

In this section we are going to see the main tools of the electronics.

**Breadboard**

Breadboards are an essential tool for prototyping and building temporary circuits.  These boards contain holes for inserting wire and components.  Because of their temporary nature, they allow you to create circuits without soldering.  The holes in a breadboard are connected in rows both horizontally and vertically as shown below.

![Breadboard](./media/breadboard.jpg)

**Jumper Wire**

These wires are used with breadboard and development boards and are generally 22-28 AWG solid core wire.  Jumper wires can have male or female ends depending on how they need to be used.

![jumperwires](./media/jumperwires.jpg)

**Soldering Iron**

When it time to create a permanent circuit, you’ll want to solder the parts together.  To do this, a soldering iron is the tool you would use.  Of course a soldering iron isn’t any good unless you have solder to go with it.  You can choose leaded or lead-free solder in a few diameters.

![solderingiron](./media/solderingiron.jpg)

Components
----------

This section talk about the different components that make your electronic projects come to life.

**Switch** 

Switches can come in many forms such as pushbutton, rocker, momentary and others.
Their basic function is to interrupt electric current by turning a circuit on or off.

![switches](./media/switches.jpg)

**Resistor**

Resistors are used to resist the flow of current or to control the voltage in a circuit.
The amount of resistance that a resistor offers is measured in Ohms.
Most resistors have colored stripes on the outside and this code will tell you it’s value of resistance.
You can use a multimeter or Digikey’s resistor color code calculator to determine the value of a resistor.

![resistor](./media/resistors.jpg)

**Variable Resistor (Potentiometer)**

A variable resistor is also known as a potentiometer.
These components can be found in devices such as a light dimmer or volume control for a radio.
When you turn the shaft of a potentiometer the resistance changes in the circuit.

![potentiometer](./media/potentiometer.jpg)

**Light-Dependent Resistor (LDR)**

A light-dependent resistor is also a variable resistor but is controlled by the light versus turning a knob.
The resistance in the circuit changes with the intensity of the light.
These are often found in exterior lights that automatically turn on at dusk and off at dawn.

![ldr](./media/ldr.jpg)

**Capacitor**

Capacitors store electricity and then discharges it back into the circuit when there is a drop in voltage.
A capacitor is like a rechargeable battery and can be charged and then discharged.
The value is measured in F (Farad), nano Farad (nF) or pico Farad (pF) range.

![capacitor](./media/capacitor.jpg)

**Diode**

A diode allows electricity to flow in one direction and blocks it from flowing the opposite way.
The diode’s primary role is to route electricity from taking an unwanted path within the circuit.

![diode](./media/diode.jpg)

**Light-Emitting Diode (LED)**

A light-emitting diode is like a standard diode in the fact that electrical current only flows in one direction.
The main difference is an LED will emit light when electricity flows through it.
Inside an LED there is an anode and cathode.
Current always flows from the anode (+) to the cathode (-) and never in the opposite direction.
The longer leg of the LED is the positive (anode) side.

![led](./media/led.jpg)

**Transistor**

Transistor are tiny switches that turn a current on or off when triggered by an electric signal.
In addition to being a switch, it can also be used to amplify electronic signals.
A transistor is similar to a relay except with no moving parts.

![transistor](./media/transistor.jpg)

**Relay**

A relay is an electrically operated switch that opens or closes when power is applied.
Inside a relay is an electromagnet which controls a mechanical switch.

![relay](./media/relay.jpg)

**Integrated Circuit (IC)**

An integrated circuit is a circuit that’s been reduced in size to fit inside a tiny chip.
This circuit contains electronic components like resistors and capacitors but on a much smaller scale.
Integrated circuits come in different variations such as 555 timers, voltage regulators, microcontrollers and many more.
Each pin on an IC is unique in terms of it’s function.

![integrated-circuit](./media/integrated-circuit.jpg)

{{< youtube id="CzjO1LY8ZoE">}}

Circuits
--------

Before you design an electronic project, you need to know what a circuit is and how to create one properly.

An electronic circuit is a circular path of conductors by which electric current can flow.
A closed circuit is like a circle because it starts and ends at the same point forming a complete loop.
urthermore, a closed circuit allows electricity to flow from the (+) power to the (-) ground uninterrupted.

In contrast, if there is any break in the flow of electricity, this is known as an open circuit.
As shown below, a switch in a circuit can cause it to be open or closed depending on it’s position.

![open/close circuit](./media/open-and-closed-circuits.jpg)

All circuits need to have three basic elements.  These elements are a voltage source, conductive path and a load.

The voltage source, such as a battery, is needed in order to cause the current to flow through the circuit.
In addition, there needs to be a conductive path that provides a route for the electricity to flow.
Finally, a proper circuit needs a load that consumes the power.
The load in the above circuit is the light bulb.

**Schematic Diagram**

When working with circuits, you will often find something called a schematic diagram.
These diagrams use symbols to illustrate what electronic components are used and where they’re placed in the circuit.
These symbols are graphic representations of the actual electronic components.

Below is an example of a schematic that depicts an LED circuit that is controlled by a switch.
It contains symbols for an LED, resistor, battery and a switch.
By following a schematic diagram, you are able to know which components to use and where to put them.
These schematics are extremely helpful for beginners when first learning circuits.

![schematic circuit](./media/schematic.jpg)

There are many types of electronic symbols and they vary slightly between countries.
Below are a few of the most commonly used electronic symbols in the US.

![electronic symbol](./media/electronic-symbols.jpg)

**How To Determine A Resistor Size**

Resistors are commonly used in electronics projects and it’s important to know which size to use.
To find the resistor value, you need to know the voltage and the amps for your LED and battery.

A standard LED generally needs a voltage of around 2V and a current of 20mA or .02A to operate correctly.
Next, you need to find out what voltage your battery is.
In this example, we will be using a 9V battery.
In order to determine the resistor size, we need to use a formula known as Ohm’s law as shown below.

Resistance (R) = Voltage (V) / Current (I)

- Resistance is measured in Ohms (Ω)
- Voltage is measured in volts (V)
- Current is measured in amps (A)

![resistor-size](./media/resistors-size.jpg)


