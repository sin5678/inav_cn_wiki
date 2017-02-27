# Method 1.

Tune for maximum performance.  
Have the FF-gain do most of the work steering the airplane, leaving only P and I controller to fight turbulence and drift.  

1. Figure out the maximum rates your airplane can do, both for rolling, loops and yaw turn

Fly in passthrough mode, have some way of recording the flight, blackbox, video camera or both. Do hard roll, hard loops and one 360deg yaw turn. ( Use full stick on all )

Note down the maximum rates, typical 360deg/s on roll, 100deg/s on pitch and 60deg/s yaw.  
Enter these values as your rates in configurator.  

2. Zero out P and I gain on Roll, Pitch and YAW controller. Increase FF-gain(D-gain) untill you get 90% of full servo throw when having sticks at full throw.

This is so the FF-gain does most of the work turning the airplane, but leaving some for the P and I gain to work with.  
Now add example 10 P-gain and 15 I-gain to Roll, Pitch and Yaw axis.

3. Go out and fly in acro mode. If airplane drifts to one side or up and down add I-gain to the axis it drifts in. If you want more stabiliation against wind try and add more P-gain.

4. Want to calm your airplane down? Now is the time to reduce rates to fit your needs.

Note: Yes it`s normal to get reduced servo throw when reducing rates at this point, if you got full servo throw at this stages you would overshoot the target deg/s you wanted.
