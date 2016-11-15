# 1. Setting up the hardware

## Vibration dampening
iNav firmware is using inertial navigation system (INS), this means that firmware is dependant on ways of accurately measuring acceleration. Vibration is essentially a periodic acceleration and will confuse the INS up to the total inability to do its job correctly. There are two ways of fighting vibraton - balancing props and motors and vibration dampening. If applied together these two methods greatly improve INS performace.

## GPS
iNav supports Ublox gps and NMEA (untested)

Tested and recommend GPS are M8N versions ( example [Ublox NEO-M8N](http://m.banggood.com/Ublox-NEO-M8N-Flight-Controller-GPS-with-Protective-Shell-for-PIX-PX4-Pixhawk-p-1005394.html?AID=12202217&PID=3836173&SID=ikzicawnsk0004o402ecu&source=affiliate&utm_source=Banggood_CJ&utm_medium=commission_junction&utm_campaign=OpenPilot&utm_content=sandy) and [Beitian BN-880](http://m.banggood.com/UBLOX-NEO-M8N-BN-880-Flight-Control-GPS-Module-Dual-Module-Compass-p-971082.html) )
But both M6N and M7N should work.

With default iNav settings iNav will configure ublox GPS for you, no need to use software like u-center.

Also be aware that some of our flight controllers can cause interference with the GPS causing low satellites or even no satellites at all, keep GPS as far as possible away and think of either shield your GPS or flight controller and other equipment that can cause interference.

