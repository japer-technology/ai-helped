# +AI Specification Family v0.1

---
Status: Draft
Version: 0.1
Date: 2026-08-19
---

## Family-level normative terminology

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative.

**MUST** indicates an absolute requirement.

**MUST NOT** indicates an absolute prohibition.

**SHOULD** indicates a strong recommendation that may be departed from where a legitimate reason exists.

**SHOULD NOT** indicates a practice normally avoided but potentially justified.

**MAY** indicates an optional practice.

## Module +AI-001 — Specification Family Architecture

**Status:** Draft  
**Version:** 0.1  
**Identifier:** `+AI-001`  
**Dependencies:** None  

### Purpose

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

The semantic meaning of `+AI` is defined by `+AI-100@0`.

### Architectural principle

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

### Specification identifiers

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

### Specification families

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

### Initial specification catalogue

The following identifiers are provisionally allocated within the family.

| Identifier | Working title                          | Status       |
| ---------- | -------------------------------------- | ------------ |
| `+AI-001`  | Specification Family Architecture      | Draft        |
| `+AI-010`  | Registry and Conformance               | Provisional  |
| `+AI-020`  | Abstract Data Model                    | Draft        |
| `+AI-100`  | Core +AI Declaration                   | Draft        |
| `+AI-210`  | AI Participation Classification        | Draft        |
| `+AI-220`  | AI-Primary Production                  | Provisional  |
| `+AI-310`  | Human Review                           | Draft        |
| `+AI-320`  | Independent Verification               | Draft        |
| `+AI-330`  | Validation and Testing                 | Provisional  |
| `+AI-410`  | Provenance Record                      | Draft        |
| `+AI-420`  | Contribution Chain                     | Provisional  |
| `+AI-430`  | Artifact Derivation                    | Provisional  |
| `+AI-510`  | Delegation and Authority               | Provisional  |
| `+AI-520`  | AI Agent Activity                      | Provisional  |
| `+AI-530`  | Autonomous AI Release                  | Draft        |
| `+AI-610`  | Responsible-Party Identity             | Provisional  |
| `+AI-620`  | AI System and Model Identity          | Provisional  |
| `+AI-630`  | Cryptographic Evidence                 | Provisional  |
| `+AI-710`  | JSON Binding                           | Draft        |
| `+AI-720`  | Web Binding                            | Provisional  |
| `+AI-730`  | Document Binding                       | Provisional  |
| `+AI-740`  | Software Binding                       | Provisional  |
| `+AI-810`  | Software Profile                       | Provisional  |
| `+AI-820`  | Research Profile                       | Provisional  |
| `+AI-830`  | Publishing and Media Profile           | Provisional  |
| `+AI-840`  | Government Profile                     | Provisional  |
| `+AI-850`  | Legal Profile                          | Provisional  |
| `+AI-860`  | Education Profile                      | Provisional  |

Allocation does not by itself define semantics.

A provisionally allocated specification has normative effect only when an applicable version has been published.

### Versioning

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

### Specification dependencies

`+AI-001@0` defines the family architecture.

`+AI-100@0` defines the canonical `+AI` accountability declaration.

A specification that extends the `+AI` declaration MUST depend upon:

```text
+AI-001@0
+AI-100@0
```

and MAY depend upon additional specifications.

A profile MAY require conformance with several specifications.

A profile MUST NOT redefine the normative meaning of a specification upon which it depends.

### Core semantic invariance

The meaning of the canonical `+AI` declaration is owned by `+AI-100@0`.

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

### Monotonic extension rule

Every extension MUST be semantically additive.

For declaration `D` and extension `E`:

```text
meaning(D[E]) = meaning(D) AND meaning(E)
```

An extension MUST NOT cause a previously asserted claim to become false.

An extension whose semantics conflict with its root declaration MUST be declared incompatible with that root.

### Absence is not negation

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

### Canonical visible-extension syntax

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

### Canonical ordering

Extension tokens MUST have a deterministic canonical order.

The default canonical order is ascending identifier of the specification defining the extension.

Where one specification defines multiple extension tokens, that specification MUST define their internal canonical order.

A renderer MAY visually rearrange extensions for presentation purposes only where the complete canonical declaration remains available.

Machine serialization MUST use canonical order.

### Extension registry

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

### Initial extension registry

The following extension tokens are initially registered or reserved.

| Token       | Defining specification | Status   |
| ----------- | ---------------------- | -------- |
| `primary`   | `+AI-220@0`            | Reserved |
| `review`    | `+AI-310@0`            | Draft    |
| `verify`    | `+AI-320@0`            | Draft    |
| `prov`      | `+AI-410@0`            | Draft    |
| `delegated` | `+AI-510@0`            | Reserved |
| `agent`     | `+AI-520@0`            | Reserved |
| `signed`    | `+AI-630@0`            | Reserved |

A reserved token MUST NOT be treated as carrying normative meaning until its defining specification establishes that meaning.

### Root declarations

`+AI` is a root declaration.

A separate root declaration MAY be defined where the intended semantics cannot validly be represented as an additive extension of `+AI`.

A new root declaration MUST have substantially distinct semantics that justify a separate root. In particular, a declaration representing release without qualifying human or organisational adoption MUST NOT be encoded as an extension that weakens or contradicts `+AI`.

The initial root-declaration registry is:

| Root declaration | Defining specification | Status | Meaning |
| ---------------- | ---------------------- | ------ | ------- |
| `+AI`            | `+AI-100@0`            | Draft  | Human or organisational adoption and responsibility for an AI-assisted Release |
| `AI[auto]`       | `+AI-530@0`            | Draft  | Autonomous AI Release without qualifying Party Adoption before the Release |

### Human-readable and graphical forms

The canonical textual declaration MUST remain sufficient to express its normative meaning.

Graphical badges, icons, colours or logos MAY accompany a declaration.

A graphical presentation MUST NOT change the semantic meaning of the underlying declaration.

Where a graphical form is used, an equivalent canonical textual representation SHOULD remain available.

### Abstract declaration model

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

### Artifact and release distinction

An `Artifact` represents a logical work.

An `ArtifactVersion` represents a particular state of that work.

A `Release` represents a decision or event by which an artifact version is published, transmitted, deployed, submitted, presented or otherwise made operative.

Responsibility declarations SHOULD be associated with a specific release.

This permits the same artifact version to have different accountability states in different releases.

### Adoption

`Adoption` represents a qualifying human or organisational act of knowingly accepting a particular artifact version for a particular release.

Delegating permission to an AI system or agent to produce an artifact does not, by itself, constitute adoption of every artifact produced under that delegation.

Delegating release authority does not, by itself, constitute artifact-specific human adoption.

### ResponsibilityDeclaration

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

### Activity graph

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

### Authority graph

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

### Assurance assertions

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

### Predicate coherence

The family preserves the following non-implication rules:

* `review` does not imply `verify`.
* `verify` does not imply `review`.
* `prov` does not imply `verify`.
* `prov` does not imply `signed`.
* `review` does not itself create a ResponsibilityDeclaration.
* `verify` does not itself create a ResponsibilityDeclaration.
* physical release execution does not imply release responsibility.

Responsibility arises only from a conforming root declaration and its associated semantic conditions.

### Projection rule

A visible declaration SHOULD be a projection of valid semantic assertions.

For example, the visible notation:

```text
+AI[review]
```

is valid only where:

1. a valid `+AI` responsibility declaration exists; and
2. a valid `+AI-310@0` human-review assertion applies to the released artifact version.

A machine MUST NOT create extension notation merely because a token string has been supplied.

The underlying semantic condition MUST be satisfied.

### Unknown extensions

A consumer encountering an unknown extension token:

* MUST NOT infer its meaning;
* MUST NOT interpret it as another known extension;
* SHOULD preserve it when round-tripping a declaration;
* MAY report that its semantics are unknown.

Unknown extensions MUST NOT invalidate known claims unless a governing profile explicitly requires complete extension recognition.

### Profiles

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
+AI-820@0 Research Profile
```

might require:

```text
+AI-100@0
+AI-310@0
+AI-410@0
```

without changing what those specifications mean.

### Bindings

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

### Persistence across transformations

An assertion MAY remain valid across a transformation where the transformation does not materially alter the subject to which the assertion applies.

Material transformations SHOULD produce a new `ArtifactVersion`.

Bindings SHOULD preserve links between derived artifact versions.

Specifications defining assurance assertions MUST state when those assertions survive transformation.

### Multiple responsible Parties

Multiple parties MAY independently accept responsibility for the same release.

Each responsible party SHOULD have an independently representable responsibility declaration.

For example:

```text
JAPER Technology +AI
Eric Mourant +AI
```

represents two responsibility declarations.

A machine-readable representation MUST NOT infer joint responsibility merely from textual proximity.

### Conformance classes

The family defines the following general conformance classes.

#### 31.1 Declaration conformance

A declaration conforms when its asserted semantic conditions are satisfied.

#### 31.2 Producer conformance

A producer conforms when it emits declarations and metadata according to the applicable specifications.

#### 31.3 Consumer conformance

A consumer conforms when it interprets known declarations according to their registered semantics and handles unknown declarations according to this specification.

#### 31.4 Binding conformance

A binding conforms when it faithfully represents the abstract model and applicable normative assertions.

#### 31.5 Profile conformance

An implementation conforms to a profile when it satisfies every requirement declared mandatory by that profile.

### Misrepresentation

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

### Evidence

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

### Evolution

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

### Canonical architecture statement

The `+AI` specification family is based on the following model:

> **A compact visible declaration represents one or more precisely defined semantic assertions. Those assertions apply to identifiable parties, artifacts, activities, adoptions and releases, and may be supported by provenance and evidence. Extensions add meaning; they do not alter the meaning already present.**

The architectural invariant is:

**Simple declaration. Explicit semantics. Extensible evidence.**

## Module +AI-020 — Abstract Data Model

**Status:** Draft  
**Version:** 0.1  
**Identifier:** `+AI-020`  
**Dependencies:** `+AI-001@0`  

### Purpose

This specification defines the abstract data model used by the `+AI` specification family.

It defines the entities and relationships required to represent:

* human and organisational parties;
* AI systems and agents;
* artifacts and artifact versions;
* human and AI activities;
* authority and delegation;
* human adoption;
* release events;
* responsibility declarations;
* assurance assertions;
* provenance;
* identity claims;
* and supporting evidence.

The abstract model is representation-independent.

JSON, document metadata, web metadata, cryptographic credentials and other technical representations are bindings of this model rather than definitions of the model itself.

### Design principle

The model separates concepts that may coincide operationally but have different semantics.

In particular:

```text
creation != adoption
authority != adoption
authority != responsibility
review != verification
artifact != artifact version
artifact version != release
release execution != release responsibility
identity != evidence
claim != proof
```

Implementations MUST NOT collapse these distinctions where doing so changes normative meaning.

### Graph model

A `+AI` record is conceptually a directed typed graph.

Nodes represent entities.

Edges represent defined relationships between entities.

A simplified graph is:

```text
Party ───── grants ─────► AuthorityGrant
                              │
                              ▼
                            Agent
                              │
                           performs
                              ▼
                           Activity
                              │
                       produces/modifies
                              ▼
                       ArtifactVersion
                         │           │
                      reviewed     adopted
                         │           │
                         ▼           ▼
                      Assertion    Adoption
                                      │
                                      ▼
                                   Release
                                      │
                                      ▼
                              Responsibility
                               Declaration
                                      │
                                   supported
                                      ▼
                                   Evidence
```

The graph MAY be incomplete.

Absence of a node or relationship MUST NOT normally be interpreted as evidence that the corresponding real-world event did not occur.

### Entity identity

Every entity represented within a conforming graph MUST have an identifier unique within the applicable record.

Identifiers MAY be:

* local identifiers;
* URIs;
* URNs;
* cryptographic identifiers;
* organisational identifiers;
* pseudonymous identifiers;
* or identifiers defined by another binding.

Two identifiers MUST NOT be assumed to represent the same entity unless an explicit equivalence relation or applicable identity specification establishes equivalence.

### Party

A `Party` is an entity capable of making human or organisational declarations within the `+AI` family.

A Party has one of the following base types:

```text
person
organisation
```

Only a Party may be the responsible party of a canonical `+AI` responsibility declaration.

An AI system or AI agent is not a Party merely because it possesses an identifier, performs actions or exercises delegated authority.

A Party MAY simultaneously perform other roles, including:

```text
author
operator
reviewer
verifier
authority grantor
adopter
releaser
responsible party
```

Those roles MUST NOT be inferred merely from Party identity.

### AISystem

An `AISystem` represents an artificial-intelligence system materially relevant to an activity.

An AISystem MAY represent:

* a model;
* a hosted service;
* a local model;
* a multimodel system;
* an inference service;
* an AI-enabled application;
* or another identifiable AI capability.

An AISystem MAY have:

```text
provider
product name
model name
model version
deployment identifier
configuration identifier
```

Identification of a model does not itself establish what activities that model performed.

### Agent

An `Agent` represents an operational actor capable of selecting or performing activities toward a goal.

An Agent MAY use one or more AISystems.

An Agent MAY:

* receive authority;
* invoke other agents;
* perform activities;
* create artifacts;
* modify artifacts;
* make operational decisions;
* and execute release actions.

An Agent MUST NOT be treated as a responsible Party under `+AI-100@0`.

An Agent and the AISystem used by that Agent are distinct entities.

Example:

```text
Agent: research-agent-17
uses:
    AISystem: model-service-x
