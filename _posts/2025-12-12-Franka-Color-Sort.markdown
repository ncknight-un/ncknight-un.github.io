---
layout: post
title:  "Vision-Based Sorting with the FER Panda Robot"
date:   2025-12-12 09:00:00 +0300
video: Final_Video_Robot.mp4
tags:  CAD Franka Git Path_Planning Python ROS_2 Rviz Vision Simulation 3D_Printing
---

As part of a team, I developed a modular motion planning and manipulation system for the FER Panda robotic arm to autonomously pick up and sort colored objects (“Turtles”) in both simulated and real laboratory environments. The system leverages ROS 2 and MoveIt for collision-aware motion planning, task execution, and real-time visualization.

**Github Link:** <a href="https://github.com/ncknight-un/Franka_Color_Sorting_MSR2025" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/Franka_Color_Sorting_MSR2025
</a>

--- 

**School:** Northwestern University  
**Location:** - Evanston, IL  
**Duration:** November 2025 - December 2025  
 
---

### Team Members:
**Miguel Pigues**: <a href="https://tmpegues.github.io/" target="_blank" rel="noopener noreferrer">
https://tmpegues.github.io 

**Halley Zhong**:  <a href="https://halleyscomet-99.github.io/" target="_blank" rel="noopener noreferrer">
https://halleyscomet-99.github.io

**Rishika Bera**:  <a href="https://rishika2024.github.io/" target="_blank" rel="noopener noreferrer">
https://rishika2024.github.io

---

### Project Demo Vidoes: 
<div class="project-gallery">

  <div class="gallery-item">
    <h4>Still Sorting Video Demo</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/Final_Video_Robot.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Future Task Demo (Moving Sort)</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/one_still.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Rviz Visualization</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/Rviz_clip.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Color Vision</h4>
    <img src="/images/vision.jpeg" alt="Color Vision">
  </div>
</div>

<br>

---

### System Architecture

The system is built around a custom **MotionPlanningInterface**, composed of three core subsystems:

- **RobotState** – Maintains the robot’s current state  
- **MotionPlanner** – Generates collision-free trajectories  
- **PlanningScene** – Represents the environment and obstacles  

These components integrate through MoveIt to produce safe and efficient motion plans while accounting for static obstacles.

---

### Perception & Visualization

- Object detection is integrated into the pipeline using vision-based inputs  
- Detected colored objects are visualized in RViz in real time  
- The active target is highlighted for clarity during execution  

---

### Task Planning & Execution

The system includes higher-level coordination through:

- **TargetDecision Node** – Identifies and selects objects to retrieve  
- **Sort Node** – Assigns placement locations and executes sorting logic  

This structure enables:
- Clear separation between perception, planning, and execution  
- Flexible and modular task sequencing  

---

### Dynamic Object Tracking (Extension Work)

An extended feature explores real-time sorting of moving objects using Hexbug-powered turtles.

- Implemented a low-latency control pathway via `fer_arm_controller`  
- Bypasses MoveIt to directly command joint trajectories  
- Enables continuous tracking of dynamic targets  

This significantly increases system complexity, as the non-linear motion of the turtles introduces challenges in prediction and control. This area remains under active development.

---

### Enclosure & CAD Designs:

- Designed the enclosure in Fusion360 to plan layout prior to construction, ensuring alignment with the robot workspace  
- **Migeul Pegues** Created a custom insert to ensure repeatable placement of the fixture between the robot base and frame  
- Designed a custom gripper to securely grasp round shells while avoiding collisions with the ground frame  
- Added rounded corners to improve safety and prevent corner trappong during operation  
- Integrated mounted AprilTag holders to ensure consistent perception and repeatable testing conditions  

**Note: I have shared all CAD files to this public repository! Feel free to build off of them!**

<div class="project-gallery">
  <div class="gallery-item">
    <h4>World Model (PreBuild)</h4>
    <img src="/images/world_model.jpeg" alt="World">
  </div>

  <div class="gallery-item">
    <h4>Hexbug Turtle Shell</h4>
    <img src="/images/shell.jpeg" alt="Shell">
  </div>

  <div class="gallery-item">
    <h4>Hexbug Positive</h4>
    <img src="/images/Hex_pos.jpeg" alt="Hex Positive">
  </div>

  <div class="gallery-item">
    <h4>Custom Grippers for FER</h4>
    <img src="/images/claw.jpeg" alt="Grippers">
  </div>
  
  <div class="gallery-item">
    <h4>World Corners</h4>
    <img src="/images/corners.jpeg" alt="Corners">
  </div>
  
  <div class="gallery-item">
    <h4>April Tag Base</h4>
    <img src="/images/tag_base.jpeg" alt="Tag Base">
  </div>

</div>

---

## Skills Improved:

- ROS 2 (nodes, topics/services, launch files)  
- MoveIt (motion planning and collision avoidance)  
- Robotic manipulation (Franka Emika Panda)  
- Motion planning and environment modeling  
- Vision-based object detection and task execution  
- Real-time visualization (RViz)  
- Modular robotics system design  
- Joint trajectory control for dynamic tracking  
- Integrated perception, planning, and control

---

## Key Takeaway:

This experience allowed me to develop a complete, end-to-end robotic manipulation system that integrates perception, motion planning, and control. I gained practical experience designing modular ROS 2 architectures, working with both collision-aware planning and real-time control for dynamic targets, and debugging complex robotic behaviors in simulation and on physical hardware. Most importantly, the project strengthened my ability to translate high-level task goals into reliable, autonomous robotic actions in real-world environments.