robotic-car
===========


Objective



The purpose of our project is to develop a mobile robot that will track and follow
lane (lines on the road) through the use of a camera mounted on a computer that
processes the image. More specically, the goal of the project entails: lane detection,
full body detection, template matching and HSV (hue saturation value) color model
for trac light detection in real-time manner. Ultimately, the robot should be able to
autonomously detect a lane of road and to follow the detected lane in order to move
with out leaving the road. The project provides benets to visually impaired peoples,
material transportation with out drivers and generally to the automotive industry.


Specications


Car Control


To control the movement of our car we need to have full rotation servo motors to be
the wheels of the car. In case of turning our car to the left, the tow left servos of the
car rotates backward while the other two right servos rotating in the forward direction;
Chapter 1. Introduction 3
and turning the car to the right will be vice-verse. The speed of the car is equal to the
speed of the servo which is between (SS = 54rpm) and (SS = 70rpm).
Once the camera has sought out the lane, we would like the car to align itself with the
detected lane and follow it. We would like the car to continue following the lane as it
turns, regardless of any turns the lane might make.




 Sub-projects
 

 Computer


 The main form of control is our personal computer (PC) running Windows.
The computer have USB port for communication with the Arduino micro-
controller for interfacing with the web camera.
 The PC handles functions such as receiving data from the web-cam, pro-
cessing the data, and communicating with the servo motors via the Arduino
microcontroller to produce locomotion and to orient the car. The system is a
closed loop in that the drive electronics indirectly aect the camera's or car's
position.


 Arduino Microcontroller



 To enable the USB port to control the servo motors, arduino microcontroller
is used.
 The arduino microcontroller acts as an intermediary to translate serial data
into arduino control signals for the servo motor control circuits.
 The arduino also receives signal from the proximity sensor through its ana-
logue input and controls the servo with out the intervention of the PC.


 Servo Motors


 Movement of the robotic car is accomplished via a four servo motor, controlled
directly by the arduino microcontroller, and thus indirectly by the PC.
 To turn on the turning points the left pair of wheels and the right pair of
wheels rotates in opposite direction according to the direction of turning.


 Vision System




 The vision data is provided through the PCs web camera.
 The camera is be relatively simple, running at 320 x 240 resolution and 30
frames per second.



Proximity Sensor



 The proximity sensor is used to detect an immediate intrusion of peoples and
animals to protect them from being killed by the car accident.
 The data from the proximity sensor is directly provided to the arduino mi-
crocontroller to its analogue input.



Power Source



 The power source from the PC battery supplies the control electronics as well
as drive electronics through the arduino microcontroller.
 +5V power is generated from the arduino the supply the servo motors.



