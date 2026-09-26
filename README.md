# 2D Lennard-Jones Molecular Dynamics Simulation

A Python-based molecular dynamics simulation of interacting particles using the **Lennard-Jones (LJ) potential**. The project models a two-dimensional system of argon-like particles in reduced units and investigates particle motion, energy evolution, temperature, and trajectories.

The simulation uses the **Velocity Verlet integration algorithm** together with **periodic boundary conditions** and a finite Lennard-Jones cutoff radius.

---

## Overview

This project implements a simple molecular dynamics framework from scratch using:

- **Python**
- **NumPy** for numerical calculations
- **Matplotlib** for visualization
- **Matplotlib `FuncAnimation`** for particle animations

The particles interact through the Lennard-Jones potential

$$
U(r) = 4\epsilon
\left[
\left(\frac{\sigma}{r}\right)^{12}
-
\left(\frac{\sigma}{r}\right)^6
\right],
$$

where:

- $\epsilon$ is the characteristic energy scale,
- $\sigma$ is the characteristic length scale,
- $r$ is the distance between two particles.

The simulation is expressed primarily in **reduced Lennard-Jones units**, with the characteristic parameters obtained from argon.

---

## Physical Model

### Lennard-Jones Potential

The Lennard-Jones potential describes the interaction between two neutral particles through a short-range repulsive term and a longer-range attractive term:

$$
U(r) = 4\epsilon
\left[
\left(\frac{\sigma}{r}\right)^{12}
-
\left(\frac{\sigma}{r}\right)^6
\right].
$$

The corresponding force is calculated from

$$
\mathbf{F}_{ij}
=
48
\left(
\frac{1}{r^{14}}
-
\frac{1}{2r^8}
\right)
\mathbf{r}_{ij},
$$

in reduced units.

A cutoff radius of

$$
r_c = 2.5\sigma
$$

is used to limit the range of pairwise interactions.

---

## Argon Parameters

The simulation uses characteristic Lennard-Jones parameters based on argon:

| Parameter | Value |
|---|---:|
| $\sigma$ | $3.4\times10^{-10}$ m |
| $\epsilon$ | $1.65\times10^{-21}$ J |
| Mass | $6.69\times10^{-26}$ kg |
| Cutoff | $2.5\sigma$ |

The corresponding reduced units are constructed from

$$
t_0 = \sigma\sqrt{\frac{m}{\epsilon}},
$$

$$
v_0 = \sqrt{\frac{\epsilon}{m}},
$$

and

$$
F_0 = \frac{\epsilon}{\sigma}.
$$

---

## Simulation Parameters

The current configuration uses:

```python
num_particles = 36
size_of_box = 10
DT = 0.005
TOTAL_TIME = 5
