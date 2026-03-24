# Langevin Equation

The Langevin equation is a stochastic differential equation widely used
in nonequilibrium statistical physics.

$$
m \ddot{x} = -\gamma \dot{x} - \nabla U(x) + \eta(t)
$$

For overdamped motion, one often writes

$$
\gamma \dot{x} = - \nabla U(x) + \eta(t)
$$ (eq:overdamped-langevin)

Equation {eq}`eq:overdamped-langevin` is the starting point for many
coarse-grained descriptions.

## Noise correlation

A common assumption is

$$
\langle \eta(t)\eta(t') \rangle = 2 \gamma k_B T \delta(t-t').
$$
