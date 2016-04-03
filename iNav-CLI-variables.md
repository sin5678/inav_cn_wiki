Cleanflight CLI variables related to navigation features

**General/Shared Variables**

| `Variable`                      | Description/Units                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Min    | Max    |
|---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|--------|
| `align_mag`                        | When using an external magnetometer sensor this should be set to actual sensor alignment relative to board. Values: DEFAULT, CW0, CW90, CW180, CW270, CW0FLIP, CW90FLIP, CW180FLIP, CW270FLIP | | |
| `align_board_roll`                 | Board alignment on ROLL axis (deg * 10) | -1800 | 3600 |
| `align_board_pitch`                | Board alignment on PITCH axis (deg * 10) | -1800 | 3600 |
| `align_board_yaw`                  | Board alignment on YAW axis (deg * 10) | -1800 | 3600 |
| `gps_provider`                     | GPS hardware type: NMEA, UBLOX, NAZA, I2C-NAV | | |
| `gps_nav_model`                    | GPS navigation model: LOW_G (Pedestrian), HIGH_G (Airborne<4G). Currently supported only of Ublox GPS modules. HIGH_G may increase accuracy, especially on fast and agile airplanes, but it requires much better satellite signal quality. Safe default is "LOW_G". | | |
| `failsafe_procedure`               | Failsafe type: SET-THR - set throttle to `failsafe_throttle`, RTH - execute RTH sequence if possible, land otherwise | | |
| `inav_accz_unarmedcal`             | Controls if inertial position estimator should compute gravity offset on accelerometer Z-axis dynamically when drone is unarmed. Mostly affects accuracy of altitude estimation and althold performace. No real reason to disable this feature. | OFF | ON |
| `inav_use_gps_velned`              | Defined if iNav should use velocity data provided by GPS module for doing position and speed estimation. If set to OFF iNav will fallback to calculating velocity from GPS coordinates. Using native velocity data may improve performance on some GPS modules. Some GPS modules introduce significant delay and using native velocity may actually result in much worse performance. Safe default is "OFF" | OFF | ON |
| `inav_gps_delay`                   | GPS position and velocity data usually arrive with a delay. This parameter defines this delay. Default should be reasonable for most GPS receivers. | 0 | 500 |
| `inav_gps_min_sats`                | Minimum number of GPS satellites in view to consider GPS position valid. Some GPS receivers appeared to be very inaccurate with low satellite count. | 5 | 10 |
| `inav_w_z_baro_p`                  | | 0 | 10 |
| `inav_w_z_gps_p`                   | | 0 | 10 |
| `inav_w_z_gps_v`                   | | 0 | 10 |
| `inav_w_xy_gps_p`                  | | 0 | 10 |
| `inav_w_xy_gps_v`                  | | 0 | 10 |
| `inav_w_xy_dr_v`                   | | 0 | 10 |
| `inav_w_z_res_v`                   | | 0 | 10 |
| `inav_w_xy_res_v`                  | | 0 | 10 |
| `inav_w_acc_bias`                  | | 0 | 1 |
| `inav_max_eph_epv`                 | | 0 | 9999 |
| `inav_baro_epv`                    | | 0 | 9999 |
| `nav_alt_p`                        | | | |
| `nav_alt_i`                        | | | |
| `nav_alt_d`                        | | | |
| `nav_vel_p`                        | | | |
| `nav_vel_i`                        | | | |
| `nav_vel_d`                        | | | |
| `nav_pos_p`                        | Controls how fast the drone will fly towards the target position. This is a multiplier to convert displacement to target velocity | | |
| `nav_pos_i`                        | Controls deceleration time. Measured in 1/100 sec. Expected hold position is placed at a distance calculated as _decelerationTime * currentVelocity_ | | |
| `nav_pos_d`                        | | | |
| `nav_posr_p`                       | P gain of Position-Rate (Velocity to Acceleration) PID controller. Higher P means stronger response when position error occurs. Too much P might cause "nervous" behavior and oscillations | 0 | 255 |
| `nav_posr_i`                       | I gain of Position-Rate (Velocity to Acceleration) PID controller. Used for drift compensation (caused by wind for example). Higher I means stronger response to drift. Too much I gain might cause target overshot | 0 | 255 |
| `nav_posr_d`                       | D gain of Position-Rate (Velocity to Acceleration) PID controller. It can damp P and I. Increasing D might help when drone overshoots target. | 0 | 255 |
| `nav_navr_p`                       | | | |
| `nav_navr_i`                       | | | |
| `nav_navr_d`                       | | | |
| `nav_use_midrc_for_althold`        | | OFF | ON |
| `nav_extra_arming_safety`          | If set to ON drone won't arm if no GPS fix | OFF | ON |
| `nav_user_control_mode`            | Defines how Pitch/Roll input from RC receiver affects flight in POSHOLD mode: ATTI - right stick controls attitude like in ANGLE mode; CRUISE - right stick controls velocity in forward and right direction. | | |
| `nav_position_timeout`             | If GPS fails wait for this much seconds before switching to emergency landing mode (0 - disable) | 0 | 10 |
| `nav_wp_radius`                    | Waypoint radius. Waypoint would be considered reached if machine is within this radius | 100 | 2000 |
| `nav_max_speed`                    | Maximum velocity firmware is allowed in full auto modes (POSHOLD, RTH, WP)  | 10 | 2000 |
| `nav_manual_speed`                 | Maximum velocity firmware is allowed when processing pilot input for POSHOLD/CRUISE control mode | | |
| `nav_manual_climb_rate`            | Maximum climb/descent rate firmware is allowed when processing pilot input for ALTHOLD control mode | | |
| `nav_pos_hold_deadband`            | | 10 | 250 |
| `nav_alt_hold_deadband`            | | 10 | 250 |
| `nav_min_rth_distance`             | | | |
| `nav_rth_alt_mode`                 | Altitude control mode: CURRENT, EXTRA, FIXED, MAX, AT_LEAST | | |
| `nav_rth_altitude`                 | | | |
| `gyro_soft_lpf_hz`                 | Software-based filter to remove mechanical vibrations from the gyro signal.  Value is cutoff frequency (Hz). For larger frames with bigger props set to lower value. Default 60Hz | 0 | 200 |
| `acc_soft_lpf_hz`                  | Software-based filter to remove mechanical vibrations from the accelerometer measurements.  Value is cutoff frequency (Hz). For larger frames with bigger props set to lower value. Default 15Hz | 0 | 200 |
| `baro_tab_size`                    | | | |
| `baro_noise_lpf`                   | | | |
| `magzero_x`                        | | | |
| `magzero_y`                        | | | |
| `magzero_z`                        | | | |
| `acczero_x`                        | | | |
| `acczero_y`                        | | | |
| `acczero_z`                        | | | |
| `accgain_x`                        | | | |
| `accgain_y`                        | | | |
| `accgain_z`                        | | | |