```

This distinction permits the same Agent to use different AISystems over time.

### Artifact

An `Artifact` represents a logical work or object.

Examples include:

```text
document
email
software project
source file
image
dataset
analysis
report
video
audio recording
presentation
decision record
machine-generated output
```

An Artifact may exist through multiple versions.

Assertions requiring precise subject identity SHOULD apply to an `ArtifactVersion`, not merely to the logical Artifact.

### ArtifactVersion

An `ArtifactVersion` represents a particular substantive state of an Artifact.

A material modification MUST produce a distinct ArtifactVersion for purposes of assertions affected by that modification.

An ArtifactVersion MAY be identified by:

* content digest;
* version identifier;
* repository commit;
* immutable object identifier;
* signed manifest;
* or another sufficiently precise mechanism.

Byte-for-byte identity is sufficient but not always necessary.

A non-material transformation MAY create a different technical representation without creating a materially different artifact state.

### Material equivalence

Two technical representations MAY be considered materially equivalent where their differences do not materially alter the meaning, function or relevant properties of the artifact.

Examples may include:

```text
DOCX → PDF conversion
lossless image transformation
archival packaging
printing
routine pagination changes
metadata preservation
```

Material equivalence MUST NOT be presumed where the transformation may alter substantive content or behaviour.

A specification relying on material equivalence SHOULD define the relevant equivalence criteria.

### Activity

An `Activity` represents an event or process in which an actor does something materially relevant to the graph.

Examples include:

```text
create
draft
analyse
transform
translate
edit
review
verify
test
approve
adopt
release
delegate
sign
```

An Activity SHOULD identify:

```text
actor
activity type
inputs
outputs
time
materiality
applicable authority
supporting evidence
```

An Activity MAY have multiple actors.

### Actor

An `Actor` is a role capable of performing an Activity.

An Actor reference MAY identify:

```text
Party
Agent
AISystem
```

The model does not imply equal legal, ethical or accountability capacity between those actor classes.

Actor means only that the entity participated causally in an Activity.

### Material AI participation

Material AI participation exists where one or more AISystem or Agent Activities materially affected the applicable artifact or relevant decision.

Materiality is qualitative.

It MUST NOT be inferred solely from:

```text
token counts
character percentages
file size
number of prompts
elapsed AI processing time
percentage of sentences
```

A provenance record MAY describe quantitative contribution metrics, but such metrics do not replace the applicable materiality test.

### AuthorityGrant

An `AuthorityGrant` records authority given by one actor to another actor.

It SHOULD identify:

```text
grantor
grantee
scope
permitted activities
release authority
delegation authority
validity period
parent authority
conditions
evidence
```

An AuthorityGrant may be narrow or broad.

Examples:

```text
draft this document
research these topics
modify this repository
send replies within this policy
publish qualifying status updates
delegate research to another agent
```

### Authority constraints

Authority is scoped.

An actor MUST NOT be inferred to possess authority outside the recorded or otherwise established scope.

A child delegation MUST NOT exceed the authority possessed by its parent grant.

Therefore:

```text
authority(child) ⊆ authority(parent)
```

unless an independent authority source exists.

### Release authority

Release authority means authority to cause an artifact to be published, transmitted, deployed, submitted, presented or otherwise made operative.

Release authority and human adoption are distinct.

An Agent MAY possess:

```text
may_release = true
```

without any human having adopted the specific artifact version that the Agent later releases.

Such standing authority does not by itself satisfy the human-adoption requirement of `+AI-100@0`.

### Adoption

An `Adoption` represents a qualifying act by a Party in which that Party knowingly accepts a specific ArtifactVersion for a specific Release or defined release decision.

A conforming Adoption MUST identify:

```text
party
artifact version
release or intended release
acceptance
time
```

Adoption is artifact-specific.

General approval of:

```text
an AI system
an agent
a workflow
a policy
a content category
a standing publication rule
```

does not automatically constitute adoption of every ArtifactVersion produced under that authority.

### Knowledge requirement

Adoption requires the Party to know which artifact or artifact state is being accepted to a degree sufficient to constitute a meaningful act of acceptance.

Adoption does not necessarily require:

```text
word-by-word review
independent verification
professional validation
personal authorship
complete understanding of AI internal reasoning
```

Those are separate properties.

Blind or purely mechanical approval MUST NOT be treated as qualifying adoption.

### Release

A `Release` represents an event or decision by which an ArtifactVersion becomes externally or operationally effective.

Release modes may include:

```text
publish
send
submit
deploy
issue
broadcast
commit
merge
execute
present
transmit
```

A Release MUST identify the ArtifactVersion being released.

A Release MAY identify the actor that physically executed the release.

Physical execution and responsibility are distinct.

### Automated release

A Release MAY be executed by an Agent or AISystem after qualifying human adoption.

For example:

```text
Human adopts Version 7
        │
        ▼
Agent automatically publishes Version 7
```

The fact that an Agent physically performed the publication does not make the Release autonomous for `+AI` purposes if qualifying human adoption occurred beforehand.

### Autonomous release

For the purposes of this model, an `AutonomousRelease` is a Release materially selected or executed by an AISystem or Agent without a qualifying Party Adoption applying to that artifact version and release beforehand.

The presence of prior general authority does not prevent classification as autonomous release.

The normative declaration for this condition is defined by `+AI-530@0`.

### ResponsibilityDeclaration

A `ResponsibilityDeclaration` records a Party's acceptance of responsibility according to an applicable accountability specification.

For `+AI-100@0`, it MUST bind at least:

```text
responsible Party
ArtifactVersion
Adoption
Release
applicable specification
```

The referenced Adoption, Release and ArtifactVersion MUST be mutually consistent.

### Release-specific responsibility

Responsibility declarations are release-specific unless an applicable specification explicitly defines broader scope.

The same ArtifactVersion may therefore have:

```text
Release R1 → autonomous
Release R2 → human-adopted +AI
Release R3 → different responsible Party +AI
```

These states do not conflict because they apply to distinct Releases.

### Multiple responsible parties

Multiple Parties MAY independently accept responsibility for the same Release.

Each Party MUST have a separately representable:

```text
Adoption
ResponsibilityDeclaration
```

unless another specification explicitly defines collective adoption.

Two names displayed together MUST NOT be interpreted by a machine as joint responsibility without corresponding semantic records.

### Assertion

An `Assertion` represents a proposition declared about one or more entities.

Assertion classes may include:

```text
accountability
participation
review
verification
validation
identity
provenance
authority
signature
conformance
```

An Assertion SHOULD identify:

```text
issuer
subject
predicate/type
value or outcome
time
applicable specification
supporting evidence
```

### Assurance Assertion

An `AssuranceAssertion` is an Assertion about an assurance process or result.

Examples include:

```text
human review
independent verification
testing
validation
certification
```

An Assurance Assertion MUST NOT automatically create a ResponsibilityDeclaration.

A verifier may verify an artifact without accepting responsibility for releasing that artifact.

### IdentityClaim

An `IdentityClaim` associates an entity with identifying information.

IdentityClaims may concern:

```text
people
organisations
agents
AI systems
models
services
cryptographic keys
```

An IdentityClaim MAY be supported by Evidence.

Identity alone does not establish authorship, authority, adoption or responsibility.

### Evidence

`Evidence` is information capable of supporting an Assertion or relationship.

Examples include:

```text
cryptographic digest
digital signature
timestamp
activity log
review record
verification report
repository history
attestation
identity credential
workflow record
```

Evidence MUST be represented separately from the claim it supports.

The existence of Evidence does not by itself establish that the supported claim is true.

### Provenance

Provenance is the graph of relevant entities, activities and derivations associated with an ArtifactVersion.

A provenance graph MAY describe:

```text
human activities
AI activities
agent activities
input artifacts
output artifacts
transformations
authority chains
reviews
verification
releases
```

Provenance SHOULD represent contribution as activities and derivations rather than attempting to assign a percentage of authorship.

### Temporal ordering

Where times are known, the following ordering constraints apply.

A qualifying Adoption for a Release MUST occur before or contemporaneously with the release decision it authorises.

A pre-release assurance assertion MUST be complete before the Release to which that assurance applies.

A material change after an assertion creates a new ArtifactVersion to which the prior assertion MUST NOT automatically propagate.

### No implicit role inference

The model MUST NOT infer:

```text
producer → responsible party
operator → responsible party
authority grantor → responsible party
reviewer → responsible party
verifier → responsible party
publisher → author
AI provider → responsible party
agent owner → responsible party
```

Such relationships require explicit assertions or rules from another specification.

### Incomplete graphs and omitted relationships

The abstract model follows the family rule in `+AI-001@0`: absence of a represented node, relationship or assertion is not normally negation. An incomplete graph means only that the corresponding fact is not represented by that record.

### Predicate mappings

The abstract model provides representational support for the family predicates without redefining them.

* `+AI-100@0` accountability is represented through Party, Adoption, Release and ResponsibilityDeclaration relationships.
* `+AI-310@0` human review is represented through an AssuranceAssertion of type `human_review` applying to an identifiable ArtifactVersion.
* `+AI-320@0` independent verification is represented through an AssuranceAssertion that includes subject, scope, method, outcome and independence basis.
* `+AI-530@0` autonomous release is represented through a Release materially controlled by an AISystem or Agent together with the absence of qualifying Party Adoption for that ArtifactVersion and Release.

The authoritative normative predicates remain defined by their respective modules.

### Graph invariants

A conforming representation of this model MUST preserve the following invariants:

1. references resolve to entities of the required class;
2. entity identifiers are unique within the applicable record;
3. a Release identifies exactly which ArtifactVersion it releases;
4. an Adoption identifies the same ArtifactVersion and Release to which it applies;
5. a ResponsibilityDeclaration identifies a compatible Adoption, Party, ArtifactVersion and Release;
6. material changes produce distinct ArtifactVersions for affected assertions;
7. authority does not imply adoption;
8. adoption does not imply review;
9. review does not imply verification;
10. verification does not imply responsibility;
11. physical release execution does not imply release responsibility;
12. an AISystem or Agent is not transformed into a Party merely by being assigned responsibility-like metadata.

### Minimal graph

A minimal `+AI` graph may contain:

```text
Party
AISystem or Agent activity establishing material participation
ArtifactVersion
Adoption
Release
ResponsibilityDeclaration
```

Additional provenance is optional unless another specification or profile requires it.

### Canonical model statement

The `+AI` family models AI-assisted artifacts as relationships between:

**Actors, activities, artifacts, authority, adoption, release, assertions and evidence.**

Its foundational distinction is:

> **Who or what produced an artifact is not necessarily who authorised it, adopted it, released it, reviewed it, verified it or accepts responsibility for it.**

## Module +AI-100 — Core +AI Declaration

**Status:** Draft  
**Version:** 0.1  
**Identifier:** `+AI-100`  
**Dependencies:** `+AI-001@0`  

### Purpose

The `+AI` notation provides a compact method for identifying an artifact as materially assisted by artificial intelligence while identifying a human or organisation that accepts responsibility for the resulting artifact.

The canonical expression is:

**`<Responsible Party> +AI`**

Example:

**Eric Mourant +AI**

The fundamental meaning is:

**AI helped. I take responsibility.**

### Design principle

`+AI` does not attempt to determine whether an artifact is “human-created” or “AI-created.”

Modern artifacts may pass repeatedly between human and artificial intelligence systems during their creation.

Instead, `+AI` communicates two facts:

1. artificial intelligence materially assisted the work; and
2. an identifiable human or organisation accepts responsibility for the resulting artifact.

The standard therefore concerns **AI participation and human accountability**, rather than exclusive authorship.

### Canonical notation

The canonical mark is:

`+AI`

The canonical human-readable form is:

**`<Responsible Party> +AI`**

Examples:

**Eric Mourant +AI**

**JAPER Technology +AI**

The mark is case-sensitive.

The canonical form MUST use:

* a plus sign `+`;
* followed immediately by uppercase Latin characters `AI`;
* with no internal whitespace.

Therefore:

`+AI`

is canonical.

The following are not canonical equivalents:

`+Ai`

`+aI`

`+ ai`

`AI+`

`AI assisted`

Variants MAY later be defined by extensions to this specification, but they MUST NOT be assumed to carry the canonical `+AI` meaning unless explicitly defined.

### Meaning of the mark

A responsible party using `+AI` declares that:

#### 5.1 AI participation

Artificial intelligence materially assisted in creating, analysing, transforming, generating, evaluating, structuring or presenting the associated artifact.

#### 5.2 Knowledge

The responsible party knows or reasonably believes that material AI assistance occurred.

#### 5.3 Authority

The responsible party authorised, initiated, directed or knowingly adopted the relevant use of artificial intelligence.

#### 5.4 Human or organisational control

The responsible party retained authority over whether the artifact would be published, transmitted, deployed, submitted, presented or otherwise released.

#### 5.5 Adoption

The responsible party accepts the artifact in the form in which it is being presented.

#### 5.6 Responsibility

The responsible party accepts responsibility for the decision to release, use or represent the artifact.

These elements collectively constitute the `+AI` declaration.

### Material assistance

The mark SHOULD be used when AI participation materially affected the resulting artifact.

Material assistance may include AI contribution to:

writing;

reasoning;

analysis;

recommendations;

research synthesis;

software code;

data interpretation;

design;

images;

audio;

video;

translation where substantive interpretation occurs;

planning;

decision support;

mathematical or technical work;

editing that materially changes meaning;

or other substantive intellectual or creative work.

Incidental or purely mechanical AI functionality does not necessarily require `+AI`.

Examples may include automatic spelling correction, basic autocomplete, routine formatting or other features that do not materially affect the substance of an artifact.

The determining question is not the percentage of content produced by AI.

The determining question is:

> **Did AI materially influence the artifact being presented?**

### Responsibility

Responsibility is the defining property of `+AI`.

By using the mark, the responsible party does not transfer responsibility to an artificial intelligence system, model, provider, agent or tool.

A statement equivalent to:

> “The AI generated it, therefore I am not responsible for it.”

is incompatible with the intended meaning of `+AI`.

The responsible party MAY rely heavily on AI assistance.

The responsible party MAY publish content substantially generated by AI.

The responsible party MAY accept suggestions that they could not independently have produced.

None of these conditions prevents use of `+AI`, provided that the responsible party knowingly adopts the resulting artifact and accepts responsibility for releasing it.

### What +AI does not mean

Unless an additional declaration explicitly states otherwise, `+AI` does NOT assert that:

the artifact is error-free;

every factual statement has been independently verified;

every citation has been independently checked;

the artifact satisfies any particular professional standard;

the artifact is legally correct;

the artifact is medically correct;

the artifact is safe for any particular purpose;

the artifact contains no hallucinations;

the responsible party personally wrote every component;

AI generated the majority of the artifact;

AI generated only a minority of the artifact;

the artifact is original;

no third-party intellectual property is present;

confidential information was not supplied to an AI system;

a particular AI provider, model or system was used;

the responsible party agrees with every intermediate AI output;

or the responsible party can reproduce or explain the internal reasoning of the AI system.

`+AI` is an **accountability declaration**, not a warranty of correctness.

### Human review baseline

Version 0.1 of the root declaration does not require that every component of an ArtifactVersion be manually reviewed word-by-word or element-by-element.

The responsible Party MUST, however, knowingly accept the ArtifactVersion being released.

Blind or automatic forwarding of unreviewed AI output SHOULD NOT be represented using `+AI` where no meaningful act of Adoption has occurred.

Stronger assurance claims are defined separately by `+AI-310@0` and `+AI-320@0`.

### Individuals

An individual MAY apply the notation after their name.

Example:

**Eric Mourant +AI**

This means:

> Artificial intelligence materially assisted the associated work, and Eric Mourant accepts responsibility for releasing that work.

The mark relates to the associated artifact or communication.

It does not necessarily mean that every activity undertaken by the individual uses artificial intelligence.

### Organisations

An organisation MAY use `+AI`.

Example:

**JAPER Technology +AI**

This means that the organisation assumes responsibility for the associated AI-assisted artifact according to its applicable governance and authority structures.

Where useful, both an organisation and responsible individual MAY be identified.

Example:

**JAPER Technology**
**Eric Mourant +AI**

### Email and messaging

In personal communication, the preferred presentation is:

**Kindest regards,**
**Eric Mourant +AI**

The mark MAY be hyperlinked to a canonical explanation of its meaning.

A hyperlink MUST NOT alter the visible notation.

Plain text MUST remain sufficient to express the declaration.

### Documents

The notation MAY appear in an author, preparer, reviewer or responsible-party field.

Examples:

**Author: Eric Mourant +AI**

**Prepared by: Eric Mourant +AI**

**Issued by: JAPER Technology +AI**

Placement SHOULD make clear which person or organisation is assuming responsibility.

### Software

The notation MAY be used in software repositories, commits, source-code headers, documentation, release notes and generated artifacts.

Example:

```text
Author: Eric Mourant +AI
```

A project MAY additionally declare:

```text
This project uses +AI.
```

Such a project-level statement SHOULD identify the responsible person or organisation where practical.

### Creative artifacts

The notation MAY accompany images, audio, video, designs, illustrations, presentations and other creative works.

Example:

**Created by Eric Mourant +AI**

The mark does not itself specify which elements were generated or modified by AI.

More detailed provenance metadata MAY be associated separately.

### Research and technical work

The mark MAY be used in research, scientific, engineering or technical work where permitted by applicable institutional, publication or professional requirements.

`+AI` MUST NOT be represented as replacing any more specific disclosure required by a publisher, regulator, employer, professional body or law.

The notation MAY supplement such disclosure.

### Machine-readable representation

Systems MAY represent the declaration using structured metadata.

A minimal representation is:

```json
{
  "provenance": "+AI"
}
```

A richer representation is:

```json
{
  "ai_assistance": {
    "material": true,
    "responsibility": "human",
    "responsible_party": "Eric Mourant",
    "notation": "+AI"
  }
}
```

Machine-readable forms SHOULD preserve the same semantic meaning as the visible notation. The canonical JSON binding for declaration graphs is defined by `+AI-710@0`.

### Persistence

The `+AI` notation SHOULD survive reasonable transformations of an artifact where attribution is preserved.

Examples include conversion between document formats, archival, printing, export, republication and transmission.

Where metadata is stripped, the visible plain-text mark SHOULD remain sufficient to communicate the declaration.

### Open use

The `+AI` notation is intended for unrestricted public use.

Use of the notation SHOULD NOT require:

registration;

membership;

payment;

certification;

approval;

or use of any particular AI product or provider.

The usefulness of the notation depends upon its ability to function as a universal convention.

### Neutrality

`+AI` does not express approval or disapproval of artificial intelligence.

It does not indicate whether use of AI was necessary, desirable or superior to unaided human work.

It records only material AI participation and human or organisational accountability.

### Misrepresentation

A person or organisation SHOULD NOT use `+AI` where:

there is no identifiable responsible Party;

the named Party has not adopted the ArtifactVersion for the applicable Release;

the artifact is being issued automatically without meaningful human or organisational authority;

or the notation is being used to create a false impression of human accountability.

Autonomous AI output without qualifying human or organisational Adoption is outside the canonical scope of `+AI` and is addressed separately by `+AI-530@0`.

### Relationship to authorship

`+AI` deliberately does not assign a percentage of authorship.

An artifact MAY contain predominantly human-originated material and still qualify.

An artifact MAY contain predominantly AI-originated material and still qualify.

The relevant test is whether:

**AI materially assisted, and the named party takes responsibility for the result.**

### Canonical public explanation

Where a short explanation is required, the preferred language is:

**AI helped. I take responsibility.**

Where a longer explanation is required:

> **`+AI` means artificial intelligence materially assisted this work and the named person or organisation accepts responsibility for the resulting artifact.**

### The +AI test

Before applying the mark, a person should be able to answer **yes** to both questions:

**Did AI materially help produce this?**

**Am I willing to take responsibility for releasing it?**

If both answers are yes:

**+AI**

### Future extensions

Future versions or additional family modules MAY define further notation addressing matters such as:

minor AI assistance;

AI-primary generation;

autonomous agent activity;

cryptographic provenance;

AISystem identification;

model identification;

or chains of human and machine contribution.

Existing draft modules already define review, verification, provenance and autonomous-release semantics within this family.

Such extensions SHOULD preserve `+AI` as the simple canonical mark for:

**AI-assisted work with identifiable human responsibility.**

### Canonical declaration

A person or organisation applying `+AI` makes the following declaration:

> **Artificial intelligence materially assisted this work. I have chosen to accept, publish, transmit, deploy or otherwise release the resulting work, and I take responsibility for that decision and for the work as presented.**

The public shorthand is:

**AI helped. I take responsibility.**

The canonical mark is:

**+AI**

---

#### +AI Specification v0.1

**Human-AI Provenance and Accountability**

**AI helped. I take responsibility.**

## Module +AI-210 — AI Participation Classification

**Status:** Draft  
**Version:** 0.1  
**Identifier:** `+AI-210`  
**Dependencies:** `+AI-001@0`, `+AI-020@0`  
**Related specifications:** `+AI-100@0`, `+AI-220@0`, `+AI-520@0`  

### Purpose

This specification defines a common classification model for describing artificial-intelligence participation in an artifact, activity or release.

It establishes classifications for:

* incidental AI participation;
* material AI participation;
* minor material participation;
* collaborative participation;
* primary AI participation;
* direct AI participation;
* agentic participation;
* and mixed participation.

The classification model deliberately does not assign percentages of authorship or ownership.

### Design principle

AI participation is multidimensional.

A single continuum such as:

```text
0% AI ─────────────────────────── 100% AI
```

is insufficient to describe modern human-AI workflows.

The classification model therefore distinguishes at least:

```text
materiality
production role
operational mode
```

These dimensions answer different questions.

#### Materiality

> Did AI materially affect the artifact or release?

#### Production role

> What substantive role did AI play in producing the resulting artifact?

#### Operational mode

> How did the AI participate operationally?

The dimensions MUST NOT be collapsed into a single numerical authorship score.

### Classification object

A conforming participation classification MAY contain:

```text
materiality
production_role
operational_mode
scope
basis
activities
```

A canonical conceptual representation is:

```json
{
  "materiality": "material",
  "production_role": "primary",
  "operational_mode": "agentic"
}
```

These values describe different properties and MAY be combined.

### No authorship percentages

A classification MUST NOT require assignment of a percentage of authorship.

Implementations MUST NOT infer a participation class solely from:

```text
percentage of words generated
percentage of characters generated
percentage of source lines generated
percentage of pixels generated
token count
prompt count
editing count
wall-clock time
computational cost
```

Such measurements MAY be recorded as supplementary provenance where useful.

They do not determine the normative participation classification.

### Materiality dimension

The materiality dimension has two canonical values:

```text
incidental
material
```

These values concern whether AI participation materially affected the relevant artifact, activity or release.

### Incidental participation

`incidental` means AI functionality was present but did not materially affect the substantive artifact or outcome.

Examples may include:

```text
routine spelling correction
mechanical formatting
non-substantive autocomplete
file conversion
simple deterministic classification
interface assistance
```

The determining condition is:

> Removal of the AI participation would not reasonably be expected to alter the substantive meaning, function, decision, recommendation, creative result or material presentation of the artifact.

Incidental participation alone does not satisfy the material-AI-participation condition required by `+AI-100@0`.

### Material participation

`material` means AI participation materially affected the resulting artifact, activity, decision or release.

Material participation may include AI contribution to:

```text
writing
reasoning
analysis
research synthesis
recommendations
software
design
data interpretation
mathematics
technical work
translation involving substantive interpretation
planning
decision support
creative production
material editing
```

The canonical test is qualitative:

> **Would the resulting artifact, decision or release be substantively different without the AI participation?**

If yes, the participation will normally be material.

### Materiality is contextual

The same AI activity MAY be incidental in one context and material in another.

Example:

```text
AI corrects spelling in a casual note
→ incidental
```

but:

```text
AI changes a technical term whose meaning affects a contractual obligation
→ potentially material
```

Materiality therefore depends upon substantive effect rather than tool category.

### Production-role dimension

Where materiality is `material`, a production role MAY be classified as:

```text
minor
collaborative
primary
```

These classifications describe the role AI played in producing the substantive result.

They MUST NOT be treated as numerical bands.

### Minor material participation

`minor` means:

1. AI participation was material;
2. its substantive contribution was bounded in scope;
3. the central structure, direction or production of the artifact remained predominantly determined through non-AI activity.

The term **minor** does not mean non-material.

Example:

```text
A human writes and structures a technical report.

