iNav is designed to work as well as possible with the default settings, but there can still be benefits or even be required to change a few of them, those settings will be listed and explained here here.

# Settings that are required to change:
### nav_mc_hover_thr
//TODO Explain what it does how to tune it



# Settings that are optional to change:
### nav_user_control_mode = ATTI
//TODO Explain difference (and risks) between CRUISE and ATTI

***
### gps_dyn_model = AIR_1G
* **PEDESTRIAN** Only use this if you really have to! Can help ublox 6m GPS units get more satellites, but be very careful with this setting because the gps position can get wrong if you fly aggressive, this will cause a fly-away if you are in position hold!
* **AIR_1G** Default. //TODO what is the advantage of this over AIR_4G?
* **AIR_4G** Use this if you have a fast copter/plane.

***

//TODO Explain velned on/off

//TODO Explain gyro_lpf