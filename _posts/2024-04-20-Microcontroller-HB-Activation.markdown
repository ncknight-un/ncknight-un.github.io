---
layout: post
title:  "Embedded Control: Bio-Motor Activation"
date:   2023-05-10 09:00:00 +0300
video: Fish_Controller.mp4
tags:   Biofeedback C Embedded_Systems Microcontrollers Signal_Processing 
---

This project involved designing and developing a bioinstrument that triggers motor movement in response to a person’s heartbeat. The system processes ECG signals and converts them into motor actuation, creating a visual representation of cardiac activity through moving elements in a fish tank.

---

**School:** Purdue University - Indianapolis  
**Location:** Indianapolis, IN   
**Duration:** March 2023 - May 2023

---

## Project Gallery

**Github Link:** <a href="https://github.com/ncknight-un/BioSense-Motor-Activation" target="_blank" rel="noopener noreferrer">
https://github.com/ncknight-un/BioSense-Motor-Activation
</a>

### Biosense Fishtank:
<div class="project-gallery">

  <div class="gallery-item">
    <h4>Fish Tank Setup</h4>
    <img src="/images/fish_setup.jpg" alt="Fish Setup">
  </div>

  <div class="gallery-item">
    <h4>Hardware Achitecture</h4>
    <img src="/images/circuit_diagram.jpg" alt="Circuits">
  </div>

  <div class="gallery-item">
    <h4>Artificial Heart Device</h4>
    <img src="/images/heart_sim.jpg" alt="Heart Sim">
  </div>

  <div class="gallery-item">
    <h4>Activation Oscilloscope</h4>
    <img src="/images/oscope.jpg" alt="Activation">
  </div>
</div>

---

## System Architecture

The device integrates multiple hardware components:

- **Microcontroller:** MSP430-FR2355  
- **Sensor:** ECG module  
- **Motor Driver:** TB6612FNG  

These components work together to process biological signals and control motor behavior.

---

## Signal Processing & Control

- The MSP430 acts as the central processor, converting analog ECG signals into digital outputs  
- A heartbeat is detected based on the QRS complex of the ECG signal  
- An LED flashes to visually confirm heartbeat detection  

---

## Motor Control

- The motor driver receives signals from the microcontroller  
- **PWM signals** control motor speed  
- **Standby input** enables or disables motor operation  
- **AI1 and AI2 pins** control direction using an H-bridge mechanism  

---

## Testing & Demonstration

- An artificial heart signal (Fluke PS410) was used to streamline testing  
- The ECG signal is processed in real time  
- A square wave signal at the QRS peak triggers motor activation  

---

## Skills Improved

- Embedded systems design and integration  
- ADC for biosignal (ECG) processing  
- Biomedical sensor interfacing  
- Motor control (TB6612FNG, H-bridge, PWM)  
- C programming for embedded systems  

---

## Key Takeaway

This project provided hands-on experience integrating biological signals with embedded systems by converting ECG data into real-time motor control. It reinforced the role of microcontrollers in sensing, signal processing, and actuation.

Working on this system strengthened my understanding of motor control (PWM speed regulation and H-bridge direction control) and highlighted the challenges of hardware–software co-design in timing-sensitive applications. It also improved my ability to write low-level C code, debug embedded systems, and interpret hardware datasheets for system integration.