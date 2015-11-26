# 1. Setting up the hardware

## Vibration dampening
iNav firmware is using inertial navigation system (INS), this means that firmware is dependant on ways of accurately measuring acceleration. Vibration is essentially a periodic acceleration and will confuse the INS up to the total inability to do its job correctly. There are two ways of fighting vibraton - balancing props and motors and vibration dampening. If applied together these two methods greatly improve INS performace.

## Magnetometer
Accurately setting up the compass is vital because it is the primary source of heading information. Without an accurate heading the drone will not move in the correct direction in autopilot modes (POSHOLD, RTH, Waypoint). This can lead to circling (aka “toiletbowling”) or even fly-aways.
Magnetometer measures magnetic field strength so it should be placed away from any sources of magnetic interference - power wires, ESCs, motors, beepers, metal parts of the frame. The best way is to place the compass on a mast along with GPS module.

# 2. Setting up the software
## Accelerometer calibration
A proper accelerometer calibration is madnatory if you plan to use GPS-assisted flight moedes (POSHOLD, RTH, WP). Please refer to [[Advanced accelerometer calibration|Advanced-accelerometer-calibration]] page for detailed explanation on how to calibrate the accelerometer properly.

## Compass calibration
### Performing the calibration
Press "Calibrate Magnetometer" button. You have 30 seconds to hold the copter in the air and rotate it so that each side (front, back, left, right, top and bottom) points down towards the earth. However the algorithm is smart enough to calculate the proper calibration values even if you simply wave the copter in the air for 30 seconds after pressing "Calibrate Magnetometer" button.

### Verifying that compass is calibrated properly
Connect the copter to Cleanflight Configurator and observe the attitude values on the "Setup" screen (values of Heading, Pitch and Roll). Point your copter's nose North and verify that heading is reading 0 deg. Tilt the copter 30 degrees forward, right, left and back while observing the Heading value. Value of 0 ged shouldn't change more than several degrees. Repeat the process with copter's nose pointing East (heading=90 deg), South (heading=180 deg), West (heading=270 deg).

If the value is incorrect when copter is level, you likely don't have **align_mag** CLI variable set to proper compass alignment value. If heading value is correct when copter is level but drifts when you tilt the copter, then your should re-calibrate the compass.

Also, remember to set magnetic declination to a proper value on the "Configuration" screen.

# 3. Setting flight modes