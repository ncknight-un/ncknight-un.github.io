---
layout: post
title:  "Sealbot 2.0: BlueROV Mod for Flow Detection and Feedback Control"
date:   2026-09-05 09:00:00 +0300
video: Sealbot_Init_Bouy_Test.mp4
tags:  CAD Embedded_Systems ROS_2 Jetson_Orin 3D_Printing Machining
---

Sealbot 2.0 is a custom embedded platform for the BlueROV to support data collection as a part of the 
Hartmann Laboratory: Sensory and Neural Systems Engineering (SeNSE) Lab (<a href="https://sense-lab.github.io/" target="_blank" rel="noopener noreferrer">SeNSE_Lab</a>)

Sealbot 2.0 is designed to operate using **ROS 2**, utilizing **Ubuntu** and **Docker** to communicate across the station PC, BlueROV Raspberry Pi, and NVIDIA Jetson Orin Nano.

Prior work on this research topic for detecting flow patterns using artificial whiskers in water was performed by Sayantani Bhattacharya. My approach builds off this concept by creating a more uniform robotics platform for better data collection and future implementation. Sayantani's data collection methods can be found at (<a href="https://sayantanib.com/posts/rov/" target="_blank" rel="noopener noreferrer">Sealbot_1.0</a>)

Currently, Sealbot 2.0 is in a beginning stage for data collection. The goal is to have the station PC host manual control of the ROV during data collection, where the whisker array positions are detected onboard by the NVIDIA Jetson Orin Nano. This separation of detection handoff to the onboard computer allows us to save the data internally for missions and significantly reduces bandwidth across the tether, so that we do not need to send raw or compressed image data back to the station PC. I designed this process with the idea that future implementation may allow for real-time feedback control of motor commands given onboard flow pattern detections using an embedded ML framework. 

Current work includes finalizing buoyancy testing and stabilization of the BlueROV to allow for fully submerged data collection, and integrating cross communication and time synchronization across PCs. 

**GitHub Link:** <a href="https://github.com/ncknight-un/Ncknight_Sealbot_System_2026" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/Ncknight_Sealbot_System_2026
</a>

---

### Motivation & Background

- **Why flow sensing?** Seals detect hydrodynamic wakes with their whiskers, the lab theorizes that we can learn patterns in whisker oscillations to detect current flows and objects moving in front of the robot. This could allow for the potential of the robot to follow moving objects in the water by factoring out abnormalities in flow patterns. If successful, Sealbot 2.0 could be used as a bio-inspired alternative to vision/sonar in low-visibility water.
- **Why the BlueROV platform?** Repeatable, established platform for ROV use with existing ROS integration. 
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
      <td align="center"> ~3 meters </td>
      <td align="center"> Validated ✅ </td>
    </tr>
    <tr>
      <td> Onboard Whisker Detection </td>
      <td align="center">  60 FPS </td>
      <td align="center"> In-Progress 🔄 </td>
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

### System Architecture

Sealbot 2.0 system architecture consists of a station PC, the BlueROV Raspberry Pi, and an embedded Jetson Orin Nano. The Station PC utilizes Docker to run ROS2 Humble with CycloneDDS for data sharing with the onboard Jetson. The station PC is also responsible for running MAVROS to extract onboard information during data colection. The Jetson Orin Nano is running Ubuntu 22.04 with ROS2 Humble in order to operate the existing ROS2 VimbaX package for the Alvium ML camera used in tag detection. The PC will be responsible for operating the service client during testing for camera bringup, PWM light management, and ROS bag collection.

<br>
<div class="gallery-item">
  <h4>System Architecture Diagram</h4>
  <img src="/images/sealbot_2_system_architecture.png" alt="System Architecture">
</div>

**Data flow:**
1. Station PC → [Manual control commands / ROS2 Service Bringup]
2. Raspberry Pi → [Motor commands / MAVLink / Telemetry]
3. Jetson Orin Nano → [Whisker Detections, Camera Bringup/Light PWM Control, ROSbag]

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

- The Embedded System in the custom housing contains a Lithium Ion Battery to power the Jetson, onboard lights, and Alvium camera. The chamber contains a 12V DC-DC converter to supply a steady voltage to the Jetson during operation and another 5V DC-DC converter for the onboard lights power supply.

<div class="project-gallery">
  <div class="gallery-item">
    <h4>ROV Assembly with Sealbot 2.0 Mod</h4>
    <img src="/images/rov_assembled.jpeg" alt="ROV Assembly">
  </div>

  <div class="gallery-item">
    <h4>Embedded Assembly</h4>
    <img src="/images/embed_assem.jpeg" alt="Embedded Assembly">
  </div>
</div>

---

### Software & Embedded Design

