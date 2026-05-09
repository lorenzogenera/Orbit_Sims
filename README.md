**Orbital Mechanics Sandbox**

Four orbital-mechanics simulations from first principles: Chenciner–Montgomery figure-eight, Hohmann transfers, Mercury's GR precession, and the Earth–Sun Lagrange points.

Each section starts from first principles and implements its own numerical integrator or method (Euler-Cromer, RK2, Velocity Verlet and fsolve). 

How to run

Open `An_exploration_about_orbits.ipynb` in Google Colab or Jupyter and run cells top-to-bottom. Cell 12 takes 30–60 s on a laptop.

- Built on: Python 3.12 (3.6+ should work)
- Dependencies: `numpy`, `matplotlib`, `scipy`


The original class assignment was something to the effect of “reproduce the three body problem”

**Part 1: Three-Body**

First, I attempted to use Euler-Cromer, where bodies have the same mass, but one is fixed at the origin. This produced a symmetric, periodic-looking trajectory, but preserved by symmetry rather than by dynamical stability. Not the figure-eight.


<img width="866" height="855" alt="Unknown" src="https://github.com/user-attachments/assets/93640d68-0073-47a0-9d26-815697fc9176" />

<img width="654" height="290" alt="Screenshot 2026-05-09 at 2 51 59 PM" src="https://github.com/user-attachments/assets/becd0ce6-c689-4c66-af79-0acecf35a5ad" />

Then, I used the known solutions for the initial conditions., found by Chenciner and Montgomery, in 2000. All three bodies trace the same curve, offset by one-third of a period. In this case, the orbit solution is incredibly sensitive. Changing or rounding any initial value causes a mass to fly off the curve within a few periods.

<img width="778" height="519" alt="Screenshot 2026-05-09 at 2 52 25 PM" src="https://github.com/user-attachments/assets/7bcd637f-05c5-46d4-a024-501021a3403c" />





