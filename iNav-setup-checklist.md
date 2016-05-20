## 0. Setup hardware
Balance props and motors, install FC on a vibration-damping mount if possible.

## 1. Set board and sensor alignment values
TODO

## 2. Calibrate accelerometer
A proper accelerometer calibration is mandatory if you plan to use GPS-assisted flight moedes (POSHOLD, RTH, WP). Please refer to [[Advanced accelerometer calibration|Advanced-accelerometer-calibration]] page for detailed explanation on how to calibrate the accelerometer properly.

## 3. Calibrate compass
Press "Calibrate Magnetometer" button. You have 30 seconds to hold the copter in the air and rotate it so that each side (front, back, left, right, top and bottom) points down towards the earth. The algorithm is smart enough to calculate the proper calibration values even if you simply wave the copter in the air for 30 seconds after pressing "Calibrate Magnetometer" button.

## 4. Verify that compass is functioning properly
Point your copter to North, East, South and West. Observe **Heading** in the configurator - it should be 0, 90, 180 and 270 respectively. A 3-5 degree error is acceptable. Verify that heading doesn't change (much) when you tilt the copter in pitch/roll axis.

## 5. Set your TX midpoints
Set trim on your TX to zero. Use subtrim to adjust your TX midpoints to be precisely 1500 when Roll/Pitch/Yaw sticks are centered.

## 6. Tune your copter's Pitch/Roll/Yaw/Level PIDs
//TODO: Small mini guide for tuning.

[Tested PID values on different aircrafts](https://github.com/iNavFlight/inav/wiki/Tested-PID-values-on-different-types-of-aircrafts#pid-examples)

## 7. Trim copter to level flight
DO NOT USE TRIM the copter to level flight on your transmitter. Use board alignment settings or accelerometer trim stick combos.
[How to trim your Accelerometer](http://tldrify.com/elw)

## 8. Setup and verify failsafe on TX and iNav
[Guide for setting up failsafe](https://github.com/iNavFlight/inav/wiki/%5BWiP%5D-Quick-setup-guide#4-setting-up-failsafe-with-return-to-home)

## 9. Determine and set hover throttle
Use blackbox or Configurator to figure out throttle stick position when your copter is hovering. Set **nav_mc_hover_thr** CLI variable to that value.


## 10. Get to know the CLI values.
iNav offers a lot of customization trough CLI variables. Its strongly recommended to read trough [iNav CLI variables](https://github.com/iNavFlight/inav/wiki/iNav-CLI-variables)

Some important ones are:

| `nav_user_control_mode`            | Defines how Pitch/Roll input from RC receiver affects flight in POSHOLD mode: ATTI - right stick controls attitude like in ANGLE mode; CRUISE - right stick controls velocity in forward and right direction. | | |