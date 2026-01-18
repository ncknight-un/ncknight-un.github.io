---
layout: post
title:  "Vision-Based Sorting with the FER Panda Robot"
date:   2025-12-12 09:00:00 +0300
video: Final_Video_Robot.mp4
tags:   Ros_2 Git Python Franka 3D_Printing Path_Planning Rviz MoveIt Vision
---


As a team, I helped develop a modular motion planning and manipulation system for the FER Panda robotic arm to autonomously pick up and sort colored objects (“Turtles”) in both simulated and real laboratory environments. The system leverages ROS 2 and MoveIt to perform collision-aware motion planning, task execution, and real-time visualization.

The project introduces a custom MotionPlanningInterface composed of three tightly integrated subsystems—RobotState, MotionPlanner, and PlanningScene—which coordinate through MoveIt to generate safe, efficient trajectories while accounting for static environmental obstacles. Object detection and state feedback are visualized in RViz, where detected colored objects are displayed in real time and the current target is highlighted with a larger black cube.

Beyond motion planning, the system incorporates a TargetDecision node and a Sort node that use vision-based inputs to identify object locations, assign retrieval tasks, and place each object into a predefined home base position. This architecture enables flexible task sequencing and clear separation between perception, planning, and execution.

As an extension, the project explores real-time sorting of moving objects using Hex-Bug–powered turtles. To handle dynamic targets, a low-latency control pathway was implemented via the fer_arm_controller, bypassing MoveIt and directly commanding joint trajectories. This enables continuous target tracking and responsive manipulation, significantly increasing task complexity and realism. This task is still being explored as the highly non-linear paths of the turtles create complexity to the system.

This project demonstrates end-to-end robotic manipulation, combining perception, planning, control, and real-time visualization, and serves as a strong foundation for further research into dynamic motion planning and autonomous sorting systems!

--- 

**School:** Northwestern University  
**Location:** - Evanston, IL  
**Duration:** November 2025 - December 2025  
 
---

## Project Gallery

**Github Link:** <a href="https://github.com/ncknight-un/Franka_Color_Sorting_MSR2025" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/Franka_Color_Sorting_MSR2025
</a>

**Note: I have shared all CAD files to this public repository! Feel free to build off of them!**

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

### Enclosure & CAD Designs:
<p>
I designed the Bug World in Fusion 360 to plan the sizing and shape before building it in wood, ensuring the environment was centered around the robot. I created an insert for consistent placement of a fixture between the robot base and wooden frame. Additionally, I designed a custom gripper to safely encapsulate round shells without hitting the ground frame, and added rounded corners and mounted AprilTag holders to maintain consistency in testing.
</p>
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
    <img src="/images/grippers.jpeg" alt="Grippers">
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

## Skills Gained:

- ROS 2 (node design, topic/service communication, launch files)
- MoveIt motion planning and collision detection
- Robotic manipulation with the Franka Emika Panda (FER Panda)
- Motion planning scene design and obstacle modeling
- Vision-based object detection and task assignment
- Real-time visualization and debugging with RViz
- Modular robotics software architecture
- Joint trajectory control for real-time target tracking
- Integration of perception, planning, and control pipelines

---

## Key Takeaway:

This experience allowed me to develop a complete, end-to-end robotic manipulation system that integrates perception, motion planning, and control. I gained practical experience designing modular ROS 2 architectures, working with both collision-aware planning and real-time control for dynamic targets, and debugging complex robotic behaviors in simulation and on physical hardware. Most importantly, the project strengthened my ability to translate high-level task goals into reliable, autonomous robotic actions in real-world environments.