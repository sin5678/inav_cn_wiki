# Overview

iNav supports autonomous flight using waypoints. In order to use this capability, it is also necessary to utilise and configure some supporting technologies, including:

* A GCS (Ground Control Station). The GCS will typically provide functions to create waypoint (WP) missions, upload WP missions to the flight controller (FC), validate the mission, execute the mission and log the mission;
* Telemetry Hardware. In order to transfer the mission to the FC and monitor the mission in real time during mission execution it is necessary to install and configure a telemetry system between the GCS and the multicopter.

This wiki topic describes the software currently available and some of the telemetry options. 

# Ground Control Stations

Currently there are two GCS applications widely used for iNav mission management, ezgui <http://ez-gui.com/> (Android) and mwp <https://github.com/stronnag/mwptools> (Linux). In future, other options may become available, particularly if the MAVLink protocol becomes supported by iNav.

ezgui and mwp both support mission planning (they share a common mission definition file format, so missions can be used in either tool), mission monitoring and mission logging. ezgui also provides a FC configuration capability. 

## EZGui (Android)

ezgui can be downloaded from the Google Play store, https://play.google.com/store/apps/details?id=com.ezio.multiwii&hl=en_GB. There is a free version and a (very reasonably priced) paid-for version with additional functionality. The application is not open source. 

## mwp (Linux)

mwp can be downloaded from <https://github.com/stronnag/mwptools>. It is available only as a source distribution and it is necessary to compile and install the application. Build instructions and dependencies are provided for Ubuntu and Fedora. Arch Linux users can install mwp from the AUR (Arch User Repository) https://aur.archlinux.org/packages/mwptools-git/. 

In addition to mission planning and logger, mwp also supports the replay of blackbox logs against a geospatial background (requires blackbox-tools <https://github.com/cleanflight/blackbox-tools>) and includes numerous poorly documented scripts for mission and blackbox analysis.

## Potential solutions for other platforms

# Telemetry Protocols
## MSP
## LTM
## MAVLink

# Telemetry Hardware

# Mission Planning

# Mission / Flight Monitoring

