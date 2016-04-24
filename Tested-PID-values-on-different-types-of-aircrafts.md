# PID examples

##  Purpose of this wiki page is to give you a starting point of PID values based on different setups of multirotors and fixed wing.

**Template multirotors:**

1. **Name of frame:**
1. Size of frame:
1. Weight:
1. Totalt thrust:
1. Battery infomation:
1. iNav version:

```
PID and other values from CLI
```


**Template fixedwing:**

1. **Name of plane:**
1. Mixer used:
1. iNav version:
1. Additional infomation you see fit if not stock airplane:

```
PID and other values from CLI
```

### Tricopters


### Quadcopter

#### ZMR250 on 3S

1. iNav FP-PID controller
1. Voltage: 3S
1. FC: SPRacingF3
1. Motors: Multistar 2206 2150KV "Baby beast"
1. Props: DAL T5040 (3 blade 5x4")
1. Total weight: 550g with battery (Turnigy Graphene 1300mAh 3S)

```
set p_pitch = 82
set i_pitch = 80
set d_pitch = 145
set p_roll = 55
set i_roll = 60
set d_roll = 110
set p_yaw = 110
set i_yaw = 30
set d_yaw = 1
set gyro_soft_lpf_hz = 90
set dterm_lpf_hz = 42
set looptime = 1000
set gyro_lpf = 188HZ
```

#### Diatone Whitesheep 500 on 3S
1. iNav FP-PID controller
1. Voltage: 3S
1. FC: Seriously Dodo
1. GPS: Ublox NEO-M8N
1. Motors: Turnigy 2628 1200kv (don't buy those..)
1. Props: GEMFAN 9x4.7
1. Total weight: 1100 gram (with battery and gimbal + gopro)

```
set nav_alt_p = 50
set nav_alt_i = 0
set nav_alt_d = 0
set nav_vel_p = 100
set nav_vel_i = 50
set nav_vel_d = 10
set nav_pos_p = 65
set nav_pos_i = 120
set nav_pos_d = 10
set nav_posr_p = 180
set nav_posr_i = 15
**set nav_posr_d = 50**
set nav_navr_p = 14
set nav_navr_i = 2
set nav_navr_d = 8

set p_pitch = 45
set i_pitch = 50
set d_pitch = 70
set p_roll = 45
set i_roll = 50
set d_roll = 70
set p_yaw = 100
set i_yaw = 40
set d_yaw = 0
set p_level = 160
set i_level = 10
set d_level = 75

set looptime = 2000
```


### Hexacopters


### Various multirotors


### Fixed wing

1. **Name of plane: FMS Easytrainer 1280**
1. Mixer used: Airplane
1. iNav version: 1.0.1 Self compiled from master 24/3-2017
1. 3S 2200mAh battery on stock power system.

```
set p_pitch = 200
set i_pitch = 10
set d_pitch = 40
set p_roll = 200
set i_roll = 10
set d_roll = 40
set p_yaw = 100
set i_yaw = 0
set d_yaw = 0
set nav_navr_p = 14
set nav_navr_i = 0
set nav_navr_d = 0
```

1. **Name of plane: Multiplex Minimag**
1. Mixer used: CUSTOMAIRPLANE
1. iNav version: 1.1.0 Self compiled from master 5d556b0
1. 4S 5000mAh battery
1. Default PIDs and settings except the ones listed below:

```
set p_pitch = 120
set p_roll = 55
set p_yaw = 100
set i_yaw = 0
set nav_navr_p = 10
set nav_navr_i = 5
set gyro_sync = ON
set min_throttle = 1075
set gps_nav_model = HIGH_G
set inav_use_gps_velned = ON
set nav_rth_alt_mode = FIXED
set nav_rth_altitude = 15000
set nav_fw_cruise_thr = 1280
set nav_fw_min_thr = 1120
set nav_fw_max_thr = 1650
set nav_fw_bank_angle = 20
set nav_fw_pitch2thr = 15
set nav_fw_roll2pitch = 75
set nav_fw_loiter_radius = 7500
```