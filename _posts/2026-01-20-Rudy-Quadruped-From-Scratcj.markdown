---
layout: post
title:  "Rudy: Quadruped From Scratch (In-Progress)"
date:   2026-03-03 09:00:00 +0300
video: Rudy_Rviz_URDF.mp4
tags:  CAD Dynamixel Embedded_Systems Microcontrollers ROS_2 Quadrupeds 3D_Printing
---

Meet Rudy! An **in-progress** quadruped which I have designed and have begun building from scatch! 

Over the last few weeks I have designed, fabricated, and wired a prototype for a small quadruped controlled using Dynamixel actuators, a Robotis U2D2 paired with a Power Hub Controller, and an Ubuntu OS Raspberry Pi operating with ROS. My future goals for this project are to implement an existing bezier curve model on my kinematic model to get advanced gait control and body orientation. Currently, Rudy is getting close to walking with a Quasi-static gait using joint waypoints for each foot. You can check out my progress below and on my github!

---
## Current Progress: 
### Initial ROM Design Goals

- Two degrees of freedom at each hip:
  - Abduction/adduction
  - Flexion/extension
- One degree of freedom at each knee:
  - Flexion/extension
- Hip abduction was intentionally included to support center-of-mass shifting and balance during locomotion.

---

<!-- ### CAD Weight Breakdown
- Body: 225 g  
- Legs: 50 g each (200 g total)  
- Head: 65 g  
- Hip covers: 20 g each (80 g total)  

**Total printed plastic weight:** ~570 g (1.25 lb) -->

### Current CAD Design Validation

- Iterated on leg and joint geometry to achieve the intended **degrees of freedom**:
- Identified and removed all hip impingement points in ROM Testing.
- Achieved full intended range of motion across all joints as of January 18th, 2026.
- **Estimated Weight:** ~5 lb (Final Model now assembled!)

---

### Electronics & Motor Bring-Up

- Planned a **digital electronics and power distribution layout** incorporating the Raspberry Pi, U2D2 power hub, and battery connections to streamline integration and reduce wiring complexity.
- Fully wired all Dynamixel motors on the robot.
- Verified motor actuation using the Dynamixel computer GUI:
  - Confirmed correct joint response for every motor
  - Documented motor IDs for future ROS integration

--- 

### Software Design

- Current set-up consists of Ubuntu 24.04 LTS Desktop, ROS 2 Kilted, and Dynamixel SDK Package. 
- Initial tests have taken place to move all motors on the Quadruped using ROS 2 position publications in terminal. 
- Current Task: Design an IK package for gait approximation and control using ROS 2 written in C++ for embedded control.

---

## Project Gallery

**Github Link:** <a href="https://github.com/ncknight-un/Quadruped_Rudy" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/Quadruped_Rudy
</a>

**Throughout this project, I’ve documented my progress step by step — explore how Rudy has evolved over the past 10 weeks!**

<div class="project-gallery">

  <div class="gallery-item">
    <h4>Initial Qausti-Static Gait Testing</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_QSgait1.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>ROS Service Static Poses</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_StaticPoses.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Initial ROS 2 Testing</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_Test4.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Initial RViz Modeling</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_Rviz_URDF.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Initial Motor Testing</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_Motor_Test.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Static Weight Bearing Test</h4>
    <img src="/images/Rudy_Standing_Test.jpg" alt="Rudy Stands">
  </div>

  <div class="gallery-item">
    <h4>Testing Stand</h4>
    <img src="/images/Rudy_Stand.png" alt="Stand">
  </div>

  <div class="gallery-item">
    <h4>Circuit Diagram</h4>
    <img src="/images/Rudy_Circuit.png" alt="Circuit Diagram">
  </div>

  <div class="gallery-item">
    <h4>Final Iteration Model - Used in Sim</h4>
    <img src="/images/Rudy_FinalModel.jpeg" alt="Modeling Current">
  </div>

  <div class="gallery-item">
    <h4>Primary Iteration Model</h4>
    <img src="/images/Rudy_Iteration_Current.JPG" alt="Modeling Current">
  </div>

  <div class="gallery-item">
    <h4>Secondary Ideation Model</h4>
    <img src="/images/Rudy_It2.JPG" alt="Iteration 2">
  </div>

  <div class="gallery-item">
    <h4>Original Ideation Model</h4>
    <img src="/images/Rudy_It1.JPG" alt="Iteration 1">
  </div>

</div>
<br>

---
## Next Steps

**Continue Developing Gait Generation and Validating Kinematics**

- Use RViz to assist in validation of kinematics and continue gait prototyping
- Implement Open Loop Control Gait using RosJoy.


---

## System Architecture & Components

Key components include:

- Dynamixel XL430 and 2XL430 motors
- Raspberry Pi 4 as the main ROS controller
- U2D2 TTL adapter for Dynamixel bus communication
- 3S 5000 mAh LiPo battery
- IMU for orientation feedback
- Ultrasonic sensor + LED for basic obstacle detection

---

## Skills Gained

- Mechanical design iteration and validation for legged robots  
- CAD modeling with an emphasis on joint kinematics and range-of-motion analysis  
- Electronics integration, power distribution planning, and wiring practices
- Actuator bring-up, motor ID management, and torque-aware system design  
- Engineering documentation and project planning for multi-disciplinary systems  
- Embedded systems planning using Raspberry Pi and Dynamixel motors  
- ROS ecosystem familiarity, including URDF modeling and RViz visualization


---

## Key Takeaway

This project has quickly deepened my understanding of how mechanical design, electronics, and software must be developed together when building a robotic system from scratch. Bringing up the electronics and validating motor operation reinforced the value of careful system architecture and documentation, particularly when planning for future ROS integration. Designing the robot with simulation and software control in mind from the beginning has helped shape a more scalable and extensible platform for gait development.

Overall, this project has strengthened my confidence in tackling open-ended robotics problems that span CAD, hardware integration, and software planning. It has also sparked my interest in legged locomotion, robotic simulation, and building platforms that transition seamlessly from hardware prototypes to software-driven experimentation.
