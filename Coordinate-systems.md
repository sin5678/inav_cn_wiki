Navigation operates in 3 different coordinate systems.

## LLH (Geographic) Coordinate System

Represents position on or above earth with a latitude, longitude and height value. Height is defined as altitude above the mean sea level.

## NEU Coordinate System

* The x axis is aligned with the vector to the north pole (tangent to meridians).
* The y axis points to the east side (tangent to parallels)
* The z axis points up from the center of the earth

This is a classical cartesian coordinate system where the 3 axes are orthogonal to each other.

# Frames of reference

## Global (geodetic) frame of reference

This frame of reference defines coordinates in LLH coordinate system. This frame of reference is not used directly by the code and is provided as an interface for defining waypoints and receiving reference data from GPS.

## Local frame of reference

This frame of reference defines coordinate in NEU coordinate system relative to a GPS Origin point. GPS origin is defined as a point where GPS fix with sufficient accuracy was firstly acquired. GPS Origin is usually a point of launch. Most calculations are done in this frame of reference.

## Body-fixed frame of reference

Attached to the aircraft.

* The x axis points in forward direction (as defined by geometry and not by movement) (roll axis)
* The y axis points to the right (geometrically) (pitch axis)
* The z axis points upwards (geometrically) (yaw axis)

This frame of reference is used to read sensor data and calculate lean angles. Usually the only operations in this frame of reference are coordinate transformations to/from local frame of reference.