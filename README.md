# Void and Form

The starting point is deliberately minimal: a type with two provably unequal,
covering elements. From this single distinction, the complete graph K4 is the
unique surviving structure after exhaustive elimination. This repository
contains the machine-verified derivation and its physical identification layer.

Both files compile under `agda --safe --without-K` with zero postulates
and no standard library.


## PDFs

| Document | Link |
|----------|------|
| Void (eliminative derivation) | [latex/Void.pdf](https://github.com/de-johannes/Void-and-Form/blob/main/latex/Void.pdf) |
| Form (identification layer) | [latex/Form.pdf](https://github.com/de-johannes/Void-and-Form/blob/main/latex/Form.pdf) |
| Companion paper: Void | [papers/VoidCompanionPaper.pdf](https://github.com/de-johannes/Void-and-Form/blob/main/papers/VoidCompanionPaper.pdf) |
| Companion paper: Form | [papers/FormCompanionPaper.pdf](https://github.com/de-johannes/Void-and-Form/blob/main/papers/FormCompanionPaper.pdf) |

All PDFs are compiled from the literate Agda source (agda --latex + xelatex).
If the compiler accepted the source, every statement in the PDFs is verified.


## Files

| File | Module | Lines | Role |
|------|--------|------:|------|
| `Void.lagda.tex` | `Void` | ~25,000 | Eliminative derivation: distinction to K4, arithmetic, spectral theory, singleton record |
| `Form.lagda.tex` | `Form` | ~6,200 | Identification layer: maps K4 invariants to measured physical constants (`open import Void`) |
| `papers/VoidCompanionPaper.tex` | -- | ~530 | Companion paper: the formal chain from distinction to K4 |
| `papers/FormCompanionPaper.tex` | -- | ~530 | Companion paper: the physics record and numerical results |
| `TableOfContents.md` | -- | ~180 | Part/chapter TOC for both books; key theorem index for AI navigation |

Form depends on Void. Compile Void first.


## Architecture

```
Distinction (D0)
    |
    v  [elimination]
K4  (V=4, E=6, d=3, chi=2, kappa=8)
    |
    v  [singleton proof]
K4Record  (unique invariant record)
    |
    v  [open import Void]
Form  (identification with measured constants)
```

Void is self-contained. It derives K4, builds the natural numbers, integers,
rationals, and reals from the graph's structure, computes the Laplacian
spectrum {0,4,4,4}, and proves the invariant record is a singleton. No
number system is imported; every algebraic law is a theorem.

Form imports Void's definitions and identifies the forced invariants with
physical quantities. No new axiom enters. Every number that appears in
Form was already forced in Void.


## Five Proofs

1. **Two-distinction** -- The minimal distinction type `data Two = L | R` is
   constructed with zero assumptions. Coverage and separation are verified.
   Every other distinction is isomorphic to this one (`two-normal-form`).

2. **Four-case endomorphism classification** -- Every endomorphism of a
   distinction is one of exactly four cases: constL, constR, id, dual. The
   classification is sound, injective, and unique. All six pairs are provably
   distinct. This gives K4.

3. **K4 presentation uniqueness** (`law13-1-presentation-iso`) -- Any
   alternative vertex type equipped with the same interface produces a graph
   isomorphic to the canonical K4. No presentation freedom survives.

4. **K4Record singleton** (`K4Record-singleton`) -- The 17-field invariant
   record of K4 has exactly one inhabitant. Proved via Hedberg's theorem
   (decidable equality on N implies UIP) and record eta.

5. **Loop closure** -- The invariant record presupposes D0. The chain
   D0 -> K4 -> record -> D0 is a closed constraint, not an open arrow.
   `K4-is-inevitable : Distinction → K4Record` (forward) and
   `record-presupposes-distinction : K4Record → Distinction` (backward)
   establish the equivalence `Distinction ⟺ K4Record`.


## Projections from K4 (Form)

The following values arise internally as exact rational expressions from K4's
combinatorial invariants. Every equality is a `refl` closed by the type
checker. No value was fitted. Their comparison to measured constants is
external to the proof — the computation is theorem, the identification
is interpretation.

| Quantity | K4 formula | Tree value | Corrected | Measured | Error |
|----------|-----------|-----------|-----------|----------|-------|
| alpha^{-1} | V^d * chi + d^2 | 137 | 137.0359 | 137.0360 | 3.8e-7 |
| m_p / m_e | F2 * E^2 * d | 1836 | 1836.1528 | 1836.1527 | 6e-7 |
| m_mu / m_e | d^2 * (E + F2) | 207 | 206.7681 | 206.7683 | 8e-7 |
| m_tau / m_mu | F2 | 17 | 16.8170 | 16.8170 | 1.9e-6 |
| sin^2 theta_W | chi / kappa | 0.25 | 0.2309 | 0.2312 | 0.14% |
| Omega_b / Omega_m | kappa / (kappa*E + d) | 8/51 | 0.1569 | 0.157 | 0.1% |
| Spacetime | V = 3+1 | 4 | -- | 4 | exact |
| Generations | d = V-1 | 3 | -- | 3 | exact |
| kappa | 2V | 8 | -- | 8piG | exact |
| Lambda | d | 3 | -- | >0 | -- |

Corrections use the universal loop numerator 11, forced by exhaustive
elimination among all {0,1}-linear combinations of {E, d, chi}. The
denominators 72 (QCD) and 576 (EW) are canonical products of K4 invariants.


## Verification

```
git clone https://github.com/de-johannes/Void-and-Form
cd Void-and-Form
agda --safe --without-K Void.lagda.tex
agda --safe --without-K Form.lagda.tex
```

Requires Agda >= 2.6.4. No dependencies beyond `Agda.Primitive`.

If both files type-check, every theorem stated in this repository,
in both companion papers, and in this README is verified.


## Formal Environment

- Language: Agda
- Flags: `--safe --without-K`
- Postulates: 0
- Standard library: none
- Proof methods: `refl`, absurdity witnesses (lambda ()), ordering chains
- All infrastructure (equality, negation, decidability, N, Z, Q, R) built from scratch in Void


## Companion Papers

- `papers/VoidCompanionPaper.tex` -- The formal chain: distinction, four-case classification, drift acyclicity, presentation fixpoint, K4 uniqueness.
- `papers/FormCompanionPaper.tex` -- The physics record: numerical results, theorem/interpretation boundary, falsifiability conditions.
- `papers/TableOfContents.md` -- Part/chapter TOC for both books with key theorem names. Designed for rapid AI orientation.


## License

CC-BY-NC-SA-4.0


## DOI

10.5281/zenodo.19491035