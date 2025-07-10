# Servo-motors
program 4 servo motors in Tinkercard 

# The tools:
4 Servo , 
Arduino ,
Breadboard

# The circuit: 
<img width="968" height="522" alt="Image" src="https://github.com/user-attachments/assets/6f135eed-8284-4b1f-80c4-ddcc2f256fb0" />
<img width="1579" height="982" alt="Image" src="https://github.com/user-attachments/assets/9a73d8f3-ffd0-42d8-a09d-d02ee6240cb0" />

# The Code 
#include <Servo.h>

Servo servo1;
Servo servo2;
Servo servo3;
Servo servo4;


const int servoPin1 = 3;  
const int servoPin2 = 5;  
const int servoPin3 = 6;  
const int servoPin4 = 9;  

void setup() {
  
  Serial.begin(9600);
  
  servo1.attach(servoPin1);
  servo2.attach(servoPin2);
  servo3.attach(servoPin3);
  servo4.attach(servoPin4);
  
  
  servo1.write(90);
  servo2.write(90);
  servo3.write(90);
  servo4.write(90);
  
  Serial.println("All servos set to 90 degrees");
  
  delay(1000);
}

void loop() {
 
  for (int pos = 0; pos <= 180; pos += 1) {
    servo1.write(pos);
    servo2.write(pos);
    servo3.write(pos);
    servo4.write(pos);
    delay(11); 
  }
  
  
  for (int pos = 180; pos >= 0; pos -= 1) {
    servo1.write(pos);
    servo2.write(pos);
    servo3.write(pos);
    servo4.write(pos);
    delay(11); 
  }
}

void moveAllServos(int angle) {
  if (angle >= 0 && angle <= 180) {
    servo1.write(angle);
    servo2.write(angle);
    servo3.write(angle);
    servo4.write(angle);
    
    Serial.print("All servos moved to: ");
    Serial.print(angle);
    Serial.println(" degrees");
  } else {
    Serial.println("Invalid angle! Please use 0-180 degrees.");
  }
}
