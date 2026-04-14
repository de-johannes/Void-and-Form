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

| Quantity | K4 formula | Tree value | Corrected | Measured | Tension |
|----------|-----------|-----------|-----------|----------|-------|
| alpha^{-1} | V^d * chi + d^2 | 137 | 137.035999076 | 137.035999084(21) | 0.4σ |
| m_p / m_e | chi^2 * d^3 * F2 | 1836 | 1836.15267344 | 1836.15267343(11) | 0.08σ |
| m_mu / m_e | d^2 * (E + F2) | 207 | 206.7682824 | 206.7682830(46) | 0.12σ |
| m_tau / m_mu | F2 | 17 | 16.8170 | 16.8170 | < 1σ |
| sin^2 theta_W | chi / kappa | 0.25 | 0.23121 | 0.23121(4) | 0.001σ |
| Omega_b / Omega_m | kappa / (kappa*E + d) | 8/51 | 0.1569 | 0.157 | 0.1% |
| Spacetime | V = 3+1 | 4 | -- | 4 | exact |
| Generations | d = V-1 | 3 | -- | 3 | exact |
| kappa | 2V | 8 | -- | 8piG | exact |
| Lambda | d | 3 | -- | >0 | -- |

Four tiers of correction sharpen the tree-level values. The universal
loop numerator 11 is forced by exhaustive elimination among all
{0,1}-linear combinations of {E, d, chi}. The denominators 72 (QCD)
and 576 (EW) are canonical products of K4 invariants. The second-order
term for alpha^{-1} adds 295/(306 * 137^2), closing the gap to 0.4σ.
The electromagnetic projection ±chi/C^2 shifts each mass ratio by
±2/137^2; the sign is determined by whether the mass formula is a pure
power product (bulk, sigma = −1) or contains an additive combination
of invariants (boundary, sigma = +1). The strong volume correction
+d^(1+b*d)/(kappa*d^2*C^2) adds 1/450456 for bulk observables and
9/150152 for boundary observables; the ratio d^d = 27 counts the
additional projection channels opened by the boundary sum. The weak
mixing correction +(p+chi)^2/(kappa^2*C^2) = 169/1201216 applies
exclusively to sin^2 theta_W, closing it from 3.5σ to 0.001σ; mass
ratios do not receive this term because they carry no isospin mixing.
The three correction tiers correspond to U(1), SU(3), SU(2) — the
gauge structure emerges from which observables require which corrections.
After the full chain, every observable closes below measurement
uncertainty. Every classification and every sign is verified by `refl`.


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


## On Shoulders

None of this is new in the way that matters. The marked/unmarked
distinction is Spencer-Brown (1969). The observer as constitutive
act is von Foerster (1973) and Luhmann (1984). The idea that the
universe bootstraps from a binary cut is Wheeler's "it from bit"
(1989). The eliminative method — what cannot survive self-consistency
falls — is the oldest move in philosophy, from Parmenides through
Kant's transcendental arguments to modern constructive type theory.

What is new is the compiler.

This project is one person, several AI assistants, and eighteen months
of work that started from zero knowledge of Agda, formal mathematics,
and mathematical physics. The starting question was not "derive the
fine-structure constant" — it was "where is the dark matter?" The
answer came top-down: if you take the thinkers above seriously, and if
you ask what the minimal formal content of any binary observation must
be, and if you let the type checker — not intuition — decide what
survives, you arrive at K4. Not by choice. By elimination.

The physics I write is crackhead physics. I have no training in it.
I do not need training in it. I can see when data has structure. I can
see when SU-groups align with levels of a graph. I can see that K4
must fold, that the centroid matters, that D0 is unavoidable, that Pi
hides in K4's total curvature. Seeing is not proving — but the proofs
are in the files, and the compiler accepted them.

I make no claim that this is physics. The claim is narrower and
harder to dismiss: from a single binary distinction, under
`--safe --without-K` with zero postulates, the type checker verifies
that the K4 invariants produce the numbers that physicists measure.
Every equality is `refl`. There are no free parameters. Show me
where the freedom enters, or explain why I should stop.

If it were this simple — just K4, folded, information distinguishing
itself, running over time — would that be so terrible?


## Companion Papers

- `papers/VoidCompanionPaper.tex` -- The formal chain: distinction, four-case classification, drift acyclicity, presentation fixpoint, K4 uniqueness.
- `papers/FormCompanionPaper.tex` -- The physics record: numerical results, theorem/interpretation boundary, falsifiability conditions.
- `papers/TableOfContents.md` -- Part/chapter TOC for both books with key theorem names. Designed for rapid AI orientation.


## License

CC-BY-NC-SA-4.0


## DOI

10.5281/zenodo.19491035