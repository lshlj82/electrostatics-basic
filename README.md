# Electric charge, field and potential, step by step

An interactive web demo for general physics, based on **Prof. Sang Hoon Lee**'s general physics lecture notes. It starts with point charges (Coulomb's law, the electric field, the electric potential, and the dipole) and builds up to continuous charge on a **ring** and a **disk**.

For the ring and disk, it shows two ways to find the electric field and how the field and the potential are related:

- **Route A, add vectors.** Sum the contributions dE from each piece of charge with Coulomb's law. Symmetry cancels the sideways parts.
- **Route B, add scalars.** Sum the potentials dV, then differentiate: **E = −∇V**.

On the axis both routes give the same closed-form result. Off the axis the sideways parts no longer cancel, so the vector route gets hard while the potential is still a plain scalar sum.

The demo is available in English (`index.html`) and Korean (`index_ko.html`, 한국어). Each is a single self-contained HTML file with no build step and no dependencies, and each links to the other.

<!-- Live demo: add your GitHub Pages link here, e.g. https://<user>.github.io/<repo>/ -->

## Features

The page has five parts.

**1. Charges, forces and fields**
- Short summaries of electric charge (quantization, conservation, current), Coulomb's law, gravity (including F = mg near Earth's surface), the shell theorems, the electric field and the electric potential.
- Coulomb's law next to gravity: pick a pair (electron and proton, two protons, two electrons, two charged 1 kg balls, Earth and Moon) and compare the directions of the two forces and their sizes on a log scale. The ratio F_electric/F_gravity does not depend on distance, since both forces fall off as 1/r².
- A point-charge playground: drag up to six charges and a test charge q₀.
  - Each charge shows the Coulomb force from every other charge and their vector sum (superposition). For two charges, the readout confirms Newton's third law.
  - Field lines start on positive charges and end on negative ones.
  - Optional potential shading with equipotential curves.
  - The test charge reports E, the force q₀E and V in SI units.

**2. The electric dipole**
- The exact on-axis field compared with the dipole approximation p/(2πε₀z³) and with a single charge, on a log–log plot (slopes −3 and −2).
- Readouts of the approximation error and of the on-axis potential.

**3–5. Ring and disk, test charges, derivations**

**3D view of the summation**
- Shows point P, one charge piece dq, the piece opposite it, and their dE vectors split into axial and sideways parts.
- **Play the sum** integrates around the ring, or ring by ring outward for the disk, while the running total of E is drawn live.
- P can be moved off the axis to show that the sideways parts stop cancelling.
- Drag to rotate.

**Readouts**
- Partial sums of V, E_z, E_x and E_y as the integration progresses.
- Exact V, E_z and E_ρ at P, checked live against numerical −∂V/∂z and −∂V/∂ρ.

**Slope and area plots**
- V and the field component along a vertical or horizontal line through P.
- The tangent to V at P has slope −E_s.
- The shaded area under E_s from P out to infinity equals V(P).
- Optional limit cases: a point charge far away, and the infinite plane σ/(2ε₀) for a large disk.

**Cross-section map (x–z plane)**
- Potential shading, equipotential curves, and E = −∇V arrows.
- Hover to read V and |E| and to see that E is perpendicular to the equipotentials.
- For the ring, the saddle at the center is drawn explicitly.

**Test charges in 3D**
- Release a test charge of either sign, free in 3D or confined to the plane or the axis.
- Nudge it off the center or release it from any launch point.
- A status line reports how the run ended (escaped, hit the ring, landed on the disk, or stayed bounded), with the measured oscillation period next to the small-oscillation prediction.
- Illustrates the saddle at the ring's center and Earnshaw's theorem: no sign of Q is stably trapped there.

**Derivations**
- Both routes written out step by step for the ring and the disk.
- Limiting cases, the general off-axis ring formulas, and the saddle expansion near the center.

## Physics

With k_e = 1/(4πε₀), on the axis (z ≥ 0 for the disk):

| | Potential V(z) | Field E_z(z) |
|---|---|---|
| Ring (charge q, radius R) | k_e q / √(z² + R²) | k_e q z / (z² + R²)^(3/2) |
| Disk (surface density σ, radius R) | (σ / 2ε₀) (√(z² + R²) − z) | (σ / 2ε₀) (1 − z / √(z² + R²)) |

Off the axis, the ring's V, E_z and E_ρ are evaluated from complete elliptic integrals K(k) and E(k), with k² = 4Rρ / ((R + ρ)² + z²). The disk off the axis is built as a sum of exact rings.

Near the ring's center, V ≈ (k_e q / R)(1 + (x² + y² − 2z²) / 4R²). This is a saddle point, which gives small-oscillation frequencies ω_z² = 2ω_ρ² for the constrained motions.

## Units and numerics

- The playground in part 1 uses SI units (charges in μC, distances in cm). The dipole plot uses units of k q/d². From part 3 on, the demo uses k_e = 1. The ring has q = 1. The disk has σ/(2ε₀) = 1, so its total charge q = σπR² grows with R.
- The complete elliptic integrals are computed with the arithmetic–geometric mean.
- The disk is summed from 400 rings for the readouts, 160 for the plots and 64 for the map.
- Test-charge motion uses a fourth-order Runge–Kutta integrator with adaptive steps near the charges. Mass and |Q| are both 1.
- The off-axis formulas were checked against brute-force summation (agreement to about 6 digits) and against numerical gradients. Angular momentum about the axis is conserved to about 10⁻⁹ in the trajectories.

## Running it

Open `index.html` in a browser, or serve the folder with any static server:

```bash
python3 -m http.server
```

To publish on GitHub Pages, push the repository and enable Pages for the branch that contains `index.html` (Settings → Pages).

The page uses MathML for equations, which current Chrome, Edge, Firefox and Safari support natively. Fonts load from Google Fonts and fall back to system fonts offline. The page adapts to light and dark mode; a sun/moon button in the top-right corner switches by hand, and the choice is remembered across pages.

## Files

```
index.html      the complete demo in English (HTML, CSS and JavaScript in one file)
index_ko.html   the same demo in Korean
README.md       this file
```

## Credits

- Created by **Claude Opus 5.5**.
- Based on **Prof. Sang Hoon Lee**'s general physics lecture notes on Coulomb's law, the electric field, and the electric field and potential of point charges, dipoles and continuous charge distributions.
- Also based on the note *The Electric Potential and Field of a Uniformly Charged Ring and Spherical Shell: Why Equal Potentials Do Not Imply Equal Fields*, inspired by a lecture by Sang Hoon Lee.

## License

No license has been chosen yet. Add a `LICENSE` file (for example MIT or CC BY 4.0) to state how others may use this work.
