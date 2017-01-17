
|  Variable Name | Default Value | Description |
|  ------ | ------ | ------ |
|  looptime  | 2000 | This is the main loop time (in us). Changing this affects PID effect with some PID controllers (see PID section for details). Default of 3500us/285Hz should work for everyone. Setting it to zero does not limit loop time, so it will go as fast as possible. |
|  i2c_overclock  | OFF | Enabling this feature speeds up IMU speed significantly and faster looptimes are possible. |
|  gyro_sync  | OFF | This option enables gyro_sync feature. In this case the loop will be synced to gyro refresh rate. Loop will always wait for the newest gyro measurement. Use gyro_lpf and gyro_sync_denom determine the gyro refresh rate. Note that different targets have different limits. Setting too high refresh rate can mean that FC cannot keep up with the gyro and higher gyro_sync_denom is needed, |
|  gyro_sync_denom  | 2 | This option determines the sampling ratio. Denominator of 1 means full gyro sampling rate. Denominator 2 would mean 1/2 samples will be collected. Denominator and gyro_lpf will together determine the control loop speed. |
|  acc_task_frequency  | 500 |  |
|  attitude_task_frequency  | 250 |  |
|  async_mode  | NONE |  |
|  mid_rc  | 1500 | This is an important number to set in order to avoid trimming receiver/transmitter. Most standard receivers will have this at 1500, however Futaba transmitters will need this set to 1520. A way to find out if this needs to be changed, is to clear all trim/subtrim on transmitter, and connect to GUI. Note the value most channels idle at - this should be the number to choose. Once midrc is set, use subtrim on transmitter to make sure all channels (except throttle of course) are centered at midrc value. |
|  min_check  | 1100 | These are min/max values (in us) which, when a channel is smaller (min) or larger (max) than the value will activate various RC commands, such as arming, or stick configuration. Normally, every RC channel should be set so that min = 1000us, max = 2000us. On most transmitters this usually means 125% endpoints. Default check values are 100us above/below this value. |
|  max_check  | 1900 | These are min/max values (in us) which, when a channel is smaller (min) or larger (max) than the value will activate various RC commands, such as arming, or stick configuration. Normally, every RC channel should be set so that min = 1000us, max = 2000us. On most transmitters this usually means 125% endpoints. Default check values are 100us above/below this value. |
|  rssi_channel  | 0 |  |
|  rssi_scale  | 30 |  |
|  rssi_ppm_invert  | OFF |  |
|  rc_smoothing  | ON |  |
|  input_filtering_mode  | OFF |  |
|  min_throttle  | 1150 |  |
|  max_throttle  | 1850 |  |
|  min_command  | 1000 |  |
|  3d_deadband_low  | 1406 |  |
|  3d_deadband_high  | 1514 |  |
|  3d_neutral  | 1460 |  |
|  3d_deadband_throttle  | 50 |  |
|  motor_pwm_rate  | 400 |  |
|  motor_pwm_protocol  | STANDARD |  |
|  fixed_wing_auto_arm  | OFF |  |
|  disarm_kill_switch  | ON |  |
|  auto_disarm_delay  | 5 |  |
|  small_angle  | 25 |  |
|  reboot_character  | 82 |  |
|  gps_provider  | UBLOX |  |
|  gps_sbas_mode  | NONE |  |
|  gps_dyn_model  | AIR_1G |  |
|  gps_auto_config  | ON |  |
|  gps_auto_baud  | ON |  |
|  inav_auto_mag_decl  | ON |  |
|  inav_accz_unarmedcal  | ON |  |
|  inav_use_gps_velned  | ON |  |
|  inav_gps_delay  | 200 |  |
|  inav_gps_min_sats  | 6 |  |
|  inav_w_z_baro_p  | 0.350 |  |
|  inav_w_z_gps_p  | 0.200 |  |
|  inav_w_z_gps_v  | 0.500 |  |
|  inav_w_xy_gps_p  | 1.000 |  |
|  inav_w_xy_gps_v  | 2.000 |  |
|  inav_w_z_res_v  | 0.500 |  |
|  inav_w_xy_res_v  | 0.500 |  |
|  inav_w_acc_bias  | 0.010 |  |
|  inav_max_eph_epv  | 1000.000 |  |
|  inav_baro_epv  | 100.000 |  |
|  nav_disarm_on_landing  | OFF |  |
|  nav_use_midthr_for_althold  | OFF |  |
|  nav_extra_arming_safety  | ON |  |
|  nav_user_control_mode  | ATTI |  |
|  nav_position_timeout  | 5 |  |
|  nav_wp_radius  | 100 |  |
|  nav_max_speed  | 300 |  |
|  nav_max_climb_rate  | 500 |  |
|  nav_manual_speed  | 500 |  |
|  nav_manual_climb_rate  | 200 |  |
|  nav_landing_speed  | 200 |  |
|  nav_land_slowdown_minalt  | 500 |  |
|  nav_land_slowdown_maxalt  | 2000 |  |
|  nav_emerg_landing_speed  | 500 |  |
|  nav_min_rth_distance  | 500 |  |
|  nav_rth_climb_first  | ON |  |
|  nav_rth_tail_first  | OFF |  |
|  nav_rth_alt_mode  | AT_LEAST |  |
|  nav_rth_altitude  | 1000 |  |
|  nav_mc_bank_angle  | 30 |  |
|  nav_mc_hover_thr  | 1500 |  |
|  nav_mc_auto_disarm_delay  | 2000 |  |
|  nav_fw_cruise_thr  | 1400 |  |
|  nav_fw_min_thr  | 1200 |  |
|  nav_fw_max_thr  | 1700 |  |
|  nav_fw_bank_angle  | 20 |  |
|  nav_fw_climb_angle  | 20 |  |
|  nav_fw_dive_angle  | 15 |  |
|  nav_fw_pitch2thr  | 10 |  |
|  nav_fw_roll2pitch  | 75 |  |
|  nav_fw_loiter_radius  | 5000 |  |
|  nav_fw_launch_velocity  | 300 |  |
|  nav_fw_launch_accel  | 1863 |  |
|  nav_fw_launch_detect_time  | 40 |  |
|  nav_fw_launch_thr  | 1700 |  |
|  nav_fw_launch_motor_delay  | 500 |  |
|  nav_fw_launch_timeout  | 5000 |  |
|  nav_fw_launch_climb_angle  | 10 |  |
|  serialrx_provider  | SPEK1024 |  |
|  spektrum_sat_bind  | 0 |  |
|  telemetry_switch  | OFF |  |
|  telemetry_inversion  | ON |  |
|  frsky_default_lattitude  | 0.000 |  |
|  frsky_default_longitude  | 0.000 |  |
|  frsky_coordinates_format  | 0 |  |
|  frsky_unit  | IMPERIAL |  |
|  frsky_vfas_precision  | 0 |  |
|  frsky_vfas_cell_voltage  | OFF |  |
|  hott_alarm_sound_interval  | 5 |  |
|  smartport_uart_unidir  | OFF |  |
|  battery_capacity  | 0 |  |
|  vbat_scale  | 110 |  |
|  vbat_max_cell_voltage  | 43 |  |
|  vbat_min_cell_voltage  | 33 |  |
|  vbat_warning_cell_voltage  | 35 |  |
|  current_meter_scale  | 400 |  |
|  current_meter_offset  | 0 |  |
|  multiwii_current_meter_output  | OFF |  |
|  current_meter_type  | ADC |  |
|  align_gyro  | DEFAULT |  |
|  align_acc  | DEFAULT |  |
|  align_mag  | DEFAULT |  |
|  align_board_roll  | 0 |  |
|  align_board_pitch  | 0 |  |
|  align_board_yaw  | 0 |  |
|  gyro_lpf  | 42HZ |  |
|  moron_threshold  | 32 |  |
|  imu_dcm_kp  | 2500 |  |
|  imu_dcm_ki  | 50 |  |
|  imu_dcm_kp_mag  | 10000 |  |
|  imu_dcm_ki_mag  | 0 |  |
|  pos_hold_deadband  | 20 |  |
|  alt_hold_deadband  | 50 |  |
|  yaw_motor_direction  | 1 |  |
|  yaw_jump_prevention_limit  | 200 |  |
|  tri_unarmed_servo  | ON |  |
|  servo_lowpass_freq  | 400 |  |
|  servo_lowpass_enable  | OFF |  |
|  servo_center_pulse  | 1500 |  |
|  servo_pwm_rate  | 50 |  |
|  failsafe_delay  | 5 |  |
|  failsafe_recovery_delay  | 5 |  |
|  failsafe_off_delay  | 200 |  |
|  failsafe_throttle  | 1000 |  |
|  failsafe_kill_switch  | OFF |  |
|  failsafe_throttle_low_delay  | 100 |  |
|  failsafe_procedure  | SET-THR |  |
|  rx_min_usec  | 885 |  |
|  rx_max_usec  | 2115 |  |
|  acc_hardware  | MPU6050 |  |
|  baro_use_median_filter  | ON |  |
|  baro_hardware  | MS5611 |  |
|  mag_hardware  | NONE |  |
|  blackbox_rate_num  | 1 |  |
|  blackbox_rate_denom  | 1 |  |
|  blackbox_device  | SPIFLASH |  |
|  magzero_x  | 0 |  |
|  magzero_y  | 0 |  |
|  magzero_z  | 0 |  |
|  acczero_x  | 0 |  |
|  acczero_y  | 0 |  |
|  acczero_z  | 0 |  |
|  ledstrip_visual_beeper  | OFF |  |
|  accgain_x  | 4096 |  |
|  accgain_y  | 4096 |  |
|  accgain_z  | 4096 |  |
|  nav_alt_p  | 50 |  |
|  nav_alt_i  | 0 |  |
|  nav_alt_d  | 0 |  |
|  nav_vel_p  | 100 |  |
|  nav_vel_i  | 50 |  |
|  nav_vel_d  | 10 |  |
|  nav_pos_p  | 65 |  |
|  nav_pos_i  | 120 |  |
|  nav_pos_d  | 10 |  |
|  nav_posr_p  | 180 |  |
|  nav_posr_i  | 15 |  |
|  nav_posr_d  | 100 |  |
|  nav_navr_p  | 10 |  |
|  nav_navr_i  | 5 |  |
|  nav_navr_d  | 8 |  |
|  deadband  | 5 |  |
|  yaw_deadband  | 5 |  |
|  throttle_tilt_comp_str  | 0 |  |
|  flaperon_throw_offset  | 250 |  |
|  flaperon_throw_inverted  | OFF |  |
|  gimbal_mode  | NORMAL |  |
|  fw_iterm_throw_limit  | 165 |  |
|  mode_range_logic_operator  | OR |  |
|  default_rate_profile  | 0 |  |
|  mag_declination  | 0 |  |
|  mag_hold_rate_limit  | 90 |  |
|  p_pitch  | 40 |  |
|  i_pitch  | 30 |  |
|  d_pitch  | 23 |  |
|  p_roll  | 40 |  |
|  i_roll  | 30 |  |
|  d_roll  | 23 |  |
|  p_yaw  | 85 |  |
|  i_yaw  | 45 |  |
|  d_yaw  | 0 |  |
|  p_level  | 20 |  |
|  i_level  | 15 |  |
|  d_level  | 75 |  |
|  max_angle_inclination_rll  | 300 |  |
|  max_angle_inclination_pit  | 300 |  |
|  gyro_soft_lpf_hz  | 60 |  |
|  acc_soft_lpf_hz  | 15 |  |
|  dterm_lpf_hz  | 40 |  |
|  yaw_lpf_hz  | 30 |  |
|  yaw_p_limit  | 300 |  |
|  iterm_ignore_threshold  | 200 |  |
|  yaw_iterm_ignore_threshold  | 50 |  |
|  rate_accel_limit_roll_pitch  | 0 |  |
|  rate_accel_limit_yaw  | 10000 |  |
|  rc_expo  | 70 |  |
|  rc_yaw_expo  | 20 |  |
|  thr_mid  | 50 |  |
|  thr_expo  | 0 |  |
|  roll_rate  | 20 |  |
|  pitch_rate  | 20 |  |
|  yaw_rate  | 20 |  |
|  tpa_rate  | 0 |  |
|  tpa_breakpoint  | 1500 |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|  #VALUE! | #VALUE! |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |
|   |  |  |