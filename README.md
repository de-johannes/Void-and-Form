# Void and Form

`Void and Form` is proposed as a theory of formulability: an account of
the conditions under which mathematical, logical, and physical
description can become stable enough to be stated at all.

The project is governed by one structural claim. Formal description does
not begin from a presupposed ``nothing``. It begins only after
distinguishable positions are available. Without distinguishability, no
relation, judgement, equation, map, representation, truth-value, or
falsehood can be formulated.

`Void` names the pre-formal boundary before such formulation is
possible. It is not the empty set, not the empty type, and not a
physical nothing. It is the absence of the domain in which those notions
could already occur. `Form` names the structural interpretation of the
mathematical closure that appears once this boundary is represented.

The central claim has three layers:

- **Vision.** The work asks whether the architecture of formulability can
  be traced to a single irreducible distinction.
- **Method.** The formal core is executed in Agda under
  `--safe --without-K`. The relevant claims are implemented as terms,
  records, classifications, equivalences, and contradiction eliminations.
- **Interpretation.** The physical and ontological readings in `Form` are
  structural interpretations of the checked kernel. They are not
  presented as machine-checked proofs of physics.

This is not a retreat from the universal claim. It is the condition under
which the claim becomes scientifically legible: the formal chain carries
the architectural claim, and the architectural claim explains why the
formal chain matters.

---

## Structural schema

This table fixes the status of each layer before any technical theorem is
inspected. The first two levels state the pre-formal conditions of
formulability. From Level 2 onward, the formal claims of `Void` are
expressible and checkable inside intensional Martin-Lof type theory as
implemented in Agda; the later `Form` levels are structural readings of
that checked kernel.

### Void: conditions of formulability (pre-formal)

- **Level 0: Void.** No type, no term, no carrier. The schematic marker
  is $\mathcal{V} \notin \mathit{Set}_\omega$. Void is not a
  mathematical object inside the formal system; it names the absence of
  the domain in which objects can already be introduced.
- **Level 1: Information.** Information is difference that makes a
  difference. Without distinction, an occurrence carries no information.
  Information therefore is not added to Void; it is the first condition
  under which non-collapse can be spoken of at all.

### Void: formal execution (machine-checked)

- **Level 2: Two.** The first stable formal carrier is
  `data Two : Set where L R : Two`. It contains two separated points and
  no third generator. It is the normal form of the `Distinction` record,
  not a prior truth-value object.
- **Level 3: Logic.** Formal systems operate on structures in which
  positions can be distinguished, related, mapped, and judged. Logic
  does not create distinction; it presupposes it as the condition of its
  own syntax and semantics.
- **Level 4: Mathematics.** Once the binary carrier is represented, the
  endomorphism space `Two -> Two` has exactly four cases. Under the
  explicit representation contract of separation, complete realisation,
  and no surplus, those cases close as the complete graph on four
  vertices, $K_4$. Arithmetic, spectral structure, and invariant ledgers
  unfold over that closure; they do not supply a new generator.

### Form: structural reading and interpretation

- **Level 5: Form.** The interpretive volume reads the stability
  conditions of distinction structurally. Two distinguishable occurrences
  collapse if neither origin nor position can distinguish them.
  Non-identity of origin gives the germ of temporal order;
  non-coincidence gives the germ of spatial separation. Space and time
  are not asserted as primitive entities here. They name conditions under
  which distinction does not collapse.
- **Level 6: Physics.** Physics enters as interpretation of the preceding
  structural conditions by an observer who already operates inside them.
  Form is not physics; it is the structure from which physical
  description can be read.
- **Level 7: Contingency.** Concrete cosmology, empirical constants, and
  measured values belong to the contingent layer. They can be compared
  with the structural ledger, but they are not produced by stipulating a
  physical universe at the start.
- **Level 8: Induction.** No new external generator is postulated. Each
  new level inherits the constraint of the previous level and asks what
  still survives without contradiction.

## The claim and its chain

The formulability claim is not that Agda has proved the physical
universe. The claim is that the project gives a formal basis for a
theory of formulability.

The chain is:

1. Formal description presupposes distinguishable positions.
2. A represented binary distinction is the first stable formal carrier.
3. Every such carrier has normal form `Two`.
4. The endomorphism space `Two -> Two` has exactly four cases.
5. A faithful representation of those four cases closes as $K_4$.
6. The closed record presupposes the originating `Distinction`.
7. Arithmetic and invariant ledgers are developed internally over that
  closed kernel.
