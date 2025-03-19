# Problem 1
#  Waves on Water Surface (Single Disturbance Equation) - Notes  

## Understanding the Wave Equation  
When a small disturbance (like dropping a stone) happens in water, it creates **circular waves** that move outward. The **Single Disturbance Equation** describes how these waves behave:  

$$
\eta(x, y, t) = \frac{A}{\sqrt{r}} \cdot \cos (kr - \omega t + \phi)
$$  

### 🔹 What Do These Symbols Mean?  

- **$\eta(x, y, t)$** → The height (displacement) of the water surface at any point $(x, y)$ at time $t$.  
- **$A$** → The **amplitude** of the wave (maximum height).  
- **$r$** → The **distance** from the source $(x_0, y_0)$ to the point $(x, y)$, given by:  

  $$r = \sqrt{(x - x_0)^2 + (y - y_0)^2}$$  

- **$k = \frac{2\pi}{\lambda}$** → The **wave number**, which depends on the **wavelength** $\lambda$ (the distance between two wave crests).  
- **$\omega = 2\pi f$** → The **angular frequency**, related to the **frequency** $f$ (how many waves pass per second).  
- **$\phi$** → The **initial phase**, which determines where the wave starts.  

---

## Relationship Between the Variables  

1. **The wave height $\eta(x, y, t)$ gets smaller as distance $r$ increases**  
   - Since $\eta$ has a factor of $\frac{A}{\sqrt{r}}$, as $r$ increases, the denominator grows, making $\eta$ smaller.  
   - This means that waves lose energy as they spread out.  

2. **Higher frequency $f$ means faster oscillations**  
   - If $f$ is large, then $\omega = 2\pi f$ is also large.  
   - This causes the wave to **move up and down faster**.  

3. **Shorter wavelength $\lambda$ means more waves in a small space**  
   - Since $k = \frac{2\pi}{\lambda}$, a **smaller $\lambda$** results in a **larger $k$**.  
   - This means the waves are more tightly packed.  

4. **The initial phase $\phi$ shifts the wave**  
   - Changing $\phi$ moves the wave **forward or backward** in time.  

---

##  Example - Two Sources Interfering  

Imagine we drop **two pebbles** into a pond at different positions. Each creates its own wave, and **where they meet, interference happens**:  

- **Constructive Interference** → When two waves **add up**, they create a **higher wave**.  
- **Destructive Interference** → When two waves **cancel out**, they create a **flat surface (no wave)**.  

If we place **waves at the vertices of a square (or any polygon)**, the overlapping waves form **beautiful interference patterns!** 🌊  

---
