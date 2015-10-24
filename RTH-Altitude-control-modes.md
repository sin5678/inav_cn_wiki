RTH sequence can control altitude in several different ways, controlled by **nav_rth_alt_mode** and **nav_rth_altitude** parameters.

Default setting is NAV_RTH_AT_LEAST_ALT - climb to preconfigured altitude if below, stay at current altitude if above.

## Maintain current altitude (NAV_RTH_NO_ALT)
nav_rth_alt_mode = 0

nav_rth_altitude is ignored

![](https://github.com/digitalentity/nav-rewrite-docs/blob/master/docs/assets/NAV_RTH_NO_ALT.jpg)

## Maintain current altitude + predefined safety margin (NAX_RTH_EXTRA_ALT)
nav_rth_alt_mode = 1

nav_rth_altitude defines extra altitude margin

![](https://github.com/digitalentity/nav-rewrite-docs/blob/master/docs/assets/NAX_RTH_EXTRA_ALT.jpg)

## Predefined altitude (NAV_RTH_CONST_ALT)
nav_rth_alt_mode = 2

nav_rth_altitude defines exact RTH altitude above launch point.

If the quadcopter is below nav_rth_altitude it will enter position hold and climb to desired altitude prior to flying back home. If the machine is above the desired altitude, it will turn and fly home and descend on the way.

![](https://github.com/digitalentity/nav-rewrite-docs/blob/master/docs/assets/NAV_RTH_CONST_ALT.jpg)

## Maximum altitude since launch (NAV_RTH_MAX_ALT)
nav_rth_alt_mode = 3

nav_rth_altitude is ignored

![](https://github.com/digitalentity/nav-rewrite-docs/blob/master/docs/assets/NAV_RTH_MAX_ALT.jpg)

## At least predefined altitude above launch point (NAV_RTH_AT_LEAST_ALT)
nav_rth_alt_mode = 4

nav_rth_altitude defines exact RTH altitude above launch point

![](https://github.com/digitalentity/nav-rewrite-docs/blob/master/docs/assets/NAV_RTH_AT_LEAST_ALT.jpg)
