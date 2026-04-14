# Void and Form

## The Cut

Draw a distinction.

That is the entire input. Not a field, not a particle, not a
spacetime — a single binary separation. This side, not that side.
Spencer-Brown called it the *mark* (1969). Wheeler called it
*it from bit* (1989). In constructive type theory, it is a type
with two provably unequal, exhaustively covering elements:

```agda
data Two : Set where
  L : Two
  R : Two
```

No axioms. No postulates. No standard library. One distinction,
and the question: what does self-consistency force from here?


## What Survives

The answer is not chosen. It is what remains after everything
unstable has been eliminated.

A distinction has endomorphisms — maps from itself to itself.
There are exactly four: two constants, the identity, and the swap.
That classification is exhaustive, sound, and unique. Four vertices,
six edges between them. The complete graph K4 — a tetrahedron.

No other graph survives. The derivation is a chain of five proofs:

1. **Two-distinction** — The minimal distinction `L | R` is
   constructed with zero assumptions. Every other distinction is
   isomorphic to it.
2. **Four-case classification** — Every endomorphism falls into
   exactly one of four cases. All six pairs are provably distinct.
   This gives four vertices and six edges: K4.
3. **Presentation uniqueness** — Any alternative vertex type with
   the same interface produces a graph isomorphic to the canonical
   K4. No freedom survives.
4. **Singleton record** — The 17-field invariant record of K4 has
   exactly one inhabitant. One graph, one set of numbers.
5. **Loop closure** — The record presupposes the distinction it
   was derived from. The chain D0 → K4 → record → D0 is closed.

Each step is machine-verified in Agda under `--safe --without-K`.
The compiler is the only arbiter.


## What It Carries

K4 has six combinatorial invariants. They are not parameters — they
are theorems of the graph:

| Invariant | Definition | Value |
|-----------|-----------|------:|
| V (vertices) | \|K4\| | 4 |
| E (edges) | V(V−1)/2 | 6 |
| d (degree) | V − 1 | 3 |
| χ (Euler) | V + F − E | 2 |
| κ (coupling) | 2V | 8 |
| C (evaluation) | V^d · χ + d² | 137 |

From these six numbers, exact rational expressions produce every
value in the table below. No value was fitted. The computation is
theorem; the identification with measured constants is interpretation.

| Quantity | K4 formula | Tree | Corrected | Measured | Tension |
|----------|-----------|-----:|----------:|----------|--------:|
| α⁻¹ | V^d·χ + d² | 137 | 137.035999076 | 137.035999084(21) | 0.4σ |
| m_p/m_e | χ²·d³·F₂ | 1836 | 1836.15267344 | 1836.15267343(11) | 0.08σ |
| m_μ/m_e | d²·(E+F₂) | 207 | 206.7682824 | 206.7682830(46) | 0.12σ |
| m_τ/m_μ | F₂ | 17 | 16.8170 | 16.8170 | < 1σ |
| sin²θ_W | χ/κ | 0.25 | 0.23121 | 0.23121(4) | 0.001σ |
| Ω_b/Ω_m | κ/(κE+d) | 8/51 | 0.1569 | 0.157 | 0.1% |

Four correction tiers sharpen the tree values. The loop numerator
11 = E + d + χ is forced by exhaustive elimination. The denominators
72 and 576 are canonical products of K4 invariants. The sign of each
correction is determined by the d-content of its numerator (Void:
`SignForcing`). After the full chain, every observable closes below
measurement uncertainty. Every classification and every sign is
verified by `refl`.


## The Line

Everything to the left of this line is `refl`. Everything to the
right is physics.

| | Formal (Void) | Empirical |
|---|---|---|
| **Content** | K4 invariants produce these numbers | These numbers match what labs measure |
| **Arbiter** | Agda compiler | Experiment |
| **Free parameters** | Zero | Auxiliary hypotheses adjustable |
| **Theory-ladenness** | None | Every measurement is interpreted |

The formal derivation cannot tell you whether 137 has anything to do
with electromagnetism. The empirical measurement cannot tell you
whether its value is free or forced. These are different modes of
knowledge, and neither subsumes the other.

