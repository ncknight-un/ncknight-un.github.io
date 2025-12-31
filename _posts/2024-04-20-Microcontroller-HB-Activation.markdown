---
layout: post
title:  "MicroController: Bio-Motor Activation"
date:   2023-05-10 09:00:00 +0300
video: Fish_Controller.mp4
tags:   Microcontrollers
---

This project involves the design and development of a bioinstrument that triggers motor movement in response to a person’s heartbeat. The system uses a microcontroller (MSP430-FR2355) to process ECG data, generating a digital signal that activates a motor to move a series of fish around a fish tank. To verify heartbeats, an LED flashes when a heartbeat is detected by the microcontroller. The device architecture combines hardware components like the MSP430 microprocessor, an ECG module, and a motor driver (TB6612FNG), which work together to control the motor's speed and direction.

The MSP430 microcontroller serves as the central processing unit, converting analog ECG signals into a digital output. This digital signal controls the motor through the motor driver, which is powered by the MSP430. The motor driver uses a PWM signal for speed control and a standby input to activate or deactivate the motor, depending on the voltage signal received. Additionally, the motor’s direction is adjusted using the AI1 and AI2 pins on the motor driver, which operate via an H-bridge mechanism.

In this demo video, I used an artificial heart signal (Fluke PS410) in order to reduce the amount of setup time when testing the device. As shown, the ECG signal is delivered to the microcontroller in realtime, where it produces an analog signal for the motor driver through a square wave activation at the QRS peak complex.

In summary, the project integrates components to record ECG signals and control motor movement based on heartbeat detection. For a detailed breakdown of the software implementation, the report on GitHub provides an explanation of each line of code.

**School:** Purdue University - Indianapolis  
**Location:** Indianapolis, IN   
**Duration:** March 2023 - May 2023

---

## Project Gallery

**Github Link:** [https://github.com/ncknight-un/BioSense-Motor-Activation](https://github.com/ncknight-un/BioSense-Motor-Activation)

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

## Skills Gained:

- Embedded system design and integration
- Analog-to-digital signal conversion (ADC) for ECG data
- Interfacing biomedical sensors (ECG module)
- Motor control using TB6612FNG motor driver
- H-bridge motor control (direction and speed)
- PWM (Pulse Width Modulation) for motor speed control
- C programming for embedded systems

---

## Key Takeaway:

This project provided hands-on experience in integrating biological signals with embedded systems by converting ECG data into real-time motor control. It reinforced the role of microcontrollers as central processing units for sensing, signal conversion, and actuation. This project strengthened my understanding of motor control principles, including PWM-based speed regulation and H-bridge direction control, and demonstrated the challenges of hardware–software co-design in timing-sensitive systems. Developing this system in C improved my proficiency in low-level embedded programming, debugging, and reading hardware datasheets in order to interconnect different hardware components.