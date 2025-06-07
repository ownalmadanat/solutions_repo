# Problem 1: Investigating the Range as a Function of the Angle of Projection

## Motivation

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

* Use numerical solvers for non-ideal conditions
* Explore Python libraries like `scipy.integrate` for modeling drag
* Applications span across physics, sports analytics, military engineering, and aerospace

---

This problem encourages both a fundamental understanding and creative application of classical mechanics principles in modeling projectile motion.
