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

A single inductive type with two constructors, together with a derived
inequality witness between them, is sufficient to force a unique finite
combinatorial structure — the complete graph on four vertices — and to
obstruct every alternative carrier on which the same generating data
would embed faithfully. The arithmetic of $\mathbb{N}$, $\mathbb{Z}$,
$\mathbb{Q}$, and $\mathbb{R}$, together with sequential completeness of
the resulting reals, is then constructed from no further data. The
final theorem of the development closes the loop: every admissible
invariant record on the surviving structure already entails the
inequality witness with which the file began. The argument is fully
mechanised; the text and its verifier are the same file.

More precisely. Let `Two : Set` denote the inductive type with
constructors `L` and `R`, together with a witness `Two-L≠R : L ≠ R`
derived inside the same file. A `Distinction` is a record consisting
of a carrier `S : Set`, two designated points `ℓ r : S`, a separation
witness `ℓ ≠ r`, and a cover `(x : S) → (x ≡ ℓ) ⊎ (x ≡ r)`. Working in
intensional Martin-Löf type theory with the flags `--safe --without-K`,
no postulates, and no imports beyond what is defined in the file
itself, the development establishes the following.

1. **Uniqueness of binary distinction.** Let `Distinction : Set₁` be
   the type of carriers `S` equipped with two designated points
   `ℓ r : S`, a separation witness `ℓ ≠ r`, and a cover
   `(x : S) → (x ≡ ℓ) ⊎ (x ≡ r)`. Every inhabitant of `Distinction`
   is boundary-preservingly isomorphic to the canonical inhabitant
   `Two-distinction` built on `Two`:
   ```agda
   two-normal-form :
     (d : Distinction) → DistinctionIso d Two-distinction
   ```
   This is the formal statement that `Two` is not one possible binary
   base among many but the unique normal form for any MLTT structure
   carrying two distinguishable, exhaustive points. The further
   classification of orientations shows that the only ambiguity in
   the isomorphism is whether boundaries are preserved or swapped.
   References:
   [Void.lagda.tex L804](Void.lagda.tex#L804) (`Distinction`),
   [L1570](Void.lagda.tex#L1570) (`DistinctionIso`),
   [L1652](Void.lagda.tex#L1652) (`two-normal-form`).

2. **Endomorphism classification.** The function space `Two → Two`
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
   [Void.lagda.tex L1145](Void.lagda.tex#L1145) (`EndoCase`),
   [L1179](Void.lagda.tex#L1179) (classification module `K₄`),
   [L1405–1421](Void.lagda.tex#L1405-L1421) (top-level wrappers `k4-classification-sound`/`-unique`).

3. **Closure on four vertices.** The closure of the four-case structure
   under composition is the complete graph $K_4$. Closures on three
   vertices fail by absurd-pattern elimination; closures with more than
   four vertices add structure that is not forced by the four cases.
   The surviving carrier is captured by a record type `K4Record : Set`.
   Reference:
   [Void.lagda.tex L26681](Void.lagda.tex#L26681).

4. **Uniqueness of the closure record.** `K4Record` is inhabited and
   any two inhabitants are propositionally equal:
   ```agda
   k4Record-inhabited : K4Record
   k4Record-unique    : (r₁ r₂ : K4Record) → r₁ ≡ r₂
   ```
   Reference:
   [Void.lagda.tex L27040](Void.lagda.tex#L27040) (`K4Record-is-canonical`).

5. **Loop closure.** The existence of an inhabitant of `K4Record`
   entails an inhabitant of `Distinction`, recovering the binary
   distinction with which the file began:
   ```agda
   record-presupposes-distinction : K4Record → Distinction
   ```
   Reference:
   [Void.lagda.tex L31648](Void.lagda.tex#L31648).

6. **Forced numerical invariants.** Once the closure record is fixed,
   several integer-valued quantities of the surviving structure are
   determined by reduction; the witness in every case is `refl`. The
   list — Euler characteristic, simplex evaluation, loop numerator,
   sign forcing — is given in §7 with line references; in the abstract
   they are detail rather than headline.

7. **Sequential completeness of the present construction of $\mathbb{R}$.**
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
   [Void.lagda.tex L23951–23863](Void.lagda.tex#L23951-L23959) (`IsCauchyℝ`,
   `_converges-to_`),
   [L23972–23883](Void.lagda.tex#L23972-L23979) (`diagSeq`, `diagSeq-stable`),
   [L24007–24141](Void.lagda.tex#L24007-L24237) (`diagSeq-cauchy`),
   [L24239–24273](Void.lagda.tex#L24239-L24369) (`diagℝ`, `diagℝ-converges`,
   `ℝ-cauchy-complete`).

All claims are proved in literate Agda and machine-checked under
`--safe --without-K`, with no postulates and no standard-library
imports.

---

## Scope of the file

`Void.lagda.tex` is self-contained: every type, every operation, every
lemma it uses is defined inside the file. Nothing is imported. The
following layers are built from the base type `Two` and propositional
equality alone. The chapters of the file are interleaved by use rather
than ordered by topic; the references below point to the *defining
anchor* of each layer (record, theorem, or chapter heading) and the
chapter heading that opens it.

- **Foundations.** Propositional equality, universe lifting,
  $\Sigma$-types, disjoint unions, negation, pointwise equality `≗`.
  Chapter `Minimal Logical Infrastructure`,
  [L520](Void.lagda.tex#L520).
- **Distinction and its laws.** `Distinction` record at
  [L804](Void.lagda.tex#L804); the canonical inhabitant
  `Two-distinction` at [L1549](Void.lagda.tex#L1549); chapter
  `Non-Vacuity`, [L829](Void.lagda.tex#L829).
- **Endomorphism classification of `Two → Two`.** `EndoCase` at
  [L1145](Void.lagda.tex#L1145); classification module `K₄` at
  [L1179](Void.lagda.tex#L1179); top-level wrappers
  `k4-classification-sound` / `-unique` at
  [L1405–1421](Void.lagda.tex#L1405-L1421).
- **Two-normal form, orientation, automorphisms.** Chapter
  `Two Normal Form` at [L1521](Void.lagda.tex#L1521);
  `two-normal-form` at [L1652](Void.lagda.tex#L1652);
  `orientation-exhaustive` at [L1888](Void.lagda.tex#L1888).
- **Drift: a strict total order on $\omega$.** Chapter `Drift` at
  [L2503](Void.lagda.tex#L2503), through chapters
  `Non-Collapse of Drift`, `Cross-Stage Comparison`,
  `Drift Reachability`, `Drift Acyclicity` (last starts at
  [L3163](Void.lagda.tex#L3163)).
- **Naturals $\mathbb{N}$.** Chapter `Arithmetic Infrastructure` at
  [L5307](Void.lagda.tex#L5307); `Forced Additive Laws` at
  [L6169](Void.lagda.tex#L6169); `Multiplicative Structure and Integer
  Order` at [L6453](Void.lagda.tex#L6453).
- **Integers $\mathbb{Z}$.** Chapter `Integer Multiplication Laws` at
  [L7084](Void.lagda.tex#L7084); `Integer Order Laws` at
  [L8135](Void.lagda.tex#L8135); `Absolute Value Laws` at
  [L8538](Void.lagda.tex#L8538).
- **Rationals $\mathbb{Q}$.** Chapter `Rational Numbers and Measurement`
  at [L10293](Void.lagda.tex#L10293); `Rational Setoid and Order Laws`
  at [L11141](Void.lagda.tex#L11141); `Rational Addition and
  Multiplication Laws` at [L12783](Void.lagda.tex#L12783);
  `Rational Distance Laws` at [L17082](Void.lagda.tex#L17082).
- **Reals $\mathbb{R}$.** Chapter
  `Reals as Forced Cauchy Closure over Q` at
  [L21230](Void.lagda.tex#L21230); `record ℝ` at
  [L21272](Void.lagda.tex#L21272); chapter
  `Cauchy Completeness of R` at
  [L23758](Void.lagda.tex#L23758);
  `IsCauchyℝ` / `_converges-to_` at
  [L23951–23863](Void.lagda.tex#L23951-L23959);
  `ℝ-cauchy-complete` at [L24367](Void.lagda.tex#L24367).
- **Spectral graph theory on $K_4$, $K_8$, $K_{12}$.** Chapter
  `K₄ Neighborhood and Laplacian` at
  [L6651](Void.lagda.tex#L6651); `Laplacian as Finite-Index Operator`
  at [L11377](Void.lagda.tex#L11377); `Coupled K₄ Laplacian` at
  [L13242](Void.lagda.tex#L13242); `Triple K₄ Laplacian` at
  [L14461](Void.lagda.tex#L14461).
- **The kind classification of invariants.** Chapter at
  [L9191](Void.lagda.tex#L9191); the four-case data type
  `InvariantKind` at [L9274](Void.lagda.tex#L9274) and the closure
  theorem `kind-exhaustive` at [L9285](Void.lagda.tex#L9285).
- **Forced $K_4$ representation record and singleton.** Chapter
  `The K₄ Invariant Record` at [L5005](Void.lagda.tex#L5005);
  `K4Record` at [L26681](Void.lagda.tex#L26681);
  singleton lemma `K4Record-is-canonical` at
  [L27040](Void.lagda.tex#L27040).
- **Loop closure.** `record-presupposes-distinction` at
  [L31648](Void.lagda.tex#L31648).

The file builds under the same flags throughout. The arithmetic is not
assumed — it is built. A reader who would like to verify this can
confirm with

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

The formal stage is therefore not empty: it supplies dependent function
types, dependent pair types, inductive families, and propositional
equality with its standard eliminator. Nothing else is granted from
outside the file. The flags `--safe --without-K` exclude unsafe
primitives and the uniqueness of identity proofs, respectively. The
file declares no `postulate` and imports nothing.

```agda
{-# OPTIONS --safe --without-K #-}
module Void where
```

Reference: [Void.lagda.tex L530–535](Void.lagda.tex#L530-L535).

---

## 2. The base type

```agda
data Two : Set where
  L : Two
  R : Two

Two-L≠R : L ≠ R
Two-L≠R ()

Two-cover : (x : Two) → (x ≡ L) ⊎ (x ≡ R)
Two-cover L = inj₁ refl
Two-cover R = inj₂ refl

Two-distinction : Distinction
Two-distinction = record
  { S = Two ; ℓ = L ; r = R ; ℓ≠r = Two-L≠R ; cover = Two-cover }
```

`Two` is the inductive base type; `Two-L≠R` is the separation witness;
`Two-distinction` is the canonical inhabitant of the general
`Distinction` record. This — and only this — is the input to the
development. References:
[Void.lagda.tex L1535–1556](Void.lagda.tex#L1535-L1556),
[L1652](Void.lagda.tex#L1652) (`two-normal-form`).

---

## 3. Uniqueness of binary distinction

The choice of `Two` as the base type is not a notational preference.
Inside `Void.lagda.tex` it is shown that any MLTT structure carrying
two distinguishable, exhaustive points coincides with `Two` up to
boundary-preserving isomorphism. Such structures are captured by the
record

```agda
record Distinction : Set₁ where
  field
    S     : Set
    ℓ     : S
    r     : S
    ℓ≠r   : ℓ ≠ r
    cover : (x : S) → (x ≡ ℓ) ⊎ (x ≡ r)
```

and the normal-form theorem

```agda
two-normal-form :
  (d : Distinction) → DistinctionIso d Two-distinction
```

states that every inhabitant `d : Distinction` is isomorphic to the
canonical `Two-distinction` by an isomorphism that sends
boundary points to boundary points. The orientation classification
that follows shows that the only freedom in this isomorphism is a
global swap of the two boundary roles.

This is the formal version, inside MLTT, of the statement that
`Two` is the unique normal form for binary distinction. It does *not*
claim that every describable structure reduces to binary
distinctions; that would be a meta-theoretic statement about the
family of all theories, not a theorem inside one. The result here is
the internal one and exactly the one that is provable.

References:
[Void.lagda.tex L804](Void.lagda.tex#L804) (`Distinction`),
[L1570](Void.lagda.tex#L1570) (`DistinctionIso`),
[L1652](Void.lagda.tex#L1652) (`two-normal-form`),
[L1888–1902](Void.lagda.tex#L1888-L1902) (orientation classification:
`orientation-exhaustive`, `law1-10-orientation-exhaustive`).

---

## 4. Classification of `Two → Two`

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
[Void.lagda.tex L1145](Void.lagda.tex#L1145) (`EndoCase`),
[L1179](Void.lagda.tex#L1179) (classification module `K₄`),
[L1405–1421](Void.lagda.tex#L1405-L1421) (top-level wrappers).

---

## 5. Closure on four vertices

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

Reference: [Void.lagda.tex L26681](Void.lagda.tex#L26681) (`K4Record`).

---

## 6. Uniqueness and the loop

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
[Void.lagda.tex L27040](Void.lagda.tex#L27040) (`K4Record-is-canonical`),
[L31648](Void.lagda.tex#L31648) (`record-presupposes-distinction`).

---

## 7. Forced numerical invariants

Once the closure record is fixed, several integer-valued quantities are
determined. Each of the following holds by reduction; the witness in
every case is `refl`.

| Identity | Reference |
|---|---|
| `eulerChar-computed ≡ 2` (`law16B-3-euler`) | [L26111](Void.lagda.tex#L26111) |
| `simplex-eval ≡ 137` (`law15A-0-simplex-eval-137`) | [L10376](Void.lagda.tex#L10376) |
| `loop-numerator ≡ 11` (`law-loop-num-11`) | [L30333](Void.lagda.tex#L30333) |
| `theorem-sign-forcing` | [L31588](Void.lagda.tex#L31588) |

Inside the $70$-monomial pool of degree $\leq 4$ in $(V,E,d,\chi)$
fixed by the same forced values, the integer $137$ admits exactly one
pair-sum decomposition — the canonical identity $d^2 + V^3\chi$.
`theorem-pair-sum-degree-4-count` establishes that the hit count
is exactly 2 (the ordered pair and its mirror), and
`theorem-degree-bounded-exhaustion-deg4` packages the canonical hit,
the identity $V^3\chi = V^d \cdot \chi$, and the unique count into a
single closure record, all by `refl`
([L10849–L10871](Void.lagda.tex#L10849-L10871)).
The enumeration is a property test on the output of `simplex-eval`,
not a search for it; the pool, the bound, and the integer are
determined before any pair is examined.

`loop-numerator` is defined as `E + d + χ` and is established by
reducing eight admissible subset candidates to one via absurd-pattern
elimination.

These are claims internal to the formal development. They carry no
physical content here; see Section 9.

---

## 8. Verification

```sh
agda --safe --without-K Void.lagda.tex
```

If the command exits with code 0, every identity, classification, and
uniqueness statement above has been checked. The file declares no
`postulate` and imports no library.

---

## 9. The interpretive layer

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

## 10. What is and is not claimed

Claimed and machine-verified inside `Void.lagda.tex`:

- Sections 3–7 above, in full, under `--safe --without-K` with no
  postulates and no library imports. In particular: `Two` is the
  unique normal form of binary distinction inside MLTT (§3); the
  endomorphism space of `Two` has exactly four inhabitants up to
  pointwise equality (§4); their composition closure is uniquely
  $K_4$ (§5); the closure record is a singleton and entails the
  original separation witness (§6); the listed numerical invariants
  evaluate to the stated integers by `refl` (§7).

Hypothesised inside `Form.lagda.tex`:

- That the Void-internal invariants of Section 7 project onto specific
  physical observables. These carry the tag `physical-identification`.

Not claimed inside `Void.lagda.tex`:

- That every describable structure reduces to binary distinctions.
  This is a meta-theoretic statement about the entire family of
  formal theories and is not formalisable as an internal theorem of
  MLTT. The internal counterpart that *is* proved is §3:
  any structure that already carries the data of two distinguishable,
  exhaustive points is isomorphic to `Two`.
- That the physical identifications of `Form.lagda.tex` are correct.
- That the Form layer adds mathematical content beyond what is already
  present in `Void.lagda.tex`.

---

## 11. The reach of the universal claim

The statement of §3 — that every distinction is isomorphic to `Two` —
is a *genuine universal claim inside MLTT*. It is worth being precise
about how far that universality extends and where it stops, because
the boundary is exactly Gödel's and Tarski's.

**Tier 1 — quantification over `Set` (proved here).**
`Distinction : Set₁` is a record over carriers `S : Set`. The theorem
`two-normal-form : (d : Distinction) → DistinctionIso d Two-distinction`
therefore quantifies, internally, over *every type in `Set`* that
carries the data of two distinguishable, exhaustive points. There is
no parameter, no representative chosen by the proof; the same witness
works uniformly. This is the maximal universal claim that MLTT can
make on a single fixed universe level — and it is proved, not asserted.

**Tier 2 — quantification across the universe hierarchy (proved).**
The level-polymorphic carrier
```agda
Distinctionℓ : (ℓ : Level) → Set (lsuc ℓ)
```
([Void.lagda.tex L2512](Void.lagda.tex#L2512)) carries the same four
fields as the base record at every level. The level-polymorphic
two-element type, the canonical distinction, the boundary-preserving
isomorphism record, and the normal-form theorem
```agda
two-normal-formℓ :
  ∀ {ℓ} (d : Distinctionℓ ℓ) → DistinctionIsoℓ d (Two-distinctionℓ ℓ)
```
are proved by the same construction as the base case; the proof is the
literal level-polymorphic transport of the base-level proof. Tier 2 is
therefore not a mere routine extension waiting to be done — it is
discharged in the text itself, in the section
`Tier 2 Normal Form` immediately following the level-polymorphic
helpers.

**Tier 3 — quantification ranging over the entire universe hierarchy
at once (impossible in any consistent type theory).**
A single quantifier `(ℓ : Level) → …` does not range over Levels
themselves; it ranges over the values of an external `Level` type, and
the resulting statement lives in `Setω`. To collapse this further into
*one* universe holding *all* universes, one would need `Setω : Setω`
or its equivalent. This is exactly the Russell–Girard barrier: any
type theory that admits such a self-containing universe is
inconsistent. The boundary is therefore not a defect of `Void.lagda.tex`;
it is the boundary that *every* consistent type theory must respect.
The strongest internal universal claim available is Tier 2 above, and
the next step cannot be taken inside any sound system.

The formal arc of this work therefore reaches exactly as far as
Tier 2 reaches, and exactly stops where Tier 3 begins.

---

## 12. The directed dependency: distinction → logic → mathematics → physics

The preceding sections have stayed inside what `Void.lagda.tex` proves,
and §11 has marked the boundary at which internal proof must stop. The
present section names a structural reading of the two volumes that
*uses* those proofs but does not extend them. It is a reading, not a
theorem.

The two volumes, taken together, exhibit a directed dependency:

> distinction ⊏ logic ⊏ mathematics ⊏ physics

Each step is the *minimal* stabilisation that the previous one admits,
and each step strictly presupposes the previous one. The dependency is
one-way; the reverse arrows do not type-check.

- **distinction ⊏ logic.** Without a separation witness on a
  two-element carrier, the constructive infrastructure of
  `Void.lagda.tex` — negation, decidability on `Two`, the absurd
  patterns that drive every elimination — is vacuous. This is not a
  metaphor: the proofs in §§3–5 use `Two-L≠R : L ≠ R` (and the
  `Distinction`-field `ℓ≠r`) directly.
  Remove it and the file does not type-check.
- **logic ⊏ mathematics.** Part V of `Void.lagda.tex` constructs
  $\mathbb{N}$, $\mathbb{Z}$, $\mathbb{Q}$, $\mathbb{R}$ on top of the
  four-case classification and its decidable equality. The algebraic
  laws are theorems, not postulates. No arithmetic is granted;
  arithmetic is forced.
- **mathematics ⊏ physics.** `Form.lagda.tex` opens with
  `open import Void` and adds no mathematical content of its own.
  Every physical identification is tagged `physical-identification`
  (§9) and depends literally on the invariants exported by
  `Void.lagda.tex`. If a single invariant in `Void` were to disappear,
  the corresponding identification in `Form` would fail to type-check.

The reading that follows from this is structural: under the minimal
grant fixed in §1, **logic is the minimal stabilisation of distinction
in the form of decidability; mathematics is its extension to
relational and iterative structure; and physics is the further binding
of that structure to empirical invariants.** The three are not
independent disciplines arranged side by side. They are nested
stabilisations of the same underlying act of separation, and the
nesting is directed.

**What is and is not claimed here.** This is *not* a theorem inside
MLTT. A theorem of the form *"every formal discipline is a
stabilisation of distinction"* would quantify over the family of all
formal theories and would therefore live at the Tier 3 boundary
identified in §11 — the boundary that Tarski's undefinability of truth
and Gödel's incompleteness forbid any single theory from crossing
internally. What *is* claimed here is the architectural observation
that, *within the scope of the two volumes*, the dependency runs in
exactly this direction and in no other. `Form` cannot stand without
`Void`; `Void` cannot stand without its initial separation witness.
The reverse compositions have no inhabitants.

The reader should therefore take this section as a guide to how the
two volumes fit together, not as a proof that this is the only
possible architecture for any conceivable formal discipline. The proof
reaches only as far as Tier 1 reaches; the architectural reading
explains *why the proofs at Tier 1 are worth carrying out at all*.

---

## 13. One-line synthesis

Under the formal stage stated in §1, any structure inside that stage
whose only generating datum is the binary distinction collapses, by
elimination, onto $K_4$.

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
