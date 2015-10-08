Navigation system can function in several modes: ALTHOLD, POSHOLD_2D, POSHOLD_3D, RTH, RTH_2D, WP. These modes are exposed to pilot as different flight modes or their combination: POSHOLD, ALTHOLD, RTH, WP. Lets have a look at each mode of operation in detail.

## ALTHOLD - Altitude hold

Roll, pitch and yaw inputs do not have any special meaning, their behaviour is determined by Cleanflight flight modes. Throttle input indicate climb or sink at a predetermined maximum rate.

Activated by **ALTHOLD** flight mode.

## POSHOLD_2D - Horizontal position hold

This mode is called 2D because only X and Y local coordinates are stabilised. Pitch and roll inputs control either lean angles or velocities in forward-right direction. Altitude (Z coordinate) is not stabilised.

Activated by **POSHOLD** flight mode.

## POSHOLD_3D - Full position hold

This mode is a combination of ALTHOLD and POSHOLD_2D modes. When sticks are centered, copter will maintain position and altitude.

Activated by **POSHOLD+ALTHOLD** flight modes.

## RTH and RTH_2D - Return to home

RTH and RTH_2D both will attempt to bring copter to launch position. Launch position is defined as a point where aircraft was ARMed. The only difference is that in RTH_2D mode machine will not maintain or control altitude. Throttle input goes straight to motors. Pilot can not manually choose between RTH and RTH_2D modes, firmware choose RTH or RTH_2D based on what sensors are available. RTH requires a position sensor and altitude sensor, while RTH_2D requires only position sensor

Activated by **RTH** flight mode.

## WP - Autonomous waypoint mission

This is a work in progress mode.

## Mode switch diagram

A diagram to indicate flight modes relation to navigation modes and illustrate sensor requirements:

![](https://github.com/digitalentity/nav-rewrite-docs/blob/master/docs/assets/nav_modes_diagram.jpg)