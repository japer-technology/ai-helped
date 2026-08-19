# +AI-001 Specification Family Architecture

**Status:** Draft
**Version:** 0.1.0
**Identifier:** `+AI-001`
**Short name:** Family Architecture

---

# 1. Purpose

This specification defines the architecture of the `+AI` specification family.

It establishes:

* specification identifiers;
* specification-number ranges;
* versioning;
* dependencies;
* extension semantics;
* visible-notation composition;
* registries;
* profiles;
* bindings;
* conformance;
* the abstract declaration model;
* and rules governing evolution of the family.

This specification does not redefine the meaning of the canonical `+AI` declaration.

The semantic meaning of `+AI` is defined by `+AI-100`.

---

# 2. Architectural principle

The `+AI` specification family separates:

1. **human-readable declaration**;
2. **semantic assertions**;
3. **machine-readable representation**;
4. **supporting evidence**;
5. **domain-specific requirements**.

The human-readable notation SHOULD remain compact.

Additional semantic detail SHOULD normally be expressed through composable specifications and machine-readable metadata rather than by making the base `+AI` mark progressively more complex.

The architectural principle is:

> **Keep the declaration simple. Make the specification family extensible.**

---

# 3. Normative terminology

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative.

**MUST** indicates an absolute requirement.

**MUST NOT** indicates an absolute prohibition.

**SHOULD** indicates a strong recommendation that may be departed from where a legitimate reason exists.

**SHOULD NOT** indicates a practice normally avoided but potentially justified.

**MAY** indicates an optional practice.

---

# 4. Specification identifiers

Every specification in the family MUST have a permanent identifier of the form:

```text
+AI-NNN
```

where `NNN` is a three-digit decimal number.

Examples:

```text
+AI-001
+AI-100
+AI-310
+AI-710
```

Once allocated, a specification identifier MUST NOT be reused for a semantically unrelated specification.

A withdrawn identifier remains permanently allocated.

---

# 5. Specification families

The following number ranges are established.

| Range     | Family                | Purpose                                                                |
| --------- | --------------------- | ---------------------------------------------------------------------- |
| `000–099` | Architecture          | Architecture, terminology, registries, abstract models and conformance |
| `100–199` | Accountability        | Responsibility, adoption and release                                   |
| `200–299` | Participation         | Degree, character and mode of AI participation                         |
| `300–399` | Assurance             | Human review, verification, testing and validation                     |
| `400–499` | Provenance            | Contribution history, derivation and provenance                        |
| `500–599` | Authority and Agency  | Delegation, agent activity and autonomous activity                     |
| `600–699` | Identity and Evidence | Identity, signatures, attestations and cryptographic evidence          |
| `700–799` | Bindings              | JSON, web, document, software and protocol representations             |
| `800–899` | Profiles              | Domain-specific application profiles                                   |
| `900–999` | Reserved              | Future family-wide use                                                 |

---

# 6. Initial specification catalogue

The following identifiers are provisionally allocated.

| Identifier | Working title                          |
| ---------- | -------------------------------------- |
| `+AI-001`  | Specification Family Architecture      |
| `+AI-010`  | Registry and Conformance               |
| `+AI-020`  | Abstract Data Model                    |
| `+AI-100`  | Human-AI Provenance and Accountability |
| `+AI-210`  | AI Participation Classification        |
| `+AI-220`  | AI-Primary Production                  |
| `+AI-310`  | Human Review                           |
| `+AI-320`  | Independent Verification               |
| `+AI-330`  | Validation and Testing                 |
| `+AI-410`  | Provenance Record                      |
| `+AI-420`  | Contribution Chain                     |
| `+AI-430`  | Artifact Derivation                    |
| `+AI-510`  | Delegation and Authority               |
| `+AI-520`  | AI Agent Activity                      |
| `+AI-530`  | Autonomous AI Release                  |
| `+AI-610`  | Responsible-Party Identity             |
| `+AI-620`  | AI System and Model Identity           |
| `+AI-630`  | Cryptographic Evidence                 |
| `+AI-710`  | JSON Binding                           |
| `+AI-720`  | Web Binding                            |
| `+AI-730`  | Document Binding                       |
| `+AI-740`  | Software Binding                       |
| `+AI-810`  | Software Profile                       |
| `+AI-820`  | Research Profile                       |
| `+AI-830`  | Publishing and Media Profile           |
| `+AI-840`  | Government Profile                     |
| `+AI-850`  | Legal Profile                          |
| `+AI-860`  | Education Profile                      |

