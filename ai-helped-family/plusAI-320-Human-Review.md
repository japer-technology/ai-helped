# +AI-310 Human Review

**Status:** Draft
**Version:** 0.1.0
**Identifier:** `+AI-310`
**Canonical extension token:** `review`
**Dependencies:** `+AI-001`, `+AI-100`

---

# 1. Purpose

This specification defines a human-review assurance declaration for AI-assisted artifacts.

Its canonical visible expression is:

```text
+AI[review]
```

The extension means that the underlying `+AI` declaration remains valid and that complete substantive human review of the released artifact version has occurred.

---

# 2. Design principle

Ordinary `+AI` represents accountability.

It does not by itself represent complete human review.

`+AI[review]` therefore adds a separate assurance claim:

> **AI helped. A human substantively reviewed the resulting artifact. The responsible party still takes responsibility.**

Human review supplements accountability.

It does not replace accountability.

---

# 3. Normative terminology

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative as defined by `+AI-001`.

---

# 4. Canonical notation

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

Where additional extensions apply, canonical ordering is governed by `+AI-001`.

---

# 5. Meaning

A conforming `+AI[review]` declaration asserts that:

1. all requirements of the applicable `+AI` declaration are satisfied;
2. one or more identifiable human reviewers reviewed the applicable artifact version;
3. collectively, that review covered every material component of the artifact;
4. the review was substantive rather than ceremonial or purely mechanical;
5. the reviewer or review process had practical ability to identify issues affecting release;
6. the artifact version released was the reviewed version or a non-materially transformed equivalent;
7. no unreviewed material change occurred between completion of review and release.

These requirements collectively constitute **complete substantive human review**.

---

# 6. Review subject

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

---

# 7. Human reviewer

A qualifying reviewer MUST be a natural person.

An organisation MAY administer, record, require or attest to review, but an organisation itself is not a human reviewer.

Where an organisation is the responsible party, one or more human reviewers MAY perform review on its behalf according to the organisation's governance arrangements.

---

# 8. Identifiability

The review process MUST be capable of identifying the human reviewer or reviewers.

Public disclosure of a reviewer's legal identity is not required by this specification.

A public machine-readable representation MAY use an opaque or pseudonymous identifier where:

* that identifier uniquely represents the reviewer within the applicable provenance context; and
* applicable profiles do not require stronger identification.

---

# 9. Material component

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

---

# 10. Complete substantive review

Review is **complete** when every material component of the applicable artifact version has been subjected to meaningful human examination.

Complete review does not require conscious inspection of every byte, character, punctuation mark, pixel, sample or machine instruction.

The test is substantive coverage rather than literal microscopic inspection.

---

# 11. Distributed review

Complete review MAY be performed by multiple human reviewers.

No single reviewer is required to review every material component where:

* collectively, human review covers all material components;
* responsibility for review coverage can be determined;
* gaps in coverage are not knowingly represented as complete review.

A machine-readable record SHOULD permit review coverage to be attributed to individual reviewers where practical.

---

# 12. Meaningful examination

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

---

# 13. AI-assisted review

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

---

# 14. Review competence

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

---

# 15. Ability to act on the review

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

---

# 16. Reviewer and responsible party

The reviewer MAY be the same person as the responsible party.

The reviewer MAY be different from the responsible party.

`+AI[review]` does not imply independent review.

Independence is outside the scope of this specification.

Independent assurance is reserved for specifications such as `+AI-320`.

---

# 17. Timing

A qualifying review MUST be complete before the release to which the `+AI[review]` declaration applies.

A review performed only after a release does not retroactively make that earlier release conformant.

The same artifact MAY subsequently be reviewed and released again under a new release event.

That later release MAY qualify for `+AI[review]`.

---

# 18. Material change after review

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

---

# 19. Non-material transformation

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

---

# 20. Review and correctness

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

---

# 21. Review and verification

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

---

# 22. Review findings

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

---

# 23. Machine-readable assertion

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

---

# 24. Review predicate

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

---

# 25. Invalid uses

The following are non-conforming examples.

### 25.1 Summary-only review

A human reads an AI-generated summary but not the substantive artifact.

```text
+AI[review]
```

MUST NOT be used on that basis.

### 25.2 Spot checking

A human examines only a sample of a larger artifact.

Unless a domain specification explicitly defines that sample as complete coverage, `review` MUST NOT be used.

### 25.3 Automated reviewer

An AI system reviews another AI system's output and reports that it is acceptable.

Without qualifying human substantive examination, `review` MUST NOT be used.

### 25.4 Post-release review

An artifact is published automatically and reviewed by a human afterwards.

The original release MUST NOT be retroactively described as `+AI[review]`.

### 25.5 Material alteration

A reviewed document is materially rewritten after review.

The changed version MUST NOT carry `review` until the changed material is reviewed.

---

# 26. Multiple reviewers

Where multiple reviewers collectively establish complete coverage, the review assertion SHOULD record all contributing reviewers.

A domain profile MAY require a review coverage map.

Example:

```text
Reviewer A → sections 1–4
Reviewer B → sections 5–9
Reviewer C → data and calculations
```

If those components collectively constitute the complete material artifact, the review MAY qualify.

---

# 27. Evidence

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

A stronger evidence requirement MAY be imposed by a profile or by `+AI-630`.

---

# 28. Privacy

Human-review provenance SHOULD minimise unnecessary disclosure of personal information.

A profile MAY require stronger reviewer identification where accountability, regulation or professional practice requires it.

---

# 29. Conformance

A declaration conforms to `+AI-310` when:

1. its underlying `+AI` declaration conforms;
2. the applicable artifact version satisfies the human-review predicate;
3. the `review` extension is represented according to `+AI-001`;
4. any published machine-readable assertion accurately represents the review that occurred.

---

# 30. Canonical explanation

Where a short explanation is required:

> **`+AI[review]` means AI materially assisted this work, the named party accepts responsibility for releasing it, and the complete substantive artifact was reviewed by a human before release.**

A shorter public explanation MAY be:

# **AI helped. A human reviewed it. I take responsibility.**
