# Problem 2"""
Forced Damped Pendulum Simulation
Mathematical Formulation:

$$ \frac{d^2\theta}{dt^2} + \frac{b}{m}\frac{d\theta}{dt} + \frac{g}{L}\sin\theta = \frac{F}{mL}\cos(\omega_d t) $$

Linearized Form (small angles):
$$ \frac{d^2\theta}{dt^2} + 2\beta\frac{d\theta}{dt} + \omega_0^2\theta = A\cos(\omega_d t) $$
Where:
$$ \beta = \frac{b}{2m},\quad \omega_0 = \sqrt{\frac{g}{L}},\quad A = \frac{F}{mL} $$
"""
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

class ForcedPendulum:
    def __init__(self, b=0.5, m=1.0, L=1.0, g=9.81, F=1.2, omega_d=2.0):
        """
        Initialize pendulum parameters
        
        Parameters follow the mathematical formulation:
        $$ \frac{d^2\theta}{dt^2} + \frac{b}{m}\frac{d\theta}{dt} + \frac{g}{L}\sin\theta = \frac{F}{mL}\cos(\omega_d t) $$
        """
        self.b = b      # Damping coefficient (kg/s)
        self.m = m      # Mass (kg)
        self.L = L      # Length (m)
        self.g = g      # Gravity (m/s²)
        self.F = F      # Driving force amplitude (N)
        self.omega_d = omega_d  # Driving frequency (rad/s)
        
        # Derived parameters
        self.beta = b / (2 * m)  # Damping parameter $$ \beta $$
        self.omega0 = np.sqrt(g / L)  # Natural frequency $$ \omega_0 $$
        self.A = F / (m * L)     # Normalized amplitude $$ A $$
        
    def equation(self, t, y):
        """
        Defines the differential equation for the pendulum
        
        Returns:
        $$ \frac{d\theta}{dt} = \omega $$
        $$ \frac{d\omega}{dt} = -\frac{b}{m}\omega - \frac{g}{L}\sin\theta + \frac{F}{mL}\cos(\omega_d t) $$
        """
        theta, omega = y
        dtheta_dt = omega
        domega_dt = (-self.b/self.m)*omega - (self.g/self.L)*np.sin(theta) + \
                    (self.F/(self.m*self.L))*np.cos(self.omega_d*t)
        return [dtheta_dt, domega_dt]
    
    def linear_solution(self, t, theta0, omega0):
        """
        Analytical solution for linearized case (small angles)
        
        Returns:
        $$ \theta(t) = e^{-\beta t}(C_1\cos(\omega_1 t) + C_2\sin(\omega_1 t)) + \frac{A}{\sqrt{(\omega_0^2-\omega_d^2)^2+(2\beta\omega_d)^2}}\cos(\omega_d t - \phi) $$
        Where:
        $$ \omega_1 = \sqrt{\omega_0^2 - \beta^2} $$
        $$ \phi = \tan^{-1}\left(\frac{2\beta\omega_d}{\omega_0^2-\omega_d^2}\right) $$
        """
        omega1 = np.sqrt(self.omega0**2 - self.beta**2)
        phi = np.arctan2(2*self.beta*self.omega_d, self.omega0**2 - self.omega_d**2)
        
        # Coefficients from initial conditions
        C1 = theta0
        C2 = (omega0 + self.beta*theta0) / omega1
        
        # Transient solution
        transient = np.exp(-self.beta*t) * (C1*np.cos(omega1*t) + C2*np.sin(omega1*t))
        
        # Steady-state solution
        denominator = np.sqrt((self.omega0**2 - self.omega_d**2)**2 + 
                             (2*self.beta*self.omega_d)**2)
        steady_state = (self.A / denominator) * np.cos(self.omega_d*t - phi)
        
        return transient + steady_state
    
    def simulate(self, t_span, y0, method='RK45'):
        """Numerical solution of the nonlinear equation"""
        sol = solve_ivp(self.equation, t_span, y0, method=method, 
                       t_eval=np.linspace(t_span[0], t_span[1], 3000))
        return sol.t, sol.y[0], sol.y[1]
    
    def resonance_analysis(self):
        """
        Calculates resonance properties:
        
        Amplitude resonance frequency:
        $$ \omega_{amp} = \sqrt{\omega_0^2 - 2\beta^2} $$
        
        Quality factor:
        $$ Q = \frac{\omega_0}{2\beta} $$
        """
        omega_amp = np.sqrt(self.omega0**2 - 2*self.beta**2)
        Q = self.omega0 / (2*self.beta)
        return omega_amp, Q

def plot_results(t, theta, omega, pendulum):
    """Visualize simulation results with mathematical annotations"""
    plt.figure(figsize=(12, 8))
    
    # Time series plot
    plt.subplot(2, 2, 1)
    plt.plot(t, theta, 'b')
    plt.title(r'Time Series: $\theta(t)$')
    plt.xlabel('Time (s)')
    plt.ylabel(r'$\theta$ (rad)')
    
    # Phase portrait
    plt.subplot(2, 2, 2)
    plt.plot(theta, omega, 'b', linewidth=0.5)
    plt.title(r'Phase Portrait: $\theta$ vs $\omega$')
    plt.xlabel(r'$\theta$ (rad)')
    plt.ylabel(r'$\omega$ (rad/s)')
    
    # Poincaré section
    drive_period = 2*np.pi/pendulum.omega_d
    poincare_times = np.arange(50, t[-1], drive_period)
    poincare_indices = np.searchsorted(t, poincare_times)
    
    plt.subplot(2, 2, 3)
    plt.plot(theta[poincare_indices], omega[poincare_indices], 'ro', markersize=4)
    plt.title(r'Poincaré Section ($\omega_d = %.2f$)' % pendulum.omega_d)
    plt.xlabel(r'$\theta$ (rad)')
    plt.ylabel(r'$\omega$ (rad/s)')
    
    # Frequency analysis
    plt.subplot(2, 2, 4)
    fft_freq = np.fft.fftfreq(len(t), t[1]-t[0])
    fft_vals = np.abs(np.fft.fft(theta))
    plt.plot(fft_freq[:len(fft_freq)//2], fft_vals[:len(fft_freq)//2])
    plt.title('Frequency Spectrum')
    plt.xlabel('Frequency (Hz)')
    plt.ylabel('Amplitude')
    plt.tight_layout()
    plt.show()

def main():
    # Initialize pendulum with parameters
    pendulum = ForcedPendulum(b=0.5, F=1.2, omega_d=2.0)
    
    # Calculate resonance properties
    omega_amp, Q = pendulum.resonance_analysis()
    print(f"Natural frequency ω₀ = {pendulum.omega0:.2f} rad/s")
    print(f"Amplitude resonance frequency = {omega_amp:.2f} rad/s")
    print(f"Quality factor Q = {Q:.2f}")
    
    # Simulate the system
    t, theta, omega = pendulum.simulate(t_span=(0, 100), y0=[0.1, 0.0])
    
    # Plot results
    plot_results(t, theta, omega, pendulum)

if __name__ == "__main__":
    main()