AI identifies an important ambiguity and rewrites one consequential paragraph.

The AI participation materially affects the released report but remains bounded relative to the overall production process.
```

A classification may therefore be:

```json
{
  "materiality": "material",
  "production_role": "minor"
}
```

### Minor versus incidental

The distinction is:

```text
incidental
    ↓
AI did not materially influence the artifact
```

versus:

```text
minor
    ↓
AI materially influenced the artifact,
but its production role was bounded
```

An implementation MUST NOT treat `minor` as equivalent to `incidental`.

### Collaborative participation

`collaborative` means human and AI activities each played substantial interdependent roles in developing the artifact, without AI clearly constituting the principal production mechanism.

Examples may include:

```text
iterative human-AI drafting
joint code development
human-directed research synthesis
repeated AI analysis followed by substantive human restructuring
human and AI design iteration
```

The classification does not assert equal participation.

It asserts substantive interdependence.

### Primary AI participation

`primary` means AI constituted the principal substantive production mechanism for the artifact or for the defined scope being classified.

Indicators may include:

* AI generated the initial substantive artifact from which the released artifact substantially derives;
* AI performed the central analytical or generative work;
* human participation principally consisted of direction, selection, correction, review or adoption;
* replacing the AI contribution would effectively require recreating the substantive artifact or central result.

No quantitative threshold is required.

### Primary does not mean exclusive

`primary` does NOT mean:

```text
100% AI generated
no human editing
no human ideas
no human source material
no human review
no human responsibility
```

An artifact MAY contain extensive human contribution while AI remains the principal production mechanism.

Likewise, an artifact MAY contain large quantities of AI-generated material without AI qualifying as primary where those outputs were peripheral to the substantive result.

### Primary-production test

The recommended test is:

> **Was AI the principal mechanism by which the substantive artifact or classified scope came into existence?**

Where the answer is yes:

```text
production_role = primary
```

may be appropriate.

The detailed visible `primary` extension is reserved to `+AI-220@0`.

### Scope

Participation classification MUST identify its scope where the classification does not apply to the complete ArtifactVersion.

Possible scopes include:

```text
complete artifact
defined section
software component
analysis stage
image
calculation
research phase
release decision
```

Example:

```text
Complete report:
    collaborative

Appendix calculation:
    primary
```

A scoped classification MUST NOT silently be represented as applying to the entire ArtifactVersion.

### Operational-mode dimension

Operational mode describes how AI participated.

Canonical values are:

```text
direct
agentic
mixed
```

Operational mode is independent of production role.

Therefore all of the following may occur:

```text
minor + direct
minor + agentic
collaborative + direct
collaborative + agentic
primary + direct
primary + agentic
```

### Direct participation

`direct` means AI participation principally occurred through explicit human-directed interactions in which a human selected or initiated the substantive AI operations.

Examples include:

```text
human writes prompt
AI returns draft
human requests revision
AI returns revision
```

Direct participation may involve multiple iterations.

Direct does not mean trivial or low-impact.

A directly prompted AI system may still be classified as `primary`.

### Agentic participation

`agentic` means an AI-enabled Agent exercised material operational discretion in selecting or sequencing activities toward a goal.

Agentic participation may include discretion concerning:

```text
which tools to invoke
which information to retrieve
which intermediate steps to perform
which sub-agents to use
which candidate result to select
how to sequence tasks
whether to retry or revise
how to pursue a delegated goal
```

Agentic participation does not require autonomous release.

### Agentic does not mean autonomous

The following concepts are distinct:

```text
agentic participation
autonomous release
```

An Agent may perform extensive agentic work while a human later knowingly adopts the final ArtifactVersion.

That release may qualify for:

```text
+AI
```

Conversely, an Agent may autonomously release an artifact even where its generative work was relatively simple.

Autonomous release is governed by `+AI-530@0`.

### Agentic participation and authority

Agentic classification concerns operational behaviour.

It does not state:

```text
who authorised the Agent
whether its actions were within authority
whether it had release authority
whether a human adopted the result
whether the release was autonomous
```

Those matters are represented separately through `+AI-020@0` authority, adoption and release relationships.

### Mixed operational mode

`mixed` means materially relevant participation included both substantial direct human-AI interaction and substantial agentic activity.

Example:

```text
Human and AI collaboratively develop the specification structure.

An Agent later researches internal consistency, creates cross-reference proposals and runs conformance checks.

