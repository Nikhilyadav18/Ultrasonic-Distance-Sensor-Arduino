
# Ultrasonic Distance Sensor (Arduino)

This project uses an **HC-SR04 ultrasonic sensor** with Arduino to measure distance and display it on the Serial Monitor.

## Components Used:
- Arduino Uno
- HC-SR04 Ultrasonic Sensor
- Jumper Wires
- Breadboard
- (Optional) Buzzer/LED for alerts

## Wiring:
- VCC → 5V  
- GND → GND  
- TRIG → Pin 3  
- ECHO → Pin 2  

## Code:
```cpp
#define echo 2
#define trigg 3

void setup() {
  pinMode(trigg, OUTPUT);
  pinMode(echo, INPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(trigg, LOW);
  delayMicroseconds(2);
  digitalWrite(trigg, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigg, LOW);

  long duration = pulseIn(echo, HIGH, 30000);

  if (duration == 0) {
    Serial.println("No object detected or out of range");
  } else {
    float dis = 0.0343 * duration / 2;
    Serial.print("Distance: ");
    Serial.print(dis);
    Serial.println(" cm");
  }

  delay(500);
}
