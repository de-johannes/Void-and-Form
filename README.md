# Void and Form

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20095626.svg)](https://doi.org/10.5281/zenodo.20095626)
[![Release CI (main only)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml/badge.svg)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml)

Start with the companion: [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex) / [PDF](latex/FirstDistinction.pdf).

## What This Project Asks

`Void and Form` is a three-book literate Agda project asking whether logic, mathematics, and physical description may share a common origin in a minimal structure of distinction.

Its opening wager is simple. Stable information presupposes a successfully carried distinction. If that wager fails, the route ends immediately. If it holds, the question becomes one of reach: how far can the first distinction carry?

That question should not be shrunk and it should not be inflated.

- Too narrow would be: this project studies distinction and `K4`.
- Too grand would be: this project has already deduced reality.

The actual question is harder and more interesting: is there a common origin still beneath logic, mathematics, and physical description themselves?

This repository slows down at the first formal threshold of that larger route. Before a theory can count, compare, negate, classify, or interpret, it must already be able to hold something apart from something else. The first task is therefore not yet physics and not yet full reconstruction. It is to ask what must be granted inside a formal setting before the claim that there are two positions has any stable force.

Type theory is used here not because it is the only possible language, but because it makes the cost of each step visible. Every claim must be paid for by construction. Hidden assumptions cannot pass silently; they have to show themselves.

## The Three Books

The repository is organized as one route in three books, each with its own level of claim.

1. `The First Distinction` is the entry. It asks why distinction should be the place to begin and reaches the first formally writable and machine-checkable carrier of stable distinction.
2. `Void` is the formal core. It takes that carrier seriously as mathematics and asks how much further structure can be reconstructed under the same discipline.
3. `Form` is the interpretive volume. It asks whether parts of the checked ledger admit a physical reading, while keeping theorem, interpretation, and empirical exposure distinct.

Read them in that order:

1. [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex) / [PDF](latex/FirstDistinction.pdf)
2. [Void.lagda.tex](Void.lagda.tex) / [PDF](latex/Void.pdf)
3. [Form.lagda.tex](Form.lagda.tex) / [PDF](latex/Form.pdf)

If you read only one file first, read [FirstDistinction.lagda.tex](FirstDistinction.lagda.tex).

In compact project form, the route is:

```text
The First Distinction -> Void -> Mathematical Reconstruction -> Physical Reading -> Common-Origin Question
```

## The First Formal Threshold

The first local formal question is:

```text
A formal system says that there are two positions.
What inside the system licenses that claim as two?
```

The answer pursued here is deliberately austere: a carrier, two displayed positions, a witness that they do not collapse into one, and a witness that no third unaccounted position remains. Only after those obligations are explicit does the checked development proceed.

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

This is the first point at which the conditions of stable distinction become fully explicit and machine-checkable. Everything earlier motivates the threshold. The checked route begins only once the datum has been supplied.

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

The opening pressure motivates the construction, but it is not itself an Agda theorem.

## How To Read The Claims

The project keeps its layers distinct.

1. Before the formal threshold there is a wager: stable information presupposes successful distinction.
2. At the threshold and inside `Void`, claims are formal only when they are carried by the Agda development under `--safe --without-K`.
3. Beyond the kernel, later mathematical reconstruction asks what reappears under the same discipline.
4. In `Form`, physical statements are readings of the checked structure, not automatic consequences of it.
5. Those readings face the world only at the point of empirical exposure.

That separation matters. The formal kernel should be inspected as mathematics. The prose should be read as an account of what has been shown, what has not, and where later interpretation begins.

The same discipline also sets the limit of what this repository claims.

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

## Method

The Agda type checker under `--safe --without-K` is the formal judge of the kernel. It does not check vision, rhetoric, or credentials. It checks constructions. The relevant questions are therefore whether the formal claims type-check under the stated options, whether the prose reports them faithfully, and whether the interpretive layers keep their stated status.

## Citation

Use the DOI shown above and cite specific formal claims by file and commit hash. Cite `Form` separately from `Void`, because its physical identifications are interpretive readings over the formal ledger.
