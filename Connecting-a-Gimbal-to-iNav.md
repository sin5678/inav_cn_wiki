# Forewords

There are two ways of doing this.

1: Using channel forwarding, this is to control pitch and yaw on a self-stabilization gimbal like [this](http://www.banggood.com/Upgrade-Debugging-Edition-JIYI-FPV-G3-3D-3-Axis-Gimbal-For-Gopro-Hero3-3-Hero4-Aerial-Photography-p-1031482.html?rmmds=search) that has its own board with sensor to stabilize the gimbal itself.

2: Using servo_tilt to let the flight controller do the stabilization itself. It is example when using two servos to stabilize and camera. Like [this](https://www.youtube.com/watch?v=Py_RLdZwAlc&t=81s)

## Difference between flight controller boards and mixer used.

Because boards are different, the pinout may be different. It also depends on what Mixer is being used.

Naze32: Servos connect to pin 1 and pin 2, motors get shifted to pin 4-8

SpracingF3: Servos connect to pin 7 and 8, motors stay at pin 1-4

## Warning

On some boards (SP Racing F3 for example) servo connectors might not be 5V tolerant, while gimbal controller might be using INPUT_PULLUP 5V in Roll/Pitch inputs. This might damage flight controller