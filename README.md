# GAME201 HW1

Implemented explicit and implicit euler of **mass spring**.

Explicit euler, implemented
* Forward euler
* RK2
* RK3
* RK4

Implicit euler, implemented
* Backward euler with jacob iteration (#iteration=20)

More details:
* Code was based on **mass_spring_explicit.py** example.
* Moved "Collide with ground" to after "Compute new position" because my explicit code updates *x* and *v* at the same time (I didn't know the difference)
* Didn't know how to compute gradient in implicit euler. Used auto-grad in **taichi** to compute the gradient.

Fun facts:
* First time to use github
* First physics simulation program
