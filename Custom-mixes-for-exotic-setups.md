iNav removed native support for various exotic and not often used frames. They can not be preselected in Configurator, but their functionality can be implemented using custom mixes.

## Bicopter

Not yet ready for custom mixers, use predefined

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
mmix 1 1.0 -1.0 -1.0 0.0          // FRONT_R
mmix 2 1.0 0.0 1.0 -1.0          // REAR_L
mmix 3 1.0 1.0 -1.0 -0.0          // FRONT_L
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
mmix 0 1.0 0.0 1.0 -1.0         // REAR_TOP CW
mmix 1 1.0 -1.0 -1.0 0.0        // FRONT_R CCW
mmix 2 1.0 0.0 1.0 1.0          // REAR_BOTTOM CCW
mmix 3 1.0 1.0 -1.0 0.0         // FRONT_L CW
```

## HELI 120 CCPM

Was never really implemented in CF and others

## HELI 90 DEG

Was never really implemented in CF and others

