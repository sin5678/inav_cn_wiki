# HOWTO setup iNAV for fixed wing

## Index
1. Features

2. What is needed

3. Flashing iNAV firmware to CC3D.

4. Basic settings

Flight controller orientation.

Port settings

Configuration

Failsafe

Transmitter setup

Motors

Servo setup

Recommended power layout

OSD setup



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
- UART3 - for GPS. Switch on the option and select the correct port speed. Of course, previously you need to setup your GPS receiver to output NMEA or UBX (preferred) packets, UART speed, update rate, according to the [Gps.md article](https://github.com/iNavFlight/inav/blob/master/docs/Gps.md)

### Configuration
Next, connect your hardware according to the schemes:

Parallel PWM Receiver ([click here](http://s8.hostingkartinok.com/uploads/images/2016/02/a47fb019c7783371053239a3d23a8d46.jpg) to see the real hardware photo)

<img src="http://s8.hostingkartinok.com/uploads/images/2016/02/4e641362191528c42758d626757b747a.png" width="400" height="300" />

PPM Receiver

<img src="http://s8.hostingkartinok.com/uploads/images/2016/02/c98cfcf64df8a8a7645429dc7ac4c0ea.png" width="400" height="300" />

Of course, according to the receiver used you need to enable one of the features: `feature RX_PPM` for the PPM receiver. For more information about CC3D pinout check the [CC3D](https://github.com/iNavFlight/inav/blob/master/docs/Board%20-%20CC3D.md) page

On the Configuration tab in the Mixer group select the Airplane.
![Airplane](http://s8.hostingkartinok.com/uploads/images/2016/02/1bf925af382a8746ae8395a0efe22342.png)
Do not pay attention on the servo numbering! It will be described later.

If you don't want the motor rotation on arm, then switch on the MOTOR_STOP feature.

By default iNav won't arm without GPS fix. To disable use CLI: "set nav_extra_arming_safety = OFF"

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

See here for RTH failsafe https://github.com/iNavFlight/inav/wiki/%5BWiP%5D-Quick-setup-guide#4-setting-up-failsafe-with-return-to-home

For more information check the [failsafe](https://github.com/iNavFlight/inav/blob/master/docs/Failsafe.md) page

###Transmitter setup

You should adjust (normal or reverse) on your transmitter so sticks correspond to below:

In reciever tab:
* Throttle stick push away - increased value
* Yaw (Rudder) stick right - increased value
* Pitch (Elevator) stick push away - increased value
* Roll (Ailerons) stick right - increased value

Also use subtrim to get center value of 1500us and use travel adjustment to get at lowest value 1000us and highest 2000us when moving sticks.

### Motors

After this follow to the Motors tab, rock your plane and notice what levels are moving depending on PITCH, ROLL and YAW angles. You can remember it or write it down. ROLL - 4,5; PITCH - 3, YAW - 6.

![Motors tab](http://s8.hostingkartinok.com/uploads/images/2016/02/bb1293fb31f72ea57b11487172a87407.png)

Turn on your transmitter, switch to the Angle or Horizon flight mode and follow the Servos tab.

### Servo setup

![Servo tab](http://s8.hostingkartinok.com/uploads/images/2016/02/4774905124ad93e7fe9fe476baba3c1c.png)

Here you need to be very attentive. In this tab you set up endpoints, neutral, rates and reverse for stabilization modes. Servo numbering in the tab starts from 0!

For the Elevator, tilt the plane's tail down, and the Elevator should go down. If the elevator goes up, then you need to set the Rate (the right-most drop down list) Servo 2 with negative sign.

Tilt the left wing down. Left Aileron should go down and right one should go up. If it is not so, then put negative Rate values for Servo 3 and Servo 4 (if your ailerons are connected by means of Y-cable, than you can change the settings for only one Servo or connect the Y-cable to other Servo out). 

Turn the tail to the left, and the Rudder should go to the left. Otherwise switch the Servo 5 Rate to negative.

After this stick movement should also move servos the correct way. (General rules: Elevator stick down - elevator goes up, Aileron stick to the left - left aileron is up, right aileron is down, Rudder stick to the left, rudder goes to the left)

Attention! all the endpoints, neutrals, trimmers should be done on this tab, not in transmitter!

### Recommended power layout

To prevent brownout its wise to power servos with one BEC and the flight controller + other equipment with another BEC.

This is one way to accomplish it: 

Glued a new row of pins onto the case of the flightcontroller, the must be connected together. (See the bottom of pins)

All servos and ESC is connected to flightcontroller, except positive wire which goes to the new row. (This line gets its power from the BEC in the ESC)

Another external BEC is connected at random positive and negativ pin on flight controller to power it, the receiver and GPS.

This way if one servo get stuck and draws alot of amps you shouldnt risk your flight system to power down.

![Connection Diagram](http://s13.postimg.org/5kpkb9ppz/Connection_Diagram.png)
![Real life example](http://s28.postimg.org/jjg5paz65/Real_life_example_power_supply.png)

### CLI features worth mentioning.

"nav_extra_arming_safety" Default is on. This requirres GPS lock to get the plane armed if any modes that requirres GPS are configured.

"failsafe_procedure" Needs to be RTH if you want RTH failsafe.

Fixed wing spesific parameters, adjust to something suitable for your plane. 

set nav_fw_cruise_thr

set nav_fw_min_thr

set nav_fw_max_thr

set nav_fw_bank_angle

set nav_fw_climb_angle

set nav_fw_dive_angle

set nav_fw_pitch2thr

set nav_fw_loiter_radius

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
![MWOSD config](http://s8.hostingkartinok.com/uploads/images/2016/02/17582422170a13c2169af18d16623129.png)

Watch this demo video of the iNAV flight and RTH function:

[![iNAV on FT Duster](http://img.youtube.com/vi/GYd7mxGxNL8/0.jpg)](https://www.youtube.com/watch?v=GYd7mxGxNL8)

Good luck!