This repository does not claim to be physics. It claims that K4's
invariants produce the numbers that physicists measure, that
every equality is `refl`, and that no free parameter enters.

Show me where the freedom enters, or explain why the numbers match.


## On Shoulders

None of this is new in the way that matters. The marked/unmarked
distinction is Spencer-Brown (1969). The observer as constitutive
act is von Foerster (1973) and Luhmann (1984). The universe
bootstrapping from a binary cut is Wheeler (1989). The eliminative
method — what cannot survive self-consistency falls — is the oldest
move in philosophy, from Parmenides through Kant to modern
constructive type theory.

Standing on shoulders — or, as it turned out, inheriting a pile
of debts. What is new is only the tool: a compiler that does not
negotiate.

This project began eighteen months ago with a question about dark
matter. That failed — as thoroughly as a question can fail. But
failure has a direction: it points away from what does not work.
Away from particles. Away from models. Toward the thing every model
already presupposes but never examines. Strip away dark matter,
strip away fields, strip away spacetime. What remains? A cut. This
against that. Marked against unmarked.

The author has no training in formal mathematics or mathematical
physics. What the author has is pattern recognition — the ability
to see structure in data, to see when group ranks align with graph
levels, when a tetrahedron must fold. Seeing is not proving. But
the proofs are in the files, written with AI assistants and verified
by a compiler that does not care who wrote them.

Working with AI on an open-ended problem is dangerous. A stochastic
machine that sounds authoritative is worse than ignorance — it is
confident ignorance. The antidote is constraint. Force the machine
onto a deterministic playing field: not simulation but proof, not
exploration but elimination, not Python but Agda. The narrower the
rules, the more honest the output. Treat AI as a proof assistant,
never as an oracle.

If it were this simple — just K4, folded, information distinguishing
itself, running over time — would that be so terrible?


## Verification

```
git clone https://github.com/de-johannes/Void-and-Form
cd Void-and-Form
agda --safe --without-K Void.lagda.tex
agda --safe --without-K Form.lagda.tex
```

Requires Agda ≥ 2.6.4. No dependencies beyond `Agda.Primitive`.
If both files type-check, every theorem in this repository is verified.

- Language: Agda
- Flags: `--safe --without-K`
- Postulates: 0
- Standard library: none
- Proof methods: `refl`, absurdity witnesses `(λ ())`, ordering chains
- All infrastructure (N, Z, Q, R) built from scratch in Void


## Files

| File | Lines | Role |
|------|------:|------|
| `Void.lagda.tex` | ~26,000 | Eliminative derivation: distinction → K4 → arithmetic → spectral theory → singleton record |
| `Form.lagda.tex` | ~9,000 | Identification layer: maps K4 invariants to measured constants (`open import Void`) |
| `papers/VoidCompanionPaper.tex` | ~530 | Companion paper: the formal chain |
| `papers/FormCompanionPaper.tex` | ~530 | Companion paper: the physics record |
| `papers/TableOfContents.md` | ~180 | Chapter index for AI navigation |

```
Distinction (D0)
    │
    ▼  [elimination]
K4  (V=4, E=6, d=3, χ=2, κ=8)
    │
    ▼  [singleton proof]
K4Record  (unique invariant record)
    │
    ▼  [open import Void]
Form  (identification with measured constants)
```

Form depends on Void. Compile Void first.

| Document | Link |
|----------|------|
| Void (539 pages) | [latex/Void.pdf](https://github.com/de-johannes/Void-and-Form/blob/main/latex/Void.pdf) |
| Form (202 pages) | [latex/Form.pdf](https://github.com/de-johannes/Void-and-Form/blob/main/latex/Form.pdf) |
| Companion: Void | [papers/VoidCompanionPaper.pdf](https://github.com/de-johannes/Void-and-Form/blob/main/papers/VoidCompanionPaper.pdf) |
| Companion: Form | [papers/FormCompanionPaper.pdf](https://github.com/de-johannes/Void-and-Form/blob/main/papers/FormCompanionPaper.pdf) |


## License

CC-BY-NC-SA-4.0


## DOI

10.5281/zenodo.19491035