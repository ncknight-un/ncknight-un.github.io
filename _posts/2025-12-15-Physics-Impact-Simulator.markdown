---
layout: post
title:  "Physics Simulations: Dynamics"
date:   2025-12-01 09:00:00 +0300
video: leg_sim.mp4
tags:   Physics Impacts Python Lagrangian_Dynamics
---

During my Master’s in Robotics at Northwestern University, I took a Machine Dynamics course focused on Lagrangian dynamics and physics-based simulation. This page presents a series of small projects and simulation examples developed throughout the quarter. It was one of the most engaging and conceptually important courses I have taken in my academic career, and I felt it was important to showcase representative work from the class.

The course covered Lagrangian and Hamiltonian formulations, conservation of energy, impacts, and force constraints. Each project shown in the gallery below demonstrates one or more of these concepts. One of the main takeaways from this work was learning how to combine reference frames, orientation, and physical modeling in simulation. Properly defining coordinate frames is critical when deriving equations of motion and debugging dynamic systems.

To maintain consistency across simulations, I developed a systematic frame convention. The positive x-axis was always aligned along the length of a limb or body segment. For example, in pendulum simulations, the x-axis was oriented along the body of the pendulum. This consistency in geometry and orientation significantly simplified derivations, improved clarity when debugging, and made it easier to reuse and extend simulation code. Below are descriptions of the primary dynamics principles used in these simulations.

### 1. Lagrangian Dynamics

A system’s Lagrangian was defined as the difference between kinetic and potential energy:

$$
L = KE - PE
$$

Using symbolic differentiation, the following were derived:

- Partial derivatives of the Lagrangian with respect to the generalized coordinates $q$ and their time derivatives $\dot{q}$
- The equations of motion:

$$
\frac{d}{dt}\left(\frac{\partial L}{\partial \dot{q}}\right)
- \frac{\partial L}{\partial q}
= F_{\text{external}}
$$

These expressions were set equal to the external forces and torques acting on the system, allowing the accelerations $\ddot{q}$ to be solved symbolically. Different external forces can be applied depending on the desired simulation behavior. For example, applying an upward force equal in magnitude to gravity prevents a body from accelerating downward.

### 2. Constraints and Impact Handling

In several simulations, constraints were added to ensure physically valid interactions between bodies and the environment. For example, in the leg-split simulation, constraints were applied at the feet to prevent them from passing through the ground plane. These constraints enforce relationships between components of a system and maintain realistic contact behavior.

A representative constraint equation is shown below:

$$
\phi_1 = y_{\text{world}} - y_{\text{leg1}}
$$

**Constraint Handling:**

- **Constraint Evaluation**  
  Constraint violations were detected using an `impact_condition` function when constraints exceeded a defined threshold.

- **Impact Resolution**  
  Post-impact velocities were computed using an `impact_update` function that solves the impact equations using Lagrange multipliers $\lambda$, while enforcing conservation of energy through the Hamiltonian formulation.

Many of these projects were done as a series of different assignments as a part of this class. I have included the Jupytor notebooks for each of the simulations as a part of a Github repository shared below!

--- 

**School:** Northwestern University  
**Location:** - Evanston, IL  
**Duration:** September 2025 - December 2025  
 
---

## Project Gallery

**Github Link:**  

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

## Skills Gained:

- Lagrangian and Hamiltonian Dynamics – Formulated equations of motion and applied energy-based approaches to complex systems.
- Physics Simulation – Built symbolic and numerical simulations of dynamic systems with constraints and impacts.
- Reference Frame Management – Developed consistent coordinate frame conventions to simplify calculations and debugging.
- Constraint and Impact Handling – Applied force and motion constraints to enforce realistic interactions in simulations.
- Mathematical Modeling – Derived symbolic solutions for accelerations and forces using symbolic differentiation.
- Python for modeling and simulation.

---

## Key Takeaway:

Through this course and the associated projects, I learned the importance of consistently defining reference frames and orientations in dynamic simulations, which greatly simplifies derivations and debugging. I gained hands-on experience applying Lagrangian and Hamiltonian formulations, energy conservation, and constraint handling to model realistic physical interactions. Developing symbolic and numerical simulations reinforced my understanding of system behavior under different forces, while working with constraints and impacts highlighted the necessity of precise modeling for accurate results. Overall, this experience strengthened both my theoretical understanding of dynamics and my practical skills in building robust, repeatable simulations.