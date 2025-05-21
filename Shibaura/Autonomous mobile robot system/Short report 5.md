
# Ultrasonic Sensors

Ultrasonic sensors utilize a high-frequency sound wave, and they calculate how long it takes for the sound to bounce back after hitting an object.
It uses three key components:
- Transmitter: Produces the waves
- Receiver: Detects the reflected wave
- Control: Processes and calculates the timing information
It works by sending out a short burst of ultrasonic waves, and when the waves hit an object, they reflect back to the sensor, and the receiver will detect these waves. The sensor then calculates the distance using the time difference between sending and receiving the waves. This formula is used to calculate the distance

$$
R = \frac{V.\Delta t}{2}[m]
$$
$$
V = 331.5 + 0.607 . T \left[ \frac{m}{s} \right]
$$
$\Delta t$: Time until ultrasonic waves return
$V$: Velocity of sound in air
$T$: temperature (C)