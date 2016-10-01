**Values written here must be based on 1.2 or later!**


### History: **PLEASE WRITE HERE IF YOU CHANGE ANYTHING AND WHY.**
```
01.10.2016 oleost: Removed old PIDs based on pre 1.2
10.07.2016 oleost: Added disabling mag on flying wing aswell
24.06.2016 oleost: Created first version of this wiki
24.06.2016 oleost: Changed default to "mag_hardware = 1" on regular regular airplane because airplanes flies better with gps heading instead of mag heading.
24.06.2016 oleost: removed looptime 1000, to low for f1 targets.

```

# Change to default iNav settings 

Changes **you** think that should be done to iNav globally:

```
24.06.2016 oleost: Change default to velned on because it generally looks like a better solution. (use_gps_velned = 1)

```

# Multirotor

**150 Size:**

_PIDs:_

```

```

_Navigation PIDs:_

```

```

_Other Values:_

```

```

**250 Size:**

_PIDs:_

```

```


_Navigation PIDs:_

```

```

_Other Values:_

```
set gyro_soft_lpf_hz = 90
set dterm_lpf_hz = 42
set gyro_lpf = 188HZ
```

**450 Size:**

_PIDs:_

```

```

_Navigation PIDs:_

```

```

_Other Values:_

```
set imu_dcm_ki = 0
set gyro_sync = ON
set gyro_sync_denom = 2
set gyro_lpf = 42HZ
```

**600 Size:**

_PIDs:_

```

```

_Navigation PIDs:_

```

```

_Other Values:_

```

```


# Fixedwing

**Regular plane**

_PIDs:_

```

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

**Flying wing**

_PIDs:_

```

```

_Navigation PIDs:_

```

```

_Other Values:_

```
set mag_hardware = 1
```