Human performs further direct revision.
```

The resulting operational mode may be:

```text
mixed
```

### Classification combinations

Examples include:

#### 24.1 Material, minor, direct

```json
{
  "materiality": "material",
  "production_role": "minor",
  "operational_mode": "direct"
}
```

#### 24.2 Material, collaborative, direct

```json
{
  "materiality": "material",
  "production_role": "collaborative",
  "operational_mode": "direct"
}
```

#### 24.3 Material, primary, direct

```json
{
  "materiality": "material",
  "production_role": "primary",
  "operational_mode": "direct"
}
```

#### 24.4 Material, collaborative, agentic

```json
{
  "materiality": "material",
  "production_role": "collaborative",
  "operational_mode": "agentic"
}
```

#### 24.5 Material, primary, agentic

```json
{
  "materiality": "material",
  "production_role": "primary",
  "operational_mode": "agentic"
}
```

### Classification is not responsibility

Participation classification describes AI involvement.

It MUST NOT determine:

```text
responsible party
legal responsibility
authorship
copyright ownership
professional responsibility
release authority
human adoption
```

Those concepts are governed separately.

### Classification is not quality

No participation class asserts that an artifact is:

```text
better
worse
more accurate
less accurate
safer
riskier
more original
less original
```

Participation classification is descriptive.

### Classification and `+AI`

Where:

```text
materiality = material
```

and the requirements of `+AI-100@0` are otherwise satisfied, the canonical `+AI` declaration may apply.

Where:

```text
materiality = incidental
```

incidental participation alone does not establish the material-AI-participation predicate required by `+AI`.

### Visible notation

This specification defines participation semantics but deliberately minimises visible notation.

The base condition:

```text
materiality = material
```

is represented by the canonical `+AI` declaration where the accountability requirements of `+AI-100@0` also apply.

The visible token:

```text
primary
```

is reserved to `+AI-220@0`.

Agent-related visible notation is reserved to `+AI-520@0`.

This specification does not define a canonical visible token for `collaborative`.

### Minor visible declaration

This version reserves the term:

```text
minor
```

for potential future visible use but does not register it as a canonical extension token.

The reason is that public interpretation of the word **minor** may imply non-materiality unless carefully defined.

A future specification MAY register the token if interoperability requires it.

Until then:

```text
+AI[minor]
```

MUST NOT be assumed to be canonical.

### Machine-readable classification

A conforming classification SHOULD take a form equivalent to:

```json
{
  "spec": "+AI-210@0",
  "subject": "artifact-version:7",
  "scope": "complete_artifact",
  "materiality": "material",
  "production_role": "collaborative",
  "operational_mode": "mixed",
  "basis": "Human and AI jointly developed the substantive artifact through direct and agentic activities."
}
```

### Classification evidence

The classification MAY reference provenance evidence such as:

```text
activity records
version history
prompts
agent execution traces
tool invocation records
human editing records
artifact derivation
```

Such evidence is useful but not universally mandatory.

Profiles MAY require evidence for particular classifications.

### Classification procedure

A classifier SHOULD determine participation in the following order.

#### Step 1 — Determine materiality

Ask:

> Did AI materially affect the relevant artifact, decision or release?

If no:

```text
materiality = incidental
```

If yes:

```text
materiality = material
```

#### Step 2 — Determine production role

Where material:

Ask whether AI participation was:

```text
bounded
interdependent
principal
```

Corresponding approximately to:

```text
minor
collaborative
primary
```

#### Step 3 — Determine operational mode

Ask whether material AI activity was principally:

```text
direct
agentic
mixed
```

#### Step 4 — Declare scope

State whether the classification applies to:

```text
the complete artifact
or
a defined subset/activity
```

### Borderline classifications

Where two production-role classifications are reasonably plausible, the classifier SHOULD select the less expansive claim unless a stronger classification is adequately supported.

For example, uncertainty between:

```text
collaborative
primary
```

SHOULD normally resolve to:

```text
collaborative
```

unless the principal-production condition can reasonably be established.

### Multiple AI systems

A single ArtifactVersion MAY involve multiple AISystems or Agents with different participation classifications.

Example:

```text
Model A:
    minor, direct

Agent B:
    primary, agentic
```

An aggregate artifact-level classification MAY also be supplied.

The aggregate classification MUST NOT erase more detailed per-actor classifications where those classifications are relevant to a governing profile.

### Classification across versions

Participation classification attaches to the applicable ArtifactVersion or Activity.

A material transformation MAY alter the classification.

Example:

```text
Version 1:
    primary AI participation

Human substantially reconstructs Version 1

Version 2:
    collaborative participation
```

The earlier classification MUST NOT automatically determine the later version's classification.

### Autonomous releases

An autonomous release MAY separately carry a participation classification.

Example:

```json
{
  "materiality": "material",
  "production_role": "primary",
  "operational_mode": "agentic"
}
```

and:

```text
AI[auto]
```

answer different questions.

The first describes participation.

The second describes the absence of qualifying Party Adoption before the Release.

### Provenance integration

A `+AI-410@0` provenance record SHOULD use the classifications defined by this specification rather than inventing implementation-specific percentage scales.

Material AI Activities SHOULD identify their applicable participation properties where known.

### Conformance

A participation classification conforms where:

1. its subject is identifiable;
2. its scope is explicit or unambiguously the complete artifact;
3. its materiality value conforms to this specification;
4. any production-role value conforms to this specification;
5. any operational-mode value conforms to this specification;
6. no numerical authorship threshold is presented as the normative basis of classification;
7. no classification is represented as implying responsibility, quality or correctness.

### Canonical distinctions

The family recognises these distinctions:

```text
INCIDENTAL
AI present, but no material substantive effect

MATERIAL + MINOR
AI materially mattered, but in a bounded production role

MATERIAL + COLLABORATIVE
AI and human activity were substantively interdependent

MATERIAL + PRIMARY
AI was the principal substantive production mechanism
```

Separately:

```text
DIRECT
human-directed AI operation

AGENTIC
AI agent exercised material operational discretion

MIXED
both modes materially contributed
```

### Canonical principle

The fundamental rule is:

**Classify what AI did, not what percentage of the artifact looks AI-generated.**

Participation is determined by substantive causal role, not arithmetic authorship.

## Module +AI-310 — Human Review

**Status:** Draft  
**Version:** 0.1  
**Identifier:** `+AI-310`  
**Canonical extension token:** `review`  
**Dependencies:** `+AI-001@0`, `+AI-100@0`  

### Purpose

This specification defines a human-review assurance declaration for AI-assisted artifacts.

Its canonical visible expression is:

```text
+AI[review]
```

The extension means that the underlying `+AI` declaration remains valid and that complete substantive human review of the released artifact version has occurred.

### Design principle

Ordinary `+AI` represents accountability.

It does not by itself represent complete human review.

`+AI[review]` therefore adds a separate assurance claim:

> **AI helped. A human substantively reviewed the resulting artifact. The responsible party still takes responsibility.**

Human review supplements accountability.

It does not replace accountability.

### Canonical notation

The canonical extension token is:

```text
review
```

When applied to the `+AI` root declaration:

```text
+AI[review]
```

Example:

```text
Eric Mourant +AI[review]
```

An organisation MAY also use the declaration:

```text
JAPER Technology +AI[review]
```

Where additional extensions apply, canonical ordering is governed by `+AI-001@0`.

### Meaning

A conforming `+AI[review]` declaration asserts that:

1. all requirements of the applicable `+AI` declaration are satisfied;
2. one or more identifiable human reviewers reviewed the applicable artifact version;
3. collectively, that review covered every material component of the artifact;
4. the review was substantive rather than ceremonial or purely mechanical;
5. the reviewer or review process had practical ability to identify issues affecting release;
6. the artifact version released was the reviewed version or a non-materially transformed equivalent;
7. no unreviewed material change occurred between completion of review and release.

These requirements collectively constitute **complete substantive human review**.

### Review subject

A human-review assertion MUST apply to an identifiable `ArtifactVersion`.

It MUST NOT apply merely to:

```text
a general project
an unspecified document
a conversation as a whole
a model
a workflow
an author
an organisation
```

unless the applicable profile defines a bounded artifact set whose individual versions are identifiable.

### Human reviewer

A qualifying reviewer MUST be a natural person.

An organisation MAY administer, record, require or attest to review, but an organisation itself is not a human reviewer.

Where an organisation is the responsible party, one or more human reviewers MAY perform review on its behalf according to the organisation's governance arrangements.

### Identifiability

The review process MUST be capable of identifying the human reviewer or reviewers.

Public disclosure of a reviewer's legal identity is not required by this specification.

A public machine-readable representation MAY use an opaque or pseudonymous identifier where:

* that identifier uniquely represents the reviewer within the applicable provenance context; and
* applicable profiles do not require stronger identification.

### Material component

A **material component** is any component whose content, behaviour, omission or presentation could materially affect the meaning, function, interpretation, decision, claim, instruction or outcome represented by the artifact.

Depending upon artifact type, material components may include:

```text
prose
claims
data
calculations
source code
executable behaviour
images
charts
audio
video
instructions
recommendations
citations
interfaces
configuration
outputs
```

Purely mechanical formatting is not necessarily material.

A profile MAY define materiality more precisely for a domain.

### Complete substantive review

Review is **complete** when every material component of the applicable artifact version has been subjected to meaningful human examination.

Complete review does not require conscious inspection of every byte, character, punctuation mark, pixel, sample or machine instruction.

The test is substantive coverage rather than literal microscopic inspection.

### Distributed review

Complete review MAY be performed by multiple human reviewers.

No single reviewer is required to review every material component where:

* collectively, human review covers all material components;
* responsibility for review coverage can be determined;
* gaps in coverage are not knowingly represented as complete review.

A machine-readable record SHOULD permit review coverage to be attributed to individual reviewers where practical.

### Meaningful examination

A reviewer MUST engage directly with the material being reviewed to an extent sufficient to constitute genuine substantive examination.

The following do not, by themselves, constitute qualifying review:

```text
opening the artifact
scrolling through it without substantive inspection
reading only headings
reading only selected samples
reading only an AI-generated summary
accepting an automated "review passed" result
relying exclusively on another AI system's description
checking only spelling or formatting
```

### AI-assisted review

A human reviewer MAY use artificial intelligence during the review process.

AI MAY assist with:

```text
issue detection
comparison
summarisation
testing
analysis
cross-checking
navigation
classification
```

AI assistance MUST NOT substitute for the human act required by this specification.

A reviewer who has not meaningfully examined the substantive artifact MUST NOT claim complete human review solely because an AI system examined it.

### Review competence

This specification does not establish a universal professional-competence threshold.

A reviewer SHOULD possess sufficient contextual understanding to conduct a meaningful review for the intended release.

Domain profiles MAY require:

```text
professional qualifications
technical competence
security clearance
subject-matter expertise
organisational authority
independence
```

Absence of such additional requirements does not change the base meaning of `review`.

### Ability to act on the review

The review process MUST provide a practical means for material review findings to affect the release process.

At least one of the following MUST be possible:

```text
correct the artifact
request correction
reject the artifact
withhold release
escalate a material issue to an authorised decision-maker
```

A purely ceremonial review performed where findings cannot affect any decision SHOULD NOT be represented as `+AI[review]`.

### Reviewer and responsible party

The reviewer MAY be the same person as the responsible party.

The reviewer MAY be different from the responsible party.

`+AI[review]` does not imply independent review.

Independence is outside the scope of this specification.

Independent assurance is reserved for specifications such as `+AI-320@0`.

### Timing

A qualifying review MUST be complete before the release to which the `+AI[review]` declaration applies.

A review performed only after a release does not retroactively make that earlier release conformant.

The same artifact MAY subsequently be reviewed and released again under a new release event.

That later release MAY qualify for `+AI[review]`.

### Material change after review

A material change to an artifact after review invalidates the review assertion for the changed artifact version.

The changed artifact MUST be reviewed before `review` may be applied to that version.

Examples of potentially material change include:

```text
new substantive text
changed factual claims
changed calculations
changed recommendations
changed source code
changed executable behaviour
changed images affecting meaning
new AI-generated content
deleted qualifying information
changed instructions
```

### Non-material transformation

A review assertion MAY survive a transformation that does not materially change the reviewed artifact.

Examples may include:

```text
format conversion
printing
archival packaging
lossless media conversion
routine pagination
mechanical metadata insertion
```

Where the artifact bytes change, provenance SHOULD identify the reviewed source version and the derived version.

If material equivalence cannot reasonably be established, the transformed artifact SHOULD be reviewed again.

### Review and correctness

`+AI[review]` does NOT assert that:

```text
the artifact is correct
all facts are true
all citations are valid
all calculations are correct
the artifact is safe
the artifact complies with law
the artifact meets a professional standard
the reviewer agreed with every statement
the reviewer independently reproduced the work
the artifact has been independently verified
```

Human review is an assurance about the review process, not a warranty of correctness.

### Review and verification

Human review and independent verification are distinct.

Review asks:

> **Did a human substantively examine the complete artifact?**

Verification asks a different question:

> **Were specified claims, properties or results independently tested or checked according to a defined method?**

An artifact MAY be:

```text
reviewed but not verified
verified in part but not completely reviewed
both reviewed and verified
neither reviewed nor verified
```

### Review findings

This specification does not require that a reviewer agree with every component of an artifact.

Review findings MAY result in:

```text
correction
qualification
disclosure
acceptance of a known limitation
escalation
release without change
```

The responsible party remains responsible for the decision to release the artifact.

The `review` token indicates that complete substantive human examination occurred, not that every reviewer endorsed every proposition.

### Machine-readable assertion

A conforming machine-readable review assertion SHOULD include:

```json
{
  "id": "assurance:review-001",
  "spec": "+AI-310@0",
  "type": "human_review",
  "subject_artifact_version": "artifact-version:7",
  "reviewers": [
    "party:reviewer-1"
  ],
  "scope": "complete_substantive",
  "status": "completed",
  "completed_at": "2026-08-19T10:30:00+10:00"
}
```

A published machine-readable record MAY additionally identify:

```text
review method
component coverage
findings
review activities
supporting evidence
derived versions
responsible organisation
```

### Review predicate

For artifact version `A` and release `R`:

```text
HumanReview(A,R) :=
    ExistsHumanReviewer(A)
