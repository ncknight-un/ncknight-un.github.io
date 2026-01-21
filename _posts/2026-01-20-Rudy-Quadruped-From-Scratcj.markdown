---
layout: post
title:  "Rudy: Quadruped From Scratch"
date:   2026-01-12 09:00:00 +0300
video: Rudy_Motor_Test.mp4
tags:  CAD Dynamixel Embedded_Systems Microcontrollers ROS_2 Quadrupeds 3D_Printing
---

Meet Rudy! An in-progress quadruped which I have designed and have begun building from scatch! 

Over the last few weeks I have designed, fabricated, and wired a prototype for a small quadruped controlled using Dynamixel actuators, a Robotis U2D2 paired with a Power Hub Controller, and a Raspberry Pi. My future goals for this project are to implement ROS for future gait planning and simulation on the Raspberry Pi.

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
- **Estimated Weight:** ~5 lb once bearings are installed  

<!-- This is approximately 0.5-1 lb over initial estimates, so joint force limits will be re-evaluated to ensure safe operation.
I will also work on reducing mass through various weight reduction means over the coming weeks. New model iterations have begun 
compacting the structure more.

The added weight is primarily due to:
- Electrical components not included in early estimates
- Reinforced leg geometry and housing revisions -->

---

### Electronics & Motor Bring-Up

- Planned a **digital electronics and power distribution layout** incorporating the Raspberry Pi, U2D2 power hub, and battery connections to streamline integration and reduce wiring complexity.
- Fully wired all Dynamixel motors on the robot.
- Verified motor actuation using the Dynamixel computer GUI:
  - Confirmed correct joint response for every motor
  - Documented motor IDs for future ROS integration
- Currently waiting on bearings to assemble the final two legs.


## Project Gallery

<div class="project-gallery">
  <div class="gallery-item">
    <h4>Initial Motor Testing</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_Motor_Test.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Current Iteration Model</h4>
    <img src="/images/Rudy_Iteration_Current.JPG" alt="Modeling Current">
  </div>

  <!-- <div class="gallery-item">
    <h4>Rudy - Printed Model</h4>
    <img src="/images/Rudy_Cute.png" alt="Rudy!">
  </div>

  <div class="gallery-item">
    <h4>Electronics Layout - CAD</h4>
    <img src="/images/Rudy_CAD_Wiring.png" alt="Wiring CAD">
  </div> -->

  <div class="gallery-item">
    <h4>Electronics - Implemented</h4>
    <img src="/images/Rudy_Wiring.png" alt="Wiring">
  </div>


  <div class="gallery-item">
    <h4>Testing Stand</h4>
    <img src="/images/Rudy_Stand.png" alt="Stand">
  </div>

  <div class="gallery-item">
    <h4>Original Ideation Model</h4>
    <img src="/images/Rudy_It1.JPG" alt="Iteration 1">
  </div>

  <div class="gallery-item">
    <h4>Secondary Ideation Model</h4>
    <img src="/images/Rudy_It2.JPG" alt="Iteration 2">
  </div>

</div>
<br>

---
## Next Steps

**Next steps shift toward building the software stack**

- Install Ubuntu and ROS on the Raspberry Pi controller
- Research quadruped-focused ROS packages
- Develop a URDF model for visualization and simulation
- Use RViz to validate kinematics and begin gait prototyping
- Integrate motor control commands via ROS
- Finalize electronics layout to match the ROS architecture

**Next motor-related steps**
- Determine safe torque limits  
- Confirm joint orientation conventions for software integration  
- Finalize a detailed digital electronics layout  

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
<!-- - Embedded systems planning using Raspberry Pi and Dynamixel motors  
- ROS ecosystem familiarity, including URDF modeling and RViz visualization   -->
- Engineering documentation and project planning for multi-disciplinary systems  

---

## Key Takeaway

This project has quickly deepened my understanding of how mechanical design, electronics, and software must be developed together when building a robotic system from scratch. Bringing up the electronics and validating motor operation reinforced the value of careful system architecture and documentation, particularly when planning for future ROS integration. Designing the robot with simulation and software control in mind from the beginning has helped shape a more scalable and extensible platform for gait development.

Overall, this project has strengthened my confidence in tackling open-ended robotics problems that span CAD, hardware integration, and software planning. It has also clarified my interest in legged locomotion, robot simulation, and developing robust robotic platforms that can transition cleanly from prototype to software-driven experimentation.
