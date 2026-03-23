---
layout: post
title:  "Lagrangian Dynamics Simulations"
date:   2025-12-01 09:00:00 +0300
video: trip_pend.mp4
tags:  Lagrangian_Dynamics Physics Python Simulation
---

During my Master’s in Robotics at Northwestern University, I completed a Machine Dynamics course focused on Lagrangian dynamics and physics-based simulation. This page showcases a collection of simulation projects developed throughout the quarter.

This course was one of the most engaging and conceptually important in my academic experience, and this page highlights representative work demonstrating key principles in dynamic system modeling.

---

**School:** Northwestern University  
**Location:** - Evanston, IL  
**Duration:** September 2025 - December 2025  
 
---

## Project Gallery

<!-- **Github Link:**   -->

<div class="project-gallery">

  <div class="gallery-item">
    <h4>Fixed-Leg Splits Simulation</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/leg_sim.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  
  <div class="gallery-item">
    <h4>3-Arm Pendulum Simulation</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/3_pend.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
  
  <div class="gallery-item">
    <h4>Box Fixed-Pendulum Simulation</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/box_pendulum.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Single-Pend Impact Simulation</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/sing_pend.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>

  <div class="gallery-item">
    <h4>Triple-Pend Impact Simulation</h4>
    <video controls autoplay loop muted playsinline>
      <source src="/images/trip_pend.mp4" type="video/mp4">
      Your browser does not support the video tag.
    </video>
  </div>
</div>

---

## Frame Convention Strategy

To ensure consistency across simulations, I developed a standardized frame convention:

- The **positive x-axis** is aligned along the length of each limb or body segment  
- In pendulum systems, the x-axis follows the direction of the pendulum body  

**Benefits:**
- Simplifies mathematical derivations  
- Improves debugging clarity  
- Enables code reuse across simulations  

---

## 1. Lagrangian Dynamics

The Lagrangian is defined as:

$$
L = KE - PE
$$

Using symbolic differentiation, the following were derived:
- Partial derivatives with respect to generalized coordinates $q$ and velocities $\dot{q}$  
- Equations of motion:

$$
\frac{d}{dt}\left(\frac{\partial L}{\partial \dot{q}}\right)
- \frac{\partial L}{\partial q}
= F_{\text{external}}
$$

These equations were used to:
- Incorporate external forces and torques  
- Solve for system accelerations $\ddot{q}$ symbolically  

**Example:**  
Applying an upward force equal to gravity prevents downward acceleration.

---

## 2. Constraints and Impact Handling

Constraints were introduced to enforce physically valid interactions.

**Example:**
- Preventing a leg from passing through the ground in a leg-split simulation  

A representative constraint equation:

$$
\phi_1 = y_{\text{world}} - y_{\text{leg1}}
$$

- **Constraint Evaluation**  
  Violations were detected using an `impact_condition` function when thresholds were exceeded  

- **Impact Resolution**  
  Post-impact velocities were computed using an `impact_update` function  
  - Solves impact equations using Lagrange multipliers $\lambda$  
  - Enforces energy conservation via Hamiltonian formulation  

---

## Skills Improved:

- Lagrangian & Hamiltonian dynamics (equations of motion, energy methods)  
- Physics-based simulation (dynamic systems with constraints and impacts)  
- Reference frame design (consistent coordinate conventions)  
- Constraint and impact modeling  
- Mathematical modeling (symbolic derivation of system dynamics)  
- Python for simulation and modeling  

---

## Key Takeaway

This work reinforced the importance of consistent reference frame definitions in simplifying derivations and debugging dynamic systems. I gained hands-on experience applying Lagrangian and Hamiltonian methods, energy conservation, and constraint handling to model realistic physical interactions.

Building both symbolic and numerical simulations deepened my understanding of system behavior under varying forces, while working with constraints and impacts emphasized the need for precise modeling. Overall, this experience strengthened both my theoretical foundation in dynamics and my ability to develop robust, repeatable simulations.