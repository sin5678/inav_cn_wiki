# How auto detect works in iNav

On iNav when mag_hardware and baro_hardware is set to `AUTO` it tries to auto detect which sensor is connected.  
When it finds a sensor it will change the parameter to the found, example `BMP280`. If it fails to find any sensor it will set _hardware to `NONE`

Reason for switching from `AUTO` to the detected sensor is to make the hardware failure detection work properly.