**Multirotor**

| `Variable`                      | Description/Units                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Min    | Max    |
|---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|--------|
| `nav_mc_bank_angle`                | Maximum banking angle (deg) that multicopter navigation is allowed to set. Machine must be able to satisfy this angle without loosing altitude | 15 | 45 |
| `nav_mc_hover_thr`                 | Multicopter hover throttle hint for altitude controller. Should be set to approximate throttle value when drone is hovering. | 1000 | 2000 |
| `nav_mc_min_fly_thr`               | Max throttle value treated as one of the conditions for landing detection. Must be sufficiently low to guarantee the "not flying" state even with full battery, but high enough for Altitude Hold controller to reach it. | 1000 | 2000 |
| `throttle_tilt_comp_str`           | Can be used in ANGLE and HORIZON mode and will automatically boost throttle when banking. Setting is in percentage, 0=disabled. | 0 | 100 |


**Fixed-Wing**

| `Variable`                      | Description/Units                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | Min    | Max    |
|---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------|--------|
| `nav_fw_cruise_thr`                | | | |
| `nav_fw_min_thr`                   | | | |
| `nav_fw_max_thr`                   | | | |
| `nav_fw_bank_angle`                | | | |
| `nav_fw_climb_angle`               | | | |
| `nav_fw_dive_angle`                | | | |
| `nav_fw_pitch2thr`                 | | | |