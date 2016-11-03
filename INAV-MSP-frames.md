## MSP_INAV_PID

Frames IDs

* MSP_INAV_PID, Frame ID _6_
* MSP_SET_INAV_PID, Frame ID _7_

| length    | setting                   | Payload Length    |
| ----      | ----                      | ----              |
| 1         | async_mode                | 1                 |
| 2         | acc_task_frequency        | 3                 |
| 2         | attitude_task_frequency   | 5                 |
| 1         | mag_hold_rate_limit       | 6                 |
| 1         | MAG_HOLD_ERROR_LPF_FREQ (not implemented yet as configurable) | 7     |
| 2         | yaw_jump_prevention_limit | 9                 |
| 1         | gyro_lpf       | 10                 |
| 5         | _reserved_                | 15                |