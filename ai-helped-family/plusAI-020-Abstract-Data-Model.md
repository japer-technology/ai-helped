# +AI-020 Abstract Data Model

**Status:** Draft
**Version:** 0.1.0
**Identifier:** `+AI-020`
**Dependencies:** `+AI-001`

---

# 1. Purpose

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

---

# 2. Design principle

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

---

# 3. Normative terminology

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative as defined by `+AI-001`.

---

# 4. Graph model

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

---

# 5. Entity identity

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

---

# 6. Party

A `Party` is an entity capable of making human or organisational declarations within the `+AI` family.

A Party has one of the following base types:

```text
person
organization
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

---

# 7. AI System

An `AISystem` represents an artificial-intelligence system materially relevant to an activity.

An AI System MAY represent:

* a model;
* a hosted service;
* a local model;
* a multimodel system;
* an inference service;
* an AI-enabled application;
* or another identifiable AI capability.

An AI System MAY have:

```text
provider
product name
model name
model version
deployment identifier
configuration identifier
```

Identification of a model does not itself establish what activities that model performed.

---

# 8. Agent

An `Agent` represents an operational actor capable of selecting or performing activities toward a goal.

An Agent MAY use one or more AI Systems.

An Agent MAY:

* receive authority;
* invoke other agents;
* perform activities;
* create artifacts;
* modify artifacts;
* make operational decisions;
* and execute release actions.

An Agent MUST NOT be treated as a responsible Party under `+AI-100`.

An Agent and the AI System used by that Agent are distinct entities.

Example:

```text
Agent: research-agent-17
uses:
    AI System: model-service-x
```

This distinction permits the same Agent to use different AI Systems over time.

---

# 9. Artifact

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

---

# 10. Artifact Version

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

---

# 11. Material equivalence

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

---

# 12. Activity

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

---

# 13. Actor

An `Actor` is a role capable of performing an Activity.

An Actor reference MAY identify:

```text
Party
Agent
AISystem
```

The model does not imply equal legal, ethical or accountability capacity between those actor classes.

Actor means only that the entity participated causally in an Activity.

---

# 14. Material AI participation

Material AI participation exists where one or more AI System or Agent Activities materially affected the applicable artifact or relevant decision.

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

---

# 15. Authority Grant

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

An Authority Grant may be narrow or broad.

Examples:

```text
draft this document
research these topics
modify this repository
send replies within this policy
publish qualifying status updates
delegate research to another agent
```

---

# 16. Authority constraints

Authority is scoped.

An actor MUST NOT be inferred to possess authority outside the recorded or otherwise established scope.

A child delegation MUST NOT exceed the authority possessed by its parent grant.

Therefore:

```text
authority(child) ⊆ authority(parent)
```

unless an independent authority source exists.

---

# 17. Release authority

Release authority means authority to cause an artifact to be published, transmitted, deployed, submitted, presented or otherwise made operative.

Release authority and human adoption are distinct.

An Agent MAY possess:

```text
may_release = true
```

without any human having adopted the specific artifact version that the Agent later releases.

Such standing authority does not by itself satisfy the human-adoption requirement of `+AI-100`.

---

# 18. Adoption

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

---

# 19. Knowledge requirement

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

---

# 20. Release

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

---

# 21. Automated release

A Release MAY be executed by an Agent or AI System after qualifying human adoption.

For example:

```text
Human adopts Version 7
        │
        ▼
