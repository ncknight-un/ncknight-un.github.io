---
layout: post
title:  "SLAM: Navigation Stack From Scratch"
date:   2026-03-18 09:00:00 +0300
video: SLAM_Unknown_Data_Assoc_Final.mp4
tags:  C++ EKF Embedded_Systems GIT LiDAR Mapping Path_Planning ROS_2 SLAM
---

Designed for the Turtlebot3, this project implements a full-stack SLAM architecture using an Extended Kalman Filter (EKF). The system integrates sensing, state estimation, and mapping to enable real-time localization in an unknown environment. The focus of this project was to develop a deeper understanding of robotics perception and navigation at the system control level.

**Github Link:** <a href="https://github.com/ncknight-un/SLAM_EKF_SCRATCH_TURTLEBOT3" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/SLAM_EKF_SCRATCH_TURTLEBOT3
</a>

---
### SLAM-EKF in Simulation

- **Comparison Setup:** SLAM-EKF and odometry are simulated concurrently to highlight error accumulation in state estimation.
  - **Scenarios:** Teleoperation and circular trajectory tests  
  - **Method:** SLAM-EKF vs. odometry  
  - **Result:** EKF-based SLAM significantly reduces drift compared to odometry alone  
  - **Takeaway:** Sensor fusion improves localization accuracy and robustness over time  

<div class="project-gallery">

  <div class="gallery-item">
    <h4>Teleop Drive - SLAM EKF</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/SLAM_Unknown_Data_Assoc_Final.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Circle Drive - SLAM EKF</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/SLAM_Unknown_Data_Assoc_Circle4.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Teleop Drive - Obstacle Collision/Odom Divergence</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/SLAM_Unknown_Data_Assoc_edit.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

</div>

--- 

### Physical Testing on Turtlebot3

- When evaluated on a simple circular trajectory, the localization error was approximately **0.25 m** in both the x and y directions.  
  - This suggests that real-world performance is expected to exhibit greater error accumulation due to factors such as wheel slip, friction, and unmodeled dynamics.  
- **Ongoing work focuses on addressing the simulation-to-real gap for SLAM-EKF deployment on the physical robot.**
  - Currently adjusting parameters for algorithms to better match noise consistancy with existing LiDAR senser and control nodes.

<div class="project-gallery">

  <div class="gallery-item">
    <h4>Odometry on Turtlebot3</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/SLAM_ODOM_PT2.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

</div>

---


### Sensing & Perception

The simulation in this project compares two state estimation approaches—raw odometry and SLAM with an Extended Kalman Filter (EKF)—to demonstrate the improvements in localization accuracy achieved through sensor fusion.

- LiDAR: Provides distance measurements and enables environmental perception for SLAM-based state estimation
- Odometry: Tracks wheel-based motion estimates, serving as a baseline for comparison

Sensor data is inherently noisy and uncertain, making filtering and probabilistic inference essential for reliable state estimation.

--- 


### State Estimation (EKF)
For the SLAM state estimation, the Extended Kalman Filter is used to estimate the robot’s state, including position and orientation.

Key Steps:

- Prediction: Uses motion model to estimate next state
- Update: Corrects estimate using sensor measurements

The EKF enables robust localization by combining noisy sensor inputs into a consistent state estimate.

---

### Acknowledgements

Thank you to Dr. Matthew Elwin, director of MSR at Northwestern, who teaches this project course (ME495: Sensing, Navigation, and Machine Learning).

---

###  Skills Improved

- ROS 2 development in C++  
- CMake-based project architecture  
- Full-stack robotics system design  
- Robot navigation principles  
- Sensor integration and control algorithms  

---

### Key Takeaway

This project demonstrates the importance of sensor fusion in achieving accurate and reliable localization, highlighting how SLAM-EKF significantly reduces drift compared to raw odometry in robotic systems.