- The robot runs **Ubuntu 22.04 LTS** with **ROS 2 Humble** on a **Jetson Orin Nano**.
- Control logic is implemented using **ROS 2 nodes** that manage camera bringup, time synchronization, and whisker array detection.
- **Station PC:** [Ubuntu 24.04 LTS, ROS2 Humble, Docker]
- **Jetson Orin Nano:** [JetPack version, Ubuntu 22.04, ROS2 Humble]
- **Networking:** [DDS - Cyclone DDS, ROS_DOMAIN_ID - 16, static IPs - 192.168.2.0/24 (BlueROV)]
- **Time synchronization:** [ Plan to use chrony for Time Sync]

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
      <td align="center"> Camera Info, Image Raw </td>
      <td align="center"> None </td>
    </tr>
  </tbody>
</table>

--- 

### BlueROV Modification CAD Design

- Designed a modular attachment for the BlueROV for easy assembly and disassembly of the Sealbot 2.0 embedded apparatus. 
  - This was a project constraint due to shared resources of the BlueROV across laboratories at Northwestern University. 
- Developed layout for embedded detection and camera optics optimization using an Alvium USB 3.0 camera and NVIDIA Jetson Orin Nano computer.

<div class="project-gallery">

  <div class="gallery-item">
    <h4>Simulated Array Optical View</h4>
    <img src="/images/rov_cad_optical_view.JPG" alt="Sim View">
  </div>
</div>

--- 

<!-- ### Whisker Detection Pipeline

- **Input:** [camera resolution, frame rate, lighting/illumination method]
- **Method:** [e.g., marker/tip tracking, thresholding, blob detection, CNN, etc.]
- **Output:** [whisker tip positions in pixels/mm, published on which ROS 2 topic and at what rate]
- **Calibration:** [how you map pixels to physical deflection]
- **Performance on Jetson:** [latency, FPS, CPU/GPU usage]

<div class="project-gallery">
  <div class="gallery-item">
    <h4>Raw Camera Frame</h4>
    <img src="/images/whisker_raw.jpeg" alt="Raw Frame">
  </div>
  <div class="gallery-item">
    <h4>Detected Whisker Positions</h4>
    <img src="/images/whisker_detected.jpeg" alt="Detected Whiskers">
  </div>
</div>

--- -->

### Machined Components for Waterproof Seal & Water Testing
- Initial waterproof testing using 3D-printed parts proved to be insufficient. As a result, I machined my own waterproof components to correctly seal the whisker array and embedded system. 
  - Due to the complexity of the headpiece and its non-planar shape, I coated the part in resin epoxy to improve its water impermeability for layer line leaks. 
  - The system is also designed so that if the front mask fails and floods, the embedded computer and camera are completely enclosed by aluminum machined parts, with an optical dome separating them from the whisker array mask, so that the second inner chamber will not flood. 


<!-- - **Sealing strategy:** [O-ring types/gland dimensions, dome port, cable penetrators]
- **Manufacturing:** [3D printer/material, machining operations used (mill/lathe), tolerances that mattered] -->

<div class="project-gallery">

  <div class="gallery-item">
    <h4>Machined Parts - Water Test</h4>
    <img src="/images/water_testing_1.jpeg" alt="Water Test 1">
  </div>

  <div class="gallery-item">
    <h4>Machined Parts - Water Test</h4>
    <img src="/images/water_testing_2.jpeg" alt="Water Test 2">
  </div>

  <div class="gallery-item">
    <h4>3D Parts - Water Test</h4>
    <img src="/images/water_testing_nm_parts.jpeg" alt="Water Test NM 1">
  </div>

  <div class="gallery-item">
    <h4>3D Parts - Water Test</h4>
    <img src="/images/water_testing_nm_parts_2.jpeg" alt="Water Test NM 2">
  </div>
</div>

---

### Initial Buoyancy Testing 

- Initial tests have been performed for systemic buoyancy and locomotion with the embedded attachment.
- (#) Weights were added to the BlueROV Payload Skid, so that no changes are made to the existing ROV.

<div class="project-gallery">

  <div class="gallery-item">
    <h4>ROV Buoyancy Test - Faceview</h4>
    <img src="/images/rov_bouy_side.jpeg" alt="Buoy Side View">
  </div>

  <div class="gallery-item">
    <h4>ROV Buoyancy Test - Sideview</h4>
    <img src="/images/rov_bouy_facing.jpeg" alt="Buoy Face View">
  </div>
</div>

---

### Next Steps / Roadmap

- Finish buoyancy testing and stabilization for full submersion
- Complete time synchronization across all three computers
- Onboard mission logging + offline analysis workflow
- Closed-loop feedback control from flow detections
- [Flow pattern classification / estimation]

---

### Additional Media

<div class="project-gallery">

  <!-- <div class="gallery-item">
    <h4>Initial ROS 2 Testing</h4>
    <video autoplay loop muted playsinline controls>
      <source src="/images/Rudy_Test4.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div> -->

</div>
<br>

---

### Skills Improved

- CAD design for modular, waterproof underwater attachments
- Machining (mill/lathe) and 3D printing for sealed enclosures
- ROS 2 across multiple computers with Docker and Ubuntu
- Embedded computer vision on the Jetson Orin Nano
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