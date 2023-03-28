/*
 * HC-SR04 example sketch
 *
 * https://create.arduino.cc/projecthub/Isaac100/getting-started-with-the-hc-sr04-ultrasonic-sensor-036380
 *
 * by Aidan
 */

const int TRIGPin = 3;
const int ECHOPin = 2;

float duration, distance;

void setup() {
  pinMode(TRIGPin, OUTPUT);
  pinMode(ECHOPin, INPUT);
  Serial.begin(9600);
}

void loop() {
  digitalWrite(TRIGPin, LOW);
  delayMicroseconds(2);
  digitalWrite(TRIGPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(TRIGPin, LOW);

  duration = pulseIn(ECHOPin, HIGH);
  distance = (duration*.0343)/2;
  Serial.print("Distance: ");
  Serial.println(distance);
  delay(100);
}