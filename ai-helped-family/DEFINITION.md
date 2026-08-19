# ai-helped-family Definition

**`+AI` means material AI assistance plus identifiable human or organisational responsibility.**

That is already the semantic centre of v0.1.  Everything else should be additive.

# 1. `+AI` specification family

I would give every specification a permanent family number, while versioning that specification independently.

| Range         | Family              | Purpose                                                    |
| ------------- | ------------------- | ---------------------------------------------------------- |
| `+AI-000–099` | Architecture        | Family architecture, terminology, registries, conformance  |
| `+AI-100–199` | Accountability      | Core `+AI` declaration and responsibility                  |
| `+AI-200–299` | Participation       | Degree and type of AI participation                        |
| `+AI-300–399` | Assurance           | Human review, verification, testing, validation            |
| `+AI-400–499` | Provenance          | Contribution history, provenance graphs, derivation        |
| `+AI-500–599` | Authority & Agency  | Delegation, agents, autonomous activity                    |
| `+AI-600–699` | Identity & Evidence | Party/system identity, signatures, evidence                |
| `+AI-700–799` | Bindings            | JSON, web, document, software and protocol representations |
| `+AI-800–899` | Profiles            | Research, software, publishing, legal, government, etc.    |
| `+AI-900–999` | Reserved            | Future family-wide specifications                          |

The current document would eventually become:

```text
+AI-100
Human-AI Provenance and Accountability
Version 1.0
```

During development:

```text
+AI-100 v0.1
+AI-100 v0.2
...
+AI-100 v1.0
```

The specification itself already anticipates most of these branches: review, verification, autonomous-agent activity, cryptographic provenance, system/model identification, and contribution chains. 

## Initial catalogue

I would provision these numbers now, without necessarily writing all the specifications yet:

| ID        | Working title                          |
| --------- | -------------------------------------- |
| `+AI-001` | Specification Family Architecture      |
| `+AI-010` | Registry and Conformance               |
| `+AI-100` | Human-AI Provenance and Accountability |
| `+AI-210` | AI Participation Classification        |
| `+AI-220` | AI-Primary Production                  |
| `+AI-310` | Human Review                           |
| `+AI-320` | Independent Verification               |
| `+AI-330` | Validation and Testing                 |
| `+AI-410` | Provenance Record                      |
| `+AI-420` | Contribution Chain                     |
| `+AI-430` | Artifact Derivation                    |
| `+AI-510` | Delegation and Authority               |
| `+AI-520` | AI Agent Activity                      |
| `+AI-530` | Autonomous AI Release                  |
| `+AI-610` | Responsible-Party Identity             |
| `+AI-620` | AI System and Model Identity           |
| `+AI-630` | Cryptographic Evidence                 |
| `+AI-710` | JSON Binding                           |
| `+AI-720` | Web Binding                            |
| `+AI-730` | Document Binding                       |
| `+AI-740` | Software Binding                       |
| `+AI-810` | Software Profile                       |
| `+AI-820` | Research Profile                       |
| `+AI-830` | Publishing and Media Profile           |
| `+AI-840` | Government Profile                     |
| `+AI-850` | Legal Profile                          |
| `+AI-860` | Education Profile                      |

The important architectural rule would be:

> **A profile may constrain or require specifications, but MUST NOT redefine their meaning.**

So a research profile could require verification or provenance, but it could not redefine what `+AI` itself means.

That fits the current rule that `+AI` supplements rather than replaces more specific institutional, professional, regulatory or legal requirements. 

## Versioning

I would use:

```text
+AI-310 v1.2.0
```

with conventional semantics:

```text
MAJOR   incompatible normative semantic change
MINOR   backward-compatible normative addition
PATCH   editorial correction or non-semantic clarification
```

Machine references should normally bind to the major version:

```text
+AI-310@1
```

That means software does not break merely because `1.1` becomes `1.2`.

The visible mark itself should never become:

```text
+AI1.0
+AI2
```

`+AI` remains `+AI`.

---

# 2. The visible mark family

I think we should establish an extension grammar rather than invent numerous unrelated symbols.

The base remains:

```text
Eric Mourant +AI
```

An extended expression becomes:

```text
Eric Mourant +AI[review]
```

and extensions compose:

```text
Eric Mourant +AI[primary,review,verify,prov]
```

A provisional grammar:

```text
expression     = "+AI" [ extensions ]

extensions     = "[" extension *("," extension) "]"

extension      = token [ "=" value ]
```

Canonical extension tokens would be lowercase ASCII, registered by `+AI-010`.

### Initial visible vocabulary

| Mark             | Meaning                                                           |
| ---------------- | ----------------------------------------------------------------- |
| `+AI`            | Material AI assistance; named party accepts responsibility        |
| `+AI[primary]`   | AI was the primary production mechanism                           |
| `+AI[review]`    | Complete substantive human review occurred                        |
| `+AI[verify]`    | Independent verification occurred                                 |
| `+AI[prov]`      | Conformant provenance information is available                    |
| `+AI[signed]`    | Declaration/provenance is cryptographically bound to the artifact |
| `+AI[agent]`     | One or more AI agents materially participated                     |
| `+AI[delegated]` | Agent activity occurred under a recorded delegation of authority  |

