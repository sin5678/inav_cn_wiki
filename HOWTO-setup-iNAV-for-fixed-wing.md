# HOWTO setup iNAV for fixed wing
The guide is currently under construction

## 1. Features
- Stabilization (Angle, Horizon modes)
- RTH (baro and mag are not needed for fixed wing)
- Battery monitoring
- RSSI monitoring
- Failsafe
- etc

## 2. What is needed
- Flight controller (one from the list, this guide shows how to setup CC3D)
- OSD (minimOSD or any other that supports Cleanflight)
- GPS receiver (any that supports at least 5Hz update)
- FPV hardware, airframe, RC

## 3. Flashing iNAV firmware to CC3D.
First you need to download a precompiled firmware for the board [here](https://github.com/iNavFlight/inav/releases). Next, you can check [numerous guides](https://www.youtube.com/watch?v=nb0ZSVMW4cQ) how to flash CC3D with third party firmware. Of course you need to specify the previously downloaded firmware for the flashing.

## 4. Basic settings
### Flight controller orientation.
This can be done only from CLI because you can not use GUI to enter angles more than 360, but iNAV uses deg*10 for angles. So in order to place the CC3D flight controller with USB plug to the left you need to navigate to CLI and enter the following:

`set align_board_yaw=900`

If you need to place the FC with USB plug facing right, then:

`set align_board_yaw=2700`

To save all the settings you did in the CLI it is needed to enter the command 'save' and hit enter.

### Port settings
It is done using Ports tab ![Ports tab](http://s8.hostingkartinok.com/uploads/images/2016/02/6f1a56073c11418b2020b59e9d036c55.png).

- UART1 - leave default value. You'll connect here either OSD or FTDI to setup the FC.
- UART3 - for GPS. Switch on the option and select the correct port speed. Of course, previously you need to setup your GPS receiver to output NMEA or UBX (preferred) packets, UART speed, update rate.

### Configuration
Next, connect your hardware according to the schemes:

Parallel PWM Receiver (picture in construction)

PPM Receiver (picture in construction)

UART Receiver (picture in construction)

On the Configuration tab in the Mixer group select the Airplane.
![Airplane](http://s8.hostingkartinok.com/uploads/images/2016/02/1bf925af382a8746ae8395a0efe22342.png)
Do not pay attention on the servo numbering! It will be described later.

If you don't want the motor rotation on arm, then switch on the MOTOR_STOP feature.

Switch on the GPS feature, and select the protocol.
![GPS and other settings](http://s8.hostingkartinok.com/uploads/images/2016/02/4f30a0ab600a47fb19522436a98ce677.png)

In the Other Features group you need to enable the Telemetry feature.

If your receiver connection is other than Parallel PWM Receiver, then you'll be able to setup battery voltage, current, RSSI monitoring. For example, to switch on the battery monitoring navigate to CLI and enter:

`feature VBAT`

`set vbat_scale = xxx`

instead of the xxx you need to enter the value that corresponds to resistor divider to get 3.3V from Ubat. You can use trial and error approach and after each new vbat_scale value you can check the calculated voltage using 'status' command.
Do not use GUI for vbat_scale settings! It doesn't work! Use for the purpose CLI only.

RSSI monitoring:

`feature RSSI_ADC`

`set RSSI_SCALE = xxx`

instead of xxx you need to enter the scale coefficient (1...255). With this coefficient the RSSI value equals to 100% when the transmitter is close to the receiver. You need to find such value of the RSSI_SCALE coefficient which when incremented by one gives RSSI value less than 100%. Don't forget to save your settings made in CLI by `save` command.

On the Receiver tab set up the channel order and their correspondence to a TX sticks movements.

On the Modes tab set up the flight modes according to the position of the AUX channels. For example, if you have a 3pos switch for the AUX1 you can get at minimum the following:

- minimum channel value - do not select any mode - only gyros will work. The hand launch take off in this mode is excellent.
- middle value - Angle or Horizon.
- maximum value - RTH+Angle (or RTH+Horizon). Return to home with stabilization.
![Flight modes](http://s8.hostingkartinok.com/uploads/images/2016/02/6d23377ca96046a5f62542105b4ce878.png)

### Failsafe

Coming soon

### Servo setup

Coming soon

### Motors

Coming soon

### OSD setup
You need to upload [MWOSD](http://www.mwosd.com/) firmware to your minimOSD. You can find pretty straight forward install guide following the [link](https://github.com/ShikOfTheRa/scarab-osd/blob/master/OTHER/DOCUMENTATION/FirmwareFlashing.md). As usual you use Arduino IDE for global OSD config. All changes are done in the Config.h file

OSD HARDWARE settings:

`#define MINIMOSD`

CONTROLLER SOFTWARE

`#define CLEANFLIGHT`

AIRCRAFT/INSTALLATION TYPE settings

`#define FIXEDWING`

Serial speed settings

`#define BAUDRATE 115200`

The screenshot of the MWOSD configuration is shown below:
![MWOSD config](http://s8.hostingkartinok.com/uploads/images/2016/02/8f9fa1c9a03629d846171cd89526f626.png)

You can find the demo video of the iNAV flight and RTH function [here](https://www.youtube.com/watch?v=GYd7mxGxNL8).

Good luck!