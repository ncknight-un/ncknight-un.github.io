---
layout: post
title:  "Sealbot 2.0: BlueROV Mod for Flow Detection and State Estimation using Whiskers"
date:   2026-09-05 09:00:00 +0300
video: Sealbot_drive.mp4
tags:  CAD Embedded_Systems ROS_2 Jetson_Orin 3D_Printing Machining
---

Sealbot 2.0 is a custom embedded platform for the BlueROV to support data collection as a part of the 
Hartmann Laboratory: Sensory and Neural Systems Engineering (SeNSE) Lab (<a href="https://sense-lab.github.io/" target="_blank" rel="noopener noreferrer">SeNSE_Lab</a>).

Sealbot 2.0 is designed to operate using **ROS 2**, utilizing **Ubuntu** and **Docker** to communicate across the station PC, a BlueROV Raspberry Pi, and a NVIDIA Jetson Orin Nano.

Prior work on this research, looking to create a model for detecting flow patterns using artificial whiskers in water was performed by Sayantani Bhattacharya. My approach builds off this concept by creating a more uniform robotics platform for better data collection and future onboard decision implementation. Sayantani's data collection methods can be found at (<a href="https://sayantanib.com/posts/rov/" target="_blank" rel="noopener noreferrer">Sealbot_1.0</a>)

Currently, Sealbot 2.0 is in the beginning stages of data collection. The goal is to have the station PC host manual control of the ROV during data collection, where the whisker array positions are detected onboard by the NVIDIA Jetson Orin Nano. This separation of detection handoff to the onboard computer allows us to save the data internally for missions and significantly reduces bandwidth across the tether in comparison to Sayantani's prior research attempts. Her methods published images to the station PC then did post mission analysis. My goals are to do realtime detection and control input, greatly reducing tether bandwidth. Furthermore, I designed this process with the idea that future implementation may allow for real-time feedback control of motor commands given onboard flow pattern detections using an embedded ML framework. 

Current work has been moving into data collection as the onboard detection system and station vizualization is up and running. First tests will include verfication on the theory that we can get basic sensor information such as moving forward and backward in a straight line and ROV speed predictions. 

**GitHub Link:** <a href="https://github.com/ncknight-un/Ncknight_Sealbot_System_2026" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/Ncknight_Sealbot_System_2026
</a>

---

### Motivation & Background

- **Why flow sensing?** Seals detect hydrodynamic wakes with their whiskers, the lab theorizes that we can learn patterns in whisker oscillations to detect current flows and objects moving in front of the robot. This could allow for the potential of the robot to follow moving objects in the water by factoring out abnormalities in flow patterns. If successful, Sealbot 2.0 could be used as a bio-inspired alternative to vision in low-visibility water or close forms of sonar.
- **Why the BlueROV platform?** Repeatable, established platform for ROV use with existing sysyem information publication using ROS (MAVLINK/MAVROS). 
- **What Sealbot 1.0 lacked:** Poor data collection and consistancy, no onboard processing, limited repeatability, and poor ROV control.

---

### Project Goals & Requirements

<table width="100%">
  <thead>
    <tr>
      <th width="45%">Requirements</th>
      <th width="35%">Target</th>
      <th width="20%">Status</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td> Modular, removable attachment </td>
      <td align="center"> Minimal changes to existing ROV </td>
      <td align="center"> Validated ✅ </td> 
    </tr>
    <tr>
      <td> Waterproof Rating </td>
      <td align="center"> ~5 meters </td>
      <td align="center"> Validated ✅ </td>
    </tr>
    <tr>
      <td> Onboard Whisker Detection </td>
      <td align="center">  60 FPS </td>
      <td align="center"> Validated ✅  </td>
    </tr>
    <tr>
      <td> Tether Bandwidth </td>
      <td align="center"> No Raw/Compressed Images Sent to Station </td>
      <td align="center">In-Progress 🔄 </td>
    </tr>
    <tr>
      <td> Time Sync Across PCs </td>
      <td align="center"> ~5-10ms offset </td>
      <td align="center"> In-Progress 🔄 </td> 
    </tr>
  </tbody>
</table>
 <!-- [✅ / 🔄 / ❌] -->

---

### Ongoing Data Collection

- Current work is focused on preliminary data collection for straight line movements and speed predictions using the whisker module.
  - Next steps are looking at cleaning up in frame focus of tags and validating consistant tag identification.

<div class="project-gallery">
  <div class="gallery-item">
    <h4>Internal View of Sealhead</h4>
    <img src="/images/sealbot_cam_view.jpg" alt="Cam View">
  </div>

  <div class="gallery-item">
    <h4>Internal View of Sealhead</h4>
    <img src="/images/sealbot_tagviz.jpeg" alt="Tag Viz">
  </div>
</div>

---

### System Architecture