Thus:

```text
Eric Mourant +AI[primary]
```

means:

> AI was principally responsible for producing the artifact, but Eric knowingly adopted the resulting artifact and accepts responsibility for its release.

That works cleanly with the existing specification, because v0.1 deliberately says predominantly AI-originated work can still qualify for `+AI`. 

Likewise:

```text
JAPER Technology +AI[review,prov]
```

would mean:

> AI materially assisted; JAPER Technology accepts responsibility; qualifying human review occurred; and conformant provenance information exists.

## `[review]`

This should be significantly stronger than ordinary `+AI`.

The present specification explicitly says normal `+AI` does **not** require word-by-word or element-by-element manual review. 

I would define `[review]` approximately as:

> Every materially substantive component of the released artifact has been reviewed by a human authorised to accept, reject or modify it.

That avoids the ridiculous requirement that every punctuation mark must receive conscious inspection while still giving the mark real meaning.

## `[verify]`

This should be stronger again.

```text
+AI[verify]
```

should mean that an identifiable verifier, distinct from the production activity being verified, has performed a defined verification process.

The metadata must identify:

```text
verifier
scope
method
result
time
artifact version
```

The visible mark alone says verification exists. The record says exactly what was verified.

## `[prov]`

```text
+AI[prov]
```

means a conformant provenance record is available.

The current specification already establishes the idea of machine-readable representation and requires machine forms to preserve the visible notation's semantics. 

The provenance specification would take that from a simple declaration to an actual graph.

## `[signed]`

This must mean more than:

> There is a digital signature somewhere.

It should mean that cryptographic evidence binds at least:

```text
artifact identity
responsible party
declaration
relevant provenance record
```

so substitution becomes detectable.

---

# 3. Autonomous AI needs different semantics

Here I would **not** allow everything to compose with `+AI`.

The current specification says autonomous output without meaningful human adoption falls outside canonical `+AI`. 

That distinction is fundamental.

So I would create a companion root expression:

```text
AI[auto]
```

Meaning:

> An AI system or agent caused this artifact to be released without a qualifying human act of adoption for that release.

Therefore:

```text
+AI
```

and:

```text
AI[auto]
```

are mutually exclusive **for the same release event**.

This produces an important consequence.

Suppose an autonomous agent generates and publishes something:

```text
AI[auto]
```

A human subsequently reviews it, adopts it, and republishes it.

That second release could legitimately be:

```text
Eric Mourant +AI[review]
```

Same underlying content, different release event, different accountability state.

That leads directly to the data model.

---

# 4. The abstract `+AI` data model

The most important modelling decision I would make is:

> **A `+AI` declaration applies to an Artifact Version in the context of a Release Event—not merely to an abstract document forever.**

That solves provenance, republication, modification, delegation and autonomy cleanly.

The core entities would be:

| Entity                      | Meaning                                                               |
| --------------------------- | --------------------------------------------------------------------- |
| `Party`                     | Human or organisation capable of responsibility                       |
| `AISystem`                  | Model, application, service or composite AI system                    |
| `Agent`                     | System capable of performing delegated or autonomous activity         |
| `Artifact`                  | Logical work                                                          |
| `ArtifactVersion`           | Specific state of an artifact                                         |
| `Activity`                  | Human or AI action affecting an artifact                              |
| `AuthorityGrant`            | Delegation of authority from a party                                  |
| `Adoption`                  | Human/organisation knowingly accepts an artifact version              |
| `Release`                   | Artifact version is transmitted, published, deployed, submitted, etc. |
| `ResponsibilityDeclaration` | Party accepts responsibility for a release                            |
| `AssuranceAssertion`        | Review, verification, validation or testing claim                     |
| `Evidence`                  | Record supporting a declaration or assertion                          |
| `IdentityClaim`             | Identifies a party, system, model or agent                            |

Conceptually:

```text
Party
  │
  ├──── grants authority ────► Agent
  │                              │
  │                              │ performs
  │                              ▼
  │                           Activity
  │                              │
  │                        produces/modifies
  │                              ▼
  │                       ArtifactVersion
  │                              │
  │                              │ adopted by
  ├──────────────────────────────┘
  │
  │ authorises
  ▼
Release
  │
  └──── governed by ───► ResponsibilityDeclaration
```

Assurance sits beside this:

```text
Reviewer ──► ReviewActivity ──► AssuranceAssertion
                                     │
                                     ▼
                              ArtifactVersion
```

And evidence supports any assertion:

```text
Evidence
   │
   ├── supports responsibility declaration
   ├── supports review assertion
   ├── supports verification assertion
   ├── proves artifact digest
   └── proves identity/signature
```

---

# 5. The formal `+AI` predicate

We can actually express the current specification as a logical condition.

