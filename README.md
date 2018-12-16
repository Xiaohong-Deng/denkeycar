[image1]: ./img/donkey.jpg "Donkey"
[image2]: ./img/hybridastar.png "RACECAR"

# Denkey Car

Denkey Car is a Self-Driving RC car project that potentially consists of multiple RC cars backed by different sets of software to mimic distinct real world scenarios like highway, parking lot and off-road driving.

### Current State

A standard Donkey build. Run the default inference model on the Pi. No extra juice added yet.

### How to build a car

No rules! But if you want to have something to hold on to, the following builds are good starting point. All have parts list.

* [Donkey][0], $200
* [Berkeley BARC][1], min. $1000
* [MIT RACECAR][2], $4500
* [HyphaRos RACECAR][3], $600, low cost version of MIT RACECAR
* [GT AutoRally][4], $30000

### What challenges I can program my car to accomplish

### Donkey

Donkey is a design built to run around tracks bounded by painted lane marks.

* Implement lane changing and obstacle avoiding behaviors. (**requires a dual-lane track that I have no access to**)
* Mount more sensors, hack the donkey framework to support custom sensors.
* Use those sensors to do visual SLAM (RPLidar doesn't work on painted lane)
* Implement RNN to mitigate driving signal latency. Don't feel the urge to implement it at the moment though.

#### Related Work

* [cycloid][5] is a platform that uses wheel encoders and IMU to do visual SLAM.
* [Ghost][6] is another project that employs the IMU + encoders combination to do SLAM.

### MIT / HyphaRos RACECAR

This is likely to be my second car to implement indoor navigation from point A to point B while avoiding 3D obstacles.

Because installing encoders to RC cars can be tricky. An open source ESC named VESC can provide odometry data out of box and make sensorless brushless motor responsive under low speed (good for training). This fact makes a second car inevitable. Besides, RPLidar and depth camera require more powerful SBCs than Raspberry Pi.

Another benefit of this car is it can be tested in small and unstructured apartment where Donkey requires a large enough track (**a luxury I don't have**) to test various behaviors.

* Use RPLidar or depth camera to build a map (SLAM)
* Use the map to navigate (Hybrid A* possibly)

#### Related Work

This is the final product I am intended to reproduce.

[![alt text][image2]][7]

![alt text][image1]

---
[0]: http://www.donkeycar.com/
[1]: http://www.barc-project.com/
[2]: https://mit-racecar.github.io/
[3]: https://github.com/Hypha-ROS/hypharos_racecar
[4]: https://autorally.github.io/
[5]: https://github.com/a1k0n/cycloid
[6]: https://www.stevendaniluk.com/ghost/
[7]: https://www.youtube.com/watch?v=h8Mnkqyv338
