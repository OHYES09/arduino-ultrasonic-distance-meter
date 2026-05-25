# Arduino Ultrasonic Distance Meter

## Overview
This project is a real-time distance measurement system built using Arduino Uno and the HC-SR04 ultrasonic sensor. The system measures the distance between the sensor and nearby objects using ultrasonic wave reflection and displays the measured distance through the Serial Monitor. An LED indicator turns ON when an object comes within a predefined range.

---

## Components Used
- Arduino Uno
- HC-SR04 Ultrasonic Sensor
- LED
- 220Ω Resistor
- Breadboard
- Jumper Wires

---

## Features
- Real-time distance measurement
- LED proximity indication
- Serial monitor output
- Accurate short-range object detection
- Beginner-friendly embedded systems project

---

## Working Principle
The HC-SR04 sensor transmits ultrasonic waves and waits for the echo signal reflected from nearby objects. The Arduino calculates the travel time of the wave and converts it into distance using the speed of sound.

Distance Formula:

d = (v × t) / 2

Where:
- d = distance
- v = speed of sound
- t = echo travel time

---

## Circuit Connections

### HC-SR04 Connections

| HC-SR04 Pin | Arduino Pin |
|------------|-------------|
| VCC | 5V |
| GND | GND |
| TRIG | D9 |
| ECHO | D10 |

### LED Connections

| LED | Arduino |
|-----|----------|
| Long Leg (+) | D8 through 220Ω resistor |
| Short Leg (-) | GND |

---

## Arduino Code

```cpp
#define trigPin 9
#define echoPin 10
#define ledPin 8

void setup() {

  Serial.begin(9600);

  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  pinMode(ledPin, OUTPUT);
}

void loop() {

  long duration;
  int distance;

  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);

  digitalWrite(trigPin, LOW);

  duration = pulseIn(echoPin, HIGH);

  distance = duration * 0.034 / 2;

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  if(distance < 15) {
    digitalWrite(ledPin, HIGH);
  }
  else {
    digitalWrite(ledPin, LOW);
  }

  delay(300);
}
```

---

## Output
Example Serial Monitor Output:

```text
Distance: 52 cm
Distance: 31 cm
Distance: 14 cm
```

LED turns ON when the object is closer than 15 cm.

---

## Applications
- Obstacle Detection Systems
- Parking Assistance Systems
- Robotics
- Distance Monitoring
- Autonomous Navigation

---

## Future Improvements
- Add buzzer alert system
- Add OLED/LCD display
- Convert into radar scanner using servo motor
- Build obstacle avoiding robot
- Add wireless monitoring using ESP32

---

## Project Structure

```text
arduino-ultrasonic-distance-meter
│
├── code/
│   └── distance_meter.ino
│
├── images/
│   ├── circuit.jpg
│   ├── setup.jpg
│   └── serial-output.png
│
└── README.md
```

---

## Author
OHYES09
