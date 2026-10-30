# 3RRS-Parallel-Manipulator
This is the code for the 3RRS Parallel Manipulator that I built.

I wrote this code in the Arduino IDE, and unfortunately I did not version control any of it (possibly to my own detriment as I forgot to save a couple times and lost the changes I made— I'm definitely going to implement better versioning in my next project).

The commented out loops at the bottom are test code and a future version of the loop that I am working on. 

The stepper motors are powered with A4988 stepper drivers. These drivers need an input that tells them the STEP and DIR (Direction). These are the stepper pins defined at the top.

One pin is wired to all three enable pins on the stepper drivers to turn the drivers on and off for homing.

The main loop is only set to run every four milliseconds to reduce the loop times. Within 4ms the ball has not moved much so sending more move commands to the steppers is better than recalculating the position they need to be at and then doing it, hence the periodic updates.

The integral term in the PID controller only affects the ball when it is within 5mm of the desired point. This is because the proportional and derivative terms are all that is needed to bring the ball roughly to the desired location and it avoids integral windup. 

I would like to make the platform draw shapes with the ball eventually; however, the ball currently does not stay stable enough. I think that I need to recalibrate the center and fine tune the PID values some more to get a more accurate center and smoother balancing. I also might investigate the filtering that I am applying to the touchscreen data in the future and improve it more. 

I also would like to implement a mode switching feature in the future. I added pads for a button to the PCB and I'm planning on making it so that it can cycle through patterns and between the balancing modes when the button is pressed.
