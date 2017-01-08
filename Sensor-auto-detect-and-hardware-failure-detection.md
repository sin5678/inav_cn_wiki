# How auto detect works in iNav

On iNav when mag_hardware and baro_hardware is set to `AUTO` it tries to auto detect which sensor is connected.  
When it finds a sensor it will change the parameter to the one found, example `BMP280`. If it fails to find any sensor it will set *_hardware to `NONE`

Reason for switching from `AUTO` to the detected sensor is to make the hardware failure detection work properly.

Default value after an new firmware flash is `AUTO`, this will cause the firmware to look for sensors on first boot, and set the found sensors.

If you connect a magnetometer after first boot it will not autodetect it, then you will have to either spesify `mag_hardware` manually, or do a new `mag_hardware = AUTO` to try and auto detect mag. ( This also applies if you already have an external mag connected, but dont have it powered up on first boot )

# Hardware failure detection

Need help