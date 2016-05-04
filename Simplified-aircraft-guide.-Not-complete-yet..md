# The basic of getting iNav working on airplane

### Step 1, getting your flight controller ready.

* Flash newest iNav
* Do [Advanced accelerometer calibration](https://github.com/iNavFlight/inav/wiki/Advanced-accelerometer-calibration)
* Do Compass calibration. ( Move/point it in all direction/axis )
* Select your Mixer. (Mainly Airplane or fixed wing)

### Step 2, hooking everything up.

* Servo and ESC/MOTOR. 

Output 1 Motor/ESC

Output 2 Empty

Output 3 Elevator

Output 4 Aileron

Output 5 Aileron

Output 6 Rudder

* If using GPS connect it to UART 2.
* If using Sbus connect it to UART 3. (Note this requirres newer board like spracing f3)
* If using regular PPM connect it to IO 1 pin 1.

### Step 3, Setting up your remote, endpoinds and reverse of servos.

* Setup receiver/transmitter according to what you are using.
* If using GPS setup UART2 for GPS at baud 56000 and enable GPS if configurations.
* Your TX should no NO mixing at all, check that when moving the sticks, the right channels moves in the receiver window. Also everything should be centered at 1500us, and full stick movement should be 1000-2000us use subtrim and travel range on TX to set this up. 

The correct way is:

Throttle stick push away - increased value

Yaw (Rudder) stick right - increased value

Pitch (Elevator) stick push away - increased value

Roll (Ailerons) stick right - increased value

* Next up is making sure the servo's is moving the correct way. If something is not right. Use the Servo tab to get them center, adjust movement range and reverse of servo.

Servo 2: Elevator

Servo 3&4: Ailerons

Servo 5: Rudder

### Step 4, Replace default PIDs.

Default PIDs in iNav are mainly for multirotors. Find some PIDs [here](https://github.com/iNavFlight/inav/wiki/Tested-PID-values-on-different-types-of-aircrafts#fixed-wing) to use instead and tune from there.