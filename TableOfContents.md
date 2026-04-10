# Table of Contents — Void and Form

This file gives an AI (or any first reader) an immediate orientation.
Both books compile under `agda --safe --without-K` with zero postulates,
no standard library, and no imports except `Agda.Primitive` (Void) and
`open import Void` (Form).

The core claim: a single binary distinction forces `K4` as the unique surviving
structure. Void proves this by elimination. Form identifies the forced invariants
with measured physical constants.

Every theorem listed below is machine-verified. The full proofs are in the
literate Agda source files. Both PDFs are compiled from the same source.


---

## Void.lagda.tex  (~25,000 lines, module `Void`)

Six parts, 55 chapters. Eliminative derivation from `Distinction` to `K4`,
arithmetic, spectral theory, and singleton invariant record.

---

### Preface

- Introduction — the eliminative method and what "forced" means

---

### Part I — Foundation

1. **The Foundation of Necessity** — `Distinction` type, `Two`, propositional
   equality, `EndoCase` (constL, constR, id, dual)
2. **Non-Vacuity** — three independent witnesses that `Distinction` is inhabited
3. **Elimination and Classification** — four-case endomorphism census, K3 cannot
   close, K4 forces itself
4. **Two Normal Form** — every distinction is isomorphic to `Two`;
   `two-normal-form` is the uniqueness theorem

---

### Part II — Drift and Reachability

5. **Drift** — the primordial step from one side of a distinction to the other
6. **Non-Collapse of Drift** — drift cannot be undone; two sides stay distinct
7. **Cross-Stage Comparison** — comparing states across drift steps
8. **Drift Reachability** — from any state, all states are reachable
9. **Drift Acyclicity** — no drift sequence returns to its start; irreversibility

---

### Part III — Heteromorphisms and Presentation

10. **Heteromorphisms** — maps between distinctions; inter-distinction structure
11. **Indexed Ledger** — tick-indexed states; the drift ledger
12. **Presentation of Reachability** — canonical form; presentation uniqueness

---

### Part IV — Observables and Fixpoint

13. **Admissible Reach Observables** — what can be measured without breaking structure
14. **Ranking Principle** — admissible observables are totally ordered
15. **Presentation Fixpoint** — the unique fixpoint of the presentation map
16. **Graph Presentation** — K4 appears as the unique presentation fixpoint
17. **The K4 Invariant Record** — 17-field record; `K4Record-singleton` proves
    exactly one inhabitant exists

---

### Part V — Derived Arithmetic

18. **Arithmetic Infrastructure** — `ℕ` from vertex counting; fuel-bounded gcd, div
19. **Forced Additive Laws** — addition on `ℕ`, `ℤ` forced by K4 structure
20. **Multiplicative Structure and Integer Order** — `ℤ` multiplication, ordering
21. **K4 Neighborhood and Laplacian** — `adjacent`, `L₄`, spectrum `{0,4,4,4}`
22. **Simplex Invariants and Natural Multiplication Laws** — V, E, F, χ, κ fixed
23. **Integer Multiplication Laws** — ring axioms for `ℤ`
24. **Integer Order Laws** — transitivity, antisymmetry, totality
25. **Absolute Value Laws** — `|·|` on `ℤ`; triangle inequality
26. **Additive Monotonicity and Positive Natural Laws**
27. **Rational Numbers and Measurement** — `ℚ = ℤ × ℕ⁺`; canonical form
28. **Rational Setoid and Order Laws** — `≃ℚ`, `≤ℚ`, density
29. **Laplacian as Finite-Index Operator** — `L₄` as a bounded ℚ-linear map
30. **Measurement Symmetries** — `measurement-outcome-distinction` (second route to D0)
31. **Rational Addition and Multiplication Laws** — field axioms for `ℚ`
32. **Coupled K4 Laplacian** — `L₈` on the product graph; coupled spectrum
33. **Triple K4 Laplacian** — `L₁₂`; spectral action on the triple product
34. **Additive Order Laws for ≤ℚ**
35. **K₁₂ Iteration and Word Algebra** — free monoid over K₁₂ operators
36. **Rational Multiplication and ε-Splitting**
37. **Rational Distance Laws** — `distℚ`; triangle inequality for `ℚ`
38. **Archimedean Scaling** — every rational is within ε of a scaled natural
39. **ℤ-Span of K₁₂ Operators**
40. **Forced Spectral Action of the (I,J)-Span**
41. **Reals as Forced Cauchy Closure over ℚ** — `ℝ` forced; Cauchy completeness

---

### Part VI — Derived Constants of K4

42. **Natural-Number Division Infrastructure** — exact divisibility; needed for
    combinatorial counts
43. **K4 Forced Constants Layer** — V=4, E=6, F=4, χ=2, κ=8, `C=137` all evaluate
    to `refl`
44. **K4 Representation Theory** — uniqueness of the invariant record;
    `K4Record-singleton`; Hedberg + record eta
