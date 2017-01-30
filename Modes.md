Index:

- [ARM](#arm)
- [ANGLE](#angle)
- [HORIZON](#horizon)
- [MAG](#MAG)
- [HEADFREE](#headfree)
- [HEADADJ](#headadj)
- [CAMSTAB](#CAMSTAB)
- [PASSTHRU](#passthru)
- [BEEPER](#BEEPER)
- [LEDLOW](#ledlow)
- [LLIGHTS](#llights)
- [OSD SW](#osd-sw)
- [TELEMETRY](#telemetry)
- [BLACKBOX](#blackbox)
- [FAILSAFE](#failsafe)
- [AIR MODE](#air-mode)
- [HEADING LOCK](#heading-lock)
- [SURFACE](#surface)
- [FLAPERON](#flaperon)
- [TURN ASSIST](#turn-assist)
- [NAV LAUNCH](#launch---airplane-launch-assistant)
- [SERVO AUTOTRIM](#servo-autotrim---in-flight-adjustment-of-servo-midpoint-for-straight-flight)

## Default flight mode ( No mode selected )

The default flight mode does not self level the aircraft around the roll and the pitch axes. That is, the aircraft does not level on its own if you center the pitch and roll sticks on the radio. Rather, they work just like the yaw axis: the rate of rotation of each axis is controlled directly by the related stick on the radio, and by leaving them centered the flight controller will just try to keep the aircraft in whatever orientation it's in. This default mode is called "Rate" mode, also sometime called "Acro" (from "acrobatic") or "Manual" mode, and is active whenever no auto-leveled mode is enabled.


## Mode details

### Angle

In this auto-leveled mode the roll and pitch channels control the angle between the relevant axis and the vertical, achieving leveled flight just by leaving the sticks centered.
Maximum banking angle is limited by `max_angle_inclination_rll` and `max_angle_inclination_pit`

### Horizon

This hybrid mode works exactly like the previous ANGLE mode with centered roll and pitch sticks (thus enabling auto-leveled flight), then gradually behaves more and more like the default RATE mode as the sticks are moved away from the center position. Which means it has no limitation on banking angle and can do flips.

### MAG

The magnetometer is used in this mode.

When Mag Mode is enabled, if there is no yaw input, the copter will point forever to the same direction. MAG can be activated in all flight stabilization methods. Without this mode, you will still have a light deviation (drifting around the Z axis due to the imperfection of the gyro).

MAG MODE needs: gyro + acc + mag sensors (acc is needed also because it is used in heading angle determination)


### Headfree

In this mode, the "head" of the multicopter is always pointing to the same direction as when the feature was activated. This means that when the multicopter rotates around the Z axis (yaw), the controls will always respond according the same "head" direction.

With this mode it is easier to control the multicopter, even fly it with the physical head towards you since the controls always respond the same. This is a friendly mode to new users of multicopters and can prevent losing the control when you don't know the head direction. 

### HeadAdj

It allows you to set a new yaw origin for HEADFREE mode.

### Air mode

In the standard mixer / mode, when the roll, pitch and yaw gets calculated and saturates a motor, all motors
will be reduced equally. When motor goes below minimum it gets clipped off.
Say you had your throttle just above minimum and tried to pull a quick roll - since two motors can't go
any lower, you essentially get half the power (half of your PID gain).
If your inputs would asked for more than 100% difference between the high and low motors, the low motors
would get clipped, breaking the symmetry of the motor balance by unevenly reducing the gain.
Airmode will enable full PID correction during zero throttle and give you ability for nice zero throttle
gliding and actobatics. But also the cornering / turns will be much tighter now as there is always maximum
possible correction performed. Airmode can also be enabled to work at all times by always putting it on the
same switch like your arm switch or you can enable/disable it in air. Additional things and benefits: Airmode
will additionally fully enable Iterm at zero throttle. Note that there is still some protection on the ground
when throttle zeroed (below min_check) and roll/pitch sticks centered. This is a basic protection to limit
motors spooling up on the ground. Also the Iterm will be reset above 70% of stick input in acro mode to prevent
quick Iterm windups during finishes of rolls and flips, which will provide much cleaner and more natural stops
of flips and rolls what again opens the ability to have higher I gains for some.


### LAUNCH - airplane launch assistant
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
1. Launch sequence will finish when pilot switch off the NAV LAUNCH mode or move the 

### SERVO AUTOTRIM - In flight adjustment of servo midpoint for straight flight
The purpose of this mode is to set new midpoints for `SERVO_ELEVATOR`, `SERVO_FLAPERON_1`, `SERVO_FLAPERON_2` and `SERVO_RUDDER`.

This is so when switching into passthrough mode the plane will fly straight, its also to help the PID controller know where the plane is expected to fly straight.

How to use:

1. This is intended to use in air. 
2. Fly straight, choose what mode that suites you best. (`passthrough`, `angle` or `acro`)
3. Enable `SERVO AUTOTRIM` mode, and keep flying straight for 5 seconds. After 5 seconds it will set new midpoints based on average servo position during those 5 seconds.
4. If your are NOT happy with new midpoints disable `SERVO AUTOTRIM` mode and it will revert back to old settings. If you want to keep new midpoints keep `SERVO AUTOTRIM` turned on, land aircraft and disarm. New midpoints will be saved.

You may want to inspect your new midpoints after landing, if the servo ofset is alot you may alter your linkage mechanicaly and redo servo midpoint. 

This is not to be confused with tuning your aircraft for leveled flight in `ANGLE` mode, to do this you need to adjust your board aligment so straight flight for that aircraft is board aligment = 0 pitch and 0 roll.

### HEADING LOCK
This flight mode affects on yaw axis and can be enabled together with any other flight mode. 
It helps to maintain current heading without pilots input and  magnetometer's support. When yaw stick is neutral position, Heading Lock tries to keep total amount on rotation on yaw at zero. When pilot moves yaw stick, Heading Lock is not used.
It is a equivalent of [TauLabs Axis Lock mode](https://github.com/TauLabs/TauLabs/wiki/Flightmode-Settings#axislock) 

### FLAPERON

Activating it moves both ailerons down (or up) by predefined offset.

Configuration besides activating FLAPERON mode is pretty simple, and consists of 2 CLI variables:
- `flaperon_throw_offset` defines throw range in us for both ailerons that will be applied (before scaling) when FLAPERON mode is activated. By default it 250 with max at 400
- `flaperon_throw_inverted` [ON, OFF] inverts throw offset on both ailerons. Can be used to create SPOILERON or just to change throw direction


### TURN ASSIST

TURN ASSISTANT mode is an assisted mode to do a Yaw rotation on a ground plane, allowing one-stick turn in RATE mode and keeping ROLL and PITCH attitude though the turn.

In RATE mode it makes a perfect yaw-stick only turn and maintains attitude. There is slight drift due to not instant response of PID control, but still much easier to pilot for a RATE-mode beginners.

In ANGLE mode it also maked yaw turns much smoother and completely pirouette-less. This is expected as TURN ASSIST introduces feed-forward control in pitch/roll and maintains attitude naturally and without delay making it easier for self-leveling controller.


### FAILSAFE

Lets you activate flight controller failsafe with an aux channel.
Read [Failsafe page](https://github.com/iNavFlight/inav/wiki/Failsafe) for more info.


## Auxillary Configuration

Spare auxillary receiver channels can be used to enable/disable modes.  Some modes can only be enabled this way.

Configure your transmitter so that switches or dials (potentiometers) send channel data on channels 5 and upwards (the first 4 channels are usually occupied by the throttle, aileron, rudder, and elevator channels).

_e.g. You can configure a 3 position switch to send 1000 when the switch is low, 1500 when the switch is in the middle and 2000 when the switch is high._

Configure your tx/rx channel limits to use values between 1000 and 2000.  The range used by mode ranges is fixed to 900 to 2100.

When a channel is within a specifed range the corresponding mode is enabled.

Use the GUI configuration tool to allow easy configuration when channel.

### CLI 

There is a CLI command, `aux` that allows auxillary configuration.  It takes 5 arguments as follows:

* AUD range slot number (0 - 39)
* mode id (see mode list above)
* AUX channel index (AUX1 = 0, AUX2 = 1,... etc)
* low position, from 900 to 2100. Should be a multiple of 25.
* high position, from 900 to 2100. Should be a multiple of 25.

If the low and high position are the same then the values are ignored.

e.g.

Configure AUX range slot 0 to enable ARM when AUX1 is withing 1700 and 2100.
 
```
aux 0 0 0 1700 2100
```

You can display the AUX configuration by using the `aux` command with no arguments.