Sealbot 2.0 system architecture consists of a station PC, the BlueROV Raspberry Pi, and an embedded Jetson Orin Nano. The Station PC utilizes Docker to run ROS2 Humble with CycloneDDS for data sharing with the onboard Jetson to create verification visuals during data collection. The Jetson Orin Nano is running Ubuntu 22.04 with ROS2 Humble in order to operate the existing ROS2 VimbaX package for the Alvium ML camera used in tag detection. The PC will be responsible for operating the service client during testing for camera bringup, PWM light management, BlueROV sensor MAVROS data publication, and ROS bag collection.

<div class="gallery-item">
  <h4>System Architecture Diagram</h4>
  <img src="/images/sealbot_arch_clean.svg" alt="System Architecture">
</div>

<div class="gallery-item">
  <h4>Embedded Attachment Circuit Diagram</h4>
  <img src="/images/Sealbot_Circuit_v4.svg" alt="Circuit Diagram">
</div>

---

### Software & Embedded Design

- The system runs **Ubuntu 22.04 LTS** with **ROS 2 Humble** on a **Jetson Orin Nano**.
- Control logic is implemented using **ROS 2 nodes** that manage camera bringup, time synchronization, and whisker array detection.
- **Station PC:** [Ubuntu 24.04 LTS, ROS2 Humble, Docker]
- **Jetson Orin Nano:** [Ubuntu 22.04, ROS2 Humble]
- **Networking:** [DDS - Cyclone DDS, ROS_DOMAIN_ID - 16, static IPs - 192.168.2.0/24 (BlueROV)]
<!-- - **Time synchronization:** [ Plan to use chrony for Time Sync] -->

**Key ROS 2 Nodes / Topics:**

<table width="100%">
  <thead>
    <tr>
      <th width="25%" align="center">Node</th>
      <th width="25%" align="center">Runs On</th>
      <th width="25%" align="center">Publishes</th>
      <th width="25%" align="center">Subscribes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center"> Camera Bringup</td>
      <td align="center"> Jetson Orin Nano </td>
      <td align="center"> Camera Info/Image Raw </td>
      <td align="center"> None </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="center"> Apriltag Bringup</td>
      <td align="center"> Jetson Orin Nano </td>
      <td align="center"> April Tag Detections</td>
      <td align="center"> Camera Image Raw </td>
    </tr>
  </tbody>
  <tbody>
    <tr>
      <td align="center"> Whisker Visualization</td>
      <td align="center"> PC Station </td>
      <td align="center"> Marker Arrays </td>
      <td align="center"> April Tag Detections </td>
    </tr>
  </tbody>
</table>

--- 

### Hardware Overview

<table width="100%">
  <thead>
    <tr>
      <th width="25%">Component</th>
      <th width="45%">Model</th>
      <th width="30%">Purpose</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td> ROV </td>
      <td align="center"> BlueROV2 </td>
      <td align="center"> Base Platform </td> 
    </tr>
    <tr>
      <td> Onboard Compute </td>
      <td align="center"> NVIDIA Jetson Orin Nano </td>
      <td align="center"> Onboard Detection, Data Logging </td>
    </tr>
    <tr>
      <td> Camera </td>
      <td align="center"> Alvium 1800 U-291m USB 3.0 2.9MP, Monochrome </td>
      <td align="center"> Whisker Tag Tracking </td>
    </tr>
    <tr>
      <td> Lens / Optics </td>
      <td align="center"> 8MM MegaPixel Fixed Focal Length Lens </td>
      <td align="center"> Working Distance Focus</td>
    </tr>
    <tr>
      <td> Power </td>
      <td align="center"> 4S 14.8V Lithium Ion Battery (2200 mAh) </td>
      <td align="center"> Onboard Jetson/lights power source </td> 
    </tr>
      <tr>
      <td> Jetson/Camera Enclosure </td>
      <td align="center"> Machined Aluminum + Optical Dome </td>
      <td align="center"> Waterproofing + Light Control </td> 
    </tr>
  </tbody>
</table>

---

### Sealbot 2.0 Physical Assembly

- The Sealbot 2.0 embedded assembly is housed on a BlueROV Payload Skid. This attaches to the BlueROV main housing via 4 stainless steel bolts. The onboard Jetson and Camera attachment housing in the custom aluminum housing is connected via a single waterproof ethernet cable which plugs directly into ethernet switch housed in the BlueROV main housing cylandar. 
  - This aligns with the project constraint to be as minimally invasive to the existing blue ROV as possible. 

- The Embedded System in the custom housing contains a Lithium Ion Battery to power the Jetson, onboard lights, and Alvium camera. The chamber contains a 12V DC-DC converter to supply a steady voltage to the Jetson during operation and another 5V DC-DC converter to seperately power the onboard lights.

- In between the camera sensor and the april tags, an optical dome is positioned at the interface of the aluminum tube and the head. This acts as a secondary failsafe incase a leak does occur at the whisker array interface. Due to the head being the only non aluminum interface, I chose to add this failsafe in because of the silicon whisker arrays designed by the SeNSE Lab that get placed in the mask. 

