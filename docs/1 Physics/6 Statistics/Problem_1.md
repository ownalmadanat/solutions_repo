# Problem 1
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, theta, g=9.81):
    theta_rad = np.radians(theta)
    return (v0**2 * np.sin(2 * theta_rad)) / g

angles = np.linspace(0, 90, 100)  # Array of angles
v0 = 20  # Initial velocity (m/s)

ranges = np.array([projectile_range(v0, theta) for theta in angles])

plt.plot(angles, ranges)
plt.xlabel("Launch Angle (degrees)")
plt.ylabel("Range (m)")
plt.title("Projectile Range vs. Launch Angle")
plt.grid()
plt.show()