45. **K4 Vertex Permutations** — `Aut(K4) ≅ S4`; 2-transitivity; `edge-map`
46. **Forced Propagation** — every K4-invariant edge weight equals 1; sandwich proof
47. **Forced Minimal Action** — every K4-invariant face weight equals 1
48. **Forced Vertex Weight** — every K4-invariant vertex weight equals 1
49. **Scale Closure** — `NormalizedScaleChoice`; `measurement-outcome-distinction`;
    `record-presupposes-distinction`; loop D0 → K4 → record → D0 closes
50. **Conclusion** — residue: the specific shape of what cannot be absent

---

## Form.lagda.tex  (~6,300 lines, module `Form`)

Seven parts, 29 chapters. Identification layer. Opens `Void`; no new axioms.

---

### Part I — The Stage

1. **The Import** — `open import Void`; the single dependency
2. **The Vocabulary** — aliases, notation, physical constants as named `ℕ` values
3. **The Identity Ledger** — `VoidRef` cross-references; what Form inherits

---

### Part II — Geometry and Cosmos

4. **The Geometry of K4** — tetrahedral geometry; `ℓ = χ = 2`; coupling `δ = d/χ`
5. **The Cosmological Constant** — `Λ = d = 3`; five consistency routes, all `refl`
6. **The Density of the Universe** — `Ω_m = V/(2πχ) ≈ 0.3183`; K3/K5 eliminated
7. **The Spectral Index** — `n_s` from `(E−χ)/E`; `α⁻¹ = 137` locked; 136 and 138
   type-empty

---

### Part III — Loops and Corrections

8. **Mass and the Loop Numerator** — `m_p/m_e = χ²·d³·F₂ = 1836`; loop numerator
   `E+d+χ = 11` as unique survivor of exhaustive filter
9. **The Correction Chain** — `ArithmeticSignature`; five invariants drive all corrections
10. **Exclusivity and Doubling** — K3 and K5 eliminated by five pillars simultaneously
11. **Forces from the Graph** — Wilson loops, Regge action, geodesics, all from K4 faces
12. **The Dark Universe** — `E²+κ² = 100`; Pythagorean cosmic energy budget
13. **Quantum Mechanics from the Graph** — Born rule `1/V`; adjacency symmetry
14. **Horizons and Information** — Bekenstein-Hawking `1/4 = 1/V`; no information loss
    (K4 is complete: no disconnected interior)
15. **The Topological Brake** — K3 fails closure; K5 over-determined; K4 terminates

---

### Part IV — Spacetime

16. **The Metric Signature** — `η = diag(−1,+1,+1,+1)`; trace `= χ = 2`;
    `g_μν = d·η_μν`
17. **Curvature and Einstein's Equations** — `R = 3λ₄ = 12`; all 10 components `refl`;
    Christoffel, Riemann, Weyl tensors vanish

---

### Part V — Symmetry and Matter

18. **Pauli Matrices from K4** — three vertex pairings = three Pauli matrices;
    Klein four-group; `g = χ = 2`; `g≠1` and `g≠3` type-empty
19. **The Gauge Group** — `U(1)×SU(2)×SU(3)` from V, χ, d; total 12 bosons `= V×d`
20. **Fermions and Generations** — 3 generations `= d`; 24 fermion types `= |S4|`
21. **QFT Loop Structure** — 4 triangles + 3 squares = 7 cycles; UV cutoff = 1 Planck
    length; lattice is its own regulator

---

### Part VI — Forces and Confinement

22. **Gauge Fields and Holonomy** — discrete Stokes' theorem; pure-gauge holonomies
    vanish, all four triangles `refl`
23. **Confinement** — `QuarkIsolation` is an uninhabited type; string tension `= V > 0`
    by construction
24. **Paths and Geodesics** — path integral finite and exact; Gauss-Bonnet `4π = 4π`
    by `refl`; `OntologicalNecessity` record

---

### Part VII — The Full Picture

25. **The Discrete-Continuum Bridge** — number tower `ℕ→ℤ→ℚ→ℝ→ℂ` from K4 demands;
    where the formal chain ends and interpretation begins
26. **Perturbation Theory and Renormalization** — `b₀(QCD) = 9 > 0`; asymptotic
    freedom is a type-checked inequality
27. **String Theory Connection** — `d_bos = V·E+χ = 26`; `d_super = V+E = 10`;
    `d_M = E+d+χ = 11`; all `refl`
28. **Unification** — `StandardModelFromK4`: 31-field record; all fields `refl`;
    causality from propagation factor `= 1`
29. **The Standard Model from K4** — master record; the compiler's acceptance
    is the proof

---

## Key theorem names (for search)

**In Void:**
`Two-distinction`, `two-normal-form`, `K4Record`, `K4Record-singleton`,
`measurement-outcome-distinction`, `NormalizedScaleChoice`,
`record-presupposes-distinction`, `K4-is-inevitable`,
`law13-1-presentation-iso`, `invariant-uniform-edges`

**In Form:**
`theorem-alpha-integer`, `theorem-proton-mass`, `theorem-neutron-mass`,
`theorem-QM-SM-unification`, `theorem-ontological-necessity`,
`theorem-standard-model`, `theorem-string-connection`,
`theorem-confinement`, `theorem-gauss-bonnet`, `theorem-causality-δ`
