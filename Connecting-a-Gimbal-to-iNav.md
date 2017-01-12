# Forewords

There are two outputs that can be used, in this guide we will name them PITCH and ROLL since when turning on `CAMSTAB` they will stabilize PITCH axis and ROLL Axis

There are mainly two scenarios for using `SERVO GIMBAL` feature.


1: Using an actuall gimbal like  [this](http://www.banggood.com/Upgrade-Debugging-Edition-JIYI-FPV-G3-3D-3-Axis-Gimbal-For-Gopro-Hero3-3-Hero4-Aerial-Photography-p-1031482.html?rmmds=search), with the purpose of just having controll over PITCH and ( ROLL OR YAW ) of gimball.

2: Controlling an gimbal like device like [this](https://www.youtube.com/watch?v=Py_RLdZwAlc&t=81s), which don't have any external gimbal control board. This will enable PITCH and ROLL controll and you can optinally enable `CAMSTAB` mode so the flight controller acts as an gimbal controller and stabilize the camera. If you want to sacrifise the ROLL-axis to control an servo controlling YAW-axis you need to disable `CAMSTAB`.

## Warning

On some boards (SP Racing F3 for example) servo connectors might not be 5V tolerant, while gimbal controller might be using INPUT_PULLUP 5V in Roll/Pitch inputs. This might damage flight controller

###  Difference between flight controller boards and mixer used.

Because boards are different, the pinout may be different. It also depends on what Mixer is being used.

QuadX Naze32    : Servo / Gimbal connect to pin 1 (Pitch) and pin 2 (Roll), motors get shifted to pin 4-8

QuadX SpracingF3: Servo / Gimbal connect to pin 7 (Pitch) and pin 8 (Roll), motors stay at pin 1-4

When using an gimbal with gimbal controller, simple use `Roll` input as yaw command instead.


## Servo Tilt usage

1. Connect servo according to your flightcontroller.  
1. Enable servo tilt feature.  
1. Enable `CAMSTAB` mode if you want to stabilize it. ( Don't use this if you have an actuall gimbal controller )  
1. Tune Servo MID, MIN and MAX to match your servo / gimbal so it centered and does not exceed mechanical limits.  
1. If the servo / gimbal moves incorrectly change direction on the `SERVO` tab to negativ number instead of positive.  
1. To control the servo / gimbal using a free AUX channel enter `SERVO` tab and assign an free AUX to servo 0 (Pitch) and servo 1 (Roll).  
