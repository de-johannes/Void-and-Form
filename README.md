# Void and Form

A constructive derivation, in Agda under `--safe --without-K`, with no
postulates and no standard library, of a closed combinatorial structure
from a single inhabited two-element type. The development is contained in
[Void.lagda.tex](Void.lagda.tex); a separate interpretive layer is
contained in [Form.lagda.tex](Form.lagda.tex).

---

## Note on the author

I am not a mathematician. No degree, no institutional affiliation. Over
the last eighteen months I formalized one question in Agda: what must
necessarily follow from one binary distinction, if nothing else is
assumed? The work was developed with the help of large language models;
the Agda type checker under `--safe --without-K` is the only judge of
what stands. This document is written for readers who want to verify the
formal claims. Where my own terminology departs from standard usage, the
corresponding Agda definition is cited by line number so that the formal
content can be read directly.

---

## Abstract

Let `Two : Set` denote the two-point type with constructors `ℓ` and `r`,
together with a witness `distinct : ℓ ≠ r`. Working in intensional
Martin-Löf type theory with the flags `--safe --without-K`, no
postulates, and no imports beyond what is defined in the file itself,
the development establishes the following.

1. **Endomorphism classification.** The function space `Two → Two`
   admits exactly four inhabitants up to pointwise equality. They are
   enumerated by an inductive type `EndoCase` with constructors
   `case-constL`, `case-constR`, `case-id`, `case-dual`, and the
   classification is sound and unique:
   ```agda
   classify-sound  : (f : Two → Two) → Σ EndoCase (λ c → f ≗ interpret c)
   classify-unique : (f : Two → Two) (c₁ c₂ : EndoCase)
                  → f ≗ interpret c₁ → f ≗ interpret c₂ → c₁ ≡ c₂
   ```
   References:
   [Void.lagda.tex L1120–1130](Void.lagda.tex#L1120-L1130) (`EndoCase`),
   [L1150–1346](Void.lagda.tex#L1150-L1346) (classification module),
   [L1385–1460](Void.lagda.tex#L1385-L1460) (top-level witnesses).

2. **Closure on four vertices.** The closure of the four-case structure
   under composition is the complete graph $K_4$. Closures on three
   vertices fail by absurd-pattern elimination; closures with more than
   four vertices add structure that is not forced by the four cases.
   The surviving carrier is captured by a record type `K4Record : Set`.
   Reference:
   [Void.lagda.tex L24314–24371](Void.lagda.tex#L24314-L24371).

3. **Uniqueness of the closure record.** `K4Record` is inhabited and
   any two inhabitants are propositionally equal:
   ```agda
   k4Record-inhabited : K4Record
   k4Record-unique    : (r₁ r₂ : K4Record) → r₁ ≡ r₂
   ```
   Reference:
   [Void.lagda.tex L24507–24690](Void.lagda.tex#L24507-L24690).

4. **Loop closure.** The existence of an inhabitant of `K4Record`
   entails the original separation witness on `Two`:
   ```agda
   record-presupposes-distinction : K4Record → Two-distinction
   ```
   Reference:
   [Void.lagda.tex L29267–29290](Void.lagda.tex#L29267-L29290).

5. **Forced numerical invariants.** The following identities hold by
   reduction; the witness in every case is `refl`:
   - `eulerChar-computed ≡ 2` —
     [L23728–23744](Void.lagda.tex#L23728-L23744).
   - `simplex-eval ≡ 137` —
     [L8881–8904](Void.lagda.tex#L8881-L8904).
   - `loop-numerator ≡ 11`, where `loop-numerator = E + d + χ` and the
     eight admissible subset candidates are eliminated to one by absurd
     patterns —
     [L27951–28010](Void.lagda.tex#L27951-L28010).
   - `theorem-sign-forcing` — the orientation sign on the closing form
     is determined, not chosen —
     [L29174–29207](Void.lagda.tex#L29174-L29207).

6. **Sequential completeness of the present construction of $\mathbb{R}$.**
   $\mathbb{R}$ here is the Cauchy-sequence representation: a real is
   a pair `(seq , isCauchy)` with `seq : ℕ → ℚ` and an explicit
   modulus `isCauchy`, and equality is the setoid relation `_≃ℝ_` of
   eventual $\varepsilon$-closeness. Within this representation,
   every Cauchy sequence of reals (in the sense of `IsCauchyℝ`,
   coordinatewise on rational tails) has a limit. The limit is built
   as the diagonal sequence
   $\mathtt{diagSeq}\,r\,n = \mathtt{seq}\,(r_n)\,K_n$, where $K_n$ is
   the internal stabilisation index of $r_n$ at tolerance $1/(n+1)$:
   ```agda
   ℝ-cauchy-complete :
     (r : ℕ → ℝ) → IsCauchyℝ r → Σ ℝ (λ x → r converges-to x)
   ```
   The proof uses two triangle inequalities and an $\varepsilon/4$
   accounting; no quotient type, no choice, and no completion functor
   is invoked. The result is not novel content about the real line; it
   is the statement that this particular minimal, self-contained
   constructive presentation of $\mathbb{R}$ closes up under its own
   notion of Cauchy convergence.
   References:
   [Void.lagda.tex L22200–22215](Void.lagda.tex#L22200-L22215) (`IsCauchyℝ`,
   `_converges-to_`),
   [L22217–22240](Void.lagda.tex#L22217-L22240) (`diagSeq`, `diagSeq-stable`),
   [L22256–22485](Void.lagda.tex#L22256-L22485) (`diagSeq-cauchy`),
   [L22488–22618](Void.lagda.tex#L22488-L22618) (`diagℝ-converges`,
   `ℝ-cauchy-complete`).

All claims are proved in literate Agda and machine-checked under
`--safe --without-K`, with no postulates and no standard-library
imports.

---

## Scope of the file

`Void.lagda.tex` is self-contained: every type, every operation, every
lemma it uses is defined inside the file. Nothing is imported. The
following layers are built from the base type `Two` and propositional
equality alone, in this dependency order. Line ranges are approximate
and refer to the start of each layer.

- **Foundations.** Propositional equality, universe lifting,
  $\Sigma$-types, disjoint unions, negation, pointwise equality `≗`.
  [L529–760](Void.lagda.tex#L529-L760).
- **Distinction and its laws.** `Two-distinction` together with seven
  laws (0.0–0.7) closing every escape route from non-vacuity.
  [L762–940](Void.lagda.tex#L762-L940).
- **Endomorphism classification of `Two → Two`.** `EndoCase`,
  `classify-sound`, `classify-unique`, mutual distinctness, bijection
  with `Two → Two`.
  [L943–1505](Void.lagda.tex#L943-L1505).
- **Two-normal form, orientation, automorphisms.** Uniqueness of
  presentation, exactness of the two orientations, automorphism
  classification.
  [L1509–2210](Void.lagda.tex#L1509-L2210).
- **Drift: a strict total order on $\omega$.** Boundary-preserving
  lifts as a category, no terminal state, no cycles, trichotomy.
  [L2522–3810](Void.lagda.tex#L2522-L3810).
- **Naturals $\mathbb{N}$.** Addition, multiplication, order;
  associativity, commutativity, distributivity, monotonicity,
  cancellation; positive naturals $\mathbb{N}^+$.
  [L5808–6720](Void.lagda.tex#L5808-L6720).
- **Integers $\mathbb{Z}$.** Pair-level construction, normalization,
  ring laws, ordered ring, transport, positivity elimination.
  [L6723–8540](Void.lagda.tex#L6723-L8540).
- **Rationals $\mathbb{Q}$.** Setoid construction, arithmetic,
  congruences, additive identity and inverse, ordered field structure,
  multiplicative monotonicity.
  [L8820–11530](Void.lagda.tex#L8820-L11530).
- **Reals $\mathbb{R}$.** Cauchy sequences of rationals (`record ℝ`
  with field `isCauchy`), equivalence as eventual $\varepsilon$-closeness
  (`_≃ℝ_`), addition, negation, multiplication, asymptotic strict and
  weak order, reflexivity, transitivity, antisymmetry, additive
  monotonicity. **Sequential completeness:** every Cauchy sequence of
  reals has a limit (`ℝ-cauchy-complete`), the limit being the
  diagonal sequence assembled from each row's own stabilisation index.
  The construction is the constructive Cauchy completion of
  $\mathbb{Q}$, presented as a setoid; no quotient type and no choice
  principle is invoked.
  [L19494–22620](Void.lagda.tex#L19494-L22620).
- **Spectral graph theory on $K_4$, $K_8$, $K_{12}$.** Laplacian
  operators, spectral form $L = 4I - J$, eigenvector classification,
  minimal polynomials, spectral packages, eigenvalue exhaustion.
  [L9664–19410](Void.lagda.tex#L9664-L19410).
- **Metric structure.** Metric axioms, triangle inequality, translation
  invariance, multiplicative scaling, distance bounds.
  [L15344–17180](Void.lagda.tex#L15344-L17180).
- **Forced $K_4$ representation record and singleton.** The closure
  record `K4Record`, existence, determination, uniqueness, singleton,
  cross-constraints, observable principle.
  [L23698–25180](Void.lagda.tex#L23698-L25180).
- **Loop closure.** `record-presupposes-distinction`.
  [L29267–29290](Void.lagda.tex#L29267-L29290).

The file consists of 242 sections, every one of which type-checks
under the same flags. The arithmetic is not assumed — it is built. A
reader who would like to verify this can confirm with

```sh
grep -nE '^(import|open import)' Void.lagda.tex
```

which returns no occurrences inside `module Void`.

---

## 1. Setting

The development takes place in intensional Martin-Löf type theory as
realized by Agda. The motivation is to make a uniqueness claim — that
exactly this combinatorial structure follows from this assumption —
into an object that the type checker either accepts or rejects, rather
than a claim defended in prose.

Three properties of the foundation are essential here:

- propositions are types, hence existence and uniqueness are
  inhabitants;
- there is no excluded middle and no choice, so every case must be
  carried out by hand;
- definitional equality is decided by reduction, so identities of
  closed terms reduce to `refl` or fail to type-check.

The flags `--safe --without-K` exclude unsafe primitives and the
uniqueness of identity proofs, respectively. The file declares no
`postulate` and imports nothing.

```agda
{-# OPTIONS --safe --without-K #-}
module Void where
```

Reference: [Void.lagda.tex L518–522](Void.lagda.tex#L518-L522).

---

## 2. The base type

```agda
data Two : Set where
  ℓ : Two
  r : Two

record Two-distinction : Set where
  field
    distinct : ℓ ≠ r
```

This is the entire input to the development. References:
[Void.lagda.tex L1516–1538](Void.lagda.tex#L1516-L1538),
[L1633–1682](Void.lagda.tex#L1633-L1682) (`two-normal-form`).

---

## 3. Classification of `Two → Two`

The four endomorphism cases are enumerated by

```agda
data EndoCase : Set where
  case-constL : EndoCase
  case-constR : EndoCase
  case-id     : EndoCase
  case-dual   : EndoCase
```

with an interpretation `interpret : EndoCase → Two → Two`. The two
classification theorems

```agda
classify-sound  : (f : Two → Two) → Σ EndoCase (λ c → f ≗ interpret c)
classify-unique : (f : Two → Two) (c₁ c₂ : EndoCase)
               → f ≗ interpret c₁ → f ≗ interpret c₂ → c₁ ≡ c₂
```

together state that `interpret` is a bijection between `EndoCase` and
the function space `Two → Two` modulo pointwise equality (`≗`). The
proofs proceed by case analysis on the values at `ℓ` and `r` and rule
out further cases by absurd patterns on `distinct`.

References:
[Void.lagda.tex L1120–1130](Void.lagda.tex#L1120-L1130),
[L1150–1346](Void.lagda.tex#L1150-L1346),
[L1385–1460](Void.lagda.tex#L1385-L1460).

---

## 4. Closure on four vertices

The four-case structure is asked to close under composition. A closure
on three vertices fails: any attempt to identify two distinct cases
yields an absurd pattern on `distinct`. A closure on more than four
vertices introduces a vertex not realized by any case. The unique
closure that admits all four cases without identification is the
complete graph on four vertices.

The carrier is recorded as

```agda
record K4Record : Set where
  field
    -- vertices, edges, faces and the discrete combinatorics they fix
    ...
```

Reference: [Void.lagda.tex L24314–24371](Void.lagda.tex#L24314-L24371).

---

## 5. Uniqueness and the loop

```agda
k4Record-inhabited             : K4Record
k4Record-unique                : (r₁ r₂ : K4Record) → r₁ ≡ r₂
record-presupposes-distinction : K4Record → Two-distinction
```

The first two state that `K4Record` is a singleton up to propositional
equality. The third states that the existence of an inhabitant of
`K4Record` entails the original separation witness on `Two`, closing
the chain
`Two-distinction ⇒ EndoCase ⇒ K₄ ⇒ K4Record ⇒ Two-distinction`.

References:
[Void.lagda.tex L24507–24690](Void.lagda.tex#L24507-L24690),
[L29267–29290](Void.lagda.tex#L29267-L29290).

---

## 6. Forced numerical invariants

Once the closure record is fixed, several integer-valued quantities are
determined. Each of the following holds by reduction; the witness in
every case is `refl`.

| Identity | Reference |
|---|---|
| `eulerChar-computed ≡ 2` | [L23728–23744](Void.lagda.tex#L23728-L23744) |
| `simplex-eval ≡ 137` | [L8881–8904](Void.lagda.tex#L8881-L8904) |
| `loop-numerator ≡ 11` | [L27951–28010](Void.lagda.tex#L27951-L28010) |
| `theorem-sign-forcing` | [L29174–29207](Void.lagda.tex#L29174-L29207) |

`loop-numerator` is defined as `E + d + χ` and is established by
reducing eight admissible subset candidates to one via absurd-pattern
elimination.

These are claims internal to the formal development. They carry no
physical content here; see Section 8.

---

## 7. Verification

```sh
agda --safe --without-K Void.lagda.tex
```

If the command exits with code 0, every identity, classification, and
uniqueness statement above has been checked. The file declares no
`postulate` and imports no library.

---

## 8. The interpretive layer

The companion file [Form.lagda.tex](Form.lagda.tex) imports `Void` and
proposes identifications between Void-internal invariants and physical
observables. These identifications are tagged explicitly:

```agda
data ClaimLevel : Set where
  formal-ledger             : ClaimLevel
  forced-ledger             : ClaimLevel
  physical-identification   : ClaimLevel
  experimental-test         : ClaimLevel
```

Identifications at level `physical-identification` are hypotheses, not
theorems. The Form layer does not strengthen any claim made in
`Void.lagda.tex` and is cited separately.

References:
[Form.lagda.tex L268](Form.lagda.tex#L268),
[L900](Form.lagda.tex#L900),
[L1342–1346](Form.lagda.tex#L1342-L1346).

---

## 9. What is and is not claimed

Claimed and machine-verified inside `Void.lagda.tex`:

- Sections 3–6 above, in full, under `--safe --without-K` with no
  postulates and no library imports.

Hypothesised inside `Form.lagda.tex`:

- That the Void-internal invariants of Section 6 project onto specific
  physical observables. These carry the tag `physical-identification`.

Not claimed:

- That the physical identifications of `Form.lagda.tex` are correct.
- That the Form layer adds mathematical content beyond what is already
  present in `Void.lagda.tex`.

---

## Files

- [Void.lagda.tex](Void.lagda.tex) — formal development.
- [Form.lagda.tex](Form.lagda.tex) — interpretive layer.
- [latex/](latex/) — generated PDF/LaTeX output.

## License and citation

See [LICENSE](LICENSE). Citations should refer to `Void.lagda.tex` by
commit hash; `Form.lagda.tex` should be cited separately as the
interpretive layer.

DOI: [10.5281/zenodo.19491035](https://doi.org/10.5281/zenodo.19491035)
