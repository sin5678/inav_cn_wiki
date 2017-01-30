# List off all flight modes in iNav

|  Mode name | Description |
|  ------ | ------ |
|  ARM | Used to switch arm aircraft |
|  [`ANGLE`](/iNavFlight/inav/wiki/Modes) | Stabilized mode with self leveling and restricted banking angles |
|  [`HORIZON`](/iNavFlight/inav/wiki/Modes)  | Stabilized mode with self leveling but without restricted banking angles |
|  NAV ALTHOLD | Used to hold altitude |
|  MAG | Used to lock heading using magnetometer |
|  [`HEADFREE`](/iNavFlight/inav/wiki/Modes) | Head Free - When enabled yaw has no effect on pitch/roll inputs |
|  [`HEADADJ`](/iNavFlight/inav/wiki/Modes) | Heading Adjust - Sets a new yaw origin for HEADFREE mode |
|  [`CAMSTAB`](/iNavFlight/inav/wiki/Modes) | Used to stabilize SERVO GIMBAL outputs |
|  NAV RTH | Used for Return-to-home. Does not need any other mode selected. |
|  NAV POSHOLD | Used to hold posision in 2d space with GPS. Combine with ALTHOLD to get 3d posision lock |
|  [`PASSTHRU`](/iNavFlight/inav/wiki/Modes) | Used with fixedwings to controll everything manually. ( Direct servo controll ) |
|  [`BEEPER`](/iNavFlight/inav/wiki/Modes) | Used to activate beeper |
|  [`LEDLOW`](/iNavFlight/inav/wiki/Modes) | Missing |
|  [`LLIGHTS`](/iNavFlight/inav/wiki/Modes) | Missing |
|  [`OSD SW`](/iNavFlight/inav/wiki/Modes) | Missing |
|  TELEMETRY | Missing |
|  BLACKBOX | Used to manually start blackbox logging. ( If not configured it will automaticle start on ARM ) |
|  FAILSAFE | Used to manually initate FAILSAFE |
|  NAV WP | Used to fly WAYPOINT mission. Does not need any other mode selected. |
|  [`AIR MODE`](/iNavFlight/inav/wiki/Modes) | Keeps PID controller active at zero throttle |
|  HOME RESET | Used to set new home position and current aircraft posision. |
|  GCS NAV | Used to allow ground station to controll aircraft to do stuff like `Follow me` |
|  HEADING LOCK | Locks heading like MAG mode, but without using magnetometer. |
|  SURFACE | Used to follow terrain, in combination with SONAR |
|  FLAPERON | Used to activate flaperons on fixed-wings |
|  TURN ASSIST | Makes copter do Yaw turns on parallel to the ground plane regardless of tilt. |
|  NAV LAUNCH | Used to detect and automaticle launch fixed-wings. |
|  SERVO AUTOTRIM | Used to trim midpoint for servos to maintain straight. |