Agent automatically publishes Version 7
```

The fact that an Agent physically performed the publication does not make the Release autonomous for `+AI` purposes if qualifying human adoption occurred beforehand.

---

# 22. Autonomous release

For the purposes of this model, an `AutonomousRelease` is a Release materially selected or executed by an AI System or Agent without a qualifying Party Adoption applying to that artifact version and release beforehand.

The presence of prior general authority does not prevent classification as autonomous release.

The normative declaration for this condition is defined by `+AI-530`.

---

# 23. Responsibility Declaration

A `ResponsibilityDeclaration` records a Party's acceptance of responsibility according to an applicable accountability specification.

For `+AI-100`, it MUST bind at least:

```text
responsible Party
ArtifactVersion
Adoption
Release
applicable specification
```

The referenced Adoption, Release and ArtifactVersion MUST be mutually consistent.

---

# 24. Release-specific responsibility

Responsibility declarations are release-specific unless an applicable specification explicitly defines broader scope.

The same ArtifactVersion may therefore have:

```text
Release R1 → autonomous
Release R2 → human-adopted +AI
Release R3 → different responsible Party +AI
```

These states do not conflict because they apply to distinct Releases.

---

# 25. Multiple responsible parties

Multiple Parties MAY independently accept responsibility for the same Release.

Each Party MUST have a separately representable:

```text
Adoption
ResponsibilityDeclaration
```

unless another specification explicitly defines collective adoption.

Two names displayed together MUST NOT be interpreted by a machine as joint responsibility without corresponding semantic records.

---

# 26. Assertion

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

---

# 27. Assurance Assertion

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

---

# 28. Identity Claim

An `IdentityClaim` associates an entity with identifying information.

Identity Claims may concern:

```text
people
organizations
agents
AI systems
models
services
cryptographic keys
```

An Identity Claim MAY be supported by Evidence.

Identity alone does not establish authorship, authority, adoption or responsibility.

---

# 29. Evidence

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

---

# 30. Provenance

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

---

# 31. Temporal ordering

Where times are known, the following ordering constraints apply.

A qualifying Adoption for a Release MUST occur before or contemporaneously with the release decision it authorises.

A pre-release assurance assertion MUST be complete before the Release to which that assurance applies.

A material change after an assertion creates a new ArtifactVersion to which the prior assertion MUST NOT automatically propagate.

---

# 32. No implicit role inference

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

---

# 33. No implicit negative inference

Absence of a relationship MUST NOT normally be treated as proof that the relationship does not exist.

For example, absence of a `ReviewAssertion` means:

> no qualifying review assertion is represented.

It does not necessarily mean:

> no human review occurred.

This principle supports partial provenance records.

---

# 34. Core accountability predicate support

The model supports the `+AI-100` accountability condition conceptually as:

```text
PlusAI(P,V,R) :=
    MaterialAIParticipation(V or R)
AND Party(P)
AND QualifyingAdoption(P,V,R)
AND ResponsibilityDeclaration(P,V,R)
```

The complete normative semantics of `+AI` remain owned by `+AI-100`.

This specification defines only the entities necessary to represent those semantics.

---

# 35. Human-review predicate support

The model supports `+AI-310` through:

```text
HumanReview(V,R) :=
    AssuranceAssertion(
        type = human_review,
        subject = V,
        scope = complete_substantive,
        status = completed
    )
AND CompletedBeforeRelease
AND NoUnreviewedMaterialChange
```

The complete normative meaning of `review` remains owned by `+AI-310`.

---

# 36. Independent-verification predicate support

The model supports `+AI-320` through an AssuranceAssertion containing at least:

```text
verifier
subject
verification scope
verification method
outcome
completion time
independence basis
```

The complete normative meaning of `verify` remains owned by `+AI-320`.

---

# 37. Autonomous-release predicate support

The model supports `+AI-530` conceptually as:

```text
AutonomousRelease(V,R) :=
    Release(R,V)
AND AIOrAgentMateriallyControlsRelease(R)
AND NOT EXISTS P:
        QualifyingAdoption(P,V,R)
```

General or standing authority MAY exist.

Its existence does not make the artifact human-adopted.

---

# 38. Graph invariants

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
12. an AI System or Agent is not transformed into a Party merely by being assigned responsibility-like metadata.

---

# 39. Minimal graph

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

---

# 40. Canonical model statement

The `+AI` family models AI-assisted artifacts as relationships between:

# **Actors, activities, artifacts, authority, adoption, release, assertions and evidence.**

Its foundational distinction is:

> **Who or what produced an artifact is not necessarily who authorised it, adopted it, released it, reviewed it, verified it or accepts responsibility for it.**
