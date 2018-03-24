# PID Controler Project

In this project a PID controller has been implemented, the PID controller gets feedback from the simulator and returns the steereing angle.

## Basic Build Instructions

1. Make a build directory: `mkdir build && cd build`
2. Compile: `cmake .. && make`
3. Run it: `./pid`. 



## Student describes the effect of the P, I, D component of the PID algorithm in their implementation. Is it what you expected?

Visual aids are encouraged, i.e. record of a small video of the car in the simulator and describe what each component is set to.


* The proportional gain of the controller moves the car to the center line, however if we only use this value then the controller has an overshoot, therefore, the car is oscillating around the center line.

* The diferentional gain is used to decrease the oscilation of the error, therefore the cars moves around the center line without the oscilation.

* The integral gain is used to eliminate a posible bias, in such case the controller never converge.

- The proportional portion of the controller tries to steer the car toward the center line (against the cross-track error). If used along, the car overshoots the central line very easily and go out of the road very quickly. An example video where this component is used along is [./videos/only-proportional.mov](./videos/only-proportional.mov).

- The integral portion tries to eliminate a possible bias on the controlled system that could prevent the error to be eliminated. If used along, it makes the car to go in circles. In the case of the simulator, no bias is present. An example video where this component is used along is [./videos/only-integral.mov](./videos/only-integral.mov).

- The differential portion helps to counteract the proportional trend to overshoot the center line by smoothing the approach to it. An example video where this component is used along is [./videos/only-differential.mov](./videos/only-differential.mov).

[P video ](./PID_videos/P.mov)



[Video with only P value](https://www.dropbox.com/s/14qbofaenn2sno2/P.mov?dl=0)



## Student discusses how they chose the final hyperparameters (P, I, D coefficients). This could be have been done through manual tuning, twiddle, SGD, or something else, or a combination!


The PID parameters were choosen manually by try and error. First, I choose a value for the Proportional gain of 0.5, the cars move to the center however it has a severe oscillation, therefore I reduce the value. 

To remove the oscilation I set the Differential gain, and the results were better since the cars goes to the center without the overshoot.

Finally I try the Integral gain, with this value the behaivor of the car was an oscillation, therefore I decide to set its value to zero.

The final parameters were P=0.15, I=0, D=3.0