8. `Form` reads the kernel as a structural basis for physical and
  epistemological description.

If any formal step in this chain fails, the formulability claim loses
its formal base. If the chain holds, the claim is not a stylistic
flourish: it is the architectural reading of the checked dependency
structure.

## Meta-theoretical status

Levels 0 and 1 are not formal statements inside a type system. They
state the conditions under which formal statements can appear. From
Level 2 onward the formal theory begins, and the claims are expressible
and checkable in Martin-Lof type theory as implemented by Agda.

This distinction is the core discipline of the project. Treat the
pre-formal boundary as an Agda theorem, and the beginning overclaims.
Treat the checked theorems as metaphor, and the execution is lost.
Treat the physical readings as premises, and the interpretation becomes
numerology. Treat the formulability claim as a mere slogan, and the
chain loses its reason for being. The work stands only while claim,
proof, and interpretation keep their proper status.

### Status ledger

The strongest claims in the project do not all have the same epistemic
status.

- **Boundary markers.** Pre-formal distinguishability, `Void` as the
  boundary before type/term/carrier, and the passage from that boundary
  to the record `Distinction` are not Agda theorems. They mark the
  conditions under which a formal theorem can begin, and the formal
  file then receives those conditions as explicit data.
- **Framework contracts.** The binary entry, the representation contract
  of separation/realisation/no surplus, and the use of MLTT/Agda under
  `--safe --without-K` are argued and fixed as the framework of formal
  execution. They are not hidden `refl`-facts.
- **Checked kernel.** From the displayed `Distinction` data onward, the
  normal form `Two`, the four endomorphism cases, the $K_4$ closure
  relative to the representation contract, the loop back to
  `Distinction`, and the invariant/evaluation records are machine
  checked inside the stated formal setting.
- **Structural interpretation.** The physical readings in `Form` are
  presented as interpretations of the checked kernel. They can be
  argued, compared, and falsified as readings of the world, but they are
  not labelled as Agda theorems.

## Inheritance

The thesis that distinction precedes structured description is not new.
It belongs to a long line that includes George Spencer-Brown's
`Laws of Form`, Gregory Bateson's definition of information as a
difference that makes a difference, Wheeler's `it from bit`, and the
logical boundary work of Wittgenstein, Godel, and Tarski.

What is new here is not the question but the execution. The constraints
are explicit, minimal, and mechanically checked once the formal
threshold is crossed. The work does not merely design a system; it asks
what structure remains when weaker or richer beginnings are eliminated.
That survivor is the formal basis of the proposed theory of
formulability.

## Reading order

Start with [VoidCompanion.lagda.tex](VoidCompanion.lagda.tex) and its
generated [PDF](latex/VoidCompanion.pdf). The companion is the compact
map and self-contained formal kernel of the repository. It states the
boundary, then proves the small spine a reviewer can inspect without
first reading the full book.

Then read [Void.lagda.tex](Void.lagda.tex). It is the long formal
development: it rebuilds the infrastructure internally, derives the
binary normal form, classifies the four endomorphism cases, closes them
at $K_4$, and carries the arithmetic and invariant ledger that remain
inside the formal layer.

[Form.lagda.tex](Form.lagda.tex) is the interpretive volume. It carries
the theory of formulability into physical and epistemological language.
Its identifications are structural hypotheses about the world, not
theorems of `Void`.

## Formal hinge

Once the data of a binary distinction are represented - two separated,
exhaustive points, and no further generator - the Agda-checked spine is
the following:

