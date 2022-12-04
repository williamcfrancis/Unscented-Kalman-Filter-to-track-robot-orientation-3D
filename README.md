## Unscented Kalman Filter to track robot orientation in 3D
Kalman filtering, also known as linear quadratic estimation (LQE), is an algorithm that uses a series of measurements observed over time, including statistical noise and other inaccuracies, and produces estimates of unknown variables that tend to be more accurate than those based on a single measurement alone, by estimating a joint probability distribution over the variables for each timeframe. It works good, but the downside of using Kalman Filter is that it only works for linear systems.

The next generation of KF was the Extended Kalman Filter (EKF) and it was a successful filter because it takes account to non-linearity. The only drawback with EKF is that it’s too difficult to do in real time practice at a microcontroller. Note that EKF is just a linearized KF by using jacobians, which is not very easy to use in practice. Therefore, another filter was created to replace EKF, it was Unscented Kalman Filter (UKF) and it was the most successful kalman filter ever made. 

Here I developed the UKF for the IMU data and the vicon data for calibration and tuning of the filter, this is typical of real applications where the robot uses an IMU but the filter running on the robot will be calibrating before test-time in the lab using an expensive and accurate sensor like a Vicon.

I have referred to the paper 

### Data
The data consist of observations from an inertial measurement unit (IMU) that consists of gyroscopes and accelerometers and corresponding data from a motion-capture system called Vicon. See [this video](https://www.youtube.com/watch?v=qgS1pwsHQIA&ab_channel=TravisErickson) to get a better understand of the Vicon system.

The data is given as .mat files in /imu and /vicon folders.

