# PID PROJECT

## What is the purpose of my project
-  To design an instrument used by me to regulate the speed of a balance beam trying to get a ball to level out as quickly as possible, and by using pid code and other process variables in industrial control systems to help make the PID work as smoothly as possible.

# Why did I choose to do this project
- At the beginning of this project David Deirof put me to the task of researching the best method of PID to create. Researching had been very difficult until I realized that in order to create a solid simple pid within the deadline set I needed to create a balance and it was the best decision I could have possibly made. Working by myself has been the hardest challenge of all because I've never worked alone on any project before. So looking at David Dierof's project I decided to create a smaller scale simple and sleek design and overall it worked. 

# The planning stage 
: In order to complete this task as quickly and efficiently as possible I needed to plan out a time frame.

# Planning Section Materials 
1) a list of materials:
when doing this project the materials needed are a 9-volt battery pack, male-to-female wires, male-to-male wires, cut-out pieces of acrylic, 3D printed pieces made on on shape, A prototyping shield, and a ping pong ball (pink of course) 

2) goal for the project:
the goal for my project is to get a balance and a ping pong ball on the balance to reach the desired setpoint as fast as possible

3) A list of criteria and constraints
- The criteria for this project is to design, and Program a device that uses PID feedback control.
- The constraints for the project are as listed Use only an Arduino and other standard components in the Sigma Lab
Use 4 or 6 AA batteries and a battery pack for power
Include a power switch and an LED power indicator
Ensure everything is securely mounted.

## The First Week 
- The first week was the core for the planning stage researching videos (https://www.youtube.com/watch?v=JFTJ2SS4xyA ,https://www.youtube.com/watch?v=YOPTksabdbM, https://www.youtube.com/watch?v=-h1OtBgMqcE) and looking at David Deirof's project to come to a good understanding what PID actually is and how it works on a balance.

## The second week though tell the documentation week
- The second week through telling the documentation was made primarily focused on designing my model in Cad and then taking it and putting it in the real world in order to do that I had to create sketches and with those sketches, I made my model in cad. and after creating the model in cad getting everything 3D printed and putting everything together. Having a light to indicate that the balance is on and having a switch for power. And lastly designing a counterweight system underneath the ultrasonic sensor to make sure that one side was heavier than the other. 

## Reflection/ Documentation week 
- The documentation would be done last because working solo I have to make sure my actual 3d project is done and works as well as possible and documentation is helpful I put it to the end. 

# My balance beam in action!
https://github.com/BigDaddyT1/PID/assets/113116205/a228fb77-b409-4b1f-a717-e45738ebe41a
- The goal of the balance is to get it to reach the midpoint as fast as possible using pid and I've gotten it to level out within a 20-second time frame VERY COOL!

## These are images of my PID diagram 

![WIN_20230602_09_37_24_Pro](https://github.com/BigDaddyT1/PID/assets/113116205/7fc2ffca-cf62-4324-8834-39e3719b3004)
- In this image, it is showing you that I used a slip tie knot and connected it to the bottom of one of my end cap pieces, and the other is connected to the ultrasonic sensor, and with both of those end pieces connected to a laser cute 2 inch by 14-inch piece of acrylic made up what I called (ball holder) 

![WIN_20230602_09_37_17_Pro](https://github.com/BigDaddyT1/PID/assets/113116205/8d7ea64d-2cce-4aab-9a78-d7afc368533a)
- In this image, it is showing the blue connection piece I designed in order to hold the balance up. I designed this to let the ball move from about 300 degrees in total and the rod that the blue piece is connected to holds the balance up high enough so that the balance has more room to work with.

![WIN_20230602_09_36_52_Pro](https://github.com/BigDaddyT1/PID/assets/113116205/17f184cc-8dd1-4b90-8c5e-618fc6c76a61)
- In this image, it shows the base I designed to structure my whole project around. I designed it in a circle because I knew I wanted all of the sides to get the same amount of force and I could base the rest of the design around it. In addition to that, I also created an extension to that and it helped hold the 180 servo that would later be connected to the string down. I designed 2 pieces for that: a solid base for the Arduino to sit on and the piece overtop to clamp it down to the acrylic. 

![WIN_20230602_09_36_32_Pro](https://github.com/BigDaddyT1/PID/assets/113116205/1fff1fe8-5f3a-4bf1-af4e-c8416dfaf862)
- In this image, it shows the wiring I used connected to the Arduino in addition to the breadboard I put on top of that. Besides that the battery holder I used 9 volts to power my Arduino is essential in the project.

## This is a link to all of the parts I designed and the full assembly that I created in Onshape 
- https://cvilleschools.onshape.com/documents/35ae1394c693d43da04649b9/w/ab67fec34452d17ff0ef8f23/e/32506171eeb7c41383a34b11

### MY favorite part 
<img src="https://github.com/BigDaddyT1/PID/assets/113116205/73efd967-d86f-4bc7-b783-31637f84baa1" alt="part" width="500">
<img src="https://github.com/BigDaddyT1/PID/assets/113116205/d935f5a7-4c21-4e78-9a82-99bf900303c8" alt="part" width="500">
- This I would say was the funniest piece to design on cad it was very essential but what made it fun was how intricate this piece is. It is the most essential piece in the project and the to hold it in was a great and very playful idea. 

# How Did I get my PID libraries 
In order to create my PID code I needed PID libraries and thanks to copper2880z he made my life so much easier because I had no idea how to create a PID library he was a very big help I could not have done what I created without his libraries: Here is the link to his libraries https://github.com/Copper280z/CircuitPython_simple-pid

#  This is my favorite piece of code I created during the coding portion of my project


        if dist < 5 or dist > 35:
            output = 175
            time.sleep(0.1)            
        
        print('dist: ', dist, 'PID Output: ', output)
        p,i,d = pid.components
        print(p, i, d)
        my_servo.angle = (180-output)
        time.sleep(0.1)
        
- Because during this portion is where I actually discovered what PID actually stands for (Proportional, Interval, and Derivative), and in my code, at the beginning of the process it was showing pid output and Interols, and changing that to this has taken out all the unnecessary useless bits of code and changed that to give me (Proportional, Interval, and Derivative) outputs which helped me so that I can tune the balance to reach the center point as fast as possible.
# Full code here 
: https://github.com/BigDaddyT1/PID/blob/main/PID.py 

# This is a wiring diagram I made
![image](https://github.com/BigDaddyT1/PID/assets/113116205/92f31f71-5a8a-423a-8f7d-a5d2894724fa)

# Biggest Problem 
- My biggest problem was when importing the PID the 180 servos would keep switching sides, therefore, messing up my code and almost destroying it to the point where I would have to start over. It could have ended very badly.
### Solution
- My solution was to design a piece to clamp it down and ensure it would stay in one position and I could fix my code. It took some time but in the end, it really worked out. 

# Reflection
Although there was a lot of troubleshooting done during this project this pid project was the best fun I've had since I've been here. I've learned to work by myself for a change and that I can do anything I put my mind to. I had some excellent guidance from David Deirof and Karl Helmstetter. They both have helped me overcome so much during this project I did not know was possible. The hardest part of this project would be that I felt as though I was taking so many steps forward but ultimately realizing that I was way further behind than  I imagined it helped me to push myself to the limit and I got it done. The easiest part I would say was the designing portion of the project. It is very fun and very cool designing something and seeing it come to life was by far the best part of the project. One key piece of advice I would give is to always make sure you have a counterweight system for balance lord knows I needed to figure that out way quicker than I did. Overall I would definitely recommend this to future students, definitely a 10/10 project.



