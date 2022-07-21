# Robot Arm

Hello, I am Enmanuel. My project is a mechanical arm that can be controlled through a variety of ways, including processing. The arm will be able to grab, hold, and transfer small, light items. This will be accomplished through the usage of five servo motors that will be connected to the robot arm.

<p align="center">
  <a href="https://ibb.co/8zCDMN4"><img src="https://i.ibb.co/DGJD4zg/Face.jpg" alt="Face" border="0"></a>
</p>

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Enmanuel | The Renaissance Charter School | Electrical Engineering | Incoming Senior

# My Project

<p align="center">
  <a href="https://ibb.co/zfzqFBn"><img src="https://i.ibb.co/Jk9DqGB/Arm.jpg" alt="Arm" border="0"></a>
</p>

# Final Milestone
My final milestone is using processing to control the arm. Processing is a new computer language/extension of the Java language which aims to introduce programming languages to electronic art and electronic art to programmers. The first step to my final milestone was to download processing, which was very simple. The next step was to upload the code to the arm that would allow it to receive and inputs from processing. Finally, I had to run the code in the processing app that would allow it to send inputs in the first place. Once all of this was complete, I was able to control the arm through the processing interface. I can also control it using my keyboard.

[![Final Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612573869/video_to_markdown/images/youtube--F7M7imOVGug-c05b58ac6eb4c4700831b2b3070cd403.jpg )](https://www.youtube.com/watch?v=F7M7imOVGug&feature=emb_logo "Final Milestone"){:target="_blank" rel="noopener"}

# Second Milestone
My second milestone is controlling the robot arm with five potentiometers and through a GUI powered by python. To accomplish control with the potentiometers, I uploaded the code to the arduino board which would allow it to receive and translate the inputs of the potentiometers to motion of the arm. After that, I was able to control the arm with the potentiometers. In contrast, the GUI took a little more effort; the first step was to download python, which would allow the servosGUI.py file to work. After that, I uploaded the code to the arduino board that would allow it to communicate with my computer in such a way that would allow it to be controlled with the GUI. Finally, I opened the servosGUI.py file and connected it to COM6 (the port that the arm was connected to). After all of this, control of the arm was successful.

[![Milestone 2](https://res.cloudinary.com/marcomontalbano/image/upload/v1657898837/video_to_markdown/images/youtube--Uyg9Bej54NE-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://youtu.be/Uyg9Bej54NE "Milestone 2"){:target="_blank" rel="noopener"}

# First Milestone
My first milestone is controlling the servo motor with my phone via bluetooth. The first step was to write a code that would allow the arduino to receive data packets from the bluetooth module and then transmit those data packets to the servo motor. After that, I connected the servo motor to the GND, -9, and 3.3V pins of the arduino uno board. Then I had to download the .apk app that would control the servo motor. After doing all of this, I was able to control the motor with my phone.

[![Milestone 1](https://res.cloudinary.com/marcomontalbano/image/upload/v1657377720/video_to_markdown/images/youtube--TEca-ZLHSUo-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://youtu.be/TEca-ZLHSUo "Milestone 1"){:target="_blank" rel="noopener"}

# Materials List 

This is a table containing all the materials for the project and where to obtain them. It also lists the cost of each material.

| Item | Qty | Price | Where to Buy |
| ------------- | ------------- | ------------- | ------------- |
| Adeept Robotic Arm Kit  | 1  | $64.99  | https://www.amazon.com/dp/B087R8DLG6 |
| Breadboard  | 1 |  $6.75  | https://www.amazon.com/BB400-Solderless-Plug-BreadBoard-tie-points/dp/B0040Z1ERO |
| Potentiometer  | 1 | $1.85  |  https://www.tubesandmore.com/products/potentiometer-alpha-linear-38-bushing  |
| Micro Servo | 1 | $5.95 | https://www.adafruit.com/product/169  |
| Jumper Wires  | 6 | 10¢/wire  |  https://www.amazon.com/Breadboard-Jumper-Wire-75pcs-pack/dp/B0040DEI9M |
| Arduino Uno Board  | 1  | $27.60  | https://store-usa.arduino.cc/products/arduino-uno-rev3?selectedStore=us  |
| Arduino IDE  | 1  | $0  | https://www.arduino.cc/en/software/ |

# Example Code (Processing)

```
#include <Servo.h>
int servopin1 = 9;    //Define servo interface digital interface 9
int servopin2 = 6;    //Define servo interface digital interface 6
int servopin3 = 5;    //Define servo interface digital interface 5
int servopin4 = 3;    //Define servo interface digital interface 3
int servopin5 = 11;   //Define servo interface digital interface 11

int moveServoData;
int servo1Angle=90;
int servo2Angle=90;
int servo3Angle=90;
int servo4Angle=90;
int servo5Angle=90;
Servo servo1;
Servo servo2;
Servo servo3;
Servo servo4;
Servo servo5;
int angle = 90;        //Angle of rotation of the servo

boolean autoLock = false;
//boolean key_mouse_lock = false;
boolean closeLock = false;

void setup() {
  // put your setup code here, to run once:
  pinMode(servopin1,OUTPUT);//Set the servo interface as the output interface
  pinMode(servopin2,OUTPUT);//Set the servo interface as the output interface
  pinMode(servopin3,OUTPUT);//Set the servo interface as the output interface
  pinMode(servopin4,OUTPUT);//Set the servo interface as the output interface
  pinMode(servopin5,OUTPUT);//Set the servo interface as the output interface
  Serial.begin(9600);
  servo1.attach(servopin1);
  servo2.attach(servopin2);
  servo3.attach(servopin3);
  servo4.attach(servopin4);
  servo5.attach(servopin5);
  servo1.write(90);
  servo2.write(90);
  servo3.write(90);
  servo4.write(90);
  servo5.write(90); 
  delay(20);
  //servo1Pulse(90);
}
void loop() {
  delay(20);
  do{
    moveServoData = Serial.read();
    if (moveServoData == 111) {//o
      autoLock = false;
      closeLock=false;
      servo1Angle++;
      if(servo1Angle>=180){servo1Angle=180;}
      servo1.write(servo1Angle);
    }
    if (moveServoData == 112){//p
      autoLock = false;
      closeLock=false;
      servo1Angle--;
      if(servo1Angle<=0){servo1Angle=0;}
      servo1.write(servo1Angle);
    }
    if (moveServoData == 117) {//u
      autoLock = false;
      closeLock=false;
      servo2Angle++;
      if(servo2Angle>=180){servo2Angle=180;}
      servo2.write(servo2Angle);
    }
    if (moveServoData == 105) {//i
      autoLock = false;
      closeLock=false;
      servo2Angle--;
      if(servo2Angle<=0){servo2Angle=0;}
      servo2.write(servo2Angle);
    }
    if (moveServoData == 116) {//t
      autoLock = false;
      closeLock=false;
      servo3Angle++;
      if(servo3Angle>=180){servo3Angle=180;}
      servo3.write(servo3Angle);
    }
    if (moveServoData == 121) {//y
      autoLock = false;
      closeLock=false;
      servo3Angle--;
      if(servo3Angle<=0){servo3Angle=0;}
      servo3.write(servo3Angle);
    }



    
    if (moveServoData == 101) {//e
      autoLock = false;
      closeLock=false;
      servo4Angle++;
      if(servo4Angle>=180){servo4Angle=180;}
      servo4.write(servo4Angle);
    }
    if (moveServoData == 114) {//r
      autoLock = false;
      closeLock=false;
      servo4Angle--;
      if(servo4Angle<=0){servo4Angle=0;}
      servo4.write(servo4Angle);
    }
    if(moveServoData == 113) {//q 
      autoLock = false;
      closeLock=false;
      servo5Angle++;
      if(servo5Angle>=90){servo5Angle=90;}
      servo5.write(servo5Angle);
    }
    if(moveServoData == 119) {//w
      autoLock = false;
      closeLock=false;
      servo5Angle--;
      if(servo5Angle<=35){servo5Angle=35;}
      servo5.write(servo5Angle);
    } 
    if(moveServoData == 110){//n
      autoLock = true;
//      key_mouse_lock = false;
      closeLock=false;
    }
  }
  while(Serial.available()>0);

}

```
