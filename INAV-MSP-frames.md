## INAV 1.4 MSP API Version 1.22

### MSP_INAV_PID

Frame IDs:

* MSP_INAV_PID, Frame ID _6_
* MSP_SET_INAV_PID, Frame ID _7_

| length    | setting                       | Notes                         |
| ----      | ----                          | ----                          |
| 1         | `async_mode`                  |                               |
| 2         | `acc_task_frequency`          |                               |
| 2         | `attitude_task_frequency`     |                               |
| 1         | `mag_hold_rate_limit`         |                               |
| 1         | MAG_HOLD_ERROR_LPF_FREQ       | not implemented yet as configurable     |
| 2         | `yaw_jump_prevention_limit`   |                               |
| 1         | `gyro_lpf`                    |                               |
| 1         | `acc_soft_lpf_hz`             |                               |
| 4         | _reserved_                    | reserved for further usage    |

## MSP_FILTER_CONFIG

Compatible with Betaflight

Frame IDs:

* MSP_FILTER_CONFIG Frame ID _92_
* MSP_SET_FILTER_CONFIG Frame ID _93_

| length    | setting                       | Notes                         |
| ----      | ----                          | ----                          |
| 1         | `gyro_soft_lpf_hz`            |   |
| 2         | `dterm_lpf_hz`                |   |
| 2         | `yaw_lpf_hz`                  |   |
| 2         | _not used_                    | Betaflight `masterConfig.gyro_soft_notch_hz_1`    |
| 2         | _not used_                    | Betaflight `masterConfig.gyro_soft_notch_cutoff_1`    |
| 2         | _not used_                    | Betaflight `pidProfile.dterm_notch_hz`    |
| 2         | _not used_                    | Betaflight `pidProfile.dterm_notch_cutoff`    |
| 2         | _not used_                    | Betaflight `masterConfig.gyro_soft_notch_hz_2`    |
| 2         | _not used_                    | Betaflight `masterConfig.gyro_soft_notch_cutoff_2`    |

## MSP_PID_ADVANCED

Compatible with Betaflight

Frame IDs:

* MSP_PID_ADVANCED Frame ID _94_
* MSP_SET_PID_ADVANCED Frame ID _95_

| length    | setting                       | Notes                         |
| ----      | ----                          | ----                          |
| 2         | `rollPitchItermIgnoreRate`    |                               |
| 2         | `yawItermIgnoreRate`          |                               |
| 2         | `yaw_p_limit`                 |                               |
| 1         | _not used_                    | Betaflight `deltaMethod`      |
| 1         | _not used_                    | Betaflight `vbatPidCompensation` |
| 1         | _not used_                    | Betaflight `setpointRelaxRatio`  |
| 1         | _not used_                    | Betaflight `dtermSetpointWeight` |
| 1         | _reserved_                    |                               |
| 1         | _reserved_                    |                               |
| 1         | _not used_                    | Betaflight `itermThrottleGain`    |
| 2         | `rate_accel_limit_roll_pitch` | divided by `1000` for BF compatibility    |
| 2         | `rate_accel_limit_yaw`        | divided by `1000` for BF compatibility    |

## INAV 1.3 MSP API 1.21

### case MSP_ADVANCED_CONFIG:

Frame IDs:

* MSP_ADVANCED_CONFIG, Frame ID _90_
* MSP_SET_ADVANCED_CONFIG, Frame ID _91_

| length    | setting                       | Notes               |
| ----      | ----                          | ----                |
| 1         | `gyro_sync_denom`             |                     |
| 1         | _not used_                    | Betaflight `masterConfig.pid_process_denom` |
| 1         | _not used                     | Betaflight `masterConfig.motorConfig.useUnsyncedPwm`  |
| 1         | `motor_pwm_protocol`          | _dictionary_  |
| 2         | `motor_pwm_rate`              |   |
| 2         | `servo_pwm_rate`              |   |
| 1         | `gyro_sync`                   | _boolean_  |
