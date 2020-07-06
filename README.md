# GAME201 HW1

Implemented explicit and implicit euler of **mass spring**.

Explicit euler, implemented
* Forward euler
* RK2
* RK3
* RK4

Implicit euler, implemented
* Backward euler with jacobi iteration (#iteration=20)

More details:
* Code was based on **mass_spring_explicit.py** example.
* Moved "Collide with ground" to after "Compute new position" because my explicit code updates *x* and *v* at the same time (I didn't know whether this was acceptable or not)
* Didn't know how to compute gradient in implicit euler. Used auto-grad in **taichi** to compute the gradient.
* Settings:
  * #particles = 10
  * damping = 20.0
  * dt = 1e-3

Comparsion
\ |Forward Euler | RK2 | RK3 | RK4 | Implicit euler
---- | ----- | ------ | ---- | ---- | --------
latency per step **\*** | ~0.4ms | ~0.5ms | ~0.6ms | ~0.7ms | ~5m (~3m w/o auto-grad computing time)
energy stableness **\*\*** | ~0.92 | ~0.92 | ~0.92 | ~0.92 | ~0.98
max spring stiffness | ~7,500 | ~45,000 | ~300,000 | ~700,000 | ~300,000 (similar value for #iteration=50)
max dt (spring stiffness=1000) | ~2e-3 | ~8e-3 | ~0.02 | ~0.03 | ~0.15

**\*** environment (windows 10, ram=16G, cpu=AMD Ryzen 1700X, gpu=Nvidia GTX 1700Ti)

**\*\*** energy (mgh + mv^2 / 2 + kΔx^2 / 2) stableness = moving average rate of (energy at step **t** / energy at step **t-100**) after the movement of springs becomes small and before the spring hits the ground.

GIFs
Forward Euler | RK2 | RK3 
----- | ------ | ----
<img src="https://github.com/hakic/GAME201_HW1/blob/master/forward_euler.gif?raw=true" width="400"> | <img src="https://github.com/hakic/GAME201_HW1/blob/master/RK2.gif?raw=true" width="400"> | <img src="https://github.com/hakic/GAME201_HW1/blob/master/RK3.gif?raw=true" width="400">

RK4 |  Implicit euler
----- | ------
<img src="https://github.com/hakic/GAME201_HW1/blob/master/RK4.gif?raw=true" width="400"> | <img src="https://github.com/hakic/GAME201_HW1/blob/master/implicit_euler.gif?raw=true" width="400">
