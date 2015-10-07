# Inertial position estimator (INAV)

Position estimator is a vital component for navigation subsystem. It takes data from all available sensors and fuses them together to figure out coordinates and velocities in the local frame of reference. All navigational decisions are made based on estimated position/velocity data. 

It is currently desined for multirotors.

## Priciple of operation

The key sensor for INAV is an accelerometer. Measured acceleration is translated from body-fixed frame to local NEU coordinates and integrated to yield velocities in North, East and Up directions. Velocity is further integrated to produce coordinates.

As accelerometer tend to drift, estimated velocities and coordinates tend to drift as well. This accumulated error is corrected from various reference sources - GPS, BARO, SONAR. Position estimator also maintains estimated position error for horizontal (X-Y) and vertical (Z) position.

When reference source is not available for some reason, estimated position error increases until it reaches a certain threshold. Beyond that threshold position is no longer updated and marked invalid until a valid reference source is available avain. This allows, for example, to fly through short (measured in seconds) GPS outages.

Using multiple sensors for estimation allows to filter noisy data (e.g. from barometer), interpolate between rare readings (e.g. from GPS), and immediately react on fast motion changes (using accelerometers) in the same time.

## Data soures

The following reference sources (with corresponding parameters for weight) are available for altitude and climb rate:

* Barometer - altitude (**inav_w_z_baro_p**)
* Barometer - velocity (**inav_w_z_baro_v**)
* Sonar - altitude (**inav_w_z_sonar_p**)
* Sonar - velocity (**inav_w_z_sonar_v**)
* GPS - altitude (**inav_w_z_gps_p**)
* GPS - velocity (**inav_w_z_gps_v**)

Sonar is optional source, it's only used when available and valid data received. GPS altitude is very noisy and is limited to FIXED_WING aircraft (experimental and untested).

The following reference sources (with corresponding parameters for weight) are available for position and velocity:

* GPS - position (**inav_w_xy_gps_p**)
* GPS - velocity (**inav_w_xy_gps_v**)

## Dead reckoning and handling sensor unavailability

* Enable dead reckoning (**inav_enable_dead_reckoning**)

* Dead reckoning - position (**inav_w_xy_dr_p**)
* Dead reckoning - velocity (**inav_w_xy_dr_v**)

* Velocity decay rate, XY-axis (**inav_w_xy_res_v**)
* Velocity decay rate, Z-axis (**inav_w_z_res_v**)

## Estimated position error thresholds

* Maximum acceptable position error (**inav_max_eph_epv**)
* Position error for SONAR sensor (**inav_sonar_epv**)
* Position error for BARO sensor (**inav_baro_epv**)

## GPS delay compensation

GPS data is not updated instantly. GPS module needs time to calculate new position and velocity. INAV has means of compensating for this delay. Expected GPS delay in milliseconds is controlled by **inav_gps_delay_ms** parameter. Typical value for GPS delay is 200ms.