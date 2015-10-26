Accelerometer calibration is mandatory if inertial position estimation is used. Modern accelerometer sensors are accurate, but they require calibration it we want precise measurements. Sensors might be biased, gains on different axis might be different. Advanced 6-point calibration takes care of all irregularities sensor might have.

## Accelerometer calibration steps

![](https://github.com/digitalentity/nav-rewrite-docs/blob/master/docs/assets/acc-calibration-positions.jpg)

0. Connect the copter to the "Configurator" software, select the "Setup" tab.
1. Place copter level (pos 1), press "Calibrate Accelerometer" button. Advanced calibration has been activated and recorded the 1-st data point.
2. Place copter to all sides in sequence (pos 2-6): on right side, left side, nose down, nose up and on its back. Press "Calibrate Accelerometer" button in every position. Advanced calibration algorythm will record 2-nd to 6-th data points.
3. After all 6 positions have beed recorded advanced calibration will calculate offsets and gains and store them in EEPROM. Accelerometer calibration done.
4. Use CLI to verify that **accgain_x**, **accgain_y** and **accgain_z** parameters and **NOT ZERO**. If they are, algorithm failed to converge, calibration failed and need to be repeated.

There is no need to place copter perfectly aligned, the algorythm does not care about exact positions as long as they are close to 90 degree apart and copter is stationary in every position.

## Level calibration

Proper accelerometer calibration does not guarantee copter being level. Chip might be misaligned on board or the board itself might be mounted at some tiny angle. For level flight and navigation features to work you need to trim the firmware to level flight using "Board Alignment" on the "Configuration" tab. 

**NOTE!** Unline in "official" Cleanflight firmware board alignment angles are set in degrees*10, so if you need to trim your board 1.5 degrees you should enter "15".

**NOTE2!** To keep things compatible with official Configurator, angles more than 36 deg and less than -18 deg can only be set through CLI parameters: **align_board_pitch**, **align_board_roll** and **align_board_yaw**. 

This applies to mounting the flight controller at 90 degree to keep USB port accessible. You have to set **align_board_yaw=900** from CLI.

## Backup and restore the settings

To avoid going through full calibration after resetting the configuration new CLI settings are introduced to get and set accelerometer offsets and gains: **acczero_x**, **acczero_y**, **acczero_z**, **accgain_x**, **accgain_y**, **accgain_z**.
