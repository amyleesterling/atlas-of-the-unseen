# Numerics

## Explicit diffusion stability

For a 2D five-point Laplacian with equal grid spacing, a sufficient explicit-Euler condition is:

\[
r = D\Delta t/\Delta x^2 \le 1/4
\]

With:

- \(D = 1.8\)
- \(\Delta t = 1/60\)
- \(\Delta x = 1\)

we obtain:

\[
r = 1.8/60 = 0.03
\]

which is comfortably below \(0.25\).

## Determinism

- seeded Mulberry32 RNG is used only during initialization
- simulation uses a fixed timestep
- no random jitter is applied after initialization
- identical seed plus identical intervention sequence should produce identical results within a browser engine

## Known limitations

1. The compact deposition kernel is an approximation, not a continuous Gaussian.
2. Rendering uses tone mapping and interpolation; visible color is not a linear measurement of concentration.
3. Particle-wall reflection and pair repulsion are extra laws, included for boundedness and readability.
4. Full replay of timestamped interventions is not implemented in v1.
5. Browser floating-point behavior is expected to be consistent but not formally bit-identical across all engines.
6. Resolution convergence has not yet been automated; this document does not claim it has.
