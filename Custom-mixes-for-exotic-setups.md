iNav removed native support for various exotic and not often used frames. They can not be preselected in Configurator, but their functionality can be implemented using custom mixes.

## Bicopter

Not yet ready for custom mixers, use predefined

```
mmix reset
mmix 0 1.0 1.0 0.0 0.0 //left motor
mmix 1 1.0 -1.0 0.0 0.0 //right motor

smix reset
smix 0 4 2 100 0 0 100 0 //Servo 4 for left motor pitch change
smix 1 4 1 100 0 0 100 0 //Servo 4 for left motor pitch change
smix 2 5 2 100 0 0 100 0 //Servo 5 for right motor pitch change
smix 3 5 1 100 0 0 100 0 //Servo 5 for right motor pitch change
```

## HELI 120 CCPM

Was never really implemented in CF and others

## HELI 90 DEG

Was never really implemented in CF and others