Allocation does not by itself define semantics.

A provisionally allocated specification has normative effect only when an applicable version has been published.

---

# 7. Versioning

Specifications use:

```text
MAJOR.MINOR.PATCH
```

Example:

```text
+AI-310 v1.2.0
```

A **MAJOR** version change indicates an incompatible normative semantic change.

A **MINOR** version change indicates a backward-compatible normative addition or clarification.

A **PATCH** version change indicates an editorial correction or other change that does not alter normative semantics.

Versions below `1.0.0` are developmental.

Compatibility between `0.x` versions MUST NOT be assumed.

Stable machine dependencies SHOULD normally reference the specification identifier and major version:

```text
+AI-310@1
```

Draft dependencies MAY reference:

```text
+AI-310@0
```

Visible `+AI` notation MUST NOT encode specification version numbers unless another specification explicitly defines such a presentation.

---

# 8. Specification dependencies

`+AI-001` defines the family architecture.

`+AI-100` defines the canonical `+AI` accountability declaration.

A specification that extends the `+AI` declaration MUST depend upon:

```text
+AI-001
+AI-100
```

and MAY depend upon additional specifications.

A profile MAY require conformance with several specifications.

A profile MUST NOT redefine the normative meaning of a specification upon which it depends.

---

# 9. Core semantic invariance

The meaning of the canonical `+AI` declaration is owned by `+AI-100`.

Extension specifications MUST NOT:

* weaken the meaning of `+AI`;
* silently replace its accountability semantics;
* redefine its responsible party;
* convert responsibility into mere attribution;
* or imply that responsibility belongs to an AI system.

Extensions MAY add additional claims.

Therefore:

```text
+AI[review]
```

means:

```text
meaning(+AI)
AND
meaning(review)
```

It does not mean a different form of `+AI`.

---

# 10. Monotonic extension rule

Every extension MUST be semantically additive.

For declaration `D` and extension `E`:

```text
meaning(D[E]) = meaning(D) AND meaning(E)
```

An extension MUST NOT cause a previously asserted claim to become false.

An extension whose semantics conflict with its root declaration MUST be declared incompatible with that root.

---

# 11. Absence is not negation

Absence of an extension MUST NOT be interpreted as the negation of that extension.

Therefore:

```text
Eric Mourant +AI
```

does not imply:

```text
not reviewed
not verified
human-primary
no provenance
unsigned
no agents
```

It asserts only the claims defined by the specifications actually represented.

This rule applies to both human-readable and machine-readable representations.

---

# 12. Canonical visible-extension syntax

The base mark remains:

```text
+AI
```

An extended declaration MAY use:

```text
+AI[extension]
```

Multiple extensions MAY be composed:

```text
+AI[extension1,extension2,extension3]
```

The canonical grammar is:

```text
declaration    = root [ "[" extension-list "]" ]

extension-list = extension *("," extension)

extension      = token

token          = lower *( lower / digit / "-" )
```

where `lower` is an ASCII lowercase character `a-z`.

Canonical extension syntax:

* MUST use lowercase extension tokens;
* MUST NOT contain whitespace inside the brackets;
* MUST separate tokens with a single comma;
* MUST NOT duplicate a token;
* MUST use registered canonical tokens.

Example:

```text
+AI[primary,review,prov]
```

---

# 13. Canonical ordering

Extension tokens MUST have a deterministic canonical order.

The default canonical order is ascending identifier of the specification defining the extension.

Where one specification defines multiple extension tokens, that specification MUST define their internal canonical order.

A renderer MAY visually rearrange extensions for presentation purposes only where the complete canonical declaration remains available.

Machine serialization MUST use canonical order.

---

# 14. Extension registry

Each registered extension MUST contain at least:

```text
token
defining specification
status
canonical order
permitted root declarations
incompatible declarations
human-readable meaning
machine-readable assertion type
```