AND CompleteMaterialCoverage(A)
AND SubstantiveExamination(A)
AND ReviewCouldAffectRelease(A,R)
AND ReviewCompletedBeforeRelease(A,R)
AND ReleasedVersionMatchesReviewedVersion(A,R)
AND NoUnreviewedMaterialChange(A,R)
```

The extension:

```text
+AI[review]
```

is valid only where:

```text
PlusAI(A,R)
AND
HumanReview(A,R)
```

are both true.

### Invalid uses

The following are non-conforming examples.

#### 25.1 Summary-only review

A human reads an AI-generated summary but not the substantive artifact.

```text
+AI[review]
```

MUST NOT be used on that basis.

#### 25.2 Spot checking

A human examines only a sample of a larger artifact.

Unless a domain specification explicitly defines that sample as complete coverage, `review` MUST NOT be used.

#### 25.3 Automated reviewer

An AI system reviews another AI system's output and reports that it is acceptable.

Without qualifying human substantive examination, `review` MUST NOT be used.

#### 25.4 Post-release review

An artifact is published automatically and reviewed by a human afterwards.

The original release MUST NOT be retroactively described as `+AI[review]`.

#### 25.5 Material alteration

A reviewed document is materially rewritten after review.

The changed version MUST NOT carry `review` until the changed material is reviewed.

### Multiple reviewers

Where multiple reviewers collectively establish complete coverage, the review assertion SHOULD record all contributing reviewers.

A domain profile MAY require a review coverage map.

Example:

```text
Reviewer A → sections 1–4
Reviewer B → sections 5–9
Reviewer C → data and calculations
```

If those components collectively constitute the complete material artifact, the review MAY qualify.

### Evidence

Evidence of human review MAY include:

```text
review records
comments
approval records
version-control history
workflow records
timestamps
signed attestations
change records
review checklists
```

Public evidence is not mandatory under this specification.

A stronger evidence requirement MAY be imposed by a profile or by `+AI-630@0`.

### Privacy

Human-review provenance SHOULD minimise unnecessary disclosure of personal information.

A profile MAY require stronger reviewer identification where accountability, regulation or professional practice requires it.

### Conformance

A declaration conforms to `+AI-310@0` when:

1. its underlying `+AI` declaration conforms;
2. the applicable artifact version satisfies the human-review predicate;
3. the `review` extension is represented according to `+AI-001@0`;
4. any published machine-readable assertion accurately represents the review that occurred.

### Canonical explanation

Where a short explanation is required:

> **`+AI[review]` means AI materially assisted this work, the named party accepts responsibility for releasing it, and the complete substantive artifact was reviewed by a human before release.**

A shorter public explanation MAY be:

**AI helped. A human reviewed it. I take responsibility.**

## Module +AI-320 — Independent Verification

**Status:** Draft  
**Version:** 0.1  
**Identifier:** `+AI-320`  
**Canonical extension token:** `verify`  
**Dependencies:** `+AI-001@0`, `+AI-020@0`, `+AI-100@0`  

### Purpose

This specification defines an independent-verification assurance declaration for AI-assisted artifacts.

Its canonical visible expression is:

```text
+AI[verify]
```

The declaration means that:

1. the underlying `+AI` accountability declaration is valid; and
2. an identifiable independent verifier successfully completed a defined verification of the applicable artifact version before the relevant release.

### Design principle

Human review and independent verification are different assurance activities.

Human review asks:

> **Did a human substantively examine the artifact?**

Independent verification asks:

> **Did a sufficiently independent verifier test or check defined claims, properties or results using a defined method?**

Neither assertion implies the other.

### Canonical notation

The canonical token is:

```text
verify
```

Applied to the `+AI` root:

```text
+AI[verify]
```

Example:

```text
Eric Mourant +AI[verify]
```

Where human review also qualifies:

```text
Eric Mourant +AI[review,verify]
```

Canonical token ordering is defined by `+AI-001@0`.

### Meaning

A conforming `+AI[verify]` declaration asserts that:

1. the underlying `+AI` declaration conforms;
2. a defined verification subject exists;
3. a defined verification scope exists;
4. a defined verification method exists;
5. one or more qualifying independent verifiers performed that method;
6. the verification was completed before release;
7. the verification produced a qualifying successful outcome;
8. the subject was not materially changed after verification without corresponding re-verification.

### Verification subject

Verification MUST identify what is being verified.

The subject MAY include:

```text
factual claims
calculations
data transformations
software behaviour
test results
citations
provenance claims
cryptographic claims
technical properties
experimental results
conformance properties
specified outputs
```

The subject MUST be sufficiently bounded for the verification claim to be meaningful.

### Defined scope

Verification MUST have an explicit scope.

Examples include:

```text
all factual claims in sections 1–8
all calculations in workbook version 12
the behaviour covered by test suite X
all citations in the released report
the provenance chain represented by record P
specified safety properties A, B and C
```

A statement such as:

```text
verified
```

without a determinable scope is insufficient for conformance.

### Scope and visible notation

The visible token:

```text
verify
```

means:

> **Independent verification was successfully completed under a defined scope and method.**

It MUST NOT be interpreted to mean that every conceivable property of the artifact has been independently verified.

The verification scope SHOULD be reasonably accessible wherever practical.

A domain profile MAY require the scope to be displayed publicly.

### Verification method

A conforming verification MUST use a method capable of testing the assertions or properties within the declared scope.

Methods MAY include:

```text
source checking
independent calculation
reproduction
testing
static analysis
dynamic analysis
comparison against primary data
citation validation
formal verification
measurement
cryptographic validation
controlled experiment
```

The method MUST be more than a statement of approval.

### Verification outcome

The canonical `verify` token requires a successful verification outcome.

A qualifying outcome means that the subject satisfied the verification criteria defined for the declared scope.

The following MUST NOT independently qualify for `verify`:

```text
verification incomplete
verification failed
verification abandoned
verification result unknown
unresolved material discrepancies
```

A verification report MAY contain non-material observations without invalidating the outcome.

Material exceptions MUST be resolved or explicitly excluded from the verification scope before `verify` is used.

### Independent verifier

A verifier MAY be:

```text
a natural person
an organisational verification function
an independent organisation
```

The verifier MUST be identifiable within the applicable provenance record.

An organisation acting as verifier SHOULD identify the human or controlled verification process that actually performed the substantive verification where practical.

### Independence

A verifier is sufficiently independent when the verifier has enough separation from the production and release decision to provide a genuinely distinct check.

At minimum:

* the verifier MUST NOT be the same natural person who materially produced the subject being verified;
* the verifier MUST NOT verify their own substantive work as independent verification;
* the verifier MUST NOT be controlled by the AISystem or Agent whose output is being verified;
* the verification result MUST be capable of producing a finding contrary to the interests or expectations of the production process.

### Organisational independence

Where the responsible Party is an organisation, a verifier MAY operate within the same organisation if the verification function has meaningful functional independence from the production activity.

A conforming internal independent-verification function SHOULD have:

```text
distinct personnel or function
separate review responsibility
authority to report adverse findings
ability to prevent or escalate release where required
documented independence basis
```

A domain profile MAY require external verification.

### External verification

External verification means the verifying Party is organisationally separate from the responsible Party.

External verification is stronger evidence of organisational separation but does not automatically establish:

```text
competence
correctness
absence of conflict
completeness
professional certification
```

Those properties require separate criteria.

### Prior participation

A verifier MUST NOT have materially contributed to producing the specific content, calculation, code, result or other property that the verifier later claims to independently verify.

Incidental activities that do not compromise independence MAY be permitted.

Examples may include:

```text
providing the verification protocol beforehand
defining acceptance criteria
supplying reference data
administrative coordination
```

Where prior participation could reasonably compromise independence, it MUST be disclosed or another verifier used.

### Responsible party and verifier

The verifier SHOULD be distinct from the responsible Party.

Where the responsible Party is an individual, that same individual MUST NOT satisfy the independent-verifier requirement.

Where the responsible Party is an organisation, a qualifying functionally independent verifier within that organisation MAY satisfy the requirement unless an applicable profile requires external independence.

### AI-assisted verification

A verifier MAY use AI systems during verification.

AI MAY assist with:

```text
search
comparison
testing
calculation
anomaly detection
source matching
code analysis
data analysis
```

The verifier remains responsible for the verification assertion it issues.

Use of AI does not inherently invalidate independence.

### Fully automated verification

A verification process MAY include fully automated technical checks where those checks are appropriate to the declared method.

However, the `verify` assertion MUST be issued or adopted by an identifiable qualifying verifier.

An AISystem or Agent MUST NOT independently confer the `verify` token on its own output.

A future specification MAY define autonomous machine-verification assertions separately.

### Reproduction

Independent reproduction is a strong form of verification but is not universally required.

Where reproduction is claimed, the verifier SHOULD independently recreate the relevant result from defined inputs and methods.

The ordinary `verify` token MUST NOT be interpreted as implying complete independent reproduction unless the verification record states that reproduction occurred.

### Verification versus review

An artifact MAY be independently verified without receiving complete human review.

For example:

```text
a software output may be independently tested
without every source file being manually reviewed
```

Likewise, an artifact may receive complete human review without independent verification.

Therefore:

```text
+AI[review]
```

and:

```text
+AI[verify]
```

are orthogonal assertions.

### Timing

Verification for a release MUST be complete before that Release.

A verification performed after Release does not retroactively cause the earlier Release to qualify for `+AI[verify]`.

A later Release of the same ArtifactVersion MAY qualify once verification has been completed.

### Material change after verification

A material change to a verified subject invalidates the verification assertion for the changed subject.

The changed material MUST be re-verified before `verify` may apply.

An unrelated material change outside the declared verification scope MAY leave the verification assertion intact, provided the change cannot reasonably affect the verified property.

### Non-material transformations

A verification assertion MAY survive a non-material transformation where the verified properties remain unchanged.

For example:

```text
a verified calculation in a report
may remain verified after lossless PDF conversion
```

Provenance SHOULD identify both representations.

### Partial verification

Partial verification is permitted as an underlying AssuranceAssertion.

However, its scope MUST be explicit.

A visible `verify` token MAY be used only where the verification record clearly defines the verified scope and a reasonable reader would not thereby be given a materially false impression of broader verification.

Domain profiles MAY impose stricter display requirements for partial verification.

### Verification evidence

A verification assertion SHOULD retain evidence sufficient to determine:

```text
who verified
what was verified
how it was verified
when verification occurred
what criteria were applied
what result was reached
which ArtifactVersion was tested
```

Evidence MAY include:

```text
verification reports
test logs
independent calculations
source records
signatures
reproduction records
formal proofs
audit records
```

### Machine-readable assertion

A conforming machine representation SHOULD contain information equivalent to:

```json
{
  "id": "assurance:verify-001",
  "spec": "+AI-320@0",
  "type": "independent_verification",
  "subject_artifact_version": "artifact-version:7",
  "verifier": "party:verifier-1",
  "scope": {
    "type": "defined",
    "description": "All factual claims and citations"
  },
  "method": "Independent source and citation validation",
  "independence": {
    "basis": "external"
  },
  "outcome": "verified",
  "completed_at": "2026-08-19T09:40:00+10:00"
}
```

### Independence basis

A machine-readable verification assertion SHOULD identify one of:

```text
external
functional
other-defined
```

`external` means organisational separation.

`functional` means documented independence within the responsible organisation.

`other-defined` requires an accompanying explanation.

A profile MAY define additional independence classes.

### Verification predicate

For ArtifactVersion `V`, Release `R`, verifier `Q`, scope `S` and method `M`:

```text
IndependentVerification(V,R) :=
    DefinedSubject(V)
AND DefinedScope(S)
AND DefinedMethod(M)
AND IdentifiableVerifier(Q)
AND SufficientlyIndependent(Q,V)
AND MethodPerformed(Q,S,M)
AND Outcome = Verified
AND CompletedBeforeRelease(R)
AND NoUnverifiedMaterialChangeToSubject(V,R)
```

The visible extension is valid only where:

```text
PlusAI(V,R)
AND
IndependentVerification(V,R)
```

are both true.

### What `verify` does not mean

Unless separately asserted, `+AI[verify]` does NOT mean:

```text
the entire artifact is error-free
every possible claim was checked
the artifact was professionally certified
the verifier accepts release responsibility
the verifier authored the work
the artifact meets applicable legal requirements
the artifact is medically safe
the artifact has complete human review
the verification was external
the verification used no AI
```

### Invalid uses

The following do not qualify.

#### 30.1 Self-verification

A person creates a calculation and then checks that same calculation themselves.

This may be review or checking.

It is not independent verification.

#### 30.2 AI self-check

An AI system generates an answer and then prompts itself to verify the answer.

This does not establish independent verification.

#### 30.3 Undefined approval

A second person says:

> looks good

without a defined verification scope or method.

This does not qualify.

#### 30.4 Failed verification

An independent verifier finds unresolved material errors.

`verify` MUST NOT be used until the verified subject passes the applicable criteria.

#### 30.5 Verification after modification

Version 7 is verified.

Version 8 materially changes the verified calculation.

Version 8 MUST NOT inherit the assertion.

### Canonical explanation

Where a concise explanation is required:

> **`+AI[verify]` means AI materially assisted this work, the named party accepts responsibility for releasing it, and an independent verifier successfully checked a defined scope of the work using a defined method before release.**

A shorter public explanation MAY be:

**AI helped. Independently verified. I take responsibility.**

## Module +AI-410 — Provenance Record

**Status:** Draft  
**Version:** 0.1  
**Identifier:** `+AI-410`  
**Canonical extension token:** `prov`  
**Dependencies:** `+AI-001@0`, `+AI-020@0`  
**Related specifications:** `+AI-100@0`, `+AI-210@0`, `+AI-530@0`, `+AI-620@0`, `+AI-630@0`, `+AI-710@0`  

### Purpose

This specification defines a machine-readable provenance record for artifacts and releases within the `+AI` specification family.

It establishes:

* provenance-record identity;
* provenance scope;
* artifact-version identification;
* release association;
* actor and system references;
* activity graphs;
* derivation relationships;
* AI-participation classifications;
* authority and adoption references;
* disclosure levels;
* explicit unknown and withheld information;
* evidence references;
* and the visible `prov` extension.

### Design principle

Provenance answers:

> **What materially happened, involving whom or what, to produce and release this artifact?**

A provenance record SHOULD describe causal and governance relationships.

It SHOULD NOT attempt to reduce provenance to a single authorship percentage.

The preferred representation is a graph.

### Canonical visible token

The canonical extension token is:

```text
prov
```

Permitted forms include:

```text
+AI[prov]
```

and:

```text
AI[auto,prov]
```

where the requirements of the corresponding root declaration are satisfied.

### Meaning of `prov`

The `prov` extension asserts that:

1. a conforming `+AI-410@0` provenance record exists;
2. the record applies to the relevant ArtifactVersion and Release;
3. the provenance record declares its disclosure level;
4. the record identifies its known limitations;
5. the record is accessible to the intended relying party through the applicable binding.

`prov` does NOT assert that the provenance record contains every event that occurred.

### Provenance subject

Every provenance record MUST identify at least one subject ArtifactVersion.

Where the provenance relates to release accountability, it SHOULD identify the applicable Release.

A record MAY describe multiple related ArtifactVersions.

### Provenance graph

A provenance record consists conceptually of:

```text
entities
activities
relationships
assertions
evidence references
```

Typical graph structure:

```text
Party
  │
  ├── grants authority ──► Agent
  │                         │
  │                      performs
  │                         ▼
  │                      Activity
  │                         │
  │                      produces
  │                         ▼
  │                  ArtifactVersion
  │                    │          │
  │                 derives     adopted
  │                    │          │
  │                    ▼          ▼
  │              ArtifactVersion Adoption
  │                               │
  │                               ▼
  └──────────────────────────── Release
                                  │
                                  ▼
                         Responsibility
                          Declaration
