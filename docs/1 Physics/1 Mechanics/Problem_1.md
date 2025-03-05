# Problem 1
<<<<<<< HEAD
This problem involves both theoretical derivations and computational simulations. I'll help you structure your solution by guiding you through each section.
=======

---

### **Step 1: Theoretical Foundation**
1. **Governing Equations**  
   Projectile motion follows Newton’s Second Law:  
   - In the horizontal direction: \( a_x = 0 \) (no acceleration in ideal conditions)  
   - In the vertical direction: \( a_y = -g \) (acceleration due to gravity)  

   These lead to the following motion equations:  
   \[
   x(t) = v_0 \cos(\theta) t
   \]
   \[
   y(t) = v_0 \sin(\theta) t - \frac{1}{2} g t^2
   \]
   
2. **Time of Flight**  
   Solve for \( t_f \) when \( y(t) = 0 \):  
   \[
   0 = v_0 \sin(\theta) t - \frac{1}{2} g t^2
   \]
   \[
   t_f = \frac{2 v_0 \sin(\theta)}{g}
   \]

3. **Range Equation**  
   Substituting \( t_f \) into \( x(t) \):  
   \[
   R = v_0 \cos(\theta) \times \frac{2 v_0 \sin(\theta)}{g}
   \]
   \[
   R = \frac{v_0^2}{g} \sin(2\theta)
   \]

---

### **Step 2: Analysis of the Range**
- The range is **maximum at** \( \theta = 45^\circ \) because \( \sin(2\theta) \) is maximized at \( 90^\circ \).
- Increasing initial velocity \( v_0 \) increases \( R \).
- Increasing gravity \( g \) reduces \( R \).

---

### **Step 3: Practical Applications**
- In sports (e.g., soccer, baseball), optimizing launch angle maximizes distance.
- In engineering, artillery and rockets require precise angle calculations.
- In astrophysics, launch angles affect orbital trajectories.

---

### **Step 4: Implementation (Python Simulation)**
I’ll now provide a Python script for simulating and plotting range vs. angle.

This script calculates and plots the projectile range as a function of launch angle. Let me know if you want to add features like air resistance or uneven terrain! 

