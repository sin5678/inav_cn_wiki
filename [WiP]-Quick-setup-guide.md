# 1. Setting up the hardware

## Vibration dampening
iNav firmware is using inertial navigation system (INS), this means that firmware is dependant on ways of accurately measuring acceleration. Vibration is essentially a periodic acceleration and will confuse the INS up to the total inability to do its job correctly. There are two ways of fighting vibraton - balancing props and motors and vibration dampening. If applied together these two methods greatly improve INS performace.

## Magnetometer
Accurately setting up the compass is vital because it is the primary source of heading information. Without an accurate heading the drone will not move in the correct direction in autopilot modes (POSHOLD, RTH, Waypoint). This can lead to circling (aka “toiletbowling”) or even fly-aways.
Magnetometer measures magnetic field strength so it should be placed away from any sources of magnetic interference - power wires, ESCs, motors, beepers, metal parts of the frame. The best way is to place the compass on a mast along with GPS module. When external compass is used remember to set correct "align_mag", see iNav CLI variables for more infomation.

Also when using an external magnetometer 9/10 times you need to physically(remove chip from board or cut a trace) remove the internal one if you have on. You can't use two identical chips/magnetometers on the same I2C bus. The 1/10 time you dont need to physially remove your internal mag is when you have different magnetometers on the flight controller and the external one. Example you cant use two HMC5883L magnetometers.

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


