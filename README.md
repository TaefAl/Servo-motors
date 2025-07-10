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





# The Algorithm for humanoid robot 
* Initialization: Setting up the robot's initial state and parameters
* Walking Phases (repeated for each step):

Phase 1: Weight shift to support foot
Phase 2: Lift swing foot off ground
Phase 3: Swing foot forward
Phase 4: Lower foot to ground
Phase 5: Transfer weight to new support foot

* Finalization: Stabilize and return to standing position
The algorithm uses a state machine approach where each phase has specific joint angle targets and center of mass adjustments. The loop continues until the desired number of steps is completed, then the robot stabilizes in a balanced standing position.
Key decision points include determining which foot to swing (alternating left/right) and checking if more steps are needed. Each phase includes safety checks and gradual movements to maintain balance throughout the walking cycle