For responsible party `P`, artifact version `A`, and release `R`:

```text
PlusAI(P,A,R) :=
    MaterialAIParticipation(A)
AND Identifiable(P)
AND KnowsOrReasonablyBelieves(P, MaterialAIParticipation(A))
AND AuthorisedDirectedOrAdoptedAIUse(P,A)
AND ControlsRelease(P,R)
AND Adopts(P,A)
AND Releases(R,A)
AND AcceptsResponsibility(P,A,R)
```

That is essentially the machine-level equivalent of Sections 5.1–5.6 of the existing specification. 

Then autonomous release becomes:

```text
AutonomousAI(A,R) :=
    AIProducedOrControlled(A,R)
AND Releases(R,A)
AND NOT EXISTS P:
        PlusAI(P,A,R)
```

That gives the family a rigorous semantic foundation.

---

# 6. Activities become the provenance graph

An artifact does not need a simplistic percentage such as:

```text
73% AI
27% human
```

Instead it gets a sequence or graph of activities:

```text
Artifact v1
    │
    ▼
Human research
    │
    ▼
AI synthesis
    │
    ▼
Human restructuring
    │
    ▼
AI drafting
    │
    ▼
Human review
    │
    ▼
AI copy-editing
    │
    ▼
Artifact v7
```

Each activity can record:

```text
actor
activity type
input artifacts
output artifacts
AI system
authority
timestamp
materiality
evidence
```

This also aligns with the existing design decision not to assign percentages of authorship. 

---

# 7. Delegation becomes first-class

For agents, we need more than provenance.

We need **authority provenance**.

For example:

```text
Eric
  │
  │ grants
  ▼
Agent A
  │
  │ delegates
  ▼
Agent B
  │
  │ invokes
  ▼
Model C
  │
  ▼
Artifact
```

An `AuthorityGrant` should contain something resembling:

```json
{
  "grantor": "party:eric",
  "grantee": "agent:a",
  "scope": [
    "research",
    "draft",
    "revise"
  ],
  "may_release": false,
  "may_delegate": true
}
```

The crucial field is:

```json
"may_release": false
```

because **permission to create is not permission to publish**.

That maps particularly well to the current specification's distinction between AI participation and the responsible party retaining authority over release. 

Eventually you can ask a machine:

```text
Who authorised this action?
```

and traverse the authority graph backwards.

---

# 8. Proposed JSON architecture

The existing v0.1 JSON can evolve into something like:

```json
{
  "specifications": [
    "+AI-100@1",
    "+AI-310@1",
    "+AI-410@1",
    "+AI-710@1"
  ],

  "artifact": {
    "id": "urn:sha256:...",
    "type": "document",
    "version": "7"
  },

  "release": {
    "id": "release:12345",
    "artifact": "urn:sha256:..."
  },

  "responsible_party": {
    "id": "party:eric-mourant",
    "name": "Eric Mourant",
    "type": "person"
  },

  "ai_participation": {
    "material": true,
    "primary": true
  },

  "adoption": {
    "party": "party:eric-mourant",
    "artifact": "urn:sha256:..."
  },

  "assurance": [
    {
      "type": "human_review",
      "scope": "complete"
    }
  ],

  "provenance": {
    "record": "prov:12345"
  },

  "declaration": {
    "notation": "+AI[primary,review,prov]",
    "responsibility": true
  }
}
```

The important point is that **the notation is derived from the assertions**.

It should not merely be an arbitrary string somebody typed.

---

# 9. A conformance rule worth establishing immediately

I would make this foundational:

> **Every extension adds a claim. No extension may weaken, alter or silently reinterpret another claim.**

Therefore:

```text
+AI[review]
```

means everything `+AI` means **plus** everything `[review]` means.

It cannot mean a different flavour of `+AI`.

Likewise:

```text
+AI[primary,review,prov]
```

is simply the intersection of four independently defined assertions.

This gives us true composability.

Another critical rule:

> **Absence of a mark MUST NOT imply the negation of that mark.**

Thus:

```text
Eric Mourant +AI
```

does not mean:

```text
not reviewed
not verified
no provenance
human-primary
```

It means only what `+AI` declares.

That is essential for safe inference.

---

# 10. The architecture that emerges

We end up with three layers:

```text
VISIBLE DECLARATION

Eric Mourant +AI[primary,review,prov]

              │
              ▼

SEMANTIC ASSERTIONS

material AI participation
responsible party
AI-primary production
complete human review
provenance available

              │
              ▼

EVIDENCE GRAPH

Party
AI systems
Agents
Activities
Artifacts
Versions
Authority
Adoption
Release
Review
Verification
Evidence
Signatures
```

And above those sit domain profiles:

```text
Research Profile
       │
       ├── requires +AI-100
       ├── requires +AI-310
       ├── may require +AI-320
       └── requires +AI-410
```

That is no longer merely a disclosure notation.

It becomes a **protocol for declaring AI participation, human responsibility, authority, assurance and provenance**.

And I think that is the correct long-term conceptual boundary for the family.
