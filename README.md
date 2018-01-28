# **PID Control**

![simulator screen capture](./images/sim_capture.png)

## Goals
* Keep the center of the road with PID control

## Files
* README.md: this file
* CMakeLists.txt: cmake list file
* cmakepatch.txt: cmake patch file
* install-*.sh: scripts for installing uWebSockets
* images/*: captured image file(s) for this markdown file
* src/*: source code to calculate steer_value with PID control


## Prerequisites
* cmake &ge; 3.5
* make &ge; 4.1 (Linux, Mac), 3.8 (Windows)
* gcc/g++ &ge; 5.4
* uWebSocketIO from [here](https://github.com/uNetworking/uWebSockets)
* *simulator* from [here](https://github.com/udacity/self-driving-car-sim/releases/)

## Test Method
0. run install-*.sh for installing uWebSockets library
1. In the shell prompt, type **cmake**
2. Then type **make**
3. Run **./pid**
4. Run simulator from another shell or file explorer!!
5. Select project 4

## Reflection and Result

#### 1. Tuning PID Gain
###### Kp : proportional gain
###### Ki : integration gain
###### Kd : derivertive gain

(1) Kp=-0.5 Ki=0 Kd=0
  - Car tries to track the center but off the track after the first corner with oscillation increasing
  
(2) Kp=-0.5 Ki=0 Kd=-5
  - Add Kd for reducing oscillation
  - Too many oscillation during and after left corners and some offset from the center after oscillation

(3) Kp=-0.5 Ki=-0.001 Kd=-5
  - Add Ki for improving offset from the center
  - Improved offset from center but still too many oscillation during and after corners
  
(4) Kp=-0.5 Ki=-0.005 Kd=-15
  - Increase Ki and Kd to improve offset and reduce oscillation
  - Good tracking with reduced oscillation. This shows good result. (Final values)

#### 2. Improvements
- May need to control `throttle` to achieve more stability in the curve. But to do this, I need data for predicted path from the simulator.

#### 3. Tuned values
  - Kp = -0.5
  - Ki = -0.005
  - Kd = -15
