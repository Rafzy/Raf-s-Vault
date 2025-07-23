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
- Steep slope: Close to a switch - either on or off

## Diode Ratings and Selection

![[image-142.png|469x212]]

### Selection guideline
1. VRRM -> Peak to peak voltage (Vp-p)
2. IF(AV) -> 2x estimated max current
3. IFSM -> 10x estimated average current

For AC applications:
$V_{p-p} = 2\sqrt{ 2 } VRMS (1+\epsilon)$
$\epsilon$ = expected fluctuation
## Diode Applications

### Rectifier circuits
#### Power OR circuits
- Two power sources with diodes
- Output gets power from whichever source is higher
- prevents reverse current flow between sources

#### Full-wave rectifier
- Bridge configuration with 4 diodes
- Converts AC to pulsating DC
- Both halves of AC cycles are used

### Protection Circuits

#### Flywheel (Flyback) Diode
- Protects against inductive voltage spikes
- Placed across inductors/coils
- Provides path for current when switch opens 
#### Clamping diode
- Protects semiconductors from overvoltage
- Limits voltage to safe levels

### Zener Diodes

Special diodes with controlled breakdown
- Steep reverse characteristics = constant voltage
- Used for voltage regulation
- Current must be limited!

Applications:
- Voltage regulatros
- Input protection circuits
- Reference voltage sources

## Light Emitting Diodes (LEDs)

### LED Basics
- Recombination of carriers produces photons (light)
- Different colors have different forward voltages
	- Infrared: ~1.2V
	- Red: ~1.8V
	- Orange: ~2.0V
	- Green : ~2.2V
	- Yellow: ~2.2V
	- Blue: ~3.0V
	- White: ~3.2V
	- UV: ~3.5V

### LED Driving Circuit

Formula:
$$
R = \frac{V-V_{f}}{I_{f}}
$$

- $R$ = Current limiting resistor
- $V$ = Supply voltage
- $V_{f}$ = LED Forward voltage
- $I_{f}$ = Desired LED current

==LEDs can act as light sensors in reverse!!!==

## Photodiodes

- Operates in reverse bias mode
- Light increases reverse current
- Two modes:
	- Photovoltaic: Generates voltage
	- Photoconductive: Current proportional to light intensity


# Session 4

## Introduction to switches

### Basic function

Switch turns on or off a current

Different functions of switches:
- Toggle/power switch: For power control
- DIP Switch: Input presetting
- Tact switch: Momentary input in real time
- Reed switch: Sensor (activated by magnetic field)
- Microswitch: Sensor with mechanical actuation
- Joyswitch: Not technically a switch but has switch functionality


## Switch forms and terminology

![[image-143.png]]

### Poles and throws
**Throw:** Number of contacts
- Single throw (ST): Form A or B (one contact position)
- Double throw (DT): Form C (two contact position)

**Pole:** number of circuits
- Single Pole (SP): Single circuit
- Double Pole (DP): Double circuit (Like two independent switches)

### Common configurations
1. SPST (Single pole single throw): Simple ON/OFF
2. SPDT (Single Pole Double Throw): One input, two outputs
3. DPST (Double Pole, single throw): Two independent ON/OFF
4. DPDT (Double Pole, Double Throw): Two independent changeover switches

## Switch Actions

### Momentary vs alternate action

#### Momentary Action:
- Returns to original position when released
- Example: Push button (springs back)

#### Alternate action:
- Stays in new position after actuation
- Example: Toggle switch

## Switch rating and arc generation

### Operating Range chart

![[image-144.png]]

As current increases, maximum safe voltage decreases.

### Arc generation
Term when switch contacts separate but:
- Current tries to continue flowing
- Creates an electric arc between contacts
- Can damage contacts and create safety hazards

DC ratings are lowr than AC because
- AC naturally crosses zero 120 times/second
- This helps extinguish arcs
- DC has no zero crossings, making arcs harder to break


## Switch logic and microcontroller interface

### Switch status vs logic
=='1' doesn't always mean ON==

1. Active high (Pull down)
	- Switch ON = Logic '1' (5v)
	- Switch OFF = Logic '0' (0v)
2. Active Low (Pull up)
	- Switch ON = Logic '0' (0v)
	- Switch OFF = Logic '1' (5v)

### Basic switch circuits for microcontroller
- Pull-up/Pull-down resistor : Ensures defined logic level
- Current protection resistor: Protects against short

## Switch bouncing

### Problem
When a mechanical switch changes state:
- Contacts don't make clean connection immediately
- Bounce multiple times (milliseconds)
- Creates multiple ON/OFF tranisitions
- Can cause false triggers

### Solution
1. Mechanical debouncing
	- Spring loaded mechanisms
	- Bistable action
2. Electrical debouncing
	- R1 (100$\ohm$ + C1(100$nF$) creates a low pass filter
	- Schmitt trigger provides clean digital output
	- Filters out fast bounces
3. Software debouncing
```
1. Check switch state
2. If changed, wait 10-50ms (blocking delay)
3. Check again
4. If still changed, accept new state
```


# Session 5

## Introduction to sensors

### What are sensors
Devices that convert physical phenomena into electrical signals that can be processed by microcontrollers

**Goal:** Produce a changing voltage signal to be fed into microprocessor

### Typical Electrical Signal gates
- Resistance gates (Thermistors, photoresistors)
- Capacitance change (humidity, proximity)
- Voltage change (thermocouples, piezoelectric)
- Current changes (photodiodes)

## Sensor terminology

### Key Terms
#### Transfer function
- Signal response from the sensor
- Mathematical relationship between input and output
#### Sensitivity
- Slop of transfer function
- How much output changes per unit input charge
#### Resolution
- Minimum detectable change in input signal
- Smallest increment sensor can detect
#### Etc


## Analog vs Digital Signals

### Analog signals
- Contains all information
- Continuous values
- Attenuates, contains noise
- Most sensors inherently analog

### Digital signals
- Information is quantized (discrete values)
- Robust, easy to transmit long distances
- Most microprocessors inherently digital


## Thermistor

Types:
- NTC (Negative temperature coefficient): Resistance decreases with temperature
- PTC (Positive temperature coefficient): Resistance increases with temperature


Temperature formula:
$$
T[C\degree] = \frac{298.15 \beta}{298.15 \ln\left( \frac{c}{1023-c}+\beta \right)} - 273.15
$$
![[image-146.png]]

## Photoresistor

### Characteristics:
- Light energy-dependent resistor
- Similar to human's eye's spectral response

![[image-145.png|327x159]]

## Vibration switch

Mechanical switch consisting of high compliance spring

![[image-147.png|396x219]]

# Session 7

## Event driven programming vs Traditional programming

Traditional programming -> sequential/synchronous
Event driven programming -> Asynchronous (the program's flow is determined by events, which are unpredictable occurrences).

### Events, Actions, States

- **Events**: Instantaneous change in environment
- **Actions**: Instantaneous response to an event
- **State**: Condition or mode of the system resulting from an action

![[image-148.png]]


## Finite state machine

(Honestly u learned this in software design)
Just be careful about what counts as events, it needs to be an **Instantaneous** change

![[image-150.png|579x328]]

![[image-149.png|577x286]]



# Session 9

## Transistors as switches

Transistors are more versatile switches because they use a small current at the base to control a much larger current flowing from the **collector** to the **emitter**. Separating the control (input) and load (output) circuits.

