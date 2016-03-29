# 1. Setting up the hardware

## Vibration dampening
iNav firmware is using inertial navigation system (INS), this means that firmware is dependant on ways of accurately measuring acceleration. Vibration is essentially a periodic acceleration and will confuse the INS up to the total inability to do its job correctly. There are two ways of fighting vibraton - balancing props and motors and vibration dampening. If applied together these two methods greatly improve INS performace.

## Magnetometer
Accurately setting up the compass is vital because it is the primary source of heading information. Without an accurate heading the drone will not move in the correct direction in autopilot modes (POSHOLD, RTH, Waypoint). This can lead to circling (aka “toiletbowling”) or even fly-aways.
Magnetometer measures magnetic field strength so it should be placed away from any sources of magnetic interference - power wires, ESCs, motors, beepers, metal parts of the frame. The best way is to place the compass on a mast along with GPS module. When external compass is used remember to set correct "align_mag", see iNav CLI variables for more infomation.

## GPS
iNav supports Ublox gps and NMEA (untested)

Tested and recommend GPS are M8N versions ( example [Ublox NEO-M8N](http://m.banggood.com/Ublox-NEO-M8N-Flight-Controller-GPS-with-Protective-Shell-for-PIX-PX4-Pixhawk-p-1005394.html?AID=12202217&PID=3836173&SID=ikzicawnsk0004o402ecu&source=affiliate&utm_source=Banggood_CJ&utm_medium=commission_junction&utm_campaign=OpenPilot&utm_content=sandy) and [Beitian BN-880](http://m.banggood.com/UBLOX-NEO-M8N-BN-880-Flight-Control-GPS-Module-Dual-Module-Compass-p-971082.html) )
But both M6N and M7N should work.

With default iNav settings iNav will configure ublox GPS for you, no need to use software like u-center.

Also be aware that some of our flight controllers can cause interference with the GPS causing low satellites or even no satellites at all, keep GPS as far as possible away and think of either shield your GPS or flight controller and other equipment that can cause interference.


# 2. Setting up the software
## Accelerometer calibration
A proper accelerometer calibration is mandatory if you plan to use GPS-assisted flight moedes (POSHOLD, RTH, WP). Please refer to [[Advanced accelerometer calibration|Advanced-accelerometer-calibration]] page for detailed explanation on how to calibrate the accelerometer properly.

## Compass calibration
### Performing the calibration
Press "Calibrate Magnetometer" button. You have 30 seconds to hold the copter in the air and rotate it so that each side (front, back, left, right, top and bottom) points down towards the earth. However the algorithm is smart enough to calculate the proper calibration values even if you simply wave the copter in the air for 30 seconds after pressing "Calibrate Magnetometer" button.

### Verifying that compass is calibrated properly
Connect the copter to Cleanflight Configurator and observe the attitude values on the "Setup" screen (values of Heading, Pitch and Roll). Point your copter's nose North and verify that heading is reading 0 deg. Tilt the copter 30 degrees forward, right, left and back while observing the Heading value. Value of 0 deg shouldn't change more than several degrees. Repeat the process with copter's nose pointing East (heading=90 deg), South (heading=180 deg), West (heading=270 deg).

If the value is incorrect when copter is level, you likely don't have **align_mag** CLI variable set to proper compass alignment value. If heading value is correct when copter is level but drifts when you tilt the copter, then your should re-calibrate the compass.

Also, remember to set magnetic declination to a proper value on the "Configuration" screen.

# 3. Setting flight modes


# 4. Setting up failsafe with return to home.

1. Make sure your radio receiver failsafe is set to "No pulses"

2. Set cli parameter "failsafe_procedure" to "RTH"
Type in cli "set failsafe_procedure = RTH"

3. 

3.1 In failsafe tab choose the aux channel where you have angle mode and instead of hold you set in to the value where "angle" mode is active.
Do the same for nav alt hold mode and nav pos hold

3.2 In failsafe tab set throttle to "hold". (If you are using an airplane it's probably safest to keep it at "auto" if your plane glide well without throttle.)


4. Verify that your failsafe works. 

4.1 Remove all props

4.2 While still connected to computer arm, apply throttle and turn of controller. The modes we configured in section 3 should activate, the throttle should stay and the rest of the controller should go to theyr center posisition.

4.3 Go outside, arm and apply throttle, walk with it 20meter away from home and then turn off transmitter. The aircraft should now try to climb (increase throttle) also verify that your able to regain control by turning on transmitter.

4.4 Real test, take the props on again. Take off, fly at least 20 meters from home and turn of transmitter. Tip do this over soft grass. If it's an airplane it's better to have soem altitude.