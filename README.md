# Void and Form

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20095626.svg)](https://doi.org/10.5281/zenodo.20095626)
[![Release CI (main only)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml/badge.svg)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml)

Start with the compact companion: [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) / [PDF](latex/VoidCompanion.pdf).

## The Question

`Void and Form` is a literate Agda project about the first formal burden of distinction.

Before a theory can count, compare, map, negate, classify, or interpret, it must already be able to hold something apart from something else. The project slows down at that hinge. It asks what has to be given inside a formal setting before the claim that there are two positions has any stable force.

The guiding question is:

```text
A formal system says that there are two positions.
What inside the system licenses that claim as two?
```

The answer pursued here is deliberately austere. A stable two-count needs a carrier in which the positions live, two displayed positions in that carrier, a proof that the positions remain distinct, and a proof that the carrier contains no third unaccounted position. Only after those obligations have been made explicit does the checked development proceed.

This gives the project its basic rhythm:

```text
Leibniz pressure -> Distinction -> Two -> End(Two) -> K4 closure -> Distinction
```

The first phrase names the pressure that motivates the construction. The remaining phrases name the checked route: a distinction datum, its canonical two-point normal form, the four endomorphism cases of that normal form, a faithful four-vertex closure of those cases, and a return from the closure record to the originating distinction.

## The First Pressure

The opening pressure is Leibnizian. If a system has no way to separate two alleged positions by any predicate available inside the system, then the system has no formal ground for treating them as a stable pair.

In the full file this appears as a small lemma after a carrier and equality have already been fixed:

```agda
leibniz-collapse :
  {S : Set} (a b : S) ->
  ((P : S -> Set) -> P a -> P b) ->
  a ≡ b
leibniz-collapse a b ind = ind (λ x -> a ≡ x) refl
```

The proof chooses the predicate `λ x -> a ≡ x`. Since `a ≡ a` is given by `refl`, complete predicate transfer from `a` to `b` yields `a ≡ b`.

The lemma functions as a formal marker. It shows the cost of indistinguishability once a language already has a carrier, predicates, and equality. The constructive entry point of the project is the record that supplies the missing data explicitly.

## The Formal Threshold

The central record in the full book is `Distinction`:

```agda
record Distinction : Set1 where
  field
    S     : Set
    ℓ     : S
    r     : S
    ℓ≠r   : ℓ ≠ r
    cover : (x : S) -> (x ≡ ℓ) ⊎ (x ≡ r)
```

Each field has a separate role.

- `S` is the carrier in which positions can be addressed.
- `ℓ` and `r` are the displayed boundary positions.
- `ℓ≠r` is anti-collapse data: the displayed positions are held apart.
- `cover` is anti-surplus data: every carrier point is one of the displayed positions.

The compact companion uses the readable field names `left`, `right`, `separated`, and `cover`. The full book uses `ℓ`, `r`, and `ℓ≠r`. The record is the same threshold in both presentations: separation and exhaustion are supplied as data inside the formal object.

## What The Kernel Checks

From `Distinction`, the companion and the full book verify a short spine of formal claims.

`Two-distinction` supplies the canonical two-point witness. It is the concrete model against which arbitrary distinction records are compared.

`two-normal-form` proves that every inhabitant of `Distinction` is boundary-preservingly isomorphic to that canonical witness. This is the point where the record stops being a suggestive shape and becomes a normal form theorem.

`EndoCase`, `classify-sound`, and `classify-unique` classify the endomorphisms `Two -> Two`. There are four cases: identity, swap, the constant-left map, and the constant-right map. The classification is a checked case analysis over the canonical two-point carrier.

`FaithfulClosure`, `MinimalClosure`, and the richer `K4Record` state the representation contract for those four cases. A closure must keep the four cases separated, realise all of them, and introduce no surplus vertices.

`record-presupposes-distinction` then reads a distinction back from the closure record. The closure remains accountable to the datum that generated it.

This is the compact load-bearing hinge of the repository. The longer files elaborate, route, and interpret it, but this spine is the first place to inspect the mathematical claim.

## Why A Four-Vertex Closure Appears

The four vertices arise from the four classified endomorphism cases of `Two`. Once the cases are represented under the separation, completeness, and no-surplus requirements, the resulting closure has the shape of a complete four-vertex graph.

That is the role of `K4` in this repository. It is a representation of the classified endomorphism space under a stated contract. The important point is the dependency order: distinction gives the canonical two-point form; the two-point form gives four endomorphism cases; the representation contract gives the four-vertex closure; the closure record returns to the distinction datum.

The geometry becomes legible after this route is visible: first the four cases are classified, then the closure represents them as a complete four-vertex object.

## The Volumes

The repository has several literate sources because the project has several layers.

1. [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) / [PDF](latex/VoidCompanion.pdf) is the intended first reading. It gives the compact licensing problem, the `Distinction` record, the normal-form theorem, the endomorphism classification, the closure contract, and the return to the originating datum.

2. [Void.lagda.tex](Void.lagda.tex) / [PDF](latex/Void.pdf) is the full book-length development. It rebuilds the internal equality infrastructure, develops the distinction kernel, continues through arithmetic and rational structure, and carries later invariant machinery inside the same literate Agda file.

3. [VoidTopos.lagda.tex](VoidTopos.lagda.tex) / [PDF](latex/VoidTopos.pdf) follows the categorical route. It treats distinction-induced readings, the raw obstruction, quotient and skeleton completion, and the displayed set-like burden that arises from the route.

4. [Form.lagda.tex](Form.lagda.tex) / [PDF](latex/Form.pdf) is the interpretive volume. It reads the formal ledger structurally and physically. Its identifications are proposed readings over the checked kernel and belong to the interpretive layer.

A first inspection should begin with the companion. The full book is intentionally large; the companion gives the shortest route to the hinge on which the rest depends.

## How To Read The Claims

The repository separates three kinds of statement.

Formal statements are Agda terms. They have names such as `two-normal-form`, `classify-unique`, `K4Record`, and `record-presupposes-distinction`. These are the claims whose status is decided by type checking under the options declared in the literate files.

Structural statements explain why those checked terms matter. They connect the formal steps into a readable argument: pressure, datum, normal form, classification, closure, and return.

Interpretive statements appear most clearly in `Form`. They ask how the checked ledger may be read in physical or epistemological terms. Their role is to expose hypotheses and interfaces while keeping them visibly separate from theorem.

This layer discipline is central to the project. The formal kernel should be inspected as mathematics; the surrounding prose should be read as the guide that makes the mathematics legible.

## Terms Used In The Repository

- **Carrier** means the type in which the named positions live.
- **Boundary positions** means the two displayed points of the distinction record. The word marks the named endpoints of the datum in this local vocabulary.
- **Anti-collapse** means that the displayed positions are propositionally distinct.
- **Anti-surplus** means that every element of the carrier is accounted for by the displayed positions.
- **Endomorphism case** means one of the four functions `Two -> Two`: identity, swap, constant-left, or constant-right.
- **No-surplus representation** means that a later closure uses exactly the vertices, cases, or degrees of freedom supplied by the classified data.
- **Return to the datum** means that the closure record remains dependent on the distinction from which it arose.

## Verification

The main type checks are:

```sh
agda VoidCompanion.lagda.tex
agda VoidTopos.lagda.tex
agda Void.lagda.tex
agda Form.lagda.tex
```

To regenerate a PDF, run `agda --latex` on the corresponding literate source and then run XeLaTeX twice in [latex/](latex/) for the generated `.tex` file.

Example:

```sh
agda --latex Void.lagda.tex
cd latex
xelatex -interaction=nonstopmode Void.tex
xelatex -interaction=nonstopmode Void.tex
```

The generated PDFs in [latex/](latex/) are produced from the literate Agda and LaTeX sources.

## Intellectual Placement

The question stands near several older threads.

Leibniz supplies the pressure of indistinguishability: where there is no expressible difference, the basis for a stable two-count disappears.

Constructive type theory supplies the execution discipline: witnesses, proof terms, explicit case splits, and checked dependencies.

George Spencer-Brown's `Laws of Form` stands near the distinctional starting point. This repository translates the pressure of distinction into explicit type-theoretic data and follows the consequences inside Agda.

Gregory Bateson's phrase "a difference that makes a difference" names the information-theoretic resonance of the problem. The checked layer begins where that resonance is rendered as formal data.

Lawvere and Tarski mark the later semantic and categorical neighborhood: structures become visible through the maps, models, and interpretations they admit.

The contribution of this repository is the mechanically inspectable route through one small threshold, together with a book-length attempt to keep formal proof, categorical continuation, and interpretation in contact without confusing their statuses.

## Files

- [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) / [PDF](latex/VoidCompanion.pdf): compact companion and first inspection point.
- [Void.lagda.tex](Void.lagda.tex) / [PDF](latex/Void.pdf): full formal development.
- [VoidTopos.lagda.tex](VoidTopos.lagda.tex) / [PDF](latex/VoidTopos.pdf): categorical obstruction, completion, and classification route.
- [Form.lagda.tex](Form.lagda.tex) / [PDF](latex/Form.pdf): interpretive volume and empirical exposure of later readings.
- [latex/](latex/): generated LaTeX/PDF output.
- [LICENSE](LICENSE): license terms.

## Author And Method

The repository presents its claims through inspectable material: Agda sources, theorem names, generated PDFs, a DOI, and a main-branch CI badge.

The relevant question is whether the formal claims type-check under the stated options, whether the prose reports those claims faithfully, and whether the interpretive layers keep their stated status.

## Citation

Use the DOI shown above and cite specific formal claims by file and commit hash. Cite `Form` separately from `Void`, because its physical identifications are interpretive readings over the formal ledger.