Tokens MUST NOT be assigned conflicting meanings.

A deprecated token MUST NOT be reassigned.

---

# 15. Initial extension registry

The following tokens are provisionally reserved.

| Token       | Defining specification | Status   |
| ----------- | ---------------------- | -------- |
| `primary`   | `+AI-220`              | Reserved |
| `review`    | `+AI-310`              | Draft    |
| `verify`    | `+AI-320`              | Reserved |
| `prov`      | `+AI-410`              | Reserved |
| `delegated` | `+AI-510`              | Reserved |
| `agent`     | `+AI-520`              | Reserved |
| `signed`    | `+AI-630`              | Reserved |

A reserved token MUST NOT be treated as carrying normative meaning until its defining specification establishes that meaning.

---

# 16. Root declarations

`+AI` is a root declaration.

Other root declarations MAY be defined by future specifications where their semantics cannot validly be represented as an additive extension of `+AI`.

A new root declaration MUST have substantially distinct semantics that justify a separate root.

In particular, a declaration representing release without qualifying human adoption MUST NOT be encoded as an extension that weakens or contradicts `+AI`.

This version does not define an autonomous-release root notation.

That matter is reserved for `+AI-530`.

---

# 17. Human-readable and graphical forms

The canonical textual declaration MUST remain sufficient to express its normative meaning.

Graphical badges, icons, colours or logos MAY accompany a declaration.

A graphical presentation MUST NOT change the semantic meaning of the underlying declaration.

Where a graphical form is used, an equivalent canonical textual representation SHOULD remain available.

---

# 18. Abstract model

The specification family recognises the following foundational entities:

```text
Party
AISystem
Agent
Artifact
ArtifactVersion
Activity
AuthorityGrant
Adoption
Release
ResponsibilityDeclaration
AssuranceAssertion
Evidence
IdentityClaim
```

These entities form a graph.

A specification MAY define additional entities or relationships.

---

# 19. Artifact and release distinction

An `Artifact` represents a logical work.

An `ArtifactVersion` represents a particular state of that work.

A `Release` represents a decision or event by which an artifact version is published, transmitted, deployed, submitted, presented or otherwise made operative.

Responsibility declarations SHOULD be associated with a specific release.

This permits the same artifact version to have different accountability states in different releases.

---

# 20. Adoption

`Adoption` represents a qualifying human or organisational act of knowingly accepting a particular artifact version for a particular release.

Delegating permission to an AI system or agent to produce an artifact does not, by itself, constitute adoption of every artifact produced under that delegation.

Delegating release authority does not, by itself, constitute artifact-specific human adoption.

---

# 21. Responsibility declaration

A `ResponsibilityDeclaration` binds:

```text
responsible party
artifact version
adoption
release
applicable specifications
```

A declaration SHOULD be treated as release-specific.

A subsequent release MAY require a new responsibility declaration even where the artifact version is unchanged.

---

# 22. Activity graph

Human and AI contribution SHOULD be modelled as activities rather than percentages of authorship.

An activity MAY:

```text
consume artifacts
produce artifacts
modify artifacts
evaluate artifacts
review artifacts
verify artifacts
release artifacts
delegate authority
```

Activities MAY be performed by:

```text
people
organisations
AI systems
agents
```

The provenance graph MAY therefore represent arbitrarily complex chains of human and machine contribution.

---

# 23. Authority graph

Authority MUST be modelled separately from contribution.

An `AuthorityGrant` MAY identify:

```text
grantor
grantee
scope
delegation permission
release permission
validity period
parent authority grant
```

The fact that an actor produced an artifact does not imply authority to release it.

The fact that an actor had authority to release an artifact does not imply that a qualifying human adoption occurred.

---

# 24. Assurance assertions

Review, verification, validation and testing are `AssuranceAssertion` types.

Assurance assertions MUST identify their subject.

An assurance assertion SHOULD identify:

```text
actor
scope
method
time
status
supporting evidence
```

Assurance specifications MUST state exactly what their assertions do and do not guarantee.

---

# 25. Projection rule

A visible declaration SHOULD be a projection of valid semantic assertions.

For example, the visible notation:

```text
+AI[review]
```

is valid only where:

