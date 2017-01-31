# List of all flight modes in iNav

## Default flight mode ( No mode selected )

The default flight mode is [`RATE`](/iNavFlight/inav/wiki/Modes#default-flight-mode--no-mode-selected-), this is activate when none of the `Actuall flight modes` is turned on.

`Actuall flight modes`

|  Mode name | Description |
|  ------ | ------ |
|  [`ANGLE`](/iNavFlight/inav/wiki/Modes) | Stabilized mode with self leveling and restricted banking angles |
|  [`HORIZON`](/iNavFlight/inav/wiki/Modes)  | Stabilized mode with self leveling but without restricted banking angles |
|  [`NAV RTH`](/iNavFlight/inav/wiki/Navigation-modes) | Used for Return-to-home. Does not need any other mode selected. |
|  [`NAV POSHOLD`](/iNavFlight/inav/wiki/Navigation-modes) | Used to hold position in 2d space with GPS. Combine with ALTHOLD to get 3d position lock |
|  [`PASSTHRU`](/iNavFlight/inav/wiki/Modes) | Used with fixedwings to control everything manually. ( Direct servo control ) |
|  [`NAV WP`](/iNavFlight/inav/wiki/Navigation-modes) | Used to fly WAYPOINT mission. Does not need any other mode selected. |


`Flight modes that alter behavior in combination with one of the above`

|  Mode name | Description |
|  ------ | ------ |
|  [`ARM`](/iNavFlight/inav/wiki/Modes) | Used to switch arm aircraft |
|  [`NAV ALTHOLD`](/iNavFlight/inav/wiki/Navigation-modes) | Used to hold altitude. recommend to use in combination with `angle` mode or `nav poshold` |
|  [`TURN ASSIST`](/iNavFlight/inav/wiki/Modes)  | Makes copter do Yaw turns on parallel to the ground plane regardless of tilt. |
|  [`AIR MODE`](/iNavFlight/inav/wiki/Modes) | Keeps PID controller active at zero throttle |
|  [`SURFACE`](/iNavFlight/inav/wiki/Modes) | Used to follow terrain, needs SONAR |
|  [`HEADING LOCK`](/iNavFlight/inav/wiki/Modes) | Locks heading like MAG mode, but without using magnetometer. |
|  [`MAG`](/iNavFlight/inav/wiki/Modes) | Used to lock heading using magnetometer |
|  [`HEADFREE`](/iNavFlight/inav/wiki/Modes) | Head Free - When enabled yaw has no effect on pitch/roll inputs |
|  [`HEADADJ`](/iNavFlight/inav/wiki/Modes) | Heading Adjust - Sets a new yaw origin for HEADFREE mode |


`Modes that can be enabled to activate function or other features.`
|  Mode name | Description |
|  [`CAMSTAB`](/iNavFlight/inav/wiki/Modes) | Used to stabilize SERVO GIMBAL outputs |
|  [`BEEPER`](/iNavFlight/inav/wiki/Modes) | Used to activate beeper |
|  [`LEDLOW`](/iNavFlight/inav/wiki/Modes) | Turns LEDs OFF|
|  [`LLIGHTS`](/iNavFlight/inav/wiki/Modes) | Missing description |
|  [`OSD SW`](/iNavFlight/inav/wiki/Modes) | Missing description |
|  [`TELEMETRY`](/iNavFlight/inav/wiki/Modes) | Normally telemetry is always enabled, enabling this mode allows you to turn on and off telemetry at will |
|  [`BLACKBOX`](/iNavFlight/inav/blob/master/docs/Blackbox.md) | Normally blackbox is logging as soon as you arm, configure this mode blackbox will only log flight data when the mode is active. ) |
|  [`FAILSAFE`](/iNavFlight/inav/wiki/Modes) | Used to manually initate FAILSAFE |
|  [`HOME RESET`](/iNavFlight/inav/wiki/Navigation-modes) | Used to set new home position at aircraft current position. |
|  [`GCS NAV`](/iNavFlight/inav/wiki/Navigation-modes) | Used to allow ground station to control aircraft to do stuff like `Follow me` |
|  [`FLAPERON`](/iNavFlight/inav/wiki/Modes) | Used to activate flaperons on fixed-wings |
|  [`NAV LAUNCH`](/iNavFlight/inav/wiki/Modes) | Used to detect and automatic launch fixed-wings. |
|  [`SERVO AUTOTRIM`](/iNavFlight/inav/wiki/Modes) | Used to trim midpoint for servos to maintain straight. |

