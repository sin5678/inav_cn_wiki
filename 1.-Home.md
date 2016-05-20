![](http://static.rcgroups.net/forums/attachments/1/5/9/3/2/7/a8809082-59-inav.png)

iNav is a fork of cleanflight with focus on GPS features.
It currently supports position hold, RTH with predefined climb height, waypoints and follow-me. Both with airplanes & multirotors.

iNav have some settings that are different than stock cleanflight, and simply restoring settings from older cleanflight won't work.

It is ABSOLUTELY mandatory to read this page, and the pages that it links to.
  


### Getting started

Download the *.hex file for your flight controller from the [latest stable iNav release page](https://github.com/iNavFlight/inav/releases/latest) and use the chrome app [Cleanflight Configurator](https://chrome.google.com/webstore/detail/cleanflight-configurator/enacoimjcgeinfnnnpajinjgmkahmfgb) to flash it. You can also buy the android app [Cleanflight flasher](https://play.google.com/store/apps/details?id=com.eziosoft.cleanflight_flasher) to directly download newest version and flash.

You can also install in Chrome the [INAV Configurator](https://github.com/iNavFlight/inav-configurator), but you will have to install it in a [Alternative way](https://github.com/iNavFlight/inav-configurator#alternative-way). This is a better option, as you can download the new releases directly from it. INAV Configurator, wich is designed for INAV, has some diferences and improvements over Cleanflight configurator.

If your board is not aligned “normally”, with the printed arrow pointing to the quad’s front, you have to set board alignment. This can be needed to access the usb port from the side of the quad. iNav is different from cleanflight here, board alignment angles are set in degrees*10. So if your board is mounted 90 degrees clockwise to get USB port out to the side, you should type in CLI set align_board_yaw = 900

Next you should do accelerometer calibration. This is different from cleanflight, follow the steps in the page  ["Advanced accelerometer calibration"](https://github.com/iNavFlight/inav/wiki/Advanced-accelerometer-calibration)

Then do the compass calibration

Next you need to setup your craft normally as you would with cleanflight.

[Painless360 video guide for multirotors](https://youtu.be/4OKGMhTrqOU)

[Wiki guide for fixed wing airplanes](https://github.com/iNavFlight/inav/wiki/Fixed-wing-guide-for-iNav.#the-basic-of-getting-inav-working-on-airplane)

[Wiki guide for fixed wing airplanes using CC3D](https://github.com/iNavFlight/inav/wiki/Howto:-CC3D-flight-controller,-minimOSD-and-GPS-for-fixed-wing.#howto-setup-inav-for-fixed-wing)






### Notes

* iNav has removed all other telemetry options when using Naze32 targets but LTM in official builds, if you need let's say Frsky telemetry you need to compile your own. See link. Eg. F3 board, which have more memory, have Frsky included.

* iNav does not show "GPS Signal Strength" for each satellite in the Cleanflight configurator, instead only the first one is used to show [HDOP](https://en.wikipedia.org/wiki/Dilution_of_precision_%28GPS%29)

* iNav has only one PID controller called fp-pid. This is a modified version of luxfloat, and will show up as luxfloat in cleanflight configurator.

* iNav has an extra safety feature that prevents you from arming your aircraft if no proper GPS lock is acquired. Nav_extra_arming_safety is turned ON by default.

* iNav has other GPS modes than cleanflight, or names them differently. Read this wiki page for how to use them, and combine them to get wanted position hold.

* If your copter is toilet-bowling, which means, in the beginning it holds it’s position and then starts to make bigger and bigger circles, you probably have your magnetometer not calibrated correctly or it’s seeing the magnetic field of you power lines or the beeper.

This should get you in the air, but iNav is not “plug and play”.
There are many important settings you need to change to get it flying the way you want it. You need to read through the Wiki and you should read through the iNav CLI variables, as there are variables that you may change to tailor iNav for your aircraft, and your preferences.

**Checklist if you're having issue with something:**

1. Try and look through the wiki regarding the issue you have. You can also search the Wiki.
1. Read the first post [rcgroups Cleanflight iNav thread](http://www.rcgroups.com/forums/showthread.php?t=2495732). Also read the last 5 pages in the thread to see if someone else has already mentioned it. Also try and search in the thread.
1. Explain your issue, include CLI dump and blackbox log if you have a logger. Mention what you have tried, and also if it's working as intended in stock Cleanflight.
