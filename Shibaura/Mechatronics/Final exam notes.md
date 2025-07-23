# Session 1

## Definition
Mechatronics -> smart machine design that integrates electronics and software design with traditional machine design

Mechatronics = ME (Mechanical) + EE (Electrical) + CS (Computer Science)

## Electrical circuits in mechatronics
Purpose of electrical circuits:
- Sensing/signal conditioning -> Uses voltage 
- Power/Actuator driving -> Uses current
- Communication/Pulse handling -> Digital signals
- Amplification/Sensor handling -> Analog signals


## Basic Electrical concepts

### Currents (I)
Flow of electron in a circuit loop
Formula:
$$
I=\frac{dQ}{dt}
$$
(Change in charge over time)

Unit: Amperes \[A] or Coulombs/second \[C/s]
==Important: Current flows in the opposite of electron movement (Electrons are negative)==
Current only flows in complete circuits

### Voltage (V)
Potential difference between two nodes
Good analogy: Height difference in gravitational field
Unit: Volt \[V]
Water analogy:
Voltage -> Water pressure
Current -> Water flow


## Basic Circuit law

### Ohm's law
Formula:
$$
V = IR
$$
==This defines ideal resistance; real resistance behaves close like this but not exactly==
Temp affects resistance

### Kirchoff's Law
1. Current law (KCL) : Sum of currents flowing into a node = 0
2. Voltage law (KVL) : Sum of voltages around any closed loop = 0

### Resistor properties
Resistance -> Measured in Ohms
**Power** = $P = I^{2}R = \frac{V^{2}}{R}= VI$ (Measured in watts)
Resistor limit current and emit thermal energy


## Circuit combinations

### Series resistance
$$
R_{t} = R_{1}+R_{2} + R_{3}+\dots
$$

### Parallel resistance
$$
\frac{1}{R_{t}} = \frac{1}{R_{1}} + \frac{1}{R_{2}} + \frac{1}{R_{3}}
$$

### Voltage divider
Simple series voltage divider:
$$
V_{out} = V_{in} \left( \frac{R_{2}}{R_{1}+R_{2}} \right)
$$

## Ac Circuits

### AC (Alternating Current )
Current and voltage change direction over time
Polarity reverses periodically
"Ripple" current is not AC - it has to change direction


### Phasor analysis
Converts time-domain sine function to phasor (Phase vector) representation

$j = \sqrt{ (-1) }$ in electrical engineering

Impedance in AC circuits:
- Resistor: $Z = R$
- Inductor: $Z = j \omega L$
- Capacitor: $Z = \frac{1}{j \omega C}$


## Circuit Diagrams

### Diagram vs Implementation

Illustration -> Physical representation
Diagram/Schematics -> Uses standardized symbols

![[image-139.png|421x219]]

![[image-140.png|423x239]]


![[image-141.png|428x202]]


# Session 3 (Diodes)

## Intro to Diodes

### What is a diode?
Basic semiconductor/active discrete device that allows current to flow in only one direction. There are slightly different types of diodes

- **1N4001**: Power diode that allows large current
- **1N4148**: High speed switching diode for small signals
- **1N4007**: Recommended for general use

### Active vs Passive devices
Active devices = Amplification and rectification capabilities
Semiconductors != Always active devices

Ex:
Passive semiconductors: Thermistors, photoresistors
Active non-semiconductors: Relays


## Semiconductor theory

### Energy band structure
How semiconductors work:
- Insulators -> Large bandgap between valence and conduction bands
- Conductors -> Overlapping bands
- Semiconductor -> Small bandgap that can be overcome with small energy
Concept : Semiconductors can be switched to conductors with small energy input


## Diode operation principles

### Forward and reverse bias
Diode acts as a voltage-controlled switch
**Forward biased** (Switch closed)
- Positive terminal to anode, negative to cathode
- Current flows
- Acts like a closed switch

**Reverse biased** (Switch open)
- Negative terminal to anode, positive to cathode
- No current flows
- Acts like an open switch

## V-I characteristics
### Key points
- Forward voltage (Vf) = ~0.72 for silicon diodes
- Reverse voltage (VRRM) = -100V for 1N4148
- Forward current : Increases rapidly after Vf threshold
- Reverse current: Very small ($\mu A$ range) until breakdown
- 