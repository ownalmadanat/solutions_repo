# Mechanics

## Problem 1: Investigating the Range as a Function of the Angle of Projection

### Motivation

Projectile motion, while seemingly simple, offers a rich playground for exploring fundamental principles of physics. The problem is straightforward: analyze how the range of a projectile depends on its angle of projection. Yet, beneath this simplicity lies a complex and versatile framework. The equations governing projectile motion involve both linear and quadratic relationships, making them accessible yet deeply insightful.

What makes this topic particularly compelling is the number of free parameters involved in these equations, such as initial velocity, gravitational acceleration, and launch height. These parameters give rise to a diverse set of solutions that can describe a wide array of real-world phenomena, from the arc of a soccer ball to the trajectory of a rocket.

---

## Task

### 1. Theoretical Foundation

To analyze projectile motion, we begin by deriving the basic equations from Newton's laws:

**Equations of Motion:**

* $x(t) = v_0 \cos(\theta) t$
* $y(t) = v_0 \sin(\theta) t - \frac{1}{2}gt^2$

Where:

* $v_0$ = initial velocity
* $\theta$ = angle of projection
* $g$ = gravitational acceleration

**Time of Flight (symmetric case):**

* When $y(t) = 0 \Rightarrow t = \frac{2v_0 \sin(\theta)}{g}$

**Horizontal Range:**

* $R = v_0 \cos(\theta) \cdot t = \frac{v_0^2 \sin(2\theta)}{g}$

**Family of Solutions:**

* Varying initial velocity or gravity affects the maximum range
* Changing the angle shifts the range peak, with a maximum at 45° in the absence of air resistance and equal launch/landing height

---

### 2. Analysis of the Range

* The function $R(\theta) = \frac{v_0^2 \sin(2\theta)}{g}$ is symmetric around 45°.
* As initial velocity increases, range increases quadratically
* As gravity increases, range decreases
* The optimal launch angle is 45° for flat terrain and no air resistance

---

### 3. Practical Applications

Real-world projectile scenarios differ:

* **Uneven terrain:** Adjust range using launch and landing heights
* **Air resistance:** Requires modeling drag force
* **Applications:** Sports (soccer, golf), engineering (ballistics), spaceflight (rocket trajectories)

---

### 4. Implementation

Python code example:

```python
import numpy as np
import matplotlib.pyplot as plt

def compute_range(v0, g, angles_deg):
    angles_rad = np.radians(angles_deg)
    return (v0**2 * np.sin(2 * angles_rad)) / g

v0_list = [10, 20, 30]  # m/s
g = 9.81  # m/s^2
angles = np.linspace(0, 90, 500)

plt.figure(figsize=(10, 6))
for v0 in v0_list:
    R = compute_range(v0, g, angles)
    plt.plot(angles, R, label=f'v0 = {v0} m/s')

plt.title("Projectile Range vs. Angle of Projection")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.legend()
plt.grid(True)
plt.show()
```

---

## Deliverables

* A Markdown document (this one) with embedded Python script for simulation
* A detailed theoretical derivation of the projectile range formula
* Graphical plots showing range versus angle for various initial velocities
* A discussion on extending the model to real-world scenarios

---

## Hints and Resources

* Start from the fundamental laws of motion and gradually build the general solution
* Use numerical methods or simulation tools to explore scenarios that go beyond simple analytical solutions
* Consider how this model connects to real-world systems, such as sports, engineering, and astrophysics

---

This task encourages a deep understanding of projectile motion while showcasing its versatility and applicability across various domains.

---

## Problem 2: Investigating the Dynamics of a Forced Damped Pendulum

### Motivation

The forced damped pendulum is a captivating example of a physical system with intricate behavior resulting from the interplay of damping, restoring forces, and external driving forces. By introducing both damping and external periodic forcing, the system demonstrates a transition from simple harmonic motion to a rich spectrum of dynamics, including resonance, chaos, and quasiperiodic behavior. These phenomena serve as a foundation for understanding complex real-world systems, such as driven oscillators, climate systems, and mechanical structures under periodic stress.

Adding forcing introduces new parameters, such as the amplitude and frequency of the external force, which significantly affect the pendulum's behavior. By systematically varying these parameters, a diverse class of solutions can be observed, including synchronized oscillations, chaotic motion, and resonance phenomena. These behaviors not only highlight fundamental physics principles but also provide insights into engineering applications such as energy harvesting, vibration isolation, and mechanical resonance.

---

## Task

### 1. Theoretical Foundation

Start with the differential equation governing the motion of a forced damped pendulum:

$\frac{d^2\theta}{dt^2} + \beta \frac{d\theta}{dt} + \omega_0^2 \sin(\theta) = A \cos(\omega t)$

Where:

* $\beta$ = damping coefficient
* $\omega_0$ = natural frequency
* $A$ = driving amplitude
* $\omega$ = driving frequency

Derive the approximate solutions for small-angle oscillations:

* Assume $\sin(\theta) \approx \theta$
* Analyze linearized solutions and resonance

Explore resonance conditions and their implications for the system's energy.

---

### 2. Analysis of Dynamics

* Investigate how the damping coefficient, driving amplitude, and driving frequency influence the motion
* Examine the transition between regular and chaotic motion and their physical interpretations

---

### 3. Practical Applications

Discuss real-world scenarios where the forced damped pendulum model applies:

* Energy harvesting devices
* Suspension bridges
* Oscillating electrical circuits

---

### 4. Implementation

* Create a computational model to simulate the motion
* Visualize the behavior under various damping, driving force, and initial conditions
* Plot phase diagrams and Poincaré sections to illustrate transitions to chaos

---

## Deliverables

* A Markdown document with Python script or notebook implementing the simulations
* A detailed explanation of the general solutions for the forced damped pendulum
* Graphical representations of the motion for different damping coefficients, driving amplitudes, and driving frequencies, including resonance and chaotic behavior
* A discussion on the limitations of the model and potential extensions, such as introducing nonlinear damping or non-periodic driving forces
* Phase portraits, Poincaré sections, and bifurcation diagrams to analyze transitions to complex dynamics

---

## Hints and Resources

* For small angles, approximate $\sin(\theta) \approx \theta$ to simplify the differential equation
* Employ numerical techniques (e.g., Runge-Kutta methods) for exploring the dynamics beyond the small-angle approximation
* Relate the forced damped pendulum to analogous systems in other fields, such as electrical circuits (driven RLC circuits) or biomechanics (human gait)
* Utilize software tools like Python for simulations and visualizations

---

This task bridges theoretical analysis with computational exploration, fostering a deeper understanding of forced and damped oscillatory phenomena and their implications in both physics and engineering.
