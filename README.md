# Molecular Physics Lab

An interactive, single-file web laboratory for molecular physics. It starts from the simplest diatomic models and builds up to quantum chemistry and many-body simulation. Every result is compared with NIST reference data or exact theory.

**Live:** https://obayrak.github.io/obayrak/atom-and-molecule-lab/molecular-physics-lab/
**Part of:** [Atom and Molecule Lab](https://obayrak.github.io/obayrak/atom-and-molecule-lab/) · [Interactive Physics Laboratories](https://obayrak.github.io/obayrak/)

## What's inside

| Section | Topics |
|---|---|
| **1 · Rigid rotor & harmonic oscillator** | Rotational constants, level populations, partition functions |
| **2 · Anharmonicity & Morse** | Morse oscillator, Dunham expansion, Birge–Sponer, RKR potential inversion |
| **3 · Numerical Schrödinger** | Finite-difference (Sturm bisection) and Numerov shooting solvers |
| **4 · Rovibrational spectra** | P/Q/R branches, intensities, Raman, isotopologues, CO line fit to NIST |
| **5 · Electronic structure** | H₂⁺ LCAO, H₂ Hartree–Fock + CI, I₂ B←X Franck–Condon band |
| **6 · Polyatomics & Hückel** | Normal modes, Hückel π theory, H₂O asymmetric top with Watson's A-reduced Hamiltonian |
| **7 · Molecular dynamics & thermo** | Argon MD (velocity Verlet, cell lists), virial coefficients, thermodynamics |
| **8 · Phases, transport, quantum** | Maxwell construction, Gibbs-ensemble and NpT Monte Carlo, Axilrod–Teller three-body forces, Widom chemical potential, Green–Kubo transport, 2D Ising model (Metropolis/Wolff, finite-size scaling) |
| **Q1 · Hartree–Fock SCF** | RHF/UHF, MP2/UMP2 in STO-3G, 6-31G and 6-31G* for 13 molecules; dipoles, Mulliken charges, ionisation energies (Koopmans, ΔSCF, ΔMP2) |
| **Q2 · Excited states & curves** | CIS, full CI (2 electrons), potential curves, diffusion Monte Carlo with a Jastrow factor |
| **Q3 · Vibrations & IR** | Geometry optimisation, vibrational-subspace Hessian, IR intensities, scale factors |
| **Theory & methods** | Every equation, algorithm and approximation used, with implementation details, validation and limits |
| **Validation** | Error dashboard, 61 built-in self-tests, model report, performance benchmarks |

## How results are graded

Each table compares a computed value with a reference: green ✓ means under 1 % error, amber ! means 1–5 %, red ✕ means over 5 %. A **⚠** marks a reference value that was not taken from a fetched NIST table (for example, a literature value entered from memory). Treat these as provisional and verify them before relying on them.

## Technical notes

- **One self-contained HTML file** (~550 KB). There is no build step or server. Plotly, Three.js and MathJax load from public CDNs.
- **WebAssembly kernels** for molecular-dynamics forces and two-electron integrals (written in C, embedded as base64), with JavaScript fallbacks.
- **Parallel Web Workers** for Hessians, Monte Carlo replicas and parameter scans. You choose the thread count in the toolbar.
- **IndexedDB cache** for expensive results, and seeded random numbers, so results are reproducible. Sessions can be exported and imported as JSON.
- Works in current Chrome, Edge, Firefox and Safari. Heavy runs, such as Gibbs-ensemble MC or MP2 Hessians, benefit from more CPU cores.

## Running locally

Open `molecular-physics-lab.html` directly in a browser, or serve the folder:

```bash
python -m http.server
# then visit http://localhost:8000/molecular-physics-lab.html
```

`index.html` is the site wrapper (navigation, breadcrumb, full-screen frame) used on the website.

## Reference data

- NIST Chemistry WebBook: diatomic constants, ionisation energies, thermochemistry (Shomate), argon fluid properties
- NIST CCCBDB: polyatomic geometries, frequencies, dipole moments
- NIST Triatomic Spectral Database: H₂O rotational and centrifugal-distortion constants
- Exact results where available (Onsager/Yang for the Ising model, exact He and H₂ energies)

NIST data are used for comparison and teaching. See the in-app **NIST reference data** page for sources and links.

## License

MIT. See [LICENSE](LICENSE).

© 2026 Prof. Dr. Orhan Bayrak · Department of Physics, Akdeniz University, Antalya
