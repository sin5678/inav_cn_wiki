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

| Data | Usage |
| ---- | ---- |
| Latitude | int32 decimal degrees * 10,000,000 (1E7) |
| Longitude | int32 decimal degrees * 10,000,000 (1E7) |
| Altitude, uint32, cm (m / 100) [always 0 in iNav] |
| OSD on | uchar (always 1) |
| Fix | uchar, home fix status (0 == no fix) |

## Navigation Frame (N)

The payload is 6 bytes. Note that this frame largely mirrors the Multiwii-nav `MSP_NAV_STATUS` message and this contains redundancies and values that are not used in iNav. 

| Data | Usage |
| ---- | ---- |
| GPS mode | uchar |
| Nav mode | uchar |
| Nav Action | uchar (not all used in inav) |
| Waypoint number | uchar, target waypoint |
| Nav Error | uchar |
| Flags | uchar (to be defined) |

where:

| GPS mode |  Enumeration |
| ----------- | -------- |
| 0 | None |
| 1 | PosHold |
| 2 | RTH |
| 3 | Mission |

| Nav mode  |  Enumeration |
| ----------- | -------- |
| 0 | None |
| 1 | RTH Start |
| 2 | RTH Enroute | 
| 3 | PosHold infinite |
| 4 | PosHold timed |
| 5 | WP Enroute |
| 6 | Process next |
| 7 | Jump |
| 8 | Start Land |
| 9 | Landing in Progress |
| 10 | Landed |
| 11 | Settling before landing |
| 12 | Start descent |
| 15 | Critical GPS failure (yes 15, you never want to see this) |

Note that these values were defined by Multiwii-nav and not all are applicable to iNav.

| Nav Action |  Enumeration |
| ----------- | -------- |
| 0 | UNASSIGNED |
| 1 | WAYPOINT |
| 2 | POSHOLD_UNLIM |
| 3 | POSHOLD_TIME |
| 4 | RTH |
| 5 | SET_POI |
| 6 | JUMP |
| 7 | SET_HEAD |
| 8 | LAND |

| Nav Error |  Enumeration |
| ----------- | -------- |
| 0 | Navigation system is working |
| 1 | Next waypoint distance is more than the safety limit, aborting mission |
| 2 | GPS reception is compromised - pausing mission |
| 3 | Error while reading next waypoint from memory, aborting mission |
| 4 | Mission Finished |
| 5 | Waiting for timed position hold |
| 6 | Invalid Jump target detected, aborting mission |
| 7 | Invalid Mission Step Action code detected, aborting mission |
| 8 | Waiting to reach return to home altitude |
| 9 | GPS fix lost, mission aborted |
| 10 | Disarmed, navigation engine disabled |
| 11 | Landing is in progress, check attitude |

## GPS Extra Frame (X)

The payload is 6 bytes. 

| Data | Usage |
| ---- | ---- |
| HDOP | uint16 HDOP * 100 |
| spare | 4 bytes |


