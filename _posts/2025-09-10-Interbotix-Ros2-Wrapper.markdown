---
layout: post
title:  "Autonomous Pen Grasping"
date:   2025-09-10 09:00:00 +0300
video: interbotix_grasp1.mp4
tags:   Path_Planning Python ROS_2 Vision
---

In this project, I developed a vision-guided robotic arm capable of detecting and retrieving a pen from a human hand. The system uses an Interbotix robotic arm controlled via a ROS 2 Python interface, integrating computer vision, kinematics, and motion planning to achieve precise grasping.

---

**School:** Northwestern University  
**Location:** - Evanston, IL  
**Duration:** September 2025
 
---

## Project Gallery

**Github Link:** <a href="https://github.com/ncknight-un/Interbotix_Pen_Grasping" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/Interbotix_Pen_Grasping
</a>

### Enclosure & CAD Designs:

<div class="project-gallery">

  <div class="gallery-item">
      <h4>Grasp Success Ex#1</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/interbotix_grasp1.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  
  <div class="gallery-item">
    <h4>Grasp Success Ex#2</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/interbotix_grasp2.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Repeatability</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/interbotix_repeat.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Camera - Robot Calibration</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/calibration.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
</div>

---

## Core Challenge

The primary challenge was coordinating perception with manipulation:

- Detect the pen’s position and orientation in real time  
- Plan a feasible trajectory given the arm’s 5-DOF constraints  
- Execute a smooth and accurate grasp  

---

## System Implementation

- Python scripts interface with ROS 2 nodes  
- Camera input is processed to extract target coordinates  
- Motion commands are generated and sent to the robotic arm  
- Kinematics and planning ensure feasible and precise movement to grasp pen  

---

## Skills Improved:

- **Perception:** Vision-based object detection and pose estimation using an Intel RealSense camera  
- **Python:** Data processing, trajectory planning, and robotic control  
- **System Integration:** Combined perception and control into a unified pipeline  
- **Calibration:** Sensor and system calibration for accurate perception and motion  

---

## Key Takeaway:

This was my first hands-on experience with ROS 2 and robotic manipulation. It provided practical insight into how robots perceive their environment and execute controlled movements.

Working on this system strengthened my understanding of vision-based perception, motion planning, and precise control, allowing me to demonstrate how these components come together in the real-world for robotics applications.