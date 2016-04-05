iNav removed native support for various exotic and not often used frames on STM32F1 targets. This includes CC3D, Naze32 and Flip32. The reason for this is simple: limited flash size and very few people using them while in many cases they can be implemented using custom mixers.

Removed mixer presets can not be selected in Configurator: on save it will be reverted to generic QuadX.

# Setups that can be implemented with custom mixer

Following setups can be configured with custom mixer of F1 targets:

## Quadcopter + configuration [Motors on front, rear, left and right]

```
mmix custom
mmix reset
mmix 0 1.0 0.0 1.0 -1.0   // REAR
mmix 1 1.0 -1.0 0.0 1.0   // RIGHT
mmix 2 1.0 1.0 0.0 1.0    // LEFT
mmix 3 1.0 0.0 -1.0 -1.0  // Front
```

## Hexa H6

```
mmix custom
mmix reset
mmix 0 1.0 -1.0 1.0 -1.0     // REAR_R
mmix 1 1.0 -1.0 -1.0 1.0     // FRONT_R
mmix 2 1.0 1.0 1.0 1.0       // REAR_L
mmix 3 1.0 1.0 -1.0 -1.0     // FRONT_L
mmix 4 1.0 0.0 0.0 0.0       // RIGHT
mmix 5 1.0 0.0 0.0 0.0       // LEFT
```

## Quadcopter A-tail

This configuration probably can be improved, similar to V-tail config

```
mmix custom
mmix reset
mmix 0 1.0 0.0 1.0 1.0          // REAR_R
mmix 1 1.0 -1.0 -1.0 0.0        // FRONT_R
mmix 2 1.0 0.0 1.0 -1.0         // REAR_L
mmix 3 1.0 1.0 -1.0 -0.0        // FRONT_L
```

## Quadcopter V-tail

```
mmix custom
mmix reset
mmix 0 1.0 -0.58 0.58 1.0        // REAR_R
mmix 1 1.0 -0.46 -0.39 -0.5      // FRONT_R
mmix 2 1.0 0.58 0.58 -1.0        // REAR_L
mmix 3 1.0 0.46 -0.39 0.5        // FRONT_L
```

## Hexa Y6

```
mmix custom
mmix reset
mmix 0 1.0 0.0 1.333333 1.0     // REAR
mmix 1 1.0 -1.0 -0.666667 -1.0  // RIGHT
mmix 2 1.0 1.0 -0.666667 -1.0   // LEFT
mmix 3 1.0 0.0 1.333333 -1.0    // UNDER_REAR
mmix 4 1.0 -1.0 -0.666667 1.0   // UNDER_RIGHT
mmix 5 1.0 1.0 -0.666667 1.0   // UNDER_LEFT
```

## Quad Y4

```
mmix custom
mmix reset
mmix 0 1.0 0.0 1.0 -1.0     // REAR_TOP CW
mmix 1 1.0 -1.0 -1.0 0.0    // FRONT_R CCW
mmix 2 1.0 0.0 1.0 1.0      // REAR_BOTTOM CCW
mmix 3 1.0 1.0 -1.0 0.0     // FRONT_L CW
```

## Hexa P6

```
mmix custom
mmix reset
mmix 0 1.0 -0.866025 0.5 1.0        // REAR_R
mmix 1 1.0 -0.866025 -0.5 -1.0      // FRONT_R
mmix 2 1.0 0.866025 0.5 1.0         // REAR_L
mmix 3 1.0 0.866025 -0.5 -1.0       // FRONT_L
mmix 4 1.0 0.0 -1.0 1.0             // FRONT
mmix 5 1.0 0.0 1.0 -1.0             // REAR
```

## Octa Flat P

```
mmix custom
mmix reset
mmix 0 1.0 0.707107 -0.707107 1.0       // FRONT_L
mmix 1 1.0 -0.707107 -0.707107 1.0      // FRONT_R
mmix 2 1.0 -0.707107 0.707107 1.0       // REAR_R
mmix 3 1.0 0.707107 0.707107 1.0        // REAR_L
mmix 4 1.0 0.0 -1.0 -1.0                // FRONT
mmix 5 1.0 -1.0 0.0 -1.0                // RIGHT
mmix 6 1.0 0.0 1.0 -1.0                 // REAR
mmix 7 1.0 1.0 0.0 -1.0                 // LEFT
```

## Octa Flat X

```
mmix custom
mmix reset
mmix 0 1.0 1.0 -0.414178 1.0        // MIDFRONT_L
mmix 1 1.0 -0.414178 -1.0 1.0       // FRONT_R
mmix 2 1.0 -1.0 0.414178 1.0        // MIDREAR_R
mmix 3 1.0 0.414178 1.0 1.0         // REAR_L
mmix 4 1.0 0.414178 -1.0 -1.0       // FRONT_L
mmix 5 1.0 -1.0 -0.414178 -1.0      // MIDFRONT_R
mmix 6 1.0 -0.414178 1.0 -1.0       // REAR_R
mmix 7 1.0 1.0 0.414178 -1.0        // MIDREAR_L
```

# Setups that are not available on F1 targets

Setups that uses both motors and servos can not be programmed using custom mixers yet. There is a plan to refactor custom motor and servo mixer. ATM following setups are not available on STM32F1 targets:

[mixer code is only informational, will not work yet]

## Bicopter

```
mmix custom
mmix reset
mmix 0 1.0 1.0 0.0 0.0 //left motor
mmix 1 1.0 -1.0 0.0 0.0 //right motor

smix reset
smix 0 4 2 100 0 0 100 0 //Servo 4 for left motor pitch change
smix 1 4 1 100 0 0 100 0 //Servo 4 for left motor pitch change
smix 2 5 2 100 0 0 100 0 //Servo 5 for right motor pitch change
smix 3 5 1 100 0 0 100 0 //Servo 5 for right motor pitch change
```

## Dualcopter

```
mmix custom
mmix reset
mmix 0 1.0 0.0 0.0 -1.0     // LEFT
mmix 1 1.0 0.0 0.0 1.0      // RIGHT

smix reset
smix 0 4 1 100 0 0 100 0
smix 1 5 0  100 0 0 100 0
```

## Singlecopter

***Warning*** this is highly experimental, not documented and I'm pretty sure there are not more than few in the whole world!

```
mmix custom
mmix reset

smix reset
smix 0 3 2 100 0 0 100 0
smix 1 3 1 100 0 0 100 0
smix 2 4 2 100 0 0 100 0
smix 3 4 1 100 0 0 100 0
smix 4 5 2 100 0 0 100 0
smix 5 5 0 100 0 0 100 0
smix 6 6 2 100 0 0 100 0
smix 7 6 0 100 0 0 100 0
```

## HELI 120 CCPM

Was never really implemented in CF and others. iNav makes this preset disabled.

## HELI 90 DEG

Was never really implemented in CF and others. iNav makes this preset disabled.
