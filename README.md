# Void and Form

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20095626.svg)](https://doi.org/10.5281/zenodo.20095626)
[![Release CI (main only)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml/badge.svg)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml)

Start with the compact companion: [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) / [PDF](latex/VoidCompanion.pdf).

## What This Repository Tests

`Void and Form` is a foundations project in intensional Martin-Löf type theory, checked in Agda. The literate Agda sources declare `--safe --without-K`; the full `Void` development uses no postulates.

The entry question is deliberately small:

```text
A formal system says that there are two positions.
What inside the system licenses that claim as two?
```

Two names are not enough. They may name one position twice, or they may sit inside a carrier with further unaccounted points. The project therefore begins from a licensing problem, not from `K4`, not from physics, and not from a completed truth-value object.

The pre-formal pressure is Leibnizian: if two alleged positions cannot be distinguished by anything expressible in the system, the system has no internal ground for keeping them apart as two. That pressure is not itself an Agda theorem. The checked development begins only after it is represented as explicit data.

The compact spine is:

```text
Leibniz pressure -> Distinction -> Two -> End(Two) -> K4 closure -> Distinction
```

Everything before `Distinction` explains why the datum is being asked for. Everything after `Distinction` is a formal consequence inside the stated Agda fragment.

## Formal Threshold

The main file represents the threshold by the record `Distinction`:

```agda
record Distinction : Set1 where
  field
    S     : Set
    ℓ     : S
    r     : S
    ℓ≠r   : ℓ ≠ r
    cover : (x : S) → (x ≡ ℓ) ⊎ (x ≡ r)
```

The fields have different jobs.

- `S` is the carrier in which positions can be addressed.
- `ℓ` and `r` are the displayed boundary positions.
- `ℓ≠r` is anti-collapse data: the two displayed positions are not one position.
- `cover` is anti-surplus data: every carrier point is one of the displayed positions.

The compact companion uses the readable field names `left`, `right`, `separated`, and `cover`; the full book uses `ℓ`, `r`, and `ℓ≠r`. The content is the same threshold discipline: no collapse, no hidden surplus.

## Terms

- **Carrier** means the type in which the named positions live.
- **Boundary positions** means the two displayed points of the distinction record. The word is not topological here.
- **Anti-collapse** means that the two displayed positions are not propositionally equal.
- **Anti-surplus** means that every element of the carrier is accounted for by the displayed positions.
- **No-surplus representation** means that a later closure may not add extra vertices, cases, or degrees of freedom beyond the classified data.
- **Return to the datum** means that the closure record does not become a new independent starting point; it yields back the distinction from which it arose.

## Checked Kernel

The first formal route is narrow and explicit.

- `leibniz-collapse` records the formal echo of the opening pressure after a carrier and equality have already been fixed.
- `Two-distinction` gives a concrete inhabitant of `Distinction`.
- `two-normal-form` proves that every `Distinction` is boundary-preservingly isomorphic to the canonical two-point distinction.
- `EndoCase`, `classify-sound`, and `classify-unique` classify the endomorphisms `Two -> Two` into the two constants, identity, and swap.
- `FaithfulClosure`, `MinimalClosure`, and the richer `K4Record` state the representation contract for those four cases: separated cases, complete realisation, and no surplus.
- `record-presupposes-distinction` reads the originating distinction back from the closure record.

The four endomorphisms of `Two` are not claimed to be the Klein four-group. They form the four-case endomorphism space used by the representation contract. The complete graph `K4` appears only after those cases are represented as separated, fully realised, and non-surplus vertices.

## Reading Order

If you are opening the repository for the first time, read in this order:

1. [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) / [PDF](latex/VoidCompanion.pdf): the compact licensing problem and checked kernel.
2. [Void.lagda.tex](Void.lagda.tex) / [PDF](latex/Void.pdf): the full book-length development, with internal equality, arithmetic, rational structure, and later invariant machinery rebuilt inside the file.
3. [VoidTopos.lagda.tex](VoidTopos.lagda.tex) / [PDF](latex/VoidTopos.pdf): the categorical route from distinction-induced readings to raw obstruction, quotient/skeleton completion, and displayed set-like burden.
4. [Form.lagda.tex](Form.lagda.tex) / [PDF](latex/Form.pdf): the interpretive layer. It reads the checked kernel structurally and physically, but those readings are hypotheses rather than Agda theorems.

The companion is the intended first inspection point. It is short enough to check the load-bearing hinge directly, and it keeps the pre-formal pressure separate from the checked claims.

## Status Map

| Layer | Status | What to inspect |
|---|---|---|
| Licensing problem | Pre-formal motivation. Not an Agda theorem. | This README and the openings of [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) and [Void.lagda.tex](Void.lagda.tex). |
| Formal threshold | Explicit data supplied to MLTT/Agda. | The `Distinction` record. |
| Compact kernel | Agda-checked route from `Distinction` through normal form, four-case classification, closure, and return. | [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex). |
| Full `Void` development | Book-length formal development under `--safe --without-K`, without postulates. | [Void.lagda.tex](Void.lagda.tex). |
| Topos route | Categorical obstruction, quotient/skeleton completion, and displayed classification layer. | [VoidTopos.lagda.tex](VoidTopos.lagda.tex). |
| `Form` interpretation | Structural and physical readings of the checked kernel. They can fail without breaking the kernel. | [Form.lagda.tex](Form.lagda.tex). |

This separation is the central discipline of the project. Treat the licensing pressure as a theorem and the opening overclaims. Treat the checked terms as metaphor and the execution is lost. Treat interpretation as compiler-certified and the layers collapse.

## What Is Not Claimed

- `Void` does not prove physics.
- `Void` does not prove that every possible formal system must be rebuilt from this exact record.
- `K4` is not the starting axiom. It appears after the endomorphism cases of `Two` are represented under the stated contract.
- `Form` does not add mathematical content to `Void`; it proposes interpretations of the formal ledger.
- Names in the intellectual background do not certify the results. They locate the question.

The strongest formal claims are internal to the stated setting: once the distinction record is given, the normal form, four-case endomorphism classification, representation closure, and return map are checked objects.

## Why Inspect It

The unusual part is not the pair of constructors `L` and `R`. The unusual part is the refusal to let prose do the mathematical work. The project asks what data license a two-count, then requires the next steps to be definitions, classifications, equivalences, and contradiction eliminations.

That is why the README leads to the companion instead of asking the reader to begin with the full book. If the hinge from `Distinction` to normal form and closure fails, the project fails at its root. If it holds, the larger files can be read as continuation, categorical routing, and interpretation rather than as substitutes for proof.

## Intellectual Placement

The question is not launched from nowhere. These names locate the neighborhood; they do not function as proof.

- Leibniz supplies the entry pressure through the identity of indiscernibles: without expressible difference, two alleged positions collapse.
- Constructive type theory supplies the execution discipline: witnesses, proof terms, explicit case splits, and no hidden postulates.
- George Spencer-Brown's `Laws of Form` stands near the distinctional starting point, but this project asks what happens when distinction is represented as explicit type-theoretic data.
- Gregory Bateson's phrase "a difference that makes a difference" motivates the information-theoretic reading of distinguishability. The checked layer begins later, at the displayed record.
- Lawvere and Tarski mark the later semantic and categorical orientation: structures are studied by the maps and interpretations they admit.

The contribution is not the invention of distinction as a theme. It is the attempt to make a small threshold mechanically inspectable and to keep the pre-formal, formal, categorical, and interpretive layers from replacing one another.

## Verification

The main type checks are:

```sh
agda VoidCompanion.lagda.tex
agda VoidTopos.lagda.tex
agda Void.lagda.tex
agda Form.lagda.tex
```

To regenerate the PDFs, run `agda --latex` on the corresponding literate source and then run XeLaTeX twice in [latex/](latex/) for the generated `.tex` file.

For example:

```sh
agda --latex Void.lagda.tex
cd latex
xelatex -interaction=nonstopmode Void.tex
xelatex -interaction=nonstopmode Void.tex
```

The generated PDFs in [latex/](latex/) are produced from the literate Agda/LaTeX sources.

## Files

- [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) / [PDF](latex/VoidCompanion.pdf): compact companion and first inspection point.
- [Void.lagda.tex](Void.lagda.tex) / [PDF](latex/Void.pdf): full formal development.
- [VoidTopos.lagda.tex](VoidTopos.lagda.tex) / [PDF](latex/VoidTopos.pdf): categorical obstruction, completion, and classification route.
- [Form.lagda.tex](Form.lagda.tex) / [PDF](latex/Form.pdf): interpretive volume and empirical exposure of later readings.
- [latex/](latex/): generated LaTeX/PDF output.
- [LICENSE](LICENSE): license terms.

## Author and Method

This project was developed outside an institutional mathematics setting and with the help of large language models. Those facts describe the working process; they do not decide the status of the checked claims.

For that reason the repository foregrounds inspectable artifacts: Agda sources, explicit theorem names, generated PDFs, a DOI, and a main-branch CI badge. The relevant question is whether the formal claims type-check under the stated flags and whether the interpretive claims remain in their proper layer.

## Citation

Use the DOI shown above and cite specific formal claims by file and commit hash. Cite `Form` separately from `Void`, because its physical identifications are interpretive hypotheses rather than Agda theorems.