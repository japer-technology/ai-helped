# +AI-410 Provenance Record

**Status:** Draft
**Version:** 0.1.0
**Identifier:** `+AI-410`
**Canonical extension token:** `prov`
**Dependencies:** `+AI-001`, `+AI-020`
**Related specifications:** `+AI-100`, `+AI-210`, `+AI-530`, `+AI-620`, `+AI-630`, `+AI-710`

---

# 1. Purpose

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

---

# 2. Design principle

Provenance answers:

> **What materially happened, involving whom or what, to produce and release this artifact?**

A provenance record SHOULD describe causal and governance relationships.

It SHOULD NOT attempt to reduce provenance to a single authorship percentage.

The preferred representation is a graph.

---

# 3. Normative terminology

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative as defined by `+AI-001`.

---

# 4. Canonical visible token

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

---

# 5. Meaning of `prov`

The `prov` extension asserts that:

1. a conforming `+AI-410` provenance record exists;
2. the record applies to the relevant ArtifactVersion and Release;
3. the provenance record declares its disclosure level;
4. the record identifies its known limitations;
5. the record is accessible to the intended relying party through the applicable binding.

`prov` does NOT assert that the provenance record contains every event that occurred.

---

# 6. Provenance subject

Every provenance record MUST identify at least one subject ArtifactVersion.

Where the provenance relates to release accountability, it SHOULD identify the applicable Release.

A record MAY describe multiple related ArtifactVersions.

---

# 7. Provenance graph

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

---

# 8. Provenance record identity

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

---

# 9. Record version

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

---

# 10. Provenance scope

Every provenance record MUST declare its scope.

Canonical scopes include:

```text
artifact
release
defined-component
defined-activity
```

Where the scope is less than the complete artifact and release history, the limitation MUST be clear.

---

# 11. Temporal scope

A provenance record SHOULD identify the period or activity range it covers where this is not obvious from the graph.

Example:

```text
from creation of ArtifactVersion 1
through Release R7
```

A provenance record MUST NOT imply coverage of events occurring after its declared scope.

---

# 12. Disclosure level

Every conforming provenance record MUST declare one of the following levels:

```text
core
material
evidenced
```

These levels describe disclosure depth.

They do not describe artifact quality.

---

# 13. Core provenance

`core` is the minimum conforming disclosure level.

A core record MUST identify:

```text
subject ArtifactVersion
applicable Release where relevant
root declaration where applicable
responsible Party or autonomous-release state
material AI participation
AI participation classification where known
at least one materially relevant AI System or Agent reference,
    or an explicit status explaining why identification is unavailable
record scope
known provenance limitations
```

A core record need not enumerate every material Activity.

---

# 14. Material provenance

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

---

# 15. Evidenced provenance

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

---

# 16. Disclosure-level hierarchy

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

---

# 17. Visible `prov` token and disclosure level

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
+AI-820 Research Profile
requires:
    provenance >= material