- **Normal form** (`two-normal-form`, [L1693](Void.lagda.tex#L1693)).
  Every record `(S, l, r, l != r, cover)` over `S : Set` is
  boundary-preservingly isomorphic to the canonical inhabitant on
  `Two`. The theorem quantifies internally over every type in `Set`
  carrying two distinguishable, exhaustive points; the
  level-polymorphic version `two-normal-formℓ` extends the same result
  across the universe hierarchy.
- **Exhaustion of endomorphisms** (`EndoCase`, `classify-sound`,
  `classify-unique`, [L1186](Void.lagda.tex#L1186),
  [L1308](Void.lagda.tex#L1308), [L1369](Void.lagda.tex#L1369)). The endomorphism space
  `Two -> Two` has exactly four cases: identity, swap, and the two
  constants. Nothing else survives.
- **Carrier closure** (`FaithfulClosure`, `MinimalClosure`,
  `K4Record-is-canonical`, [L26754-L26763](Void.lagda.tex#L26754-L26763),
  [L27359](Void.lagda.tex#L27359)). The representation contract is
  explicit: separation keeps distinct cases apart, complete realisation
  gives every case a vertex, and no surplus forbids vertices not
  realized by a case. Under that contract, fewer than four vertices
  identify cases, while more than four add structure not forced by the
  four cases.
- **Dependency theorem** (`record-presupposes-distinction`,
  [L31967](Void.lagda.tex#L31967)). Every inhabitant of `K4Record`
  entails an inhabitant of `Distinction`. The closed record is not an
  independent axiom; it presupposes and reprojects the originating
  distinction.

If this hinge fails, the larger development fails at its root. If it
holds, the remaining formal work is continuation over the survivor, not
the addition of a new generator. This hinge is where the formulability
claim earns its formal weight: the architecture is not asserted first
and decorated later; it is carried by the dependency chain.

## Note on the author

This project was developed outside an institutional mathematics setting
and with the help of large language models. Those facts explain the
working process; they do not decide the formal status of the results.
The Agda type checker is the judge of the checked kernel. This document
is written for readers who want to inspect that kernel directly. Where
the philosophical terminology is stronger than standard mathematical
usage, the corresponding Agda definition or theorem is cited so that the
formal content can be read without relying on the prose.

---

## Scope of the file

Every type, operation, and lemma used in `Void.lagda.tex` is defined
inside the file. The chapters are interleaved by use rather than ordered
by topic; the references below point to the defining anchor of each
layer and to the chapter heading that opens it.

- **Foundations.** Propositional equality, universe lifting,
  $\Sigma$-types, disjoint unions, negation, pointwise equality `≗`.
  Chapter `Minimal Logical Infrastructure`,
  [L553](Void.lagda.tex#L553).
- **Distinction and its laws.** `Distinction` record at
  [L837](Void.lagda.tex#L837); the canonical inhabitant
  `Two-distinction` at [L1582](Void.lagda.tex#L1582); chapter
  `Non-Vacuity`, [L862](Void.lagda.tex#L862).
- **Endomorphism classification of `Two → Two`.** `EndoCase` at
  [L1178](Void.lagda.tex#L1178); classification module `K₄` at
  [L1212](Void.lagda.tex#L1212); top-level wrappers
  `k4-classification-sound` / `-unique` at
  [L1438–L1454](Void.lagda.tex#L1438-L1454).
- **Two-normal form, orientation, automorphisms.** Chapter
  `Two Normal Form` at [L1554](Void.lagda.tex#L1554);
  `two-normal-form` at [L1685](Void.lagda.tex#L1685);
  `orientation-exhaustive` at [L1921](Void.lagda.tex#L1921).
- **Drift: a strict total order on $\omega$.** Chapter `Drift` at
  [L2536](Void.lagda.tex#L2536), through chapters
  `Non-Collapse of Drift`, `Cross-Stage Comparison`,
  `Drift Reachability`, `Drift Acyclicity` (last starts at
  [L3196](Void.lagda.tex#L3196)).
- **Naturals $\mathbb{N}$.** Chapter `The Naturals as a W-Type over
  Two` at [L5342](Void.lagda.tex#L5342); `Arithmetic Infrastructure`
  at [L5440](Void.lagda.tex#L5440); `Forced Additive Laws` at
  [L6302](Void.lagda.tex#L6302); `Multiplicative Structure and Integer
  Order` at [L6586](Void.lagda.tex#L6586).
- **Integers $\mathbb{Z}$.** Chapter `Integer Multiplication Laws` at
  [L7217](Void.lagda.tex#L7217); `Integer Order Laws` at
  [L8268](Void.lagda.tex#L8268); `Absolute Value Laws` at
  [L8671](Void.lagda.tex#L8671).
- **Rationals $\mathbb{Q}$.** Chapter `Rational Numbers and Measurement`
  at [L10426](Void.lagda.tex#L10426); `Rational Setoid and Order Laws`
  at [L11274](Void.lagda.tex#L11274); `Rational Addition and
  Multiplication Laws` at [L12916](Void.lagda.tex#L12916);
  `Rational Distance Laws` at [L17215](Void.lagda.tex#L17215).
- **Reals $\mathbb{R}$.** Chapter
  `Reals as Forced Cauchy Closure over Q` at
  [L21363](Void.lagda.tex#L21363); `record ℝ` at
  [L21405](Void.lagda.tex#L21405); chapter
  `Cauchy Completeness of R` at
  [L23891](Void.lagda.tex#L23891);
  `IsCauchyℝ` / `_converges-to_` at
  [L24084–L24092](Void.lagda.tex#L24084-L24092);
  `ℝ-cauchy-complete` at [L24500](Void.lagda.tex#L24500).
- **Spectral graph theory on $K_4$, $K_8$, $K_{12}$.** Chapter
  `K₄ Neighborhood and Laplacian` at
  [L6784](Void.lagda.tex#L6784); `Laplacian as Finite-Index Operator`
  at [L11510](Void.lagda.tex#L11510); `Coupled K₄ Laplacian` at
  [L13375](Void.lagda.tex#L13375); `Triple K₄ Laplacian` at
  [L14594](Void.lagda.tex#L14594).
- **The kind classification of invariants.** Chapter at
  [L9324](Void.lagda.tex#L9324); the four-case data type
  `InvariantKind` at [L9407](Void.lagda.tex#L9407) and the closure
  theorem `kind-exhaustive` at [L9418](Void.lagda.tex#L9418).
- **Minimal $K_4$ representation contract and invariant record.**
  `FaithfulClosure` / `MinimalClosure` at
  [L26746-L26755](Void.lagda.tex#L26746-L26755);
  `K4Record` at [L26992](Void.lagda.tex#L26992);
  singleton lemma `K4Record-is-canonical` at
  [L27351](Void.lagda.tex#L27351).
- **Loop closure.** `record-presupposes-distinction` at
  [L31959](Void.lagda.tex#L31959).

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
equality with its standard eliminator.

```agda
{-# OPTIONS --safe --without-K #-}
module Void where
```

Reference: [Void.lagda.tex L563–L568](Void.lagda.tex#L563-L568).

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
[Void.lagda.tex L1568–L1589](Void.lagda.tex#L1568-L1589),
[L1685](Void.lagda.tex#L1685) (`two-normal-form`).

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
[Void.lagda.tex L837](Void.lagda.tex#L837) (`Distinction`),
[L1603](Void.lagda.tex#L1603) (`DistinctionIso`),
[L1685](Void.lagda.tex#L1685) (`two-normal-form`),
[L1921–L1935](Void.lagda.tex#L1921-L1935) (orientation classification:
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
[Void.lagda.tex L1178](Void.lagda.tex#L1178) (`EndoCase`),
[L1212](Void.lagda.tex#L1212) (classification module `K₄`),
[L1438–L1454](Void.lagda.tex#L1438-L1454) (top-level wrappers).

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

Reference: [Void.lagda.tex L26992](Void.lagda.tex#L26992) (`K4Record`).

---

## 6. Uniqueness and the loop

```agda
k4Record-inhabited             : K4Record
k4Record-unique                : (r₁ r₂ : K4Record) → r₁ ≡ r₂
record-presupposes-distinction : (p : K4Record) → Distinction
```

The first two state that `K4Record` is a singleton up to propositional
equality. The third states that any inhabitant of `K4Record` entails a
`Distinction`; for the canonical record this recovers `Two-distinction`,
closing the chain
`Two-distinction ⇒ EndoCase ⇒ K₄ ⇒ K4Record ⇒ Two-distinction`.

References:
[Void.lagda.tex L27351](Void.lagda.tex#L27351) (`K4Record-is-canonical`),
[L31959](Void.lagda.tex#L31959) (`record-presupposes-distinction`).

---

## 7. Forced numerical invariants

Once the closure record is fixed, several integer-valued quantities are
determined. Each of the following holds by reduction; the witness in
every case is `refl`.

| Identity | Reference |
|---|---|
| `eulerChar-computed ≡ 2` (`law16B-3-euler`) | [L26244](Void.lagda.tex#L26244) |
| `simplex-eval ≡ 137` (`law15A-0-simplex-eval-137`) | [L10509](Void.lagda.tex#L10509) |
| `loop-numerator ≡ 11` (`law-loop-num-11`) | [L30644](Void.lagda.tex#L30644) |
| `theorem-sign-forcing` | [L31899](Void.lagda.tex#L31899) |

Inside the $70$-monomial pool of degree $\leq 4$ in $(V,E,d,\chi)$
fixed by the same forced values, the integer $137$ admits exactly one
pair-sum decomposition — the canonical identity $d^2 + V^3\chi$.
`theorem-pair-sum-degree-4-count` establishes that the hit count
is exactly 2 (the ordered pair and its mirror), and
`theorem-degree-bounded-exhaustion-deg4` packages the canonical hit,
the identity $V^3\chi = V^d \cdot \chi$, and the unique count into a
single closure record, all by `refl`
([L10982–L11004](Void.lagda.tex#L10982-L11004)).
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
uniqueness statement above has been checked.

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
[Form.lagda.tex L270](Form.lagda.tex#L270),
[L897](Form.lagda.tex#L897),
[L1341–L1345](Form.lagda.tex#L1341-L1345).

### Empirical surface of Form

The separation above does not reduce `Form` to a catalogue of suggestive
integers. Its claim is sharper and more vulnerable: once a
Void-internal invariant is read as a physical observable, the reading is
tested by correction chains, sigma deviations, and explicit failure
conditions. A failed physical identification would not break `Void`, but
it would break that part of `Form`.

The current Form ledger reports the following post-correction empirical
comparisons:

| Observable | Form comparison |
|---|---|
| $\alpha^{-1}$ | second-order correction $137 + 11/306 + 295/(306 \cdot 137^2) = 137.035\,999\,076\ldots$, within $0.4\sigma$ of CODATA; alternative interpolation degrees are listed as $2445\sigma$ and $4891\sigma$ failures ([Form.lagda.tex L4907–L4945](Form.lagda.tex#L4907-L4945)). |
| $m_p/m_e$ | correction chain $949\sigma \to 20\sigma \to 0.08\sigma$ ([Form.lagda.tex L5799](Form.lagda.tex#L5799)). |
| $m_\mu/m_e$ | correction chain $36\sigma \to 13\sigma \to 0.12\sigma$ ([Form.lagda.tex L5800](Form.lagda.tex#L5800)). |
| $m_\tau/m_\mu$ | remains closed at about $0.1\sigma$ through the mass-ratio chain ([Form.lagda.tex L5801](Form.lagda.tex#L5801)). |
| $\sin^2\!\theta_W$ | weak-mixing chain $7.7\sigma \to 5.0\sigma \to 3.5\sigma \to 0.001\sigma$ ([Form.lagda.tex L6031](Form.lagda.tex#L6031)). |
| $\Omega_m$ | $K_4$ gives $\Omega_m \approx 0.3183$, within $0.5\sigma$ of Planck; $K_3$ and $K_5$ are reported as $10.9\sigma$ and $11.8\sigma$ away ([Form.lagda.tex L1717–L1735](Form.lagda.tex#L1717-L1735)). |

`Form` also names tests that remain open or frontier-facing. The
B-meson lepton-universality anomaly is tied to the muon bridge factor
$16/69 \approx 0.232$ as a Wilson-coefficient target, to be tested
against the full published $R_K$ central value and uncertainty
([Form.lagda.tex L8899–L8931](Form.lagda.tex#L8899-L8931)). The doubly
charmed baryon ledger predicts the two-slot $\Xi_{cc}$ doublet structure,
with the reported LHCb $7\sigma$ observation read as physical occupation
of that ledger rather than as a mass prediction
([Form.lagda.tex L9010–L9034](Form.lagda.tex#L9010-L9034)). The frontier
register predicts exactly two gravitational-wave polarizations, no scalar
or vector extras, a neutrino seesaw at loop depth $5$, Planck-scale
curvature $R = 12$, no fourth generation, and no extra spacetime
dimension ([Form.lagda.tex L10990–L11112](Form.lagda.tex#L10990-L11112)).

---

## 10. What is and is not claimed

Claimed and machine-verified inside `Void.lagda.tex`:

- Sections 3–7 above, in full. In particular: `Two` is the
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
([Void.lagda.tex L2545](Void.lagda.tex#L2545)) carries the same four
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
reaches only as far as Tier 2 reaches; the architectural reading
explains *why those proofs are worth carrying out at all*.

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
