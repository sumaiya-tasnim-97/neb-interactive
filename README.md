# Nudged Elastic Band (NEB) Explorer

An interactive, single-file visualization of how the **nudged elastic band** method finds minimum-energy paths and saddle points, run live on 2D toy potentials (Müller–Brown, a curved double well, and a two-route surface).

**Open `index.html` in any browser.** No install, no libraries, no build step.

## Features

- gnuplot-style 3D energy surface (rotate / zoom), plus a 2D contour view
- Live NEB, climbing-image NEB, plain elastic band, F⊥-only and −∇V-only modes for comparison
- Per-image vectors: unit tangent τ̂ and the net force resolved into F⊥ and F∥ (tap an image, or show all)
- Target minimum-energy path (pre-computed 41-image CI-NEB) that the band settles into
- Convergence tab (max |F|, max/RMS |F⊥|, max |F∥| vs iteration, log scale) with an adjustable stopping threshold
- Forces-per-image bar chart, energy profile along the band, exact saddle points and minima
- Surface styles: shaded, line mesh only, faint + target MEP; light and dark themes
- Everything in reduced units: length L₀, energy ε, force ε/L₀, spring constant ε/L₀²

## Method

For each interior image *i* with tangent τ̂ᵢ (improved tangent estimate):

```
F⊥   = −∇V(Rᵢ) + (∇V·τ̂) τ̂
F∥ˢ  = k (|Rᵢ₊₁ − Rᵢ| − |Rᵢ − Rᵢ₋₁|) τ̂
F_NEB = F⊥ + F∥ˢ
```

The climbing image uses `F = −∇V + 2(∇V·τ̂)τ̂` with no springs. Images are relaxed with quick-min (or steepest descent) until the largest net force on the band falls below the threshold.

## References

1. H. Jónsson, G. Mills, K. W. Jacobsen, in *Classical and Quantum Dynamics in Condensed Phase Simulations*, World Scientific, 385–404 (1998).
2. G. Mills, H. Jónsson, G. K. Schenter, *Surf. Sci.* **324**, 305 (1995). doi:10.1016/0039-6028(94)00731-4
3. R. Elber, M. Karplus, *Chem. Phys. Lett.* **139**, 375 (1987). doi:10.1016/0009-2614(87)80576-6
4. G. Henkelman, H. Jónsson, *J. Chem. Phys.* **113**, 9978 (2000). doi:10.1063/1.1323224
5. G. Henkelman, B. P. Uberuaga, H. Jónsson, *J. Chem. Phys.* **113**, 9901 (2000). doi:10.1063/1.1329672
6. K. Müller, L. D. Brown, *Theor. Chim. Acta* **53**, 75 (1979). doi:10.1007/BF00547608
7. D. Sheppard, R. Terrell, G. Henkelman, *J. Chem. Phys.* **128**, 134106 (2008). doi:10.1063/1.2841941
8. VTST Tools, Nudged Elastic Band — https://theory.cm.utexas.edu/vtsttools/neb
9. ASE, Nudged elastic band — https://docs.ase-lib.org/ase/neb.html
10. W. E, W. Ren, E. Vanden-Eijnden, *Phys. Rev. B* **66**, 052301 (2002). doi:10.1103/PhysRevB.66.052301

## Author

Designed by **Sumaiya Tasnim** — tasnims@duq.edu — Duquesne University