```

---

# 18. Public availability

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

---

# 19. Explicit disclosure state

Where a provenance field cannot be populated normally, the implementation SHOULD use an explicit disclosure state rather than omit the field ambiguously.

Canonical states are:

```text
known
unknown
withheld
unavailable
not-applicable
```

---

# 20. Unknown

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

---

# 21. Withheld

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

---

# 22. Unavailable

`unavailable` means the information may once have existed or may exist elsewhere but is not available to the provenance issuer.

Examples include:

```text
lost log
third-party record inaccessible
legacy system did not preserve field
```

---

# 23. Not applicable

`not-applicable` means the field has no semantic application to the represented activity.

It MUST NOT be used as a synonym for unknown.

---

# 24. Omission

Omission of an optional field means only:

> this record makes no representation concerning that field.

Implementations SHOULD prefer explicit disclosure states where omission could materially affect interpretation.

---

# 25. Party provenance

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

---

# 26. AI System provenance

Where known and permitted, a provenance record SHOULD identify materially participating AI Systems.

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

---

# 27. Agent provenance

Materially participating Agents SHOULD be represented independently from the AI Systems they use.

An Agent record MAY identify:

```text
agent identifier
operator
purpose
software version
AI Systems used
authority grant
sub-agent relationships
```

---

# 28. Activity

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

---

# 29. Canonical activity classes

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

---

# 30. Material activity

A Material Activity is an Activity whose occurrence materially affected:

```text
the ArtifactVersion
a material decision concerning it
its assurance state
its release state
```

Material provenance MUST represent all material Activities known to the provenance issuer that fall within the declared scope, subject to explicit withheld or unavailable states.

---

# 31. Non-material activity

A record MAY include non-material Activities.

Their presence does not make them material.

Implementations SHOULD avoid overwhelming provenance records with mechanically generated events that do not improve substantive understanding.

---

# 32. Activity ordering

Activity ordering MAY be represented using:

```text
timestamps
sequence identifiers
dependency edges
input/output derivation
```

Exact wall-clock timestamps are not required where meaningful causal ordering can otherwise be established.

---

# 33. Derivation

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

---

# 34. Non-material transformation

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

---

# 35. Participation classification

Material AI participation SHOULD use `+AI-210`.

Example:

```json
{
  "materiality": "material",
  "production_role": "primary",
  "operational_mode": "agentic"
}
```

A provenance record SHOULD NOT substitute implementation-specific authorship percentages for the normative participation classification.

---

# 36. Multiple AI contributors

Where multiple AI Systems or Agents materially participate, provenance SHOULD represent each separately where known.

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

---

# 37. Authority provenance

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

---

# 38. Adoption provenance

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

---

# 39. Autonomous-release provenance

Where `AI[auto]` applies, the provenance record SHOULD identify:

```text
Agent or AI System materially controlling the Release
ArtifactVersion
Release
relevant AuthorityGrants
absence of qualifying Adoption
operator where known
```

The absence of qualifying Adoption is a semantic condition defined by `+AI-530`, not merely an omitted field.

---

# 40. Review provenance

Where `+AI[review]` applies, the provenance record SHOULD identify the applicable `+AI-310` AssuranceAssertion.

At `material` level or higher, it SHOULD also identify the substantive review Activity or Activities.

---

# 41. Verification provenance

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

---

# 42. Evidence links

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

---

# 43. Cryptographic evidence

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

The normative requirements for cryptographic provenance are reserved to `+AI-630`.

---

# 44. Provenance integrity

A provenance record SHOULD be bound to its subject ArtifactVersion using an integrity mechanism where practical.

At the `evidenced` level, ArtifactVersion identity MUST be sufficiently precise to distinguish material alteration.

A content digest is RECOMMENDED where technically appropriate.

---

# 45. Provenance issuer

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

---

# 46. Assertion versus observation

A record MAY distinguish between:

```text
observed events
asserted events
imported events
inferred relationships
```

Where a relationship is inferred rather than directly observed or asserted, that status SHOULD be represented.

---

# 47. Provenance confidence

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

---

# 48. Provenance boundaries

Every non-trivial provenance record SHOULD state relevant boundaries.

Example:

```text
This record covers substantive activities from initial AI research through publication.

It does not cover creation of third-party source documents.
```

A provenance boundary prevents a scoped record from being misinterpreted as a universal history.

---

# 49. Imported artifacts

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

---

# 50. Recursive provenance

A provenance record MAY reference another provenance record.

Example:

```text
Artifact A
    provenance → Record A

Artifact B derives from Artifact A

Record B references Record A
```

Implementations SHOULD avoid unnecessary duplication where stable provenance references exist.

---

# 51. Provenance persistence

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

---

# 52. Privacy

Provenance SHOULD disclose no more personal information than required by the applicable specification, profile or use case.

Pseudonymous identifiers MAY be used where identity can remain sufficiently stable for the intended provenance purpose.

Profiles MAY impose stronger identification requirements.

---

# 53. Confidentiality

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

---

# 54. Security

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

---

# 55. Machine-readable minimal record

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

---

# 56. Material-level example

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

---

# 57. Graph completeness

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

---

# 58. Unknown provenance

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

---

# 59. Level downgrade

Where a record cannot satisfy the requirements of its stated disclosure level, it MUST:

```text
correct the record
or
declare a lower conforming level
```

It MUST NOT retain a higher level merely because the issuer intends to collect the missing information later.

---

# 60. `prov` conformance

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

---

# 61. `prov` does not mean complete

The following inference is invalid:

```text
+AI[prov]
therefore
every human and AI activity is disclosed
```

The valid inference is:

> A conforming scoped provenance record exists, and that record declares its disclosure level and limitations.

---

# 62. `prov` does not mean verified

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

---

# 63. `prov` does not mean signed

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

---

# 64. Conformance classes

This specification defines three provenance-record conformance classes:

```text
+AI-410 Core Provenance
+AI-410 Material Provenance
+AI-410 Evidenced Provenance
```

A profile SHOULD state the minimum acceptable class where provenance is mandatory.

---

# 65. Conformance requirements

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

---

# 66. Misrepresentation

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

---

# 67. Canonical public explanation

Where a short explanation is required:

> **`prov` means a conforming provenance record is available for this artifact or release. The record identifies its scope, disclosure level and known limitations.**

A shorter expression MAY be:

# **Provenance record available.**

---

# 68. Canonical principle

The foundational rule is:

# **Provenance is a scoped graph of material activity, not a percentage of authorship and not a claim of omniscience.**

A trustworthy provenance record says both:

> **what it knows**

and:

> **what it does not disclose or does not know.**