```

### Provenance record identity

Every provenance record MUST have:

```text
record identifier
specification identifier
record version
subject
disclosure level
```

Example:

```json
{
  "id": "prov:12345",
  "spec": "+AI-410@0",
  "record_version": "1",
  "subject": "artifact-version:7",
  "disclosure_level": "material"
}
```

### Record version

The provenance-record version identifies a version of the provenance record itself.

It is distinct from the ArtifactVersion.

A provenance record MAY be updated after release to:

```text
add evidence
correct metadata
resolve previously unknown identity
add verification records
add cryptographic signatures
```

Historical record versions SHOULD remain distinguishable where practical.

### Provenance scope

Every provenance record MUST declare its scope.

Canonical scopes include:

```text
artifact
release
defined-component
defined-activity
```

Where the scope is less than the complete artifact and release history, the limitation MUST be clear.

### Temporal scope

A provenance record SHOULD identify the period or activity range it covers where this is not obvious from the graph.

Example:

```text
from creation of ArtifactVersion 1
through Release R7
```

A provenance record MUST NOT imply coverage of events occurring after its declared scope.

### Disclosure level

Every conforming provenance record MUST declare one of the following levels:

```text
core
material
evidenced
```

These levels describe disclosure depth.

They do not describe artifact quality.

### Core provenance

`core` is the minimum conforming disclosure level.

A core record MUST identify:

```text
subject ArtifactVersion
applicable Release where relevant
root declaration where applicable
responsible Party or autonomous-release state
material AI participation
AI participation classification where known
at least one materially relevant AISystem or Agent reference,
    or an explicit status explaining why identification is unavailable
record scope
known provenance limitations
```

A core record need not enumerate every material Activity.

### Material provenance

`material` includes all requirements of `core`.

It MUST additionally represent the known materially relevant activity and derivation graph sufficient to explain how the subject ArtifactVersion came into its substantive released form.

Material provenance SHOULD identify:

```text
material human Activities
material AI Activities
material Agent Activities
input ArtifactVersions
output ArtifactVersions
material transformations
review Activities
verification Activities
authority relationships where relevant
Adoption
Release
```

Where a material Activity is known but details cannot be disclosed, the record MUST represent the existence of the Activity and its disclosure state.

### Evidenced provenance

`evidenced` includes all requirements of `material`.

It MUST additionally associate supporting Evidence with material provenance claims to a degree sufficient to permit meaningful validation of the provenance record.

Evidence MAY include:

```text
artifact digests
timestamps
digital signatures
activity logs
repository commits
review records
verification reports
authority records
signed attestations
content credentials
```

`evidenced` does not mean every provenance statement has cryptographic proof.

Where evidence type is material to interpretation, it MUST be identifiable.

### Disclosure-level hierarchy

The levels are cumulative:

```text
evidenced
    ⊃
material
    ⊃
core
```

Therefore:

```text
evidenced satisfies material
material satisfies core
```

subject to all requirements being fulfilled.

### Visible `prov` token and disclosure level

The visible:

```text
prov
```

token does not encode the disclosure level.

Therefore:

```text
+AI[prov]
```

means:

> A conforming provenance record exists.

The record itself MUST state:

```text
core
material
or
evidenced
```

A profile MAY require a minimum level.

Example:

```text
+AI-820@0 Research Profile
requires:
    provenance >= material
```

### Public availability

A provenance record need not always be globally public.

It MUST, however, be accessible to the intended relying party where the `prov` token is presented as a claim.

Depending on context, accessibility MAY mean:

```text
publicly resolvable
embedded in artifact
available to recipient
available within an authenticated system
available to an auditor
available within an organisational provenance service
```

A public-facing artifact using `prov` SHOULD provide a publicly discoverable provenance summary unless legitimate constraints prevent it.

### Explicit disclosure state

Where a provenance field cannot be populated normally, the implementation SHOULD use an explicit disclosure state rather than omit the field ambiguously.

Canonical states are:

```text
known
unknown
withheld
unavailable
not-applicable
```

### Unknown

`unknown` means the information is not known to the provenance issuer.

Example:

```json
{
  "model_identity": {
    "status": "unknown"
  }
}
```

`unknown` MUST NOT be used merely to avoid disclosing known information.

### Withheld

`withheld` means the information is known but intentionally not disclosed in the applicable record.

A withheld value SHOULD include a reason class.

Examples:

```text
privacy
security
confidentiality
contractual
legal
trade-secret
safety
```

Example:

```json
{
  "model_identity": {
    "status": "withheld",
    "reason": "confidentiality"
  }
}
```

### Unavailable

`unavailable` means the information may once have existed or may exist elsewhere but is not available to the provenance issuer.

Examples include:

```text
lost log
third-party record inaccessible
legacy system did not preserve field
```

### Not applicable

`not-applicable` means the field has no semantic application to the represented activity.

It MUST NOT be used as a synonym for unknown.

### Omission

Omission of an optional field means only:

> this record makes no representation concerning that field.

Implementations SHOULD prefer explicit disclosure states where omission could materially affect interpretation.

### Party provenance

A provenance record MAY identify Parties participating as:

```text
creator
editor
operator
reviewer
verifier
authority grantor
adopter
responsible party
releaser
```

Roles MUST be represented explicitly.

Identity MUST NOT imply role.

### AI System provenance

Where known and permitted, a provenance record SHOULD identify materially participating AISystems.

Information MAY include:

```text
provider
product
model
model version
deployment
configuration
```

A model identifier MUST NOT be treated as proof that the model performed a particular Activity.

The Activity relationship must separately establish participation.

### Agent provenance

Materially participating Agents SHOULD be represented independently from the AISystems they use.

An Agent record MAY identify:

```text
agent identifier
operator
purpose
software version
AISystems used
authority grant
sub-agent relationships
```

### Activity

Every represented Activity SHOULD identify:

```text
activity identifier
activity type
actor
inputs
outputs
time or ordering
materiality
```

Where applicable it SHOULD additionally identify:

```text
AI participation classification
authority grant
evidence
tools
parameters
```

### Canonical activity classes

This specification reserves the following broad Activity classes:

```text
create
generate
analyse
research
transform
edit
translate
review
verify
test
select
approve
adopt
delegate
release
sign
```

Bindings MAY define subtypes.

A subtype MUST preserve the semantic parent activity where one exists.

### Material activity

A Material Activity is an Activity whose occurrence materially affected:

```text
the ArtifactVersion
a material decision concerning it
its assurance state
its release state
```

Material provenance MUST represent all material Activities known to the provenance issuer that fall within the declared scope, subject to explicit withheld or unavailable states.

### Non-material activity

A record MAY include non-material Activities.

Their presence does not make them material.

Implementations SHOULD avoid overwhelming provenance records with mechanically generated events that do not improve substantive understanding.

### Activity ordering

Activity ordering MAY be represented using:

```text
timestamps
sequence identifiers
dependency edges
input/output derivation
```

Exact wall-clock timestamps are not required where meaningful causal ordering can otherwise be established.

### Derivation

A derivation relationship means one ArtifactVersion materially derives from another ArtifactVersion.

Example:

```text
ArtifactVersion V1
      │
   transformed
      ▼
ArtifactVersion V2
```

The record SHOULD identify the Activity responsible for material derivation.

### Non-material transformation

A provenance graph MAY relate technically different representations through a non-material transformation relationship.

Example:

```text
DOCX V7
   │
PDF conversion
   │
   ▼
PDF representation
```

The record SHOULD indicate whether material equivalence is asserted.

### Participation classification

Material AI participation SHOULD use `+AI-210@0`.

Example:

```json
{
  "materiality": "material",
  "production_role": "primary",
  "operational_mode": "agentic"
}
```

A provenance record SHOULD NOT substitute implementation-specific authorship percentages for the normative participation classification.

### Multiple AI contributors

Where multiple AISystems or Agents materially participate, provenance SHOULD represent each separately where known.

Example:

```text
Human
  │
  ▼
Model A → research
  │
  ▼
Agent B → synthesis
  │
  ▼
Model C → editing
  │
  ▼
ArtifactVersion
```

The record MAY additionally provide an aggregate participation classification.

### Authority provenance

Where Agent activity materially depends upon delegated authority, material provenance SHOULD represent the relevant AuthorityGrant.

An authority chain MAY be represented as:

```text
Party
  │
Grant 1
  ▼
Agent A
  │
Grant 2
  ▼
Agent B
```

A child authority relationship MUST NOT imply authority beyond that represented by the applicable parent grant.

### Adoption provenance

Where a `+AI` responsibility declaration applies, provenance SHOULD identify:

```text
responsible Party
Adoption
ArtifactVersion
Release
ResponsibilityDeclaration
```

This enables a relying party to distinguish:

```text
AI-produced and human-adopted
```

from:

```text
AI-produced and autonomously released
```

### Autonomous-release provenance

Where `AI[auto]` applies, the provenance record SHOULD identify:

```text
Agent or AISystem materially controlling the Release
ArtifactVersion
Release
relevant AuthorityGrants
absence of qualifying Adoption
operator where known
```

The absence of qualifying Adoption is a semantic condition defined by `+AI-530@0`, not merely an omitted field.

### Review provenance

Where `+AI[review]` applies, the provenance record SHOULD identify the applicable `+AI-310@0` AssuranceAssertion.

At `material` level or higher, it SHOULD also identify the substantive review Activity or Activities.

### Verification provenance

Where `+AI[verify]` applies, the record SHOULD identify:

```text
verifier
verified subject
scope
method
outcome
completion time
independence basis
```

At `evidenced` level, supporting verification Evidence MUST be associated with the assertion.

### Evidence links

Evidence SHOULD be represented as a separate entity and referenced from the claim it supports.

Example:

```text
Activity
   │
supported by
   ▼
Evidence
```

rather than embedding evidence semantics implicitly within the Activity.

### Cryptographic evidence

This specification permits but does not require cryptographic evidence.

Examples include:

```text
SHA-family content digests
digital signatures
signed manifests
trusted timestamps
content credentials
transparency-log entries
```

The normative requirements for cryptographic provenance are reserved to `+AI-630@0`.

### Provenance integrity

A provenance record SHOULD be bound to its subject ArtifactVersion using an integrity mechanism where practical.

At the `evidenced` level, ArtifactVersion identity MUST be sufficiently precise to distinguish material alteration.

A content digest is RECOMMENDED where technically appropriate.

### Provenance issuer

Every conforming provenance record SHOULD identify an issuer.

The issuer is the entity asserting the provenance record.

The issuer need not be:

```text
the responsible Party
the artifact creator
the verifier
the AI provider
```

Issuer identity MUST NOT imply those roles.

### Assertion versus observation

A record MAY distinguish between:

```text
observed events
asserted events
imported events
inferred relationships
```

Where a relationship is inferred rather than directly observed or asserted, that status SHOULD be represented.

### Provenance confidence

A binding MAY represent confidence concerning provenance information.

Confidence MUST NOT replace the disclosure-state mechanism.

For example:

```text
known with low confidence
```

and:

```text
unknown
```

are semantically different.

### Provenance boundaries

Every non-trivial provenance record SHOULD state relevant boundaries.

Example:

```text
This record covers substantive activities from initial AI research through publication.

It does not cover creation of third-party source documents.
```

A provenance boundary prevents a scoped record from being misinterpreted as a universal history.

### Imported artifacts

Where an ArtifactVersion incorporates external material, the provenance record MAY represent that material as an external input without reproducing its complete provenance.

Example:

```text
ExternalSource X
     │
     ▼
Research Activity
     │
     ▼
ArtifactVersion
```

The provenance record MUST NOT imply knowledge of the complete origin of ExternalSource X unless that provenance is actually represented.

### Recursive provenance

A provenance record MAY reference another provenance record.

Example:

```text
Artifact A
    provenance → Record A

Artifact B derives from Artifact A

Record B references Record A
```

Implementations SHOULD avoid unnecessary duplication where stable provenance references exist.

### Provenance persistence

Provenance SHOULD survive reasonable artifact transformations where attribution and relevant identity are preserved.

A binding SHOULD provide mechanisms to:

```text
embed provenance
link provenance
resolve provenance
or
carry provenance across transformations
```

Where metadata is stripped, an external resolvable reference MAY preserve the association.

### Privacy

Provenance SHOULD disclose no more personal information than required by the applicable specification, profile or use case.

Pseudonymous identifiers MAY be used where identity can remain sufficiently stable for the intended provenance purpose.

Profiles MAY impose stronger identification requirements.

### Confidentiality

A conforming provenance record MAY withhold sensitive details.

Withholding MUST be explicit where the existence of the underlying material Activity or actor is relevant to the declared disclosure level.

Example:

```json
{
  "actor": {
    "status": "withheld",
    "reason": "security"
  },
  "activity_type": "analysis",
  "material": true
}
```

### Security

A provenance record MUST NOT require disclosure that would itself create an unreasonable security risk.

Examples may include:

```text
secret credentials
private keys
sensitive system prompts
exploit details
protected operational data
```

The existence of protected information MAY be represented without disclosing its contents.

### Machine-readable minimal record

A conceptual core-level record may resemble:

```json
{
  "id": "prov:12345",
  "spec": "+AI-410@0",
  "record_version": "1",
  "subject": {
    "artifact_version": "artifact-version:7",
    "release": "release:7"
  },
  "disclosure_level": "core",
  "root_declaration": "+AI",
  "responsible_party": "party:eric",
  "ai_participation": {
    "materiality": "material",
    "production_role": "collaborative",
    "operational_mode": "mixed"
  },
  "ai_systems": [
    "ai-system:1"
  ],
  "limitations": []
}
```

### Material-level example

A conceptual material-level record may resemble:

```json
{
  "id": "prov:12345",
  "spec": "+AI-410@0",
  "record_version": "2",
  "subject": {
    "artifact_version": "artifact-version:7",
    "release": "release:7"
  },
  "disclosure_level": "material",
  "activities": [
    {
      "id": "activity:1",
      "type": "research",
      "actor": "party:human-1",
      "material": true
    },
    {
      "id": "activity:2",
      "type": "generate",
      "actor": "ai-system:1",
      "material": true
    },
    {
      "id": "activity:3",
      "type": "edit",
      "actor": "party:human-1",
      "material": true
    },
    {
      "id": "activity:4",
      "type": "adopt",
      "actor": "party:human-1",
      "material": true
    },
    {
      "id": "activity:5",
      "type": "release",
      "actor": "party:human-1",
      "material": true
    }
  ]
}
```

### Graph completeness

No practical provenance system can guarantee knowledge of every causal event.

Accordingly, this specification does not use **complete provenance** as a canonical disclosure level.

Instead, records declare:

```text
scope
level
limitations
unknowns
withheld information
```

A record MUST NOT describe itself as complete unless an applicable profile precisely defines what complete means for that bounded scope.

### Unknown provenance

A provenance graph may contain gaps.

Example:

```text
Artifact V1
    │
