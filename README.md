# Void and Form

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20095626.svg)](https://doi.org/10.5281/zenodo.20095626)
[![Release CI (main only)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml/badge.svg)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml)

Start with the companion: [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex) / [PDF](latex/FirstDistinction.pdf).

## What This Repository Is

`Void and Form` is a literate Agda book project investigating whether logic, mathematics, and physical description can be understood as different appearances of a common minimal structure of distinction.

The project should not be described too narrowly and not too grandly.

- Too narrow would be: this repository studies distinction and `K4`.
- Too grand would be: this repository has already proved reality.

The actual question is more interesting. Is there a common origin still beneath logic, mathematics, and physical description themselves?

The wager that opens the route is simple. Stable information presupposes a successfully carried distinction. If that wager fails, the project ends early. If it holds, the inquiry becomes one of reach: how far can the first distinction carry?

This repository slows down at the first formal threshold of that larger route. Before a theory can count, compare, negate, classify, or interpret, it must already be able to hold something apart from something else. The first task is therefore not yet physics and not yet full reconstruction. It is to ask what must be granted inside a formal setting before the claim that there are two positions has any stable force.

The first local formal question is:

```text
A formal system says that there are two positions.
What inside the system licenses that claim as two?
```

The answer pursued here is deliberately austere: a carrier, two displayed positions, a witness that they do not collapse into one, and a witness that no third unaccounted position remains. Only after those obligations are explicit does the checked development proceed.

The repository is organized around three books that keep the levels distinct.

- `The First Distinction` establishes the first formally writable and machine-checkable carrier of stable distinction.
- `Void` develops the formal consequences of that datum and asks how much mathematics can be reconstructed from the same discipline.
- `Form` asks whether parts of that formal ledger admit a physical reading, while keeping interpretation visibly distinct from theorem.

## Read Order

The repository has three primary literate sources.

1. [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex) / [PDF](latex/FirstDistinction.pdf)
   The companion and intended first reading. It introduces the wager, begins from the pressure of origin, determination, physics, and information, and reaches the first formal threshold at which stable distinction can be written exactly.

2. [Void.lagda.tex](Void.lagda.tex) / [PDF](latex/Void.pdf)
   The formal core. It takes the threshold seriously as mathematics and continues the checked route through normal form, endomorphism classification, closure, arithmetic, and later invariant structure.

3. [Form.lagda.tex](Form.lagda.tex) / [PDF](latex/Form.pdf)
   The interpretive volume. It does not re-prove the kernel. It asks how the checked ledger may be read structurally and physically, while keeping those readings visibly distinct from theorem and empirical claim.

If you read only one file first, read [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex).

In compact project form, the route is:

```text
The First Distinction -> Void -> Mathematical Reconstruction -> Physical Reconstruction -> Common-Origin Question
```

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

The same discipline applies to the repository as a whole.

- `The First Distinction` is not the completed theory.
- `Void` is not yet physics.
- `Form` is not automatically empirical success.

The project asks a common-origin question, but each level has to earn its own claims.

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
