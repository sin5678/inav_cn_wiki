### Setting up failsafe with return to home.

1. Make sure your radio receiver failsafe is set to "No pulses". (If your radio receiver doesn't support "No pulses", or you don't want to use it, go to bottom of this page)

2. Set cli parameter "failsafe_procedure" to "RTH"
Type in cli "set failsafe_procedure = RTH"

3. Set up modes for stage 1 failsafe

 3,1 In failsafe tab go to "Channel Failsafe Settings" and change the settings for "ANGLE" (or "HORIZON" if you prefer that), "NAV ALTHOLD" and "NAV POSHOLD" from "Auto" to "Set". Set the value that shows up in the field that now shows up, to a the correct value for the mode to be activated. (eg. my remote's AUX switches toggle ON/OFF between ~1000 and ~2000, so i entered 2000 here)

 3,2 In failsafe tab set throttle to "Hold". RTH failsafe will not work (copter will crash land) if you use "auto" 

Channel Fallback Settting 1.2.1
![](http://i.imgur.com/MGlW95i.png)

4. Verify that your failsafe works. 

 4,1 Remove all props

 4,2 While still connected to computer: arm the copter, apply throttle and then turn the controller off. The modes we configured in section 3 should activate, the throttle should stay, and the rest of the controller should go to their center positions.

 4,3 Go outside, arm and apply throttle, walk with it 20meter away from home (normally the place where you armed it) and then turn off transmitter. The aircraft should now try to climb (increase throttle). Also verify that you're able to regain control by turning on transmitter again.

 4,4 Real test: Take the props on again. Take off, fly at least 20 meters from home, and turn off transmitter. Tip: Do this over soft grass. If it's an airplane it's better to have some altitude.

## Not using "No pulse" on receiver.

1. Setup everything as explained above.

1. In "Modes" tab select a switch for "Failsafe"

1. Set your switches and sticks of your radio to the following conditions:  

 `Throttle: approx. 45% (just below 6 hover throttle/cruise throttle)`  

 `Aileron: 0% (no input, stick center)`  

 `Rudder: 0% (no input, stick center)`  

 `Elevator: 0% (no input, stick center)`  

 `Failsafe mode: activated`  

 `Arm switch: activated (just if you use switch to arm)`  

1. Press your Failsafe button on the RC TX or RC RX to save this stick/switch configuration for link loss.