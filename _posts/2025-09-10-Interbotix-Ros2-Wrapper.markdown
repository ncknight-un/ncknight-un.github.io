---
layout: post
title:  "Interbotix- ROS 2 Wrapper"
date:   2025-09-10 09:00:00 +0300
video: interbotix_grasp1.mp4
tags:   Path_Planning Python  ROS_2 Vision
---
For this project, I developed a vision-guided robotic arm capable of detecting and retrieving a pen from a human hand. The system uses an Interbotix robotic arm controlled via a ROS2 wrapper with Python, integrating computer vision, kinematics, and motion planning to achieve precise grasping.

The core challenge of this project was coordinating perception with manipulation: the arm must accurately detect the pen’s position and orientation in real time, plan a possible trajectory given the arms 5-DOF, and execute a smooth grasp. Python scripts interface with the ROS2 nodes to process camera input, compute target coordinates, and command the arm’s movements.

This project was exciting because it was the first time I have been able to interact with ROS 2 and robotic arm manipulation. By combining vision and control, the arm could locate and pick up a pen from a human hand, which made the technology feel tangible and interactive. Working on this project helped me understand how robots “see” and move, and gave me hands-on experience with planning motions and controlling precise movements—skills that are important for robotics applications.

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

## Skills Gained:

- Perception: Integrated computer vision to detect objects of specific color and estimate their position and orientation using an Intel Realsense camera.
- Python: Developed scripts to process vision data, plan trajectories, and command the robotic arm for specific tasks.
- System Integration: Combined vision, perception, and control pipelines into a functional robotic application.
- Calibration: Learned how to calibrate sensors and robotic systems to ensure precise perception and motion control.

---

## Key Takeaway:

This project reinforced the importance of tightly integrating perception and manipulation in robotics. Accurate object detection and real-time position estimation are critical for reliable grasping. Working with ROS2 and Python highlighted how middleware simplifies communication between sensors and actuators, enabling modular and scalable robotic systems. Overall, this experience gave me an insight into how to implement vision-guided robotic systems capable of interacting with dynamic environments.