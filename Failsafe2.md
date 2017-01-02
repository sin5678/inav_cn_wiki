# Setting up Failsafe for RTH

##Forewords

The goal is to configured both your flight controller and radio receiver so failsafe does as expected in every situation.

For failsafe to work optimal iNav needs to know it's in a failsafe event and not just doing regular RTH. This is for example correctly handle loss of GPS while returning to home.

###Configuration of receiver

One got two options on how to configure receiver.

Option one:  
Set receiver to send out `NO PULSES`

Option two:  
1. In "Modes" tab select a switch for "Failsafe"

1. Set your switches and sticks of your radio to the following conditions:  

 `Throttle: approx. 45% (just below 6 hover throttle/cruise throttle)`  

 `Aileron: 0% (no input, stick center)`  

 `Rudder: 0% (no input, stick center)`  

 `Elevator: 0% (no input, stick center)`  

 `Failsafe mode: activated`  

 `Arm switch: activated (just if you use switch to arm)`  
