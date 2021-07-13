# SpringSqueezer
A cable mechanism testing machine. It uses Springs as load - that where the names comes from.

![Spring Squeezer F360 Screenshot 1](/images/F360_screenshot_1.png)

## What can be tested:
This machine allows for practical evaluation of a capstan based cable mechanism. It works only for Capstan mechanisms that fasten the cable on the small drum and relay on that as a significant part of their load-bearing capability. An example of such a mechanism is the one we use on our robot - Stanley.

Aspects that can be tested:
<ul>
<li>Friction wear on the drum and cable
<li>Fatigue damage of the  cable
<li>Reliability and durability of termination
<li>Slippage of the cable through the drum mounting points
</ul>


![Spring Squeezer F360 Screenshot 1](/images/F360_screenshot_2.png)


## Hardware:
### Printed:
You will need to print two major structural parts of the machine - the motor mount and the rod scaffolding and 3 smaller parts - the cable termination block and the top and bottom of the drum

### Bought:
<ul><li>
motor - Eaglepower 8308 https://pl.aliexpress.com/item/4000563826414.html?spm=a2g0s.9042311.0.0.27425c0fCLdyW7
<li> driver - moteus r4.5 (compatible with r4.3)
https://mjbots.com/collections/servos-and-controllers/products/moteus-r4-5
<li> mjbots CANFD to USB adapter - https://mjbots.com/collections/accessories/products/fdcanusb
<li> PSU capable of ~500W at 24-34V
<li>2x clamps to clamp ot to the desk
<li>4x M2.5x10 screws for the moteus driver (if no heatsink) or 4x M2.5x16 countersunk screws for the moteus driver (if org moteus heasink used)
<li>4x M4x12 hex screws- to screw down the Eaglepower 8308
<li>4x M5x50 hex screws - for connecting the linear_rod_holder with the motor_cage
<li>4x M5 square nuts - for connecting the linear_rod_holder with the motor_cage
<li>2x M4x30  hex screws - for the capstan drum
<li>2x M4 square nuts - for the capstan drum
<li>6x M3x10 countersunk hex screws - 4 of them for mounting capstan drum to the motor and 2 of the act as drum reinforcement (they screw from the bottom of "capstan_mech_small_drum_bottom")<li>4x M3x20 hex screws - for tightening the 8mm linear rod mounts
<li>6x M3x15 hex screws - for mounting the LMK8LUU linear bearings
<li>2x M3x50 hex screws - they act as structural reinforcement of the motor cage
<li>12x M3 square nuts - 4 of them for tightening the 8mm linear rod mounts, 6 of them for mounting the LMK8LUU linear bearings and 2 of them for the long structural reinforcement screws
<li>1x M5 eye bolt - or you can adapt to any other mounting method you want to use in your robot. M5 eye bolt we use: https://pl.aliexpress.com/item/1005001623167300.html?spm=a2g0s.9042311.0.0.37aa5c0fBCzdPX 
<li>1x M5 nut - for the M5 eye bolt
<li>1x Cable assembly (ours includes a crimp and 1.5mm DYNEEMA rope, but it ommits the thimble, yours can be different)
<li>2x LMK8LUU linear bearings
<li>2x 250~300mm linera rods
<li>2x Springs - We used 1,5x12x75 - but feel free to experiment with outer lengths/stifnesses - just make sure that the internal dimeter is bigger than 8

</ul>

## Software

Included in this repo in the software folder is a screipt that automates the testing. You set the parameters to your liking. You need to make sure that the system is thermaly stable and you don't cook your motor. We highly recommend pointing some kind of fan at the assembly during the tests. The deafults are what we used for our testing. The vairables with description:
<ul>
<li>pull_duration - first part of the cycle - over this amount of time the motor pulls the cable with full Troque
<li>release_duration next part of the cycle - a gradual release starting at max torque ending at standby_torque
<li>duty_cycle - cycle of the test
<li>max_torque - maximum torque exerted by the motor
<li>standbay_torque - between pulls the motor still exerts some torque - to keep the cable tight
<li>rotational_speed_safety_limit - if motor spins above that rotational velocity the test is interrupted - this makes sure that the test does not continue after the rope breaks
</ul>


## Usage

Fasten the rig to your cable with clamps, assemble your rope, set the parameters, point the fan at the test rig, make sure the rig is thermally stable and run the test till something breaks. If you interrupt the test, and you want to start it again but you want the count to continue- not start from zero - you should set the previous amount as the value of the "counter" variable.