unknown activity
    │
    ▼
Artifact V2
```

The gap SHOULD be explicitly represented where it materially affects interpretation.

A provenance gap does not automatically invalidate the entire record.

It MAY prevent conformance with a higher disclosure level.

### Level downgrade

Where a record cannot satisfy the requirements of its stated disclosure level, it MUST:

```text
correct the record
or
declare a lower conforming level
```

It MUST NOT retain a higher level merely because the issuer intends to collect the missing information later.

### `prov` conformance

The visible:

```text
prov
```

token is valid where:

```text
ConformingProvenanceRecord(P)
AND
P.subject = applicable ArtifactVersion
AND
P.release = applicable Release where release-scoped
AND
P.disclosure_level ∈ {core, material, evidenced}
AND
P is accessible to intended relying party
```

### `prov` does not mean complete

The following inference is invalid:

```text
+AI[prov]
therefore
every human and AI activity is disclosed
```

The valid inference is:

> A conforming scoped provenance record exists, and that record declares its disclosure level and limitations.

### `prov` does not mean verified

A provenance record may contain claims that have not been independently verified.

Therefore:

```text
+AI[prov]
```

does not imply:

```text
+AI[verify]
```

Likewise:

```text
+AI[verify]
```

does not automatically imply:

```text
+AI[prov]
```

### `prov` does not mean signed

A provenance record may exist without cryptographic signing.

Therefore:

```text
+AI[prov]
```

does not imply:

```text
+AI[signed]
```

Cryptographic assurance is separately defined.

### Conformance classes

This specification defines three provenance-record conformance classes:

```text
+AI-410@0 Core Provenance
+AI-410@0 Material Provenance
+AI-410@0 Evidenced Provenance
```

A profile SHOULD state the minimum acceptable class where provenance is mandatory.

### Conformance requirements

A provenance record conforms when:

1. it has an identifier;
2. it identifies its subject;
3. it identifies its scope;
4. it identifies its disclosure level;
5. it satisfies every requirement of that level;
6. its references are internally consistent;
7. its known material limitations are represented;
8. unknown and withheld information are not materially misrepresented;
9. any root declaration represented by the record is consistent with the applicable Adoption and Release state.

### Misrepresentation

A provenance record is non-conforming where it knowingly:

```text
omits material activities required by its declared level without disclosure
represents unknown information as known
represents withheld information as unknown
misidentifies an actor
misidentifies an ArtifactVersion
creates false derivation relationships
represents an autonomous Release as human-adopted
represents a human-adopted Release as autonomous
claims a higher disclosure level than it satisfies
```

### Canonical public explanation

Where a short explanation is required:

> **`prov` means a conforming provenance record is available for this artifact or release. The record identifies its scope, disclosure level and known limitations.**

A shorter expression MAY be:

**Provenance record available.**

### Canonical principle

The foundational rule is:

**Provenance is a scoped graph of material activity, not a percentage of authorship and not a claim of omniscience.**

A trustworthy provenance record says both:

> **what it knows**

and:

> **what it does not disclose or does not know.**

## Module +AI-530 — Autonomous AI Release

**Status:** Draft  
**Version:** 0.1  
**Identifier:** `+AI-530`  
**Canonical root declaration:** `AI[auto]`  
**Dependencies:** `+AI-001@0`, `+AI-020@0`  
**Related specifications:** `+AI-100@0`  

### Purpose

This specification defines a declaration for releases materially performed or determined by an AISystem or Agent where no qualifying human or organisational adoption applies to the specific ArtifactVersion and Release before release.

The canonical declaration is:

```text
AI[auto]
```

This is a separate root declaration.

It is not an extension of `+AI`.

### Design principle

`+AI` expresses human or organisational accountability for an AI-assisted release.

`AI[auto]` expresses a different condition:

> **The release occurred through AI or agent activity without a qualifying `+AI` human or organisational adoption of that specific release beforehand.**

The distinction concerns release accountability, not whether humans were involved somewhere in the wider system.

### Canonical notation

The canonical notation is:

```text
AI[auto]
```

`auto` is a root discriminator defined by this specification.

It MUST NOT be interpreted as an extension of the `+AI` root.

Therefore:

```text
+AI[auto]
```

is non-conforming.

### Canonical meaning

A conforming `AI[auto]` declaration asserts that:

1. an AISystem or Agent materially participated in determining or executing the applicable Release;
2. the applicable ArtifactVersion and Release are identifiable;
3. no qualifying Party Adoption satisfying `+AI-100@0` applied to that ArtifactVersion and Release before release.

These conditions collectively constitute an **autonomous AI release** for purposes of the `+AI` specification family.

### Meaning of autonomous

In this specification, **autonomous** refers specifically to the release state.

It does NOT necessarily mean that:

```text
no human configured the system
no human supplied prompts
no human supplied source material
no human created software
no human authorised the agent generally
no human defined policy
no human can interrupt operation
the AI is technically self-governing
```

The decisive issue is whether a qualifying Party knowingly adopted the specific ArtifactVersion for the specific Release before release.

### Artifact-specific adoption

General authority does not constitute artifact-specific adoption.

The following do not automatically prevent `AI[auto]` classification:

```text
standing permission to publish
scheduled autonomous operation
general approval of an agent
approval of a workflow
approval of a publication policy
approval of a content category
permission to make routine decisions
```

If the specific released ArtifactVersion was not knowingly adopted by a Party before release, the release may remain autonomous under this specification.

### Release execution versus release autonomy

An Agent physically executing a release does not automatically make the release autonomous.

Example:

```text
Human examines ArtifactVersion V7
Human knowingly adopts V7 for Release R
Agent uploads V7 automatically
```

This release may qualify for:

```text
Human +AI
```

because qualifying human adoption preceded the automated execution.

### Autonomous example

Example:

```text
Human authorises Agent A to publish daily summaries
Agent A generates summary V34
No human adopts V34
Agent A publishes V34
```

The release is:

```text
AI[auto]
```

even though the Agent had standing human authority to publish.

### Human involvement

Human participation elsewhere in the provenance graph does not invalidate `AI[auto]`.

For example, an autonomous release may contain:

```text
human-authored source material
human-created prompts
human-designed templates
human-written software
human policy constraints
human operational oversight
```

The mark does not claim absence of human involvement.

It claims absence of qualifying artifact-specific human or organisational adoption for that Release.

### Material AI control

An AISystem or Agent materially controls a Release where its activity materially determines one or more of:

```text
which artifact is released
the substantive content released
whether release occurs
when release occurs
to whom release occurs
which version is released
```

Purely mechanical infrastructure does not necessarily constitute material AI control.

### Mechanical automation

Traditional deterministic automation MUST NOT be classified as `AI[auto]` solely because it operates without human intervention.

Example:

```text
a fixed cron job copies an already human-approved file
```

does not become an autonomous AI release merely because publication is automated.

An AISystem or Agent must materially participate in the relevant release state.

### AI-generated but human-adopted work

An artifact may be almost entirely generated by AI and still fall under `+AI` rather than `AI[auto]`.

Example:

```text
AI generates 100% of draft
Human knowingly adopts exact ArtifactVersion
Agent publishes it
```

The appropriate root may be:

```text
Human +AI
```

The proportion of AI-generated content does not determine the root declaration.

### Human-created but autonomously released work

Conversely, an artifact may contain predominantly human-created content and still have an autonomous Release.

Example:

```text
Human writes document V1
Agent later autonomously selects V1 and sends it under standing authority
No human adopts that specific Release
```

If AI materially determined the release, the release may qualify as:

```text
AI[auto]
```

even though AI did not author the artifact.

### Mutual exclusivity for one Release

For the same Party-adoption state, ArtifactVersion and Release:

```text
+AI
```

and:

```text
AI[auto]
```

are mutually exclusive.

A Release cannot simultaneously have:

```text
qualifying artifact-specific Party Adoption
```

and:

```text
no qualifying artifact-specific Party Adoption
```

### Different Releases

The same ArtifactVersion MAY have different root declarations for different Releases.

Example:

```text
Release R1:
Agent publishes V1 without human adoption
→ AI[auto]

Release R2:
Human later reviews and adopts V1, then republishes it
→ Human +AI
```

No contradiction exists because the declarations apply to different Release events.

### Subsequent human adoption

Human adoption after an autonomous Release MUST NOT retroactively convert the earlier Release into `+AI`.

The autonomous historical record SHOULD remain intact.

A Party MAY subsequently:

* adopt the same ArtifactVersion;
* make a new ResponsibilityDeclaration;
* and create a new Release.

That later Release MAY qualify for `+AI`.

### Continued publication

Where an autonomously released ArtifactVersion remains continuously available and a Party later wishes to accept responsibility prospectively, the provenance record SHOULD represent a distinct adoption and responsibility event.

A binding or profile MAY define whether that event constitutes:

```text
re-release
reissue
adoption-in-place
new publication state
```

The original autonomous period MUST remain distinguishable.

### Human review without adoption

Human examination alone does not necessarily eliminate autonomous-release status.

A human may:

```text
inspect
monitor
audit
verify
observe
```

an artifact without accepting it for release.

To convert the release state to `+AI`, the applicable Party must perform qualifying Adoption.

### Human approval

A human approval action counts as Adoption only where it represents meaningful acceptance of the specific ArtifactVersion for the specific Release.

Examples that MAY qualify:

```text
approve this exact report for publication
send this exact message
deploy this exact build
publish this exact generated image
```

Examples that do not automatically qualify:

```text
always publish Agent A's outputs
approve all outputs matching policy X
click a generic pipeline approval without identifying the artifact
```

### Organisational adoption

An organisation MAY perform qualifying Adoption through its authorised human governance processes.

An organisation does not adopt an ArtifactVersion merely because:

```text
it owns the agent
it operates the infrastructure
it employs the developers
it pays for the AI service
it defined the general automation policy
```

A qualifying organisational adoption requires an applicable authorised act directed to the ArtifactVersion and Release.

### Legal responsibility

`AI[auto]` does NOT assert that no person or organisation has legal responsibility, liability or duty concerning the Release.

It asserts only that no qualifying `+AI-100@0` Party Adoption and ResponsibilityDeclaration applies to that Release.

Legal responsibility may arise independently of the `+AI` specification family.

### Operator identity

An autonomous-release record SHOULD identify the relevant:

```text
Agent
AISystem
operator where known
authority chain where known
```

Identification of an operator does not convert that operator into the responsible Party for purposes of `+AI`.

### Authority

An autonomous Release MAY be authorised or unauthorised.

Examples include:

```text
delegated autonomous release
release under standing policy
release exceeding delegated authority
release with unknown authority
```

`AI[auto]` does not itself claim that the Release was authorised.

Authority is represented separately through `AuthorityGrant` records.

### Delegated autonomous release

A common pattern is:

```text
Party
  │
  └── grants standing authority ──► Agent
                                      │
                                      ├── generates ArtifactVersion
                                      └── releases ArtifactVersion
                                          without Party Adoption
```

This is still:

```text
AI[auto]
```

The provenance graph MAY additionally show that the autonomous release was delegated.

### Provenance extensions

Extensions whose defining specifications permit use with the autonomous root MAY be composed.

For example, if `+AI-410@0` permits the `prov` extension for this root:

```text
AI[auto,prov]
```

may mean:

```text
autonomous AI release
AND
conforming provenance available
```

Cross-root compatibility MUST be explicitly declared by the extension's defining specification.

### Canonical ordering

Within the autonomous root:

```text
auto
```

MUST appear first.

Permitted cross-root extensions follow in normal registry order.

Example:

```text
AI[auto,prov]
```

`auto` is not independently optional.

Removing it changes the root declaration and therefore the meaning.

### Human-readable identification

The canonical mark is:

```text
AI[auto]
```

Where useful, an Agent or AISystem MAY be identified separately.

Preferred forms include:

```text
Released autonomously by Agent X
AI[auto]
```

or:

```text
Agent: Agent X
Release: AI[auto]
```

A human or organisation name SHOULD NOT be placed immediately before `AI[auto]` in a manner that could imply the accountability semantics of `<Responsible Party> +AI`.

### Machine-readable representation

A conforming record may contain:

```json
{
  "release": {
    "id": "release:34",
    "artifact_version": "artifact-version:34",
    "mode": "autonomous",
    "performed_by": {
      "kind": "agent",
      "id": "agent:daily-summary"
    }
  },
  "autonomous_release": {
    "spec": "+AI-530@0",
    "notation": "AI[auto]",
    "qualifying_party_adoption": false
  }
}
```

A simple Boolean MUST NOT replace the underlying graph where the binding is capable of representing the relevant entities and relationships.

### Autonomous-release predicate

For ArtifactVersion `V` and Release `R`:

```text
AutonomousAIRelease(V,R) :=
    Release(R,V)
AND AIOrAgentMateriallyControlsRelease(R)
AND NOT EXISTS Party P:
        QualifyingAdoption(P,V,R)
```

The canonical notation:

```text
AI[auto]
```

is valid only where `AutonomousAIRelease(V,R)` is true.

### Transition predicate

If a Party later adopts the same ArtifactVersion for a new Release `R2`:

```text
QualifyingAdoption(P,V,R2) = true
```

then `R2` may qualify for `+AI`.

This does not alter the classification of earlier Release `R1`.

### What `AI[auto]` does not mean

`AI[auto]` does NOT mean:

```text
the artifact is wholly AI-generated
no humans were involved
the AI has legal personhood
the AI accepts responsibility
no human or organisation has legal liability
the release was authorised
the release was safe
the artifact is correct
the artifact was unreviewed
the artifact was unverified
the agent acted without constraints
```

It declares a release-accountability state, not a theory of agency or legal responsibility.

### Invalid uses

#### 32.1 Human-adopted release

A human knowingly adopts exact ArtifactVersion V1 before an Agent publishes V1.

`AI[auto]` MUST NOT be used for that Release.

#### 32.2 Non-AI automation

A deterministic script sends an already approved report at 09:00.

Without material AI participation in the release state, `AI[auto]` MUST NOT be used merely because execution was automatic.

#### 32.3 General agent ownership

An organisation owns and operates an Agent.

That fact alone neither establishes nor defeats `AI[auto]`.

The specific adoption state controls classification.

#### 32.4 Retroactive relabelling

An autonomously published artifact is approved by a human three hours later.

The original Release MUST NOT be retrospectively relabelled `+AI`.

### Relationship to `+AI`

The two root declarations answer different questions.

```text
+AI
```

asks:

> **Has an identifiable Party adopted this AI-assisted artifact for this Release and accepted responsibility under `+AI-100@0`?**

```text
AI[auto]
```

asks:

> **Did AI or agent activity materially control this Release without such Party Adoption beforehand?**

They are complementary parts of the same provenance and accountability architecture.

### Canonical public explanation

Where a short explanation is required:

> **`AI[auto]` means an AI system or agent materially controlled this release and no qualifying human or organisational adoption of this specific release occurred beforehand.**

A shorter public explanation MAY be:

**AI released this autonomously. No +AI adoption preceded the release.**

### Canonical distinction

The fundamental distinction is:

```text
Human adoption before release
        ↓
       +AI
