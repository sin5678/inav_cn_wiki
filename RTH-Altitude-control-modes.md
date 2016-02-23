RTH sequence can control altitude in several different ways, controlled by **nav_rth_alt_mode** and **nav_rth_altitude** parameters.

Default setting is NAV_RTH_AT_LEAST_ALT - climb to preconfigured altitude if below, stay at current altitude if above.

## Maintain current altitude (NAV_RTH_NO_ALT)
nav_rth_alt_mode = CURRENT

nav_rth_altitude is ignored

![](images/NAV_RTH_NO_ALT.jpg)

## Maintain current altitude + predefined safety margin (NAX_RTH_EXTRA_ALT)
nav_rth_alt_mode = EXTRA

nav_rth_altitude defines extra altitude margin

![](images/NAX_RTH_EXTRA_ALT.jpg)

## Predefined altitude (NAV_RTH_CONST_ALT)
nav_rth_alt_mode = FIXED

nav_rth_altitude defines exact RTH altitude above launch point.

If the quadcopter is below nav_rth_altitude it will enter position hold and climb to desired altitude prior to flying back home. If the machine is above the desired altitude, it will turn and fly home and descend on the way.

![](images/NAV_RTH_CONST_ALT.jpg)

## Maximum altitude since launch (NAV_RTH_MAX_ALT)
nav_rth_alt_mode = MAX

nav_rth_altitude is ignored

![](images/NAV_RTH_MAX_ALT.jpg)

## At least predefined altitude above launch point (NAV_RTH_AT_LEAST_ALT)
nav_rth_alt_mode = AT_LEAST

nav_rth_altitude defines exact RTH altitude above launch point

![](images/NAV_RTH_AT_LEAST_ALT.jpg)