1. a valid `+AI` responsibility declaration exists; and
2. a valid `+AI-310` human-review assertion applies to the released artifact version.

A machine MUST NOT create extension notation merely because a token string has been supplied.

The underlying semantic condition MUST be satisfied.

---

# 26. Unknown extensions

A consumer encountering an unknown extension token:

* MUST NOT infer its meaning;
* MUST NOT interpret it as another known extension;
* SHOULD preserve it when round-tripping a declaration;
* MAY report that its semantics are unknown.

Unknown extensions MUST NOT invalidate known claims unless a governing profile explicitly requires complete extension recognition.

---

# 27. Profiles

A profile defines how specifications apply within a domain.

A profile MAY:

* require particular specifications;
* prohibit optional features;
* require additional evidence;
* define domain-specific review scopes;
* define domain-specific identity requirements;
* establish minimum assurance levels.

A profile MUST NOT redefine the meaning of a registered extension.

Example:

```text
+AI-820 Research Profile
```

might require:

```text
+AI-100
+AI-310
+AI-410
```

without changing what those specifications mean.

---

# 28. Bindings

A binding defines how the abstract model is represented in a particular technical environment.

Bindings MAY include:

```text
JSON
JSON-LD
HTML
HTTP
document metadata
software repository metadata
content credentials
digital signatures
```

A binding MUST preserve the semantics of the underlying specification.

Representation-specific limitations MUST NOT silently alter normative meaning.

---

# 29. Persistence across transformations

An assertion MAY remain valid across a transformation where the transformation does not materially alter the subject to which the assertion applies.

Material transformations SHOULD produce a new `ArtifactVersion`.

Bindings SHOULD preserve links between derived artifact versions.

Specifications defining assurance assertions MUST state when those assertions survive transformation.

---

# 30. Multiple responsible parties

Multiple parties MAY independently accept responsibility for the same release.

Each responsible party SHOULD have an independently representable responsibility declaration.

For example:

```text
JAPER Technology +AI
Eric Mourant +AI
```

represents two responsibility declarations.

A machine-readable representation MUST NOT infer joint responsibility merely from textual proximity.

---

# 31. Conformance classes

The family defines the following general conformance classes.

### 31.1 Declaration conformance

A declaration conforms when its asserted semantic conditions are satisfied.

### 31.2 Producer conformance

A producer conforms when it emits declarations and metadata according to the applicable specifications.

### 31.3 Consumer conformance

A consumer conforms when it interprets known declarations according to their registered semantics and handles unknown declarations according to this specification.

### 31.4 Binding conformance

A binding conforms when it faithfully represents the abstract model and applicable normative assertions.

### 31.5 Profile conformance

An implementation conforms to a profile when it satisfies every requirement declared mandatory by that profile.

---

# 32. Misrepresentation

A declaration is non-conforming where its notation represents a semantic assertion that is not actually satisfied.

Examples include:

```text
+AI[review]
```

where complete substantive human review did not occur;

or:

```text
+AI[prov]
```

where no conforming provenance record exists.

The visible existence of a token MUST NOT be treated as self-validating evidence.

---

# 33. Evidence

Evidence MAY support any assertion.

Evidence may include:

```text
hashes
signatures
review records
activity logs
attestations
identity credentials
timestamps
repository history
provenance records
```

Evidence and declaration are distinct.

A claim can exist without cryptographic evidence unless the applicable specification requires such evidence.

---

# 34. Evolution

New specifications SHOULD preserve:

* the simplicity of `+AI`;
* semantic composability;
* explicit human accountability;
* machine interpretability;
* deterministic representation;
* non-reliance on authorship percentages;
* and separation between declaration and evidence.

Backward-compatible capabilities SHOULD normally be introduced as new specifications or minor versions.

Existing semantics SHOULD NOT be overloaded.

---

# 35. Canonical architecture statement

The `+AI` specification family is based on the following model:

> **A compact visible declaration represents one or more precisely defined semantic assertions. Those assertions apply to identifiable parties, artifacts, activities, adoptions and releases, and may be supported by provenance and evidence. Extensions add meaning; they do not alter the meaning already present.**

The architectural invariant is:

# **Simple declaration. Explicit semantics. Extensible evidence.**
