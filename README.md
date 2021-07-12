# SpringSqueezer
A cable mechanism testing machine. It uses Springs as load - that where the names comes from.

## What can be tested:
This machine allows for practical evaluation of a capstan based cable mechanism. It works only for Capstan mechanisms that fasten the cable on the small drum and relay on that as a significant part of their load-bearing capability. An example of such a mechanism is the one we use on our robot - Stanley.

Aspects that can be tested:
<ul>
<li>Friction wear on the drum and cable
<li>Fatigue damage of the  cable
<li>Reliability and durability of termination
<li>Slippage of the cable through the drum mounting points
</ul>

## Hardware:
### Printed:
You will need to print two major structural parts of the machine - the motor mount and the rod scaffolding.

### Bought:
<ul><li>
motors - Eaglepower 8308 https://pl.aliexpress.com/item/4000563826414.html?spm=a2g0s.9042311.0.0.27425c0fCLdyW7
<li>https://pl.aliexpress.com/item/1005002190950645.html?spm=a2g0s.9042311.0.0.46c95c0fN0xeKe </ul>

<li>driver - moteus r4.5 (compatible with r4.3)
https://mjbots.com/collections/servos-and-controllers/products/moteus-r4-5

<li>2x clamps to clamp the assembly to the desk

<li>4x M2.5x8 screws for the moteus driver (if no heatsink) or 4x M2.5x14 countersunk screws for the moteus driver (if org moteus heasink used)

<li>Screws to screw the motor to the stand + screws to screw the rod to the motor, in our case it was:
<ul><li>For the Eaglepower 8308:
<ul><li>4xM4x12
<li>2xM3x30
<li>2xM3x10 countersunk</ul>

<li>For the DYS8108:
<ul><li>4xM3x12
<li>4xM3x30</ul>
</ul></ul>

## Software

Included in this repo in the software folder is a screipt that automates the testing. You just input the readouts of the scale and at the end you get a .csv with results. You need to set parameters:
<ul>
<li>rod_length - rod length from center of motor to the center of the bearing in meters
<li>max_torque - range of commanded torques will be from zero to this value
<li>step_count - how many measurements you want to do
<li>ramp_up_time - no to create a hard hit torque will ramp up to the max <li>value over this amount of time
<li>hold_time - if no user input is provided motor will turn off after this time to prevent overheating
<li>safety_max_velocity -if rotational velocity gets higher than this the machine stops commanding torque
<li>direction_flip - (True/False) you can flip the direction in which the test will be performed
</ul>

## Usage

You will be asked to perform a series of measurements. To start a measurement you will click Enter. Than the motor will start exerting force on the scale, it will quickly ramp it up (over ramp_up_time) instead of instantly turning it on to avoid a sudden hit. It will hold torque for some time (hold_time) and than release. You need to read out the value shown by the scale during the time when the motor holds (in grams)  and input it into this program, and click enter to accept the value, then enter again to start next measurement.
