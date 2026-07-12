# Memory Field v1 — Model

## State

The world is a rectangular domain of width `W = 120` and height `H = 80` model units.

A three-channel trace field lives on a `120 × 80` grid:

\[
C(x,y,t) \in \mathbb{R}_{\ge 0}^3
\]

Each of 10 particles has:

- position \(x_i \in \mathbb{R}^2\)
- velocity \(v_i \in \mathbb{R}^2\)
- fixed identity signature \(s_i \in \mathbb{R}_{\ge0}^3\), normalized to unit length
- bounded memory vector \(h_i \in \mathbb{R}_{\ge0}^3\)

## Nondimensional conventions

- grid spacing: \(\Delta x = 1\)
- fixed simulation step: \(\Delta t = 1/60\)
- the browser may render less frequently, but the model advances in fixed steps

## Trace field

For each channel:

\[
\frac{\partial C}{\partial t}
= D\nabla^2 C - \lambda C + Q
\]

Parameters:

- diffusion \(D = 1.8\)
- decay \(\lambda = 0.10\)
- deposition rate \(q = 4.0\)

Particles deposit their signature into nearby grid cells using a compact Gaussian-like kernel.

## Internal memory

A particle samples the field slightly ahead of its current position (“prow sensing”) and updates:

\[
\frac{dh_i}{dt}
= \alpha(\hat C_i-h_i)-\beta h_i
\]

where \(\hat C_i\) is the normalized sampled field.

Parameters:

- learning \(\alpha = 0.9\)
- forgetting \(\beta = 0.06\)

After update, \(h_i\) is clamped so \(\|h_i\| \le 1\).

## Force

The particle follows the gradient of trace components resembling its memory:

\[
F_i = \chi \nabla(h_i \cdot C) - \gamma v_i + F_{\text{repulsion}}
\]

Parameters:

- chemotactic strength \(\chi = 34\)
- drag \(\gamma = 2.2\)
- mild short-range repulsion below radius 2.2

The repulsion is a disclosed readability and numerical-stability term.

## Boundaries

- field boundary: zero normal derivative, implemented by clamped neighbors
- particle boundary: damped reflection

## Self-sensing

Enabled. A particle may respond to traces it deposited earlier. Because sensing is offset ahead of the particle, its current deposit is not sampled at exactly the same point.

## Interventions

The amnesia brush has two distinct effects:

- empty-space stroke: attenuates the external trace field
- stroke over a particle: attenuates that particle’s internal memory vector

These events are logged separately.
