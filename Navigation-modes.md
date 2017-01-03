This page will list and explain all the different navigational flight modes of iNav:

- [ALTHOLD - Altitude hold](#althold---Altitude-hold)
- [POSHOLD - Horizontal position hold](#poshold---horizontal-position-hold)
- [HEADING LOCK](#heading-lock)
- [RTH - Return to home](#rth---return-to-home)
- [WP - Autonomous waypoint mission](#wp---autonomous-waypoint-mission)
- [GCS_NAV - Ground control station](#gcs_nav---ground-control-station)
- [LAUNCH - airplane launch assistant](#launch---airplane-launch-assistant)
- [SERVO AUTOTRIM - In flight adjustment of servo midpoint for straight flight](#servo-autotrim---in-flight-adjustment-of-servo-midpoint-for-straight-flight)


For safety reasons, iNAV’s navigation modes can be activated only if  
- ACC and MAG are [calibrated](https://github.com/iNavFlight/inav/wiki/4.-Sensor-calibration) properly,  
- you have a valid 3D GPS fix,   
- the FC is armed.  

This applies to enabling the navigation modes in the Configurator as well as at the flying field.   
(For bench tests without(!) propellers you may change “set nav_extra_arming_safety = ON” to “OFF” in CLI.)  

- Flightmodes are self contained. For example: with RTH and WP (Waypoints) it's not neccesary to enable angle, althold or mag, it enables what it needs. Keep in mind that POSHOLD is also self contained and enables what it need, but that does not include ALTHOLD. Read more below in POSHOLD section.  

|           | POSHOLD   | WAYPOINT  | RTH       | ALTHOLD   |
| ----      | ----      | ----      | ----      | ----      |
| ANGLE     | X         | X         | X         |           |
| ALTHOLD   |           | X         | X         |           |
| MAG       |           | X         | X         |           |
| BARO      |           | X         | X         | X         |


  
- There is a companion [[wiki page further describing way point missions, tools and telemetry options|iNavFlight Missions]].

Note: All iNAV parameters for distance, velocity, and acceleration are input in  cm, cm/s and cm/s^2. 

Let's have a look at each mode of operation in detail.

## ALTHOLD - Altitude hold
When activated, the aircraft maintains its actual altitude unless changed by manual throttle input.
Throttle input indicate climb or sink up to a predetermined maximum rate (see CLI variables). Using ALTHOLD with a multicopter, you need a barometer.  
SONAR: Altitude hold code will use sonar automatically on low altitudes (< 3m) if hardware is available.  
Using ALTHOLD with a plane (fixed wing: fw) with GPS: Barometer should be ignored. (To disable barometer: "set baro_hardware=1").
  
In general you shouldn't mix up ALTHOLD and ACRO/HORIZON: ALTHOLD doesn't account for extreme acro maneuvers. 
  
Activate ALTHOLD by **ALTHOLD** flight mode.  
Altitude, as calculated by iNAV's position estimator, is recorded to BLACKBOX as navPos[2].
  
### a) Using ALTHOLD with a multicopter (mc):  
Activate AIRMODE to keep the copter stable in fast descent - now you can do the whole flight in altitude hold - from takeoff to landing.  
  
Climb rate in ALTHOLD mode:  
"set nav_max_climb_rate = 500" and "set nav_manual_climb_rate = 200" define the maximum climb and decent rate in autonomous/manual flight modes.   
The neutral position of the throttle stick to hold current altitude is defined by   
- “set nav_use_midthr_for_althold=ON”: use mid position of throttle stick as neutral. 
- “set nav_use_midthr_for_althold =OFF”: use current stick position (i.e. when activating ALTHOLD) as neutral. [Yet, if "nav_use_midthr_for_althold=OFF”, and you enable ALTHOLD with throttle stick too low (like on the ground) iNAV will take “thr_mid” as a safe default for neutral. “thr_mid” is defined In the “Receiver” tab and should be set to hover throttle.]   
  
In the moment you engage ALTHOLD iNAV always sends “nav_mc_hover_thr” to the motors as the starting value of the altitude control loop. You should configure this to your copter's hover setting, if your copter doesn't hover close to the default value of 1500us. Otherwise your copter will begin ALTHOLD with a jump or drop.  
  
Example: Let's assume "nav_mc_hover_thr” is already set correctly to your copter's hover throttle and “set nav_use_midthr_for_althold =OFF”. Let's say you have your throttle stick at 30%, and you enter ALTHOLD, your copter will maintain hover at this 30%. If increase throttle up to 40% it will start to climb. (Even if your copter needs 60% throttle to actually climb up in normal flight without ALTHOLD.)

    
"set alt_hold_deadband = 50": You have to change throttle command (e.g. move throttle stick) by at least this amount to make the copter climb or decent and change target altitude for ALTHOLD.  
If ALTHOLD is activated at zero throttle iNAV will account for deadband and move the neutral "zero climb rate" position a little bit up to make sure you are able to descend.  
  
  
PIDs for altitude hold:  
- ALT P - defines how fast copter will attempt to compensate for altitude error (converts alt error to desired climb rate)  
- ALT I - defines how fast copter will accelerate to reach desired climb rate  
- VEL P - defines how much throttle copter will add to achieve desired acceleration  
- VEL I - controls compensation for hover throttle (and vertical air movement, thermals). This can essentially be zero if hover throttle is precisely 1500us. Too much "VEL I" will lead to vertical oscillations, too low "VEL I" will cause drops or jumps when ALTHOLD is switched on.  
- VEL D - acts as a dampener for VEL P and VEL I, will slower the response and reduce oscillations from too high VEL P and VEL I  

Inability to maintain altitude can be caused by a number of reasons:  
1. insufficient ALT_P and/or ALT_I  
2. non-functional baro (please go to "Sensors" tab in Configurator and verify that baro graph changes as you move the quad up and down  
3. seriously under-powerd quad (ALTHOLD is able to compensate only to some degree. If your quad hovers at 1700 linear throttle without any expo, ALTHOLD might fail to compensate)  
4. Gaining altitude during fast flight is likely due to increased air pressure and that is treated as going down in altitude - try covering your baro with (more) foam.

ALT+VEL PID Tuning  
Lets make a small experiment: Make sure baro is well isolated. You may also want to reduce baro weight: "set iNAV_w_z_baro_p = 0.5" and "set nav_alt_p = 0" and try flying. This way the controller will attempt to keep zero climb rate without any reference to altitude. The quad should slowly drift either up or down. If it would be jumping up and down, your "nav_vel_*" gains are too high.  
As a second step you can try zeroing out "nav_vel_p" and "nav_vel_i" and "set nav_vel_d = 100". Now the quad should be drifting up/down even slower. Raise "nav_vel_d" to the edge of oscillations.  
Now raise "nav_vel_p" to the edge of oscillations. Now ALTHOLD should be almost perfect.  
And finally "set nav_mc_hover_thr" slightly (50-100) higher/lower than your actual hover throttle and tune "nav_vel_i" until the quad is able to compensate.  
Keep in mind that no tuning can fix bad baro isolation issue.    
  
If quad is buzzing while ALTHOLD is activated try lowering "nav_vel_p" a bit.  

What is the trick with "nav_vel_i"?   
"nav_vel_i" is used to compensate for "nav_mc_hover_thr" (hover throttle) being set to a slightly incorrect value. You can't set hover throttle to an exact value, there is always influence from thermals, battery charge level etc. Too much "nav_vel_i" will lead to vertical oscillations, too low "nav_vel_i" will cause drops or jumps when ALTHOLD is enabled, very low "nav_vel_i" can result in total inability to maintain altitude.
  
To deal with oscillations you can try lowering your "nav_alt_p", "nav_vel_p", "nav_max_climb_rate", and "nav_manual_climb_rate".    
  
Climb rate is calculated form the readings of the accelerometers, barometer and – if available – from GPS (“set inav_use_gps_velned = ON”). How strongly the averages of these noisy signals are taken into account in the estimation of altitude change by iNAV is controlled by  
- set inav_w_z_baro_p = 0.350  
- set inav_w_z_gps_p = 0.200    
for vertical position (z) and     
- set inav_w_z_gps_v = 0.500    
for vertical velocity. Too high “iNAV_w_z_baro_p”will make ALTHOLD nervous and too low will make it drift so you risk running into the ground when cruising around. Using GPS readings for vertical velocity allows for a lower weight for baro to make ALTHOLD smoother without making it less accurate. 
  

// TODO: explain remaining relevant settings
  
### b) Using ALTHOLD with an airplane (fixed wing, fw):  
As for multicopters, iNAV is not intended to use ALTHOLD controller in anything but ANGLE mode.  
iNAV controls pitch angle and throttle. It assumes that altitude is held (roughly) when pitch angle is zero. If plane has to climb, iNAV will also increase throttle. If plane has to dive iNAV  will reduce throttle and glide. The strength of this mixing is controlled by “nav_fw_pitch2thr”.  
Set board alignment in such a way that your plane is flying level both in "PASSTHROUGH" and in "ANGLE", when you don't touch the sticks.   

iNAV’s parameters for fixed wing:  
- set nav_fw_cruise_thr = 1400  # cruise throttle  
- set nav_fw_min_thr = 1200  # minimum throttle  
- set nav_fw_max_thr = 1700  # maximum throttle  
- set nav_fw_bank_angle = 20  
- set nav_fw_climb_angle = 20  
- set nav_fw_dive_angle = 15  
- set nav_fw_pitch2thr = 10  #  pitch to throttle  
- set nav_fw_roll2pitch = 75  # roll to pitch  
- set nav_fw_loiter_radius = 5000  
  
  
  
## POSHOLD - Horizontal position hold
When activated, the quad/plane keeps its horizontal (2D) position, throttle still controls up and down movements (z-axis).
You can use your roll and pitch stick to move around. The position hold will be resumed when you center the roll/pitch stick again.      
Please note that you have to use this with **ALTHOLD** to get a full 3D position hold!  
  
POSHOLD = 2D position hold  
POSHOLD + ALTHOLD = 3D position hold  
POSHOLD + ALTHOLD + MAG = 3D position hold and magnetic heading lock  
POSHOLD + ALTHOLD + Heading Lock = 3D position hold and heading lock  
(ANGLE mode is automatically selected in all of the above.)
    
Hints for safe operation:    
- Try yawing 180 deg in PH - will instantly reveal incorrect mag operation (e.g. wrong align_mag, interference, loose cables, ...)
- Always check POSHOLD working correctly, before you use RTH or start a WP mission.

// TODO: explain relevant settings. CRUISE ATTI
// TODO: explain what happens when you are in POSHOLD mode and GPS fails.

Activated by **POSHOLD** flight mode.

## HEADING LOCK
This flight mode affects on yaw axis and can be enabled together with any other flight mode. 
It helps to maintain current heading without pilots input and  magnetometer's support. When yaw stick is neutral position, Heading Lock tries to keep total amount on rotation on yaw at zero. When pilot moves yaw stick, Heading Lock is not used.
It is a equivalent of [TauLabs Axis Lock mode](https://github.com/TauLabs/TauLabs/wiki/Flightmode-Settings#axislock) 

// TODO: explain if this works for FW w/o magnetometer.

## RTH - Return to home
RTH will attempt to bring copter/plane to launch position. Launch position is defined as a point where aircraft was ARMed. RTH Will control both position and altitude. You will have to manually control altitude if your aircraft does not have an altitude sensor (barometer). In the case of fixed wing, altitude comes from the GPS, so you dont need a barometer in your FC (CC3D for example).

With default settings RTH will land immediately if you are close than 5 meters from launch position. If further away it will make sure to have at least 10 meters of altitude, then start going home at 3m/s, and land. It will disarm itself if so configured, otherwise you will have to manually disarm once on the ground.

// TODO: explain how this works with planes.
// TODO: explain relevant settings.
// TODO: explain what happens when you are in RTH mode and GPS fails.

There are many different modes for Altitude, see [further down on this page](https://github.com/iNavFlight/inav/wiki/7.-Navigation-modes#rth-altitude-control-modes)

Activated by **RTH** flight mode.


## WP - Autonomous waypoint mission
Autonomous waypoints are used to let the quad/plane autonomous fly a predefined mission. The mission is defined with waypoints, which have the information about latitude, longitude, height and speed between the waypoints. GUIs such as EZ-GUI and mwp can be used to set the waypoints and upload the mission. Cleanflight or iNav configurator are still not capable of creating waypoint missions.  
Uploaded missions are saved in the FC until a reboot or a new uploaded mission erases the old one.  
  
Once the waypoint mode is activated (NAV WP has to be set previously in the mode tabs to a specific switch/value), the quad/plane will start to fly the waypoint mission based upon the waypoints in numerical order. Waypoint missions can be restarted by switching NAV WP off/on, interruption during the mission is also possible with switching NAV WP off. 

Currently up to 30 waypoints can be set on F1 boards, and 60 on F3 and better.

This mode is a work in progress, it does however work well. There is an additional [[wiki page further describing way point missions, tools and telemetry options|iNavFlight Missions]].

// TODO: Explain better.
// TODO: explain what happens when you are in WP mode and GPS fails.

## GCS_NAV - Ground control station
This mode is just an permission for GCS to change position hold coordinates and the altitude.
So its not an flight mode itself, and needs to be combined with other flightmodes.

In order to let the GCS have full control over the aircraft the following modes must be activated: `NAV POSHOLD` `NAV ALTHOLD` `MAG` TOGETHER with `GCS_NAV`

This can be combined in whichever way you want to permit example manuall yawing or altitude controll.

Keep in mind that if `NAV POSHOLD` is not combined with this mode you must combine `ANGLE` as the other modes are best combined with `ANGLE` mode.


// TODO: explain what happens when you are in GSC NAV mode and GPS fails.  
 
## LAUNCH - airplane launch assistant
This flight mode is intended to provide assistance for launching the fixed-wing UAVs. Launch detection works by monitoring airplane acceleration - once it breaches the threshold for a certain amount of time launch sequence is started.


The entire time `NAV LAUNCH` mode it will try and stabilize plane, it will target zero roll, zero yaw and predefined climb angle. The I-gain of the PID regulator is also disabled to prevent I-gain growing during launch until motor is started. When succesfull launch is detected it waits for preconfigured amount of time before starting motor.

`NAV LAUNCH` is automatically aborted after 5 seconds or by any pilot input on PITCH/ROLL stick. When it has aborted it goes to whichever selected mode, which can be Angle, Rate, Horzion, RTH or a waypoint mission (if no other mode is selected it will go to Rate mode).

The `NAV LAUNCH` mode cannot be activated again in flight while armed. So its safe to keep it activated. 

See iNav CLI for all available adjustable parameters, they start with `nav_fw_launch_`

Sequence for launching airplane using `NAV LAUNCH` mode looks like this:

1. Set switch to `NAV LAUNCH` mode prior to arming (note that it won't actually enable until arming)
1. ARM the plane. Motor should start spinning at min_throttle (if `MOTOR_STOP` is active, motor won't spin)
1. Verify that motor don't respond to throttle stick motion. Don't touch the right stick!
1. Put throttle stick to desired throttle value to be set **after** launch is finished.
1. Throw the airplane
1. Motors will start at pre-configured `nav_fw_launch_thr` (default 1700) after `nav_fw_launch_motor_delay` (500ms)
1. Launch sequence will finish when pilot switch off the NAV LAUNCH mode or move the right (roll/pitch) stick

## SERVO AUTOTRIM - In flight adjustment of servo midpoint for straight flight
The purpose of this mode is to set new midpoints for `SERVO_ELEVATOR`, `SERVO_FLAPERON_1`, `SERVO_FLAPERON_2` and `SERVO_RUDDER`.

This is so when switching into passthrough mode the plane will fly straight, its also to help the PID controller know where the plane is expected to fly straight.

How to use:

1. This is intended to use in air. 
2. Fly straight, choose what mode that suites you best. (`passthrough`, `angle` or `acro`)
3. Enable `SERVO AUTOTRIM` mode, and keep flying straight for 5 seconds. After 5 seconds it will set new midpoints based on average servo position during those 5 seconds.
4. If your are NOT happy with new midpoints disable `SERVO AUTOTRIM` mode and it will revert back to old settings. If you want to keep new midpoints keep `SERVO AUTOTRIM` turned on, land aircraft and disarm. New midpoints will be saved.

This is not to be confused with tuning your aircraft for leveled flight in `ANGLE` mode, to do this you need to adjust your board aligment so straight flight for that aircraft is board aligment = 0 pitch and 0 roll.

## Mode switch diagram

A diagram to indicate flight modes relation to navigation modes and illustrate sensor requirements:

![](images/nav_modes_diagram.jpg)

# RTH Altitude control modes

RTH sequence can control altitude in several different ways, controlled by **nav_rth_alt_mode** and **nav_rth_altitude** parameters.

Default setting is NAV_RTH_AT_LEAST_ALT - climb to preconfigured altitude if below, stay at current altitude if above.

## Maintain current altitude (NAV_RTH_NO_ALT)
nav_rth_alt_mode = CURRENT

nav_rth_altitude is ignored

![](images/NAV_RTH_NO_ALT.jpg)

## Maintain current altitude + predefined safety margin (NAV_RTH_EXTRA_ALT)
nav_rth_alt_mode = EXTRA

nav_rth_altitude defines extra altitude margin

![](images/NAX_RTH_EXTRA_ALT.jpg)

## Predefined altitude (NAV_RTH_CONST_ALT)
nav_rth_alt_mode = FIXED

nav_rth_altitude defines exact RTH altitude above launch point.

If the multi-rotor is below nav_rth_altitude it will enter position hold and climb to desired altitude prior to flying back home. If the machine is above the desired altitude, it will turn and fly home and descend on the way.

![](images/NAV_RTH_CONST_ALT.jpg)

## Maximum altitude since launch (NAV_RTH_MAX_ALT)
nav_rth_alt_mode = MAX

nav_rth_altitude is ignored

![](images/NAV_RTH_MAX_ALT.jpg)

## At least predefined altitude above launch point (NAV_RTH_AT_LEAST_ALT)
nav_rth_alt_mode = AT_LEAST

nav_rth_altitude defines exact RTH altitude above launch point

![](images/NAV_RTH_AT_LEAST_ALT.jpg)