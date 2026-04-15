# On the Deductive Closure of a Two-Element Type in Constructive Type Theory

This repository contains a full mechanical formalization (approx. 26,000 lines of literate Agda) investigating the rigid formal structures that emerge unconditionally from a two-element type with decidable equality in Martin-Löf type theory.

The project operates strictly under Agda's `--safe` and `--without-K` flags, relying on no external axioms, postulates, or standard libraries.

## Derivation (`Void.lagda.tex`)
The primary type-theoretic derivation. We ask the type checker what must mechanically follow when the candidate space is constrained only by internal consistency.
- **Initial State:** A minimal two-element type with decidable equality.
- **Classification:** The endomorphism monoid partitions into exactly four pointwise-equivalence classes.
- **Graph Derivation:** Equipped with extensional inequality, this structure uniquely collapses to the complete graph $K_4$.
- **Invariant Record:** The combinatorial and spectral machinery of this derived graph evaluates exactly. An arithmetic record aggregating these invariants is proven to be a propositional singleton containing zero free parameters.

## Verification and Compilation

All deductive steps are purely logical and machine-checked by Agda.

**Requirements:**
- Agda
- No external libraries are required. The project builds upward from primitive equality to ensure complete foundational transparency.

**Checking the Proofs:**
```bash
agda --safe --without-K Void.lagda.tex
```

**Generating the Literate PDF:**
```bash
agda --latex Void.lagda.tex
cd latex
xelatex Void.tex
```