<div class="project-gallery">
  <div class="gallery-item">
    <h4>ROV Assembly with Sealbot 2.0 Mod</h4>
    <img src="/images/rov_assembled.jpeg" alt="ROV Assembly">
  </div>

  <div class="gallery-item">
    <h4>Embedded Jetson/Camera Assembly</h4>
    <img src="/images/embed_assem.jpeg" alt="Embedded Assembly">
  </div>

  <div class="gallery-item">
    <h4>Optical Dome Leak Failsafe</h4>
    <img src="/images/sealbot_dome_view.jpeg" alt="ROV Assembly">
  </div>

  <div class="gallery-item">
    <h4>Interior Head Tag Assembly</h4>
    <img src="/images/sealbot_tag_head.jpeg" alt="ROV Assembly">
  </div>
</div>

---

### BlueROV Modification CAD Design

- Developed layout for embedded detection and camera optics optimization using an Alvium USB 3.0 camera and NVIDIA Jetson Orin Nano computer prior to starting build.

<div class="project-gallery">

  <div class="gallery-item">
    <h4>Simulated Full Assembly Front-View</h4>
    <img src="/images/sealbot_cad_frontview.jpeg" alt="Full Front View">
  </div>

  <div class="gallery-item">
    <h4>Simulated Full Assembly Side-View</h4>
    <img src="/images/sealbot_cad_sideview.jpeg" alt="Full Side View">
  </div>

  <div class="gallery-item">
    <h4>Simulated Capsule View</h4>
    <img src="/images/sealbot_capsule.jpeg" alt="Capsule View">
  </div>

  <div class="gallery-item">
    <h4>Simulated Internal Capsule View</h4>
    <img src="/images/sealbot_internals.jpeg" alt="Internal Capsule View">
  </div>

  <div class="gallery-item">
    <h4>Simulated Array Optical View</h4>
    <img src="/images/rov_cad_optical_view.JPG" alt="Sim View">
  </div>
</div>

--- 

### Machined Components for Waterproof Seal & Water Testing
- Initial waterproof testing using 3D-printed parts proved to be insufficient. As a result, I machined my own waterproof components to correctly seal the whisker array and embedded system. 
  - Due to the complexity of the headpiece and its non-planar shape, I coated the part in resin epoxy to improve its water impermeability for layer line leaks. 
  - The system is also designed so that if the front mask fails and floods, the embedded computer and camera are completely enclosed by aluminum machined parts, with an optical dome separating them from the whisker array mask, so that the second inner chamber will not flood. 


<div class="project-gallery">

  <div class="gallery-item">
    <h4>3D Interface Parts - Water Test</h4>
    <img src="/images/water_testing_nm_parts.jpeg" alt="Water Test NM 1">
  </div>

  <div class="gallery-item">
    <h4>3D Interface Parts - Water Test</h4>
    <img src="/images/water_testing_nm_parts_2.jpeg" alt="Water Test NM 2">
  </div>

  <div class="gallery-item">
    <h4>Machined Parts - Water Test</h4>
    <img src="/images/water_testing_2.jpeg" alt="Water Test 2">
  </div>
</div>

---

### Buoyancy Validation

- Initial tests have been performed for systemic buoyancy and locomotion with the embedded attachment.
- Weights were added to the BlueROV Payload Skid, so that no changes are made to the existing ROV.

<div class="project-gallery">

  <div class="gallery-item">
    <h4>ROV Buoyancy Test - Sideview</h4>
    <img src="/images/sealbot_bouy_view.jpeg" alt="Buoy Side View">
  </div>

</div>

---

### Next Steps / Roadmap

- Complete time synchronization across all three computers
- Onboard mission logging + offline analysis workflow
- Closed-loop feedback control from flow detections
- [Flow pattern classification / estimation]

---
<!-- 
### Additional Media

<div class="project-gallery">

  <!-- <div class="gallery-item">
    <h4>Initial ROS 2 Testing</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_Test4.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

--- -->

### Skills Improved

- CAD design for modular, waterproof underwater attachments
- Machining (mill/lathe) and 3D printing
- ROS 2 across multiple computers with Docker and Ubuntu
- Embedded CV on the Jetson Orin Nano
- Time synchronization and bandwidth-aware system design

---
<!-- 
### Challenges & Lessons Learned

- **Waterproofing:** [What failed, how you diagnosed it, what fixed it (e.g., epoxy coating, machining)]
- **Cross-machine ROS 2 comms:** [Docker networking, DDS discovery, latency issues]
- **Buoyancy/stability:** [what surprised you]
- **Designing around shared equipment:** [constraints and tradeoffs]

--- -->

<!-- ### Key Takeaway

[2-3 sentences: what the platform enables, the biggest thing you learned, and where it's headed.]

--- -->

### Acknowledgments

- Hartmann Lab (SeNSE Lab), Northwestern University
- Sayantani Bhattacharya for Sealbot 1.0
- Mathew Elwin, Project Advisor