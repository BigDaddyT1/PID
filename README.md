# PID
## What is the purpose of my project
-  To design an instrument used by me to regulate the speed of a balance beam trying to get a ball to level out as quickly as possible, and by using pid code and other process variables in industrial control systems to help make the PID work as smoothly as possible.

# Why did I choose to do this project
- At the beginning of this project David Deirof put me to the task of researching the best method of PID to create. Researching had been very difficult until I realized that in order to create a solid simple pid within the deadline set I needed to create a balance and it was the best decision I could have possibly made. Working by myself has been the hardest challenge of all because i've never worked alone on any project before. So looking at David Dierofs project I decided to create a smaller scale simple and sleek design and overall it worked. 

# The planning stage 
:In order to complete this task as quickly and efficiently as possible I needed to plan out a time frame.
## The First Week 
- The first week was the core for the planning stage researching videos (https://www.youtube.com/watch?v=JFTJ2SS4xyA ,https://www.youtube.com/watch?v=YOPTksabdbM, https://www.youtube.com/watch?v=-h1OtBgMqcE) and looking at David Deirof's project to come to a good understanding what PID actually is and how it works on a balance.
## The second week though tell the documentation week
- The second week through tell the documentation was made is primaraly focused on desighning my model in Cad and then takingit and putting it in the real world and in order to do that i had to create sketches and with those sketches I made my model in cad. and after creating the model in cad getting everything 3D printed and putting everything together. Having a light to indicate that the balance is on and having a swich for power. And lastly designing a counterweight system underneith the ultrasonic sensor to make sure that one side was heavier than the other. 
## Reflection/ Documentation week 
- The documentation would be done last because working solo I have to make sure my  actuall 3d project is done and works as good as posible and documentation is althogh helpful I put to the end. 

# My balance beam in action !
https://github.com/BigDaddyT1/PID/assets/113116205/a228fb77-b409-4b1f-a717-e45738ebe41a
- The goal of the balance is to get it to reach the midpoint as fast as possible using pid and ive gotten it to level out within a 20 second time frame VERY COOL!
## These are images of my PID diagram 

![WIN_20230602_09_37_24_Pro](https://github.com/BigDaddyT1/PID/assets/113116205/7fc2ffca-cf62-4324-8834-39e3719b3004)
- In this image it is showing you that I used a slip tie knot and connected it to the bottom of one of my end cap pieces and the other is connected to the ultrasonic sensor and with both of those end pieces connected to a laser cute 2 inch by 14 inch piece of acrylic made up what I called (ball holder) 

![WIN_20230602_09_37_17_Pro](https://github.com/BigDaddyT1/PID/assets/113116205/8d7ea64d-2cce-4aab-9a78-d7afc368533a)
- In this image it is showing the blue connection piece I designed in order to hold the balance up. I designed this to let the ball move from about 300 degrees in total and the rod that the blue piece is connected to holds the balance up high enough so that the balance has more room to work with.

![WIN_20230602_09_36_52_Pro](https://github.com/BigDaddyT1/PID/assets/113116205/17f184cc-8dd1-4b90-8c5e-618fc6c76a61)
- In this image it shows the base I designed to structure my whole project around. I designed it in a circle because I knew I wanted all of the sides to get the same amount of force and I could base the rest of the design around it. In addition to that I also created an extension to that and it helped hold the 180 servo that would later be connected to the string down. I designed 2 pieces for that: a solid base for the arduino to sit on and the piece overtop to clamp it down to the acrylic. 

![WIN_20230602_09_36_32_Pro](https://github.com/BigDaddyT1/PID/assets/113116205/1fff1fe8-5f3a-4bf1-af4e-c8416dfaf862)
- In this image it shows the wiring I used connected to the arduino in addition to the breadboard I put on top of that. Beside that is the battery holder I used 9 volts to power my arduino is essential in the project.

## This is a link to all of the parts I designed and the full assembly that I created in Onshape 
- https://cvilleschools.onshape.com/documents/35ae1394c693d43da04649b9/w/ab67fec34452d17ff0ef8f23/e/32506171eeb7c41383a34b11
### MY favorite part 
![image](https://github.com/BigDaddyT1/PID/assets/113116205/8b881305-6d87-4b79-b47c-43a6947b946b)
![image](https://github.com/BigDaddyT1/PID/assets/113116205/0ef13085-79a9-494e-a697-ab542067b897)

- This I would say was the funnest peice to design on cad it was a very essential but what made it fun was how intricate this peice is. It is the most essential peice in the project and the to hold it in were a great and very plaful idea. 
# How Did I get my PID libraries 
In order to create my PID code I needed PID libraries and thanks to copper2880z he made my life so much easier because I had no idea how to create a pid library he was a very big help I could not have done what I created without his libraries: Here is the link to his libraries https://github.com/Copper280z/CircuitPython_simple-pid
#  This is A full description of my code 
import time
import board
import adafruit_hcsr04
import pwmio
from adafruit_motor import servo
from lib.PID import PID

sonar = adafruit_hcsr04.HCSR04(trigger_pin=board.D6, echo_pin=board.D7)

# Assume we have a system we want to control in controlled_system
# this will be our sensor value to be used as input for the PID controller
# v = controlled_system.update(0)
# create a PWMOut object on Pin A2.
pwm = pwmio.PWMOut(board.A1, duty_cycle=2 ** 15, frequency=50)

# Create a servo object, my_servo.
my_servo = servo.Servo(pwm)
# start angle 180 degrees
my_servo.angle = 180
time.sleep(.5)
# then change  start angle to 45 degreese
my_servo.angle = 60
time.sleep(.5)
setpoint= 17.5

pid = PID(8, 10, 0.05, setpoint=setpoint)
pid.output_limits = (0, 180)
# my_servo.angle = 180
# print("angle: ",x180) 
# time.sleep(10)
while True:
        dist = sonar.distance
        output = pid(dist)
        
        
    # # Feed the PID output to the system and get its current value
   
        if dist < 5 or dist > 35:
            output = 175
            time.sleep(0.1)            
        
        print('dist: ', dist, 'PID Output: ', output)
        p,i,d = pid.components
        print(p, i, d)
        my_servo.angle = (180-output)
        time.sleep(0.1)