```

versus:

```text
No qualifying human adoption before AI-controlled release
        ↓
    AI[auto]
```

The canonical rule is:

**Automation does not determine accountability. Adoption does.**

## Module +AI-710 — JSON Binding

**Status:** Draft  
**Version:** 0.1  
**Identifier:** `+AI-710`  
**Dependencies:** `+AI-001@0`, `+AI-020@0`, `+AI-100@0`, `+AI-210@0`, `+AI-310@0`, `+AI-320@0`, `+AI-410@0`, `+AI-530@0`  

### Purpose

This module defines a canonical JSON binding for the declaration graph represented by this specification family.

The binding preserves the separation between:

* participation;
* Adoption;
* Release;
* ResponsibilityDeclaration;
* autonomous-release declaration;
* assurance assertions;
* provenance; and
* Evidence.

### Design principle

The JSON binding is a representation of the abstract model defined by `+AI-020@0`. It MUST preserve the semantics of the governing root declaration.

Accordingly:

* `responsibility_declarations` represent only conforming `+AI` declarations rooted at `+AI`;
* `autonomous_release_declarations` represent only conforming `AI[auto]` declarations rooted at `AI[auto]`;
* Adoption remains separate from release execution; and
* assurance and provenance remain additive rather than substitutive.

### Canonical JSON Schema

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "urn:plusai:schema:ai-710:0.1",
  "title": "+AI Canonical Declaration Graph",
  "type": "object",
  "additionalProperties": false,
  "required": [
    "schema_version",
    "specifications",
    "parties",
    "artifact_versions",
    "releases"
  ],
  "properties": {
    "schema_version": {
      "const": "+AI-710/0.1"
    },
    "record_id": {
      "$ref": "#/$defs/id"
    },
    "specifications": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/specRef"
      },
      "uniqueItems": true
    },
    "parties": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/party"
      }
    },
    "ai_systems": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/aiSystem"
      }
    },
    "agents": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/agent"
      }
    },
    "artifact_versions": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/artifactVersion"
      }
    },
    "activities": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/activity"
      }
    },
    "authority_grants": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/authorityGrant"
      }
    },
    "releases": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/release"
      }
    },
    "adoptions": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/adoption"
      }
    },
    "responsibility_declarations": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/responsibilityDeclaration"
      }
    },
    "autonomous_release_declarations": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/autonomousReleaseDeclaration"
      }
    },
    "ai_participation": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/aiParticipationClassification"
      }
    },
    "provenance": {
      "$ref": "#/$defs/provenanceRecord"
    },
    "assurance_assertions": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/assuranceAssertion"
      }
    },
    "evidence": {
      "type": "array",
      "items": {
        "$ref": "#/$defs/evidence"
      }
    }
  },
  "$defs": {
    "id": {
      "type": "string",
      "minLength": 1
    },
    "token": {
      "type": "string",
      "pattern": "^[a-z][a-z0-9-]*$"
    },
    "specRef": {
      "type": "string",
      "pattern": "^\\+AI-[0-9]{3}@[0-9]+$"
    },
    "partyRef": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "kind",
        "id"
      ],
      "properties": {
        "kind": {
          "const": "party"
        },
        "id": {
          "$ref": "#/$defs/id"
        }
      }
    },
    "agentRef": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "kind",
        "id"
      ],
      "properties": {
        "kind": {
          "const": "agent"
        },
        "id": {
          "$ref": "#/$defs/id"
        }
      }
    },
    "actorRef": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "kind",
        "id"
      ],
      "properties": {
        "kind": {
          "enum": [
            "party",
            "ai_system",
            "agent"
          ]
        },
        "id": {
          "$ref": "#/$defs/id"
        }
      }
    },
    "digest": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "algorithm",
        "value"
      ],
      "properties": {
        "algorithm": {
          "type": "string",
          "minLength": 1
        },
        "value": {
          "type": "string",
          "minLength": 1
        }
      }
    },
    "party": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "type",
        "name"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "type": {
          "enum": [
            "person",
            "organisation"
          ]
        },
        "name": {
          "type": "string",
          "minLength": 1
        },
        "identifiers": {
          "type": "array",
          "items": {
            "type": "string"
          }
        }
      }
    },
    "aiSystem": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "name"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "name": {
          "type": "string",
          "minLength": 1
        },
        "provider": {
          "type": "string"
        },
        "model": {
          "type": "string"
        },
        "version": {
          "type": "string"
        }
      }
    },
    "agent": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "name"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "name": {
          "type": "string",
          "minLength": 1
        },
        "ai_system": {
          "$ref": "#/$defs/id"
        },
        "operator": {
          "$ref": "#/$defs/id"
        }
      }
    },
    "artifactVersion": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "artifact_id",
        "version"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "artifact_id": {
          "$ref": "#/$defs/id"
        },
        "version": {
          "type": "string"
        },
        "media_type": {
          "type": "string"
        },
        "digests": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/digest"
          }
        },
        "derived_from": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        }
      }
    },
    "activity": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "type",
        "actor",
        "material"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "type": {
          "$ref": "#/$defs/token"
        },
        "actor": {
          "$ref": "#/$defs/actorRef"
        },
        "inputs": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        },
        "outputs": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        },
        "material": {
          "type": "boolean"
        },
        "occurred_at": {
          "type": "string",
          "format": "date-time"
        },
        "authority_grant": {
          "$ref": "#/$defs/id"
        },
        "evidence": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        }
      }
    },
    "authorityGrant": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "grantor",
        "grantee",
        "scope",
        "may_delegate",
        "may_release"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "grantor": {
          "$ref": "#/$defs/actorRef"
        },
        "grantee": {
          "$ref": "#/$defs/agentRef"
        },
        "scope": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/token"
          },
          "minItems": 1,
          "uniqueItems": true
        },
        "may_delegate": {
          "type": "boolean"
        },
        "may_release": {
          "type": "boolean"
        },
        "parent_grant": {
          "$ref": "#/$defs/id"
        },
        "valid_from": {
          "type": "string",
          "format": "date-time"
        },
        "valid_until": {
          "type": "string",
          "format": "date-time"
        },
        "evidence": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        }
      }
    },
    "release": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "artifact_version",
        "mode"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "artifact_version": {
          "$ref": "#/$defs/id"
        },
        "mode": {
          "enum": [
            "human_adopted",
            "delegated_agent",
            "autonomous"
          ]
        },
        "released_at": {
          "type": "string",
          "format": "date-time"
        },
        "channel": {
          "type": "string"
        },
        "performed_by": {
          "$ref": "#/$defs/actorRef"
        },
        "evidence": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        }
      }
    },
    "adoption": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "party",
        "artifact_version",
        "release",
        "accepted"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "party": {
          "$ref": "#/$defs/id"
        },
        "artifact_version": {
          "$ref": "#/$defs/id"
        },
        "release": {
          "$ref": "#/$defs/id"
        },
        "accepted": {
          "const": true
        },
        "adopted_at": {
          "type": "string",
          "format": "date-time"
        }
      }
    },
    "responsibilityDeclaration": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "spec",
        "responsible_party",
        "artifact_version",
        "release",
        "adoption",
        "root_mark",
        "extensions",
        "notation",
        "accepted"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "spec": {
          "const": "+AI-100@0"
        },
        "responsible_party": {
          "$ref": "#/$defs/id"
        },
        "artifact_version": {
          "$ref": "#/$defs/id"
        },
        "release": {
          "$ref": "#/$defs/id"
        },
        "adoption": {
          "$ref": "#/$defs/id"
        },
        "root_mark": {
          "const": "+AI"
        },
        "extensions": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/token"
          },
          "uniqueItems": true
        },
        "notation": {
          "type": "string",
          "minLength": 3
        },
        "accepted": {
          "const": true
        },
        "declared_at": {
          "type": "string",
          "format": "date-time"
        },
        "evidence": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        }
      }
    },
    "autonomousReleaseDeclaration": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "spec",
        "artifact_version",
        "release",
        "root_mark",
        "notation",
        "qualifying_party_adoption"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "spec": {
          "const": "+AI-530@0"
        },
        "artifact_version": {
          "$ref": "#/$defs/id"
        },
        "release": {
          "$ref": "#/$defs/id"
        },
        "root_mark": {
          "const": "AI[auto]"
        },
        "extensions": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/token"
          },
          "uniqueItems": true
        },
        "notation": {
          "type": "string",
          "pattern": "^AI\\\\[auto(?:,[a-z][a-z0-9-]*)*\\\\]$"
        },
        "qualifying_party_adoption": {
          "const": false
        },
        "declared_at": {
          "type": "string",
          "format": "date-time"
        },
        "evidence": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        }
      }
    },
    "participationSubject": {
      "type": "object",
      "additionalProperties": false,
      "properties": {
        "artifact_version": {
          "$ref": "#/$defs/id"
        },
        "release": {
          "$ref": "#/$defs/id"
        },
        "activity": {
          "$ref": "#/$defs/id"
        }
      },
      "anyOf": [
        {
          "required": [
            "artifact_version"
          ]
        },
        {
          "required": [
            "release"
          ]
        },
        {
          "required": [
            "activity"
          ]
        }
      ]
    },
    "aiParticipationClassification": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "spec",
        "subject",
        "materiality"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "spec": {
          "const": "+AI-210@0"
        },
        "subject": {
          "$ref": "#/$defs/participationSubject"
        },
        "scope": {
          "type": "string"
        },
        "materiality": {
          "enum": [
            "incidental",
            "material"
          ]
        },
        "production_role": {
          "enum": [
            "minor",
            "collaborative",
            "primary"
          ]
        },
        "operational_mode": {
          "enum": [
            "direct",
            "agentic",
            "mixed"
          ]
        },
        "basis": {
          "type": "string"
        },
        "activities": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        },
        "actors": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/actorRef"
          }
        }
      }
    },
    "provenanceSubject": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "artifact_version"
      ],
      "properties": {
        "artifact_version": {
          "$ref": "#/$defs/id"
        },
        "release": {
          "$ref": "#/$defs/id"
        }
      }
    },
    "provenanceRecord": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "spec",
        "disclosure_level",
        "subject",
        "scope",
        "limitations"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "spec": {
          "const": "+AI-410@0"
        },
        "record_version": {
          "type": "string"
        },
        "subject": {
          "$ref": "#/$defs/provenanceSubject"
        },
        "disclosure_level": {
          "enum": [
            "core",
            "material",
            "evidenced"
          ]
        },
        "scope": {
          "enum": [
            "artifact",
            "release",
            "defined-component",
            "defined-activity"
          ]
        },
        "limitations": {
          "type": "array",
          "items": {
            "type": "string"
          }
        },
        "root_declaration": {
          "enum": [
            "+AI",
            "AI[auto]"
          ]
        },
        "responsible_party": {
          "$ref": "#/$defs/id"
        }
      }
    },
    "independence": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "basis"
      ],
      "properties": {
        "basis": {
          "enum": [
            "external",
            "functional",
            "other-defined"
          ]
        },
        "description": {
          "type": "string"
        }
      }
    },
    "assuranceAssertion": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "spec",
        "type",
        "subject_artifact_version",
        "actors",
        "scope",
        "status"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "spec": {
          "$ref": "#/$defs/specRef"
        },
        "type": {
          "$ref": "#/$defs/token"
        },
        "subject_artifact_version": {
          "$ref": "#/$defs/id"
        },
        "actors": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/actorRef"
          },
          "minItems": 1
        },
        "scope": {
          "enum": [
            "complete_substantive",
            "partial",
            "defined"
          ]
        },
        "scope_description": {
          "type": "string"
        },
        "status": {
          "enum": [
            "completed",
            "incomplete",
            "failed"
          ]
        },
        "outcome": {
          "type": "string"
        },
        "method": {
          "type": "string"
        },
        "independence": {
          "$ref": "#/$defs/independence"
        },
        "completed_at": {
          "type": "string",
          "format": "date-time"
        },
        "evidence": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        }
      }
    },
    "evidence": {
      "type": "object",
      "additionalProperties": false,
      "required": [
        "id",
        "type"
      ],
      "properties": {
        "id": {
          "$ref": "#/$defs/id"
        },
        "type": {
          "$ref": "#/$defs/token"
        },
        "subjects": {
          "type": "array",
          "items": {
            "$ref": "#/$defs/id"
          }
        },
        "digest": {
          "$ref": "#/$defs/digest"
        },
        "uri": {
          "type": "string",
          "format": "uri"
        },
        "value": {
          "type": "string"
        }
      }
    }
  }
}
```

### Binding notes

A conforming record MAY represent either or both of the following, as applicable to different Releases:

* a human- or organisation-adopted `+AI` Release; or
* an `AI[auto]` autonomous Release.

An autonomous record therefore does not require top-level `adoptions` or `responsibility_declarations`.

The schema also adds:

* top-level `ai_participation` for `+AI-210@0` classifications;
* top-level `provenance` for `+AI-410@0` records;
* `independence` and `scope_description` support within `assurance_assertions`; and
* a distinct `autonomousReleaseDeclaration` definition for `+AI-530@0`.

### Conformance

A JSON record conforms to this binding when:

1. it is valid against the canonical schema;
2. every reference resolves consistently within the record;
3. any `+AI` declaration is represented only through `responsibility_declarations` with `root_mark = "+AI"`;
4. any autonomous-release declaration is represented only through `autonomous_release_declarations` with `root_mark = "AI[auto]"`; and
5. the JSON representation does not collapse Adoption, Release execution, responsibility, verification or provenance into a single undifferentiated claim.
