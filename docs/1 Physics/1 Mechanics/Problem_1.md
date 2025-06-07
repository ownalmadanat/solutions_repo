Here's a structured Markdown document (suitable for a Jupyter Notebook or documentation) that addresses each part of your task. Python code is included for simulation and visualization.

---

# Investigating the Range as a Function of the Angle of Projection

---

## 📌 Motivation

Projectile motion, while a staple of introductory physics, reveals remarkable complexity when parameters such as launch angle, velocity, and environmental forces are varied. This investigation focuses on how the horizontal range of a projectile depends on its angle of projection, considering ideal conditions and moving toward more realistic scenarios.

---

## 1️⃣ Theoretical Foundation

### 🔹 Equations of Motion

Assuming no air resistance and launch/landing at the same height:

Let:

* $v_0$: initial velocity
* $\theta$: launch angle
* $g$: gravitational acceleration

Decomposing the velocity:

* Horizontal: $v_{x} = v_0 \cos(\theta)$
* Vertical: $v_{y} = v_0 \sin(\theta)$

Time of flight:

$$
t_{\text{flight}} = \frac{2v_0 \sin(\theta)}{g}
$$

Range:

$$
R(\theta) = v_0 \cos(\theta) \cdot t_{\text{flight}} = \frac{v_0^2 \sin(2\theta)}{g}
$$

### 🔹 Family of Solutions

The range formula illustrates how changing:

* $v_0$: scales the parabola of the range vs. angle
* $g$: flattens or steepens the curve (e.g., Moon vs. Earth)
* $\theta$: produces a symmetric curve with a peak at $45^\circ$

---

## 2️⃣ Analysis of the Range

### 🔹 Dependencies

* **Symmetry**: $R(\theta) = R(90^\circ - \theta)$
* **Maximum Range**: Occurs at $\theta = 45^\circ$
* **Effect of Velocity**: Quadratic dependency
* **Effect of Gravity**: Inverse relationship

---

## 3️⃣ Practical Applications

### ✳️ Real-world Extensions

* **Uneven terrain**: Launch and landing heights differ → $R = \frac{v_0 \cos(\theta)}{g} (v_0 \sin(\theta) + \sqrt{(v_0 \sin(\theta))^2 + 2gh})$
* **Air resistance**: Requires numerical modeling with drag force $F_d = -kv^2$
* **Ballistics**: Realistic models for sports, military, or aerospace require considering wind and rotation.

---

## 4️⃣ Implementation

### 🔧 Python Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

def compute_range(v0, g, angles_deg):
    angles_rad = np.radians(angles_deg)
    return (v0**2 * np.sin(2 * angles_rad)) / g

# Parameters
v0_list = [10, 20, 30]  # m/s
g = 9.81  # m/s^2
angles = np.linspace(0, 90, 500)

# Plotting
plt.figure(figsize=(10, 6))
for v0 in v0_list:
    R = compute_range(v0, g, angles)
    plt.plot(angles, R, label=f'v₀ = {v0} m/s')

plt.title("Projectile Range vs. Angle of Projection")
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (meters)")
plt.legend()
plt.grid(True)
plt.show()
```

---

## 📊 Results and Discussion

* Each curve is symmetric with a peak at 45°.
* Higher initial velocities shift the range curve upwards.
* This visualization confirms the analytical relationship.

---

## ⚠️ Limitations and Extensions

### 🧱 Idealized Model

* Assumes no air resistance, flat terrain, no rotation.
* Over-simplifies many real-world conditions.

### 🔄 Suggested Enhancements

1. **Numerical integration (Euler/Runge-Kutta)** for drag:

   $$
   \vec{a} = -g\hat{j} - \frac{k}{m} \vec{v}
   $$
2. **Variable gravity or elevation** in high-altitude contexts.
3. **Monte Carlo simulations** for stochastic wind effects.

---

## 🔗 Conclusion

Understanding the dependence of projectile range on launch angle opens doors to analyzing a wide variety of physical systems. From refining sports techniques to designing aerospace trajectories, this fundamental model—when augmented—serves as a springboard for deeper exploration in physics and engineering.

---

Would you like me to generate a downloadable Jupyter Notebook or expand this model to include air resistance or varying terrain next?
