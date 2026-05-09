# Orbital Mechanics Sandbox

Four orbital-mechanics simulations from first principles: Chenciner–Montgomery figure-eight, Hohmann transfers, Mercury's GR precession, and the Earth–Sun Lagrange points.

Each section starts from first principles and implements its own numerical integrator or method (Euler-Cromer, RK2, Velocity Verlet and fsolve). 

**How to run:**

Open `An_exploration_about_orbits.ipynb` in Google Colab or Jupyter and run cells top-to-bottom. Cell 12 takes 30–60 s on a laptop.
- Built on: Python 3.12 (3.6+ should work)
- Dependencies: `numpy`, `matplotlib`, `scipy`
  

## Part 1: Three-Body

First, I attempted to use Euler-Cromer, where bodies have the same mass, but one is fixed at the origin. This produced a symmetric, periodic-looking trajectory, but preserved by symmetry rather than by dynamical stability. Not the figure-eight.


<img width="866" height="855" alt="Unknown" src="https://github.com/user-attachments/assets/93640d68-0073-47a0-9d26-815697fc9176" />

<img width="654" height="290" alt="Screenshot 2026-05-09 at 2 51 59 PM" src="https://github.com/user-attachments/assets/becd0ce6-c689-4c66-af79-0acecf35a5ad" />

Then, I used the known solutions for the initial conditions, found by Chenciner and Montgomery, in 2000. All three bodies trace the same curve, offset by one-third of a period. In this case, the orbit solution is incredibly sensitive. Changing or rounding any initial value causes a mass to fly off the curve within a few periods.

<img width="778" height="519" alt="Screenshot 2026-05-09 at 2 52 25 PM" src="https://github.com/user-attachments/assets/7bcd637f-05c5-46d4-a024-501021a3403c" />
 

## Part 2: Hohmann

In the next part, I simulated how a spacecraft transfers between Low Earth to Geostationary Orbits (two-impulse transfer from a 300 km circular LEO to GEO). Then, I performed a sweep over the orbit-ratio r₂/r₁ to see how total Δv scales. 

LEO→GEO total Δv = 3.94 km/s; total Δv peaks at r₂/r₁ ≈ 15.58. 

I concluded the total Δv was NOT monotonic, peaking around 15. Three burns were more efficient than Hohmann, for initial and final orbit ratios above ~11.94.

<img width="628" height="366" alt="Screenshot 2026-05-09 at 2 57 36 PM" src="https://github.com/user-attachments/assets/d51f74f4-7d83-4109-847e-3b046afa20a1" />

<img width="768" height="470" alt="Unknown-1" src="https://github.com/user-attachments/assets/8af70f7f-b937-48ef-ab48-e3ac805f1046" />


## Part 3: GR precession

Next, I added a small 1/r^3 perturbation to Newtonian gravity, and tracked perihelion angles. 

This is a crude but effective general relativistic approximation. The orbit visibly precesses over time. Perihelion angles are logged each orbit to extract a measured precession rate for comparison with Mercury's observed 43 arc seconds per century. 

<img width="702" height="701" alt="Unknown-2" src="https://github.com/user-attachments/assets/11ff83ee-62c7-4063-80ad-1a755ebcdb59" />
<img width="741" height="182" alt="Screenshot 2026-05-09 at 2 59 42 PM" src="https://github.com/user-attachments/assets/9e7d8e56-af92-4e91-9412-ff8724b50bd4" />

Simulation gave 42.64 arcsec/century vs. Schwarzschild's 42.98, which agreed to within 0.8%

Mercury's actual per-orbit precession is only ~0.1 arcsec, which is too small to see, so I added a second cell, which amplifies the effect over 10⁶ years for visibility. 

<img width="702" height="701" alt="Unknown-3" src="https://github.com/user-attachments/assets/e9cded62-0e54-4d51-b5ba-f8266959cb44" />


## Part 4: Lagrange Points

Lastly, I found the stable and unstable Lagrange points, by mapping the effective potential U_eff as a heat map across the Earth-Sun rotating frame. then used fsolve on ∇U_eff = 0 to locate the five Lagrange points.  

<img width="959" height="790" alt="Unknown-4" src="https://github.com/user-attachments/assets/91ca1a7d-45d9-4831-a3b1-46c1b9ff087e" />

I found L1 at ~0.99 AU, L2 at ~1.01 AU and L3 at ~-1 AU. L1–L3 are saddles.

L4 and L5 are at the equilateral-triangle positions. L4 and L5 are stable. 


## Additionally/Philosophical notes: 

I believe learning from antecedent examples is an invaluable skill. To me, It is inspirational how simple the solutions from an engineer can be. 

I had a really good teacher, and the original problem was something like "build a 3 body orbit."

I wanted to build this in google colab, to test its limitations and pitfalls as well. Truthfully, I sort of went down a rabbit hole, but it was a good time. 

I thought this was a lot of fun and challenging to do, but I hope to look back on it and see its dainty simplicity.
