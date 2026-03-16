---
layout: post
title:  "Rudy: Quadruped From Scratch"
date:   2026-03-10 09:00:00 +0300
video: Rudy_FinalVid6.mp4
tags:  CAD Dynamixel Embedded_Systems Microcontrollers ROS_2 Quadrupeds 3D_Printing
---

Meet Rudy! A quadruped which I have designed and built from scatch!

Rudy was designed to operate using **ROS 2**, running on an **Ubuntu Raspberry Pi** and powered by **Dynamixel XC430 motors**.

Currently, Rudy walks using a **phased trot gait**. The next phase will focus on implementing **kinematics** using a custom kinematics package I developed, along with integrating **more advanced gait algorithms** to improve locomotion and control.

**Github Link:** <a href="https://github.com/ncknight-un/Quadruped_Rudy" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/Quadruped_Rudy
</a>

---
### Gait Generation

- Implemented a **trot gait** using a single **ROS 2 node** that controls **Dynamixel motors** via the **Dynamixel SDK**, with a timer callback handling **joint state publication** and **waypoint actuation**.
- **Future Work:** Implement the **body kinematics package** for gait generation using **Bezier curve trajectories**.

<div class="project-gallery">

  <div class="gallery-item">
    <h4>Final Walking Demo - Joint Waypoints</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_BestWalk.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Walking Demo - Outdoors</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_Outside.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Initial Trot Testing - Joint Waypoints</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_Trot1.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Initial Qausti-Static Gait Testing</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_QSgait1.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

</div>
<br>

--- 

### Static Poses - ROS 2 Service Calls

- I thought it would be fun to give Rudy more life by adding in static whole-body joint poses via ROS 2 service calls. 
  - Below you can find his implementation of the following poses:
    - Lie Down
    - Sit Down
    - Stand Up 
    - Kneel 
    - Shake Paw

<div class="project-gallery">
  <div class="gallery-item">
    <h4>Complete ROS Service Static Poses</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_Poses2.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>ROS Service Static Poses Test</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_StaticPoses.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
</div>
<br>

---

### CAD Design & Modeling

- Iteratively designed the robot using Fusion 360 to achieve the intended **degrees of freedom**:
- Identified and removed all joint impingement points in Range-of-Motion Testing as of January 18th, 2026.
- **Total Robot Weight:** 4.8 lb (2.18kg) - excludes battery
  - **(Final Model assembled using PLA-CF for the body and TPU for the Feet)**

<div class="project-gallery">
  <div class="gallery-item">
    <h4>Final Assembled Model - Used in Sim</h4>
    <img src="/images/Rudy_FinalModel3.jpeg" alt="Modeling Current">
  </div>

  <div class="gallery-item">
    <h4>First Assembled Model</h4>
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

---

### Range of Motion Design

- Two degrees of freedom at each hip:
  - Abduction/adduction **(15-deg Abd / 65-deg add)**
    - Hip Abad was included to support center-of-mass shifting and balance for future advanced gait control methods.
  - Flexion/extension   **(90-deg Flex/Ext)**
- One degree of freedom at each knee:
  - Flexion/extension **(112-deg Flex/Ext)**

  <div class="gallery-item">
    <h4>Range of Motion Studies</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_MotionStudy2.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

---

### Electronics Setup

- See the **Electronics Layout** below for the digital electronics and power distribution.
- Each motor is daisy-chained to the **U2D2 Power Hub Board**, which distributes power and communication to all servos.
- The U2D2 also provides the interface between the motors and the control computer.

  <div class="gallery-item">
    <h4>Electronics Layout</h4>
    <img src="/images/Rudy_Elec_Layout.jpeg" alt="Circuit Diagram">
  </div>

--- 

### Software Design

- The robot runs **Ubuntu 24.04 LTS** with **ROS 2 Kilted** on a **Raspberry Pi 4-B+**.
- Control logic is implemented using a **ROS 2 node** that generates joint trajectories and gait timing.
- The current controller implements a **trot gait** using joint waypoint trajectories for a trot gait style.
- Future work includes **kinematics** and **Bezier trajectory-based gait generation**.

  <div class="gallery-item">
    <h4>Software/System Architecture</h4>
    <img src="/images/Rudy_Arc.jpg" alt="System Arch">
  </div>

--- 

### Additional Media

<div class="project-gallery">

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

</div>
<br>

---

## Next Steps

**Continue developing gait generation and validating kinematics**

- Use **RViz** to assist with kinematic validation and continue gait prototyping.
- Implement an **open-loop gait controller** using **rosjoy** for joystick-based control.
- Implement distance awareness using Ultrasonic Sensor.

---

## Skills Improved

- Mechanical design iteration and validation for legged robots  
- CAD modeling with an emphasis on joint kinematics and range-of-motion analysis  
- Electronics integration, power distribution planning, and wiring practices
- Actuator bring-up, motor ID management, and torque-aware system design  
- Embedded systems planning using Raspberry Pi and Dynamixel motors  
- ROS ecosystem, including URDF modeling and RViz visualization from a bottom-up project


---

## Key Takeaway

This project has quickly deepened my understanding of how mechanical design, electronics, and software must be developed together when building a robotic system from scratch. Bringing up the electronics and validating motor operation reinforced the value of careful system architecture and documentation, particularly when planning for future ROS integration. Designing the robot with simulation and software control in mind from the beginning has helped shape a more scalable and extensible platform for gait development in the future beyond the initial phase shift waypoint trot gait that I currently have implemented on the robot!

Overall, this project has strengthened my confidence in tackling open-ended robotics problems that span CAD, hardware integration, and software planning. It has also sparked my interest in legged locomotion, robotic simulation, and building platforms that transition seamlessly from hardware prototypes to software-driven experimentation. I hope to continue advancing the software and gait trajectories of Rudy in the Future!