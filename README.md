# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

## Effect of Kp, Ki, Kd
1) When I set all of the three(Kp, Ki, Kd) to zero, car drove on straight line as expected, because in this case error was zero and steering angle was also zero.
2) Then I added Kp to PID controller, with value 1.0. Car tried to come to center of the lane but was oscillating. Oscillation increased with time. When Kp value was reduced oscillations were less.
3) To remove oscillation caused by Kp, I add Kd and car was able to drive stably.
4) Since with Kp and Kd I was able to drive car, that means Ki is not required.
5) less value of Kp will give less oscillation but wont be able to drive the car in sharp turns.

## Choosing final parameters
1) I started with Kp = 1.0, Ki = 0.0 and Kd = 0.0. Observation => oscillation increasing with time.
2) reduced Kp to 0.1  (Kp = 0.1, Ki = 0.0 and Kd = 0.0). Observation => less oscillation but still increasing with time.
3) added Kd 1.0 (Kp = 0.1, Ki = 0.0 and Kd = 1.0). Observation => Oscillation were gone but on sharp turns car is out of the road.
4) increased Kp to 0.12 (Kp = 0.12, Ki = 0.0, kd = 1.0) Observation => Still sometimes car goes out of boarder of the road.
5) increased Kp to 0.15 (Kp = 0.12, Ki = 0.0, kd = 1.0) Observation => better then 4, Still sometimes car goes out of boarder of the road. and more oscillations.
6) increased Kp to 0.17 and Kd = 2.0 (Kp = 0.17, Ki = 0.0, kd = 2.0) Observation => better then 5, car is able to drive on the road successfully. but some oscillations.
7) increased Kd = 3.0 (Kp = 0.17, Ki = 0.0, kd = 3.0) Observation => car is able to drive on the road.


