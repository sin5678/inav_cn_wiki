# Overview

LTM was defined by "KipK" for the Ghetto Station antenna tracking project and originally implemented in Taulabs and Baseflight. It was adopted by iNav due to its excellent characteristics for low data rate / high update date telemetry.

Since its introduction to iNav, a number of extension have been added; these are documented below, in addition to the original frames.

# Protocol Definition

## Overview

The LTM protocol starts with "$T", followed by a function byte, the payload and a simple CRC checksum. It's weakness is that there is no length parameter (so the receiver needs to know, apriori,the length for each function), and the single byte checksum is not as robust as the multi-byte checksum in for example the ublox GPS protocol. However, the high data rate ensures that good rate should be delivered over occasional transmission errors.

LTM can provide good telemetry down to 2400 (5Hz attitude updates). Due to restrictions in iNav 1.2 and earlier, 9600 is the lowest baud rate supported, which gives 10Hz attitude and 5Hz GPS data.

The function consists of a single ASCII character, described below. Data is binary, little endian. The checksum is an XOR of the payload bytes.

The follow telemetry frames are supported:

| Function Byte | Usage |
| ------------- | ----- |
| G | GPS Frame |
| A | Attitude Frame |
| S | Status Frame |
| O | Origin Frame |
| N | Navigation Frame (iNav extension) |
| X | GPS eXended data (iNav extension) |

In addition, LTM is used by nrf24l01 / deviationtx with iNav, which defines the additional frame for in-TX tuning. This frame is not transmitted for telemetry.

| Function Byte | Usage |
| ------------- | ----- |
| T | Tuning frame (iNav extension) |

## GPS Frame (G)

The payload is 14 bytes. 

| Data | Format |
| ----- | ------- |
| Latitude | int32 decimal degrees * 10,000,000 (1E7) |
| Longitude | int32 decimal degrees * 10,000,000 (1E7) |
| Ground Speed |  uchar m/s |
| Altitude | (u)int32, cm (m / 100). In the original specification, this was unsigned. In iNav it is signed and should be so interpreted by consumers |
| Sats | uchar. bits 0-1 : fix ; bits 2-7 : number of satellites |

## Attitide Frame (A)

The payload is 6 bytes

| Data | Format |
| ---- | ---- |
| Pitch | int16, degrees |
| Roll | int16, degrees |
| Heading | int16, degrees |

## Status Frame (S)

The payload is 7 bytes

| Data | Format |
| ---- | ---- |
| Vbat | uint16, mV |
| Current | uint16, mA (not implemented in iNav) |
| RSSI | uchar |
| Airspeed | uchar, m/s |
| Status | uchar |

The status byte is used as

| Bit | Usage |
| ---- | ---- |
| 0 | armed |
| 1 | failsafe |
| 2 - 6 | status, as (shifted value): |
| |  Manual (0) |
| | Rate (1) |
| | Angle (2) |
| | Horizon (3) |
| | Acro (4) | 
| | Stabilised1 (5) |
| | Stabilised2 (6) |
| | Stabilised3 (7) |
| | Altitude Hold (8) |
| | GPS Hold (9) |
| | Waypoints (10) |
| | Head free (11) |
| | Circle (12) |
| | RTH (13) |
| | Follow me (14) |
| | Land (15) |
| | Fly by wire A (16) |
| | Fly by wire B (17) |
| | Cruise (18) |
| | Unknown (19) |

As a general purpose protocol, not all status can be mapped to iNav modes.

## Origin Frame (O)

The payload is 14 bytes

Latitude, int32 decimal degrees * 10,000,000 (1E7)
Longitude, int32 decimal degrees * 10,000,000 (1E7)
Altitude, uint32, cm (m / 100) // always 0 in inav
OSD on, uchar (always 1)
Fix, uchar, home fix status (0 == no fix)

Navigation Frame (N)
~~~~~~~~~~~~~~~~~~~~

Payload: 6 bytes

GPS mode, uchar
       None
       PosHold
       RTH
       Mission

Nav mode, uchar
    "None",                 // 0
    "RTH Start",            // 1
   "RTH Enroute",          // 2
   "PosHold infinite",     // 3
   "PosHold timed",        // 4
   "WP Enroute",           // 5
   "Process next",         // 6
   "Jump",                 // 7
   "Start Land",           // 8
   "Land in Progress",     // 9
   "Landed",               // 10
   "Settling before land", // 11
   "Start descent",        // 12
   "Critical GPS failure"  // 15(?)


Nav Action, uchar (not all used in inav)
    UNASSIGNED=0,
    WAYPOINT,
    POSHOLD_UNLIM,
    POSHOLD_TIME,
    RTH,
    SET_POI,
    JUMP,
    SET_HEAD,
    LAND

Waypoint number, uchar, target waypoint

Nav Error, uchar
    "Navigation system is working", // 0
    "Next waypoint distance is more than the safety limit, aborting mission", //1
    "GPS reception is compromised - pausing mission, COPTER IS ADRIFT!", //2
    "Error while reading next waypoint from memory, aborting mission", //3
    "Mission Finished" , //4
    "Waiting for timed position hold", //5
    "Invalid Jump target detected, aborting mission", //6
    "Invalid Mission Step Action code detected, aborting mission", //7
    "Waiting to reach return to home altitude", //8
    "GPS fix lost, mission aborted - COPTER IS ADRIFT!", //9
    "Copter is disarmed, navigation engine disabled", //10
    "Landing is in progress, check attitude if possible" //11

Flags, uchar ???



