# Void and Form

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20095626.svg)](https://doi.org/10.5281/zenodo.20095626)
[![Release CI (main only)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml/badge.svg)](https://github.com/de-johannes/Void-and-Form/actions/workflows/release-ci.yml)

Start with the compact companion: [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) / [PDF](latex/VoidCompanion.pdf).

## What This Is

`Void and Form` is a foundations project in a specific sense: it studies the formal threshold at which two can be held apart as two.

The guiding question is small:

> When are two really two, and not just one appearing twice?

The project does not begin with particles, space, time, geometry, or physical law. It begins with a prior formal problem: if a system cannot separate two alleged elements by anything available inside the system, then the system has no formal reason to maintain them as two.

This is expressed by a small Leibniz-style collapse principle:

```agda
leibniz-collapse :
  {S : Set} (a b : S) →
  ((P : S → Set) → P a → P b) →
  a ≡ b
leibniz-collapse a b ind = ind (λ x → a ≡ x) refl
```

The proof chooses the predicate:

```agda
P x = a ≡ x
```

Since `P a` holds by `refl`, the assumed transfer of every predicate from `a` to `b` yields `a ≡ b`.

The point is not metaphysical. The project does not claim that indistinguishable things “do not exist”. The claim is narrower and formal:

> inside a given formal language, if nothing separates `a` from `b`, then the system cannot hold them as a stable pair.

Most formal systems begin after this point.

They already use terms, judgments, equality, functions, relations, and objects. But all of these presuppose that something can be held apart from something else. They presuppose stable distinction.

`Void and Form` does not claim to replace those systems. It tries to expose a smaller threshold that they normally pass over silently: the point at which two positions can be maintained as two rather than collapsing into one.

In this limited sense, the project is foundational. It does not provide a new foundation for all mathematics. It investigates a condition that formal foundations already rely on before they can begin to operate.

The checked development therefore does not start from a bare pair of names. It starts only after non-collapse and exhaustion have been rendered as explicit data: a carrier, two named boundary positions, a proof that they are distinct, and a cover saying that every point of the carrier is one of the two.

The compact checked spine is:

```text
Distinction -> Two -> End(Two) -> minimal K4 closure -> Distinction
```

The point is not that a two-element type can be formalized. The point is that, once the displayed distinction record is granted, the subsequent normal form, endomorphism classification, closure conditions, and return to the originating datum are machine-checked terms rather than prose.

The larger volumes continue from that spine. `Void` carries the full formal development, including arithmetic and invariant ledgers. `VoidTopos` follows the categorical route: it builds the raw reading category, locates the obstruction to a raw Topos, and classifies the free well-pointed completion that remains. `Form` is the interpretive volume: it reads the checked kernel against physical and epistemological structure, but its physical identifications are hypotheses, not Agda theorems.

## Terminology Used Here

The words below are used in a narrow technical sense throughout this README.

- **Carrier** means the type `S` in which the two named positions live.

- **Boundary positions** means the two distinguished points `left right : S`. The word “boundary” is not topological here; it only marks the two named endpoints of the displayed distinction.

- **Non-collapse** or **separation** means that the two named positions are not propositionally equal. In the code this is the field:

  ```agda
  separated : ¬ (left ≡ right)
  ```

- **Exhaustion** or **cover** means that every element of the carrier is one of the two named positions. In the code this is the field:

  ```agda
  cover : (x : S) → (x ≡ left) ⊎ (x ≡ right)
  ```

- **No-surplus** means that a later representation may not contain additional vertices, cases, or degrees of freedom not forced by the classified data.

- **Return to the datum** means that the closure structure does not become a new independent starting point; it yields back the distinction from which it arose.

These terms are introduced here to avoid treating project-specific language as if it were standard terminology.

## Formal Threshold

The checked layer begins at the `Distinction` record. In the companion, it is displayed at [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex#L408):

```agda
record Distinction : Set₁ where
  field
    S         : Set
    left      : S
    right     : S
    separated : ¬ (left ≡ right)
    cover     : (x : S) → (x ≡ left) ⊎ (x ≡ right)
```

The fields matter independently.

- `S` is the carrier.
- `left` and `right` name the boundary positions.
- `separated` prevents the Leibniz collapse of the two boundary positions.
- `cover` says that the carrier is exhausted by those two positions.

Separation alone says that the two named points are not equal. It does not say that the carrier has no further inhabitants. The cover field supplies that exhaustion explicitly.

In Martin-Löf type theory, two named points do not make a two-point type. The normal-form theorem needs both separation and cover.

Everything before this threshold explains why this datum is chosen. Everything listed in the checked spine below is a formal object after the threshold has been crossed.

## Checked Spine

- **Normal form.** `two-normal-form` proves that every inhabitant of the distinction record is boundary-preservingly isomorphic to the canonical two-point distinction ([VoidCompanion.lagda.tex](VoidCompanion.lagda.tex#L835), full version in [Void.lagda.tex](Void.lagda.tex#L3582)).

- **Endomorphism classification.** `EndoCase`, `classify-sound`, and `classify-unique` classify the function space `Two -> Two` into the four cases: identity, swap, and the two constants ([VoidCompanion.lagda.tex](VoidCompanion.lagda.tex#L887), [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex#L918), [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex#L957)).

- **Closure.** `FaithfulClosure` and `MinimalClosure` state the representation contract: separated cases, complete realization, and no surplus vertices. The canonical closure is in checked bijection with `EndoCase`, and the full book packages the richer `K4Record` ([VoidCompanion.lagda.tex](VoidCompanion.lagda.tex#L1041), [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex#L1049), [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex#L1297), [Void.lagda.tex](Void.lagda.tex#L31474)).

- **Return to the datum.** `k4-presupposes-distinction` in the companion and `record-presupposes-distinction` in the full file read a distinction back from the closure record ([VoidCompanion.lagda.tex](VoidCompanion.lagda.tex#L1328), [Void.lagda.tex](Void.lagda.tex#L36450)).

- **Categorical continuation.** `VoidTopos` builds the free well-pointed completion with NNO and packages it as a classifying topos for displayed models of the generated reading skeleton ([VoidTopos.lagda.tex](VoidTopos.lagda.tex#L2676), [VoidTopos.lagda.tex](VoidTopos.lagda.tex#L2903), [VoidTopos.lagda.tex](VoidTopos.lagda.tex#L2924)).

The long file then develops the arithmetic and invariant ledger over the same formal kernel. For example, the Cauchy-completeness theorem for the constructed real numbers is in [Void.lagda.tex](Void.lagda.tex#L28982).

## What Kind of Project This Is

`Void and Form` is not primarily a construction project.

It is an eliminative stability programme.

The central question is not:

> What structures can we freely build?

The central question is:

> What structures remain once non-forced freedom is systematically removed?

This is why the project repeatedly uses normal forms, exhaustive classifications, no-surplus conditions, canonical closure records, uniqueness proofs, and definitional collapse by `refl`.

Many equalities close by `refl` because the development is arranged to remove non-canonical freedom until different routes reduce to the same normal form.

In this project, `refl` is often not the beginning of a trick, but the endpoint of elimination.

## Start Here

If you are opening the repository for the first time, read in this order:

1. [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) / [PDF](latex/VoidCompanion.pdf): the compact kernel and map of the project.
2. [VoidTopos.lagda.tex](VoidTopos.lagda.tex) / [PDF](latex/VoidTopos.pdf): the standalone route from the reading structure to obstruction and classifying completion.
3. [Void.lagda.tex](Void.lagda.tex): the full book-length formal development.
4. [Form.lagda.tex](Form.lagda.tex): the structural and physical interpretation layer.

The companion is the intended first inspection point. It is short enough to check the spine directly, and it keeps the pre-formal motivation separate from the Agda-checked claims.

## Status Map

| Layer | Status | What to inspect |
|---|---|---|
| Pre-formal motivation | Not an Agda theorem. It names why stable distinction is treated as the entry condition for description. | This README and the opening of the companion. |
| Compact kernel | Agda-checked spine from `Distinction` through closure and return. | [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex). |
| Full `Void` development | Book-length formal development under `--safe --without-K`; no postulates. | [Void.lagda.tex](Void.lagda.tex). |
| Topos route | Categorical obstruction, completion, and classification layer. | [VoidTopos.lagda.tex](VoidTopos.lagda.tex). |
| `Form` interpretation | Physical and epistemological readings of the checked kernel. These are explicit hypotheses and can fail without breaking `Void`. | [Form.lagda.tex](Form.lagda.tex). |

This separation is the central discipline of the project. Treat the pre-formal boundary as a theorem and the beginning overclaims. Treat the checked terms as metaphor and the execution is lost. Treat the physical readings as compiler-certified and the interpretation becomes confused.

## What Is Not Claimed

- `Void` does not prove physics.
- `Void` does not simulate a universe.
- `Void` does not prove that every possible formal theory reduces to a binary distinction.
- `Void` does not replace MLTT.
- `Form` does not add mathematical content to `Void`; it imports the formal ledger and proposes interpretations.
- The names in the intellectual background below do not certify the results. They locate the question.

The strongest formal claims are internal to the stated setting: once the distinction record is given, the normal form, four-case endomorphism classification, closure contract, and return map are checked objects.

## Why This Is Worth Inspecting

The unusual part is not the constructor pair `L` and `R`.

The unusual part is the burden placed on stable two-ness.

The project asks a narrow question with a large reach: after the minimal distinction datum is made explicit, what remains if the next steps are forced to be definitions, classifications, equivalences, contradiction eliminations, no-surplus constraints, and return maps?

That is also why the README leads to the companion instead of asking the reader to begin with the full book. The companion gives the shortest route to the load-bearing hinge. If that hinge fails, the project fails at its root. If it holds, the larger volumes can be read as continuation and interpretation rather than as a substitute for proof.

## Intellectual Location

The question is not launched from nowhere. It stands near several older threads, without claiming their authority.

- George Spencer-Brown's `Laws of Form` treats distinction as a primitive mark. This project asks what happens when a distinction is represented as explicit type-theoretic data and then checked.
- Gregory Bateson's phrase "a difference that makes a difference" motivates the information-theoretic reading of distinguishability. The formal layer here begins later, at a displayed record.
- Wheeler's `it from bit` is a nearby physical slogan, but `Void` does not derive the physical world. Physical readings belong to `Form` and remain empirical hypotheses.
- Wittgenstein, Gödel, Tarski, and the Russell-Girard boundary mark the limits of total internal self-description. This project does not cross that boundary; it makes the internal threshold it can check explicit.

The contribution is therefore not the invention of the question. It is the attempt to make a small version of the threshold mechanically inspectable, and then to keep the formal, categorical, and interpretive layers from collapsing into each other.

## Author and Method

This project was developed outside an institutional mathematics setting and with the help of large language models. Those facts describe the working process; they do not decide the status of the checked claims.

For that reason the repository foregrounds inspectable artifacts: Agda files, explicit theorem names, line pointers, PDFs generated from the literate sources, a DOI, and a main-branch CI badge.

The relevant question is not whether the prose sounds familiar. The relevant question is whether the formal claims type-check under the stated flags and whether the interpretive claims are kept in their proper layer.

## Verification

The main checks are:

```sh
agda --safe --without-K VoidCompanion.lagda.tex
agda --safe --without-K VoidTopos.lagda.tex
agda --safe --without-K Void.lagda.tex
agda --safe --without-K Form.lagda.tex
```

The compact companion uses standard-library imports for readability. The full `Void` file carries the book-length development and has no postulates. The generated PDFs in [latex/](latex/) are produced from the literate Agda/LaTeX sources.

## Files

- [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) / [PDF](latex/VoidCompanion.pdf): compact companion and first inspection point.
- [VoidTopos.lagda.tex](VoidTopos.lagda.tex) / [PDF](latex/VoidTopos.pdf): categorical obstruction, completion, and classification route.
- [Void.lagda.tex](Void.lagda.tex): full formal development.
- [Form.lagda.tex](Form.lagda.tex): interpretive volume and empirical exposure of the physical readings.
- [latex/](latex/): generated LaTeX/PDF output.
- [LICENSE](LICENSE): license terms.

## Citation

Use the DOI shown above and cite specific formal claims by file and commit hash. `Form` should be cited separately from `Void`, because its physical identifications are interpretive hypotheses rather than Agda theorems.
