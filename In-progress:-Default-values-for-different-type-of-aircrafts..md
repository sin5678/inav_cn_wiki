History: **PLEASE WRITE HERE IF YOU CHANGE ANYTHING AND WHY.**
```
24.06.2016 oleost: Created first version of this wiki
24.06.2016 oleost: Changed default to "mag_hardware = 1" on regular regular airplane because airplanes flies better with gps heading instead of mag heading.

```

# Multirotor

**150 Size:**

_PIDs:_

_Navigation PIDs:_

_Other Values:_


**250 Size:**

_PIDs:_

```
set p_pitch = 82
set i_pitch = 55
set d_pitch = 145
set p_roll = 55
set i_roll = 35
set d_roll = 110
set p_yaw = 110
set i_yaw = 30
set d_yaw = 1
```


_Navigation PIDs:_

_Other Values:_

```
set gyro_soft_lpf_hz = 90
set dterm_lpf_hz = 42
set looptime = 1000
set gyro_lpf = 188HZ
```

**450 Size:**

_PIDs:_

```
set p_pitch = 120
set i_pitch = 45
set d_pitch = 125
set p_roll = 90
set i_roll = 40
set d_roll = 115
set p_yaw = 150
set i_yaw = 50
set d_yaw = 0
set p_level = 120
set i_level = 15
set d_level = 75
```

_Navigation PIDs:_

_Other Values:_

```
set imu_dcm_ki = 0
set gyro_sync = ON
set gyro_sync_denom = 2
set gyro_lpf = 42HZ
```

**600 Size:**

_PIDs:_

_Navigation PIDs:_

_Other Values:_

# Tricopters

**250 Size:**

_PIDs:_

_Navigation PIDs:_

_Other Values:_

**600 Size:**

_PIDs:_

_Navigation PIDs:_

_Other Values:_

# Fixedwing

**Regular plane**

_PIDs:_

```
set p_pitch = 100
set i_pitch = 10
set d_pitch = 40
set p_roll = 100
set i_roll = 10
set d_roll = 40
set p_yaw = 100
set i_yaw = 5
set d_yaw = 20
set p_level = 160
set i_level = 10
set d_level = 75
```

_Navigation PIDs:_

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
set nav_posr_i = 150
set nav_posr_d = 100
set nav_navr_p = 200
set nav_navr_i = 10
set nav_navr_d = 0
```

_Other Values:_

```
set mag_hardware = 1
```

**Small flying wing**

_PIDs:_

_Navigation PIDs:_

_Other Values:_

**Large flying wing**

_PIDs:_

_Navigation PIDs:_

_Other Values:_
