# feedback-and-locking
Feedback controllers, PID loops, analog and digital varieties, locking to a reference

This is a mini-course for experimental physicists, prepared by Sam Hile, in the context of the IQT research group at Sussex.

## Contents
1.	Generic process control theory
2.	Human intuition (timescale)
3.	P, I, and D equations
4.	Tuning procedures
5.	Testing/verifying parameter stability and impulse response
6.	Example 1: a course laser wavelength lock
7.	Lock-in detection
8.	PDH error signals
9.	Analog circuitry for near-instant response
10.	Example 2: Toptica FALC
11.	Digital processing and FPGA control
12.	Example 3: Sinara Suservo

## Generic process control theory
[Wiki page for PID](https://en.wikipedia.org/wiki/PID_controller) is a nice place to start. (Just read the *Fundamental operation* section fr now, and skim the rest of the page)

Once you've read a bit about the concept, dive in and [play with a simulator](http://grauonline.de/alexwww/ardumower/pid/pid.html). Here the blue line represents the setpoint (target value); red "control input" line represents a measurement of the process value; and the green "control output" line shows the actively controlled signal sent out by the controller to try to minimise the error (i.e. overlap red onto blue). The The default configuration in the simulator is slightly confusing, so I reccommend pasting in this custom model and going through the following steps initially
```
if (typeof user.h === 'undefined'){ user.h = [10,10,10,10,10,10,10,10]; };
for(var i=0;i<7;i++){ user.h[i] = user.h[i+1]; };
user.h[7] = output;
return (8*user.h[0]+6*user.h[1]+4*user.h[2]+3*user.h[3]+2*user.h[5]+30*noise)/30;
```

 * `Apply` the model code
 * set Ki to zero
 * set Kd to zero
 * set Kp to ~0.5, and wait for things to settle
 * suddenly move the setpoint from positive to negative and back again to observe how fast the system takes to react to an impulse
 * now make small changes to the gains (K values) and repeat the impluse in order to explore...

## Human intuition (timescale)
Humans are naturally pretty good PID controllers, often without realising it. If you have 3 people and a table/desk, its possible to play a game:

:blue_square: Blue player (setpoint) :blue_square: Stand behind the desk, place a blue marker/pen on the desk. Occasionally slide it to the left or to the right to change the setpoint.

:red_square: Red player (process) :red_square: Sit in front of the desk, hold a red marker/pen in front of you on the desk surface. With your other hand, hold a green marker/pen directly above your head. As the green marker (and your arm) is tilted, slide the red marker left/right in response. Try to be consistent, and **do it all with your eyes closed**.

:green_square: Blue player (setpoint) :green_square: Stand behind the red player, look at the relative error in the position of their red marker/pen and TILT the green marker/pen to suggest how they should correct for the error. Be genlte and don't break anybody's arm.



## P, I, and D equations
The standard form of the mathematical expressions is something like:
![image](https://github.com/user-attachments/assets/5420f763-cbc4-4e0a-a457-977edeae96f0)

You will also encounter this alternate form at some point in your life:
![image](https://github.com/user-attachments/assets/44c7d0ad-02e8-4db6-8831-f08d081fda69)
here the I and D terms are encoded in a way that should hint at the timescales of derivative and integral action. 

## Tuning procedures

## Testing/verifying parameter stability and impulse response

### Example 1: a course laser wavelength lock

## Lock-in detection

## PDH error signals

## Analog circuitry for near-instant response

### Example 2: Toptica FALC

## Digital processing and FPGA control
    
### Example 3: Sinara Suservo
