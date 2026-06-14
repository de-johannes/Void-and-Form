# Void and Form

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20095626.svg)](https://doi.org/10.5281/zenodo.20095626)
[![Release CI (main only)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml/badge.svg)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml)

Start with the companion: [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex) / [PDF](latex/FirstDistinction.pdf).

## What This Repository Is

`Void and Form` is a literate Agda book project about the first formal burden of distinction.

The opening pressure is simple. If the contrast between something and nothing is to be stated at all, then a distinction is already at work. Before a theory can count, compare, negate, classify, or interpret, it must already be able to hold something apart from something else.

This repository slows down at that hinge. It asks what must be granted inside a formal setting before the claim that there are two positions has any stable force.

The local formal question is:

```text
A formal system says that there are two positions.
What inside the system licenses that claim as two?
```

The answer pursued here is deliberately austere: a carrier, two displayed positions, a witness that they do not collapse into one, and a witness that no third unaccounted position remains. Only after those obligations are explicit does the checked development proceed.

## Read Order

The repository has three primary literate sources.

1. [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex) / [PDF](latex/FirstDistinction.pdf)
   The companion and intended first reading. It begins from the question of origin, moves through determination, physical limit, and information, and reaches the first formal threshold at which stable distinction can be written exactly.

2. [Void.lagda.tex](Void.lagda.tex) / [PDF](latex/Void.pdf)
   The full formal volume. It takes the threshold seriously as mathematics and continues the checked route through normal form, endomorphism classification, closure, arithmetic, and later invariant structure.

3. [Form.lagda.tex](Form.lagda.tex) / [PDF](latex/Form.pdf)
   The interpretive volume. It does not re-prove the kernel. It asks how the checked ledger may be read structurally and physically, while keeping those readings visibly distinct from theorem.

If you read only one file first, read [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex).

## The Formal Hinge

The first exact object is the distinction record:

```agda
record Distinction : Set1 where
  field
    S     : Set
    ℓ     : S
    r     : S
    ℓ≠r   : ℓ ≠ r
    cover : (x : S) -> (x ≡ ℓ) ⊎ (x ≡ r)
```

Its roles are local and strict.

- `S` is the carrier.
- `ℓ` and `r` are the displayed positions.
- `ℓ≠r` prevents collapse.
- `cover` prevents surplus.

This is the first point at which the conditions of stable distinction become fully explicit and machine-checkable.

## What The Kernel Checks

From that record, the project verifies a short checked spine.

- Every distinction has a canonical two-point normal form.
- The endomorphisms of that two-point form fall into exactly four cases.
- Those four cases admit a faithful, no-surplus closure as a four-vertex structure.
- The closure remains accountable to the distinction datum from which it arose.

In compact form, the route is:

```text
Distinction -> Two -> End(Two) -> K4 closure -> Distinction
```

The opening pressure motivates the construction, but it is not itself an Agda theorem. The checked route begins only once the distinction datum has been supplied explicitly.

## How To Read The Claims

The repository separates three kinds of statement.

- Formal statements are Agda terms checked under `--safe --without-K`.
- Structural statements explain why the checked terms belong together as one argument.
- Interpretive statements, concentrated in `Form`, test whether the checked ledger admits a physical reading.

That separation matters. The formal kernel should be inspected as mathematics. The prose should be read as an account of what has been shown, what has not, and where later interpretation begins.

## Verification

The main type checks are:

```sh
agda FirstDistinction.lagda.tex
agda Void.lagda.tex
agda Form.lagda.tex
```

To regenerate a PDF, run `agda --latex` on the relevant literate source and then run XeLaTeX twice in [latex/](latex/) on the generated `.tex` file.

Example:

```sh
agda --latex FirstDistinction.lagda.tex
cd latex
xelatex -interaction=nonstopmode FirstDistinction.tex
xelatex -interaction=nonstopmode FirstDistinction.tex
```

## Files

- [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex) / [PDF](latex/FirstDistinction.pdf): companion and first reading.
- [Void.lagda.tex](Void.lagda.tex) / [PDF](latex/Void.pdf): full formal volume.
- [Form.lagda.tex](Form.lagda.tex) / [PDF](latex/Form.pdf): interpretive volume.
- [latex/](latex/): generated LaTeX and PDF output.
- [LICENSE](LICENSE): license terms.

## Author and Method

The author has no institutional affiliation, no formal background in mathematics or physics, and no prior training in type theory or formal verification. The development was built over eighteen months with the assistance of large language models.

The Agda type checker under `--safe --without-K` is the formal judge of the kernel. It does not check credentials. It checks proofs. The relevant question is therefore whether the formal claims type-check under the stated options, whether the prose reports them faithfully, and whether the interpretive layers keep their stated status.

## Citation

Use the DOI shown above and cite specific formal claims by file and commit hash. Cite `Form` separately from `Void`, because its physical identifications are interpretive readings over the formal ledger.
