## Overview

GPS Systems can occasionally drop the signal or provide significantly inaccurate position information (aka “glitches”). While errors are more likely in conditions where the GPS signal can bounce off multiple paths before reaching the receiver (multipathing), errors can occasionally occur even with clear sky.

Without updates from GPS System, the inertial position estimation allow approximately 1.5 seconds of position information but after this the horizontal position drift becomes so large that the horizontal position cannot be maintained at all. At this point the position estimator will report invalid position to the navigation core. If you still have RC radio control it is recommended to take back control using ANGLE, HORIZON, ALTHOLD or ACRO as soon as possible.

Action taken on invalid position is dependent on current flight mode.

## Action taken on invalid position event

### ANGLE, HORIZON, ACRO, ALTHOLD mode
These modes are not GPS-dependent, nothing will happen but you will be unable to switch into an autopilot flight mode (POSHOLD, RTH, WP) until the failure clears.

### POSHOLD mode
The copter will be forced into ANGLE mode, pilot will have complete control over copter attitude. If ALTHOLD mode was selected it will remain active. When failure clears POSHOLD more will resume.

### RTH and WP modes (including failsafe RTH)
RTH and WP are considered full-auto modes. It is assumed that pilot might have no control over the copter so the best case scenario here is land. Copter will enter Emergency Landing state if failure is consistent for over 2 seconds.

## Emergency Landing
In case of critical failure, Emergency Landing is triggered. In Emergency Landing state copter is forced into ANGLE mode, ROLL and PITCH input is centered to maintain level, pilot stick input is ignored and copter enters a controlled descent.

While Emergency Landing is active pilot is unable to switch into ALTHOLD, POSHOLD, RTH or WP mode. If pilot wants to regain control of the copter he should switch to ANGLE, HORIZON or ACRO more.