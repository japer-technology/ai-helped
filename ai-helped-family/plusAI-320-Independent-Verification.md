# +AI-320 Independent Verification

**Status:** Draft
**Version:** 0.1.0
**Identifier:** `+AI-320`
**Canonical extension token:** `verify`
**Dependencies:** `+AI-001`, `+AI-020`, `+AI-100`

---

# 1. Purpose

This specification defines an independent-verification assurance declaration for AI-assisted artifacts.

Its canonical visible expression is:

```text
+AI[verify]
```

The declaration means that:

1. the underlying `+AI` accountability declaration is valid; and
2. an identifiable independent verifier successfully completed a defined verification of the applicable artifact version before the relevant release.

---

# 2. Design principle

Human review and independent verification are different assurance activities.

Human review asks:

> **Did a human substantively examine the artifact?**

Independent verification asks:

> **Did a sufficiently independent verifier test or check defined claims, properties or results using a defined method?**

Neither assertion implies the other.

---

# 3. Normative terminology

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative as defined by `+AI-001`.

---

# 4. Canonical notation

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

Canonical token ordering is defined by `+AI-001`.

---

# 5. Meaning

A conforming `+AI[verify]` declaration asserts that:

1. the underlying `+AI` declaration conforms;
2. a defined verification subject exists;
3. a defined verification scope exists;
4. a defined verification method exists;
5. one or more qualifying independent verifiers performed that method;
6. the verification was completed before release;
7. the verification produced a qualifying successful outcome;
8. the subject was not materially changed after verification without corresponding re-verification.

---

# 6. Verification subject

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
compliance properties
specified outputs
```

The subject MUST be sufficiently bounded for the verification claim to be meaningful.

---

# 7. Defined scope

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

---

# 8. Scope and visible notation

The visible token:

```text
verify
```

means:

> **Independent verification was successfully completed under a defined scope and method.**

It MUST NOT be interpreted to mean that every conceivable property of the artifact has been independently verified.

The verification scope SHOULD be reasonably accessible wherever practical.

A domain profile MAY require the scope to be displayed publicly.

---

# 9. Verification method

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

---

# 10. Verification outcome

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

---

# 11. Independent verifier

A verifier MAY be:

```text
a natural person
an organizational verification function
an independent organization
```

The verifier MUST be identifiable within the applicable provenance record.

An organisation acting as verifier SHOULD identify the human or controlled verification process that actually performed the substantive verification where practical.

---

# 12. Independence

A verifier is sufficiently independent when the verifier has enough separation from the production and release decision to provide a genuinely distinct check.

At minimum:

* the verifier MUST NOT be the same natural person who materially produced the subject being verified;
* the verifier MUST NOT verify their own substantive work as independent verification;
* the verifier MUST NOT be controlled by the AI System or Agent whose output is being verified;
* the verification result MUST be capable of producing a finding contrary to the interests or expectations of the production process.

---

# 13. Organisational independence

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

---

# 14. External verification

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

---

# 15. Prior participation

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

---

# 16. Responsible party and verifier

The verifier SHOULD be distinct from the responsible Party.

Where the responsible Party is an individual, that same individual MUST NOT satisfy the independent-verifier requirement.

Where the responsible Party is an organisation, a qualifying functionally independent verifier within that organisation MAY satisfy the requirement unless an applicable profile requires external independence.

---

# 17. AI-assisted verification

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

---

# 18. Fully automated verification

A verification process MAY include fully automated technical checks where those checks are appropriate to the declared method.

However, the `verify` assertion MUST be issued or adopted by an identifiable qualifying verifier.

An AI System or Agent MUST NOT independently confer the `verify` token on its own output.

A future specification MAY define autonomous machine-verification assertions separately.

---

# 19. Reproduction

Independent reproduction is a strong form of verification but is not universally required.

Where reproduction is claimed, the verifier SHOULD independently recreate the relevant result from defined inputs and methods.

The ordinary `verify` token MUST NOT be interpreted as implying complete independent reproduction unless the verification record states that reproduction occurred.

---

# 20. Verification versus review

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

---

# 21. Timing

Verification for a release MUST be complete before that Release.

A verification performed after Release does not retroactively cause the earlier Release to qualify for `+AI[verify]`.

A later Release of the same ArtifactVersion MAY qualify once verification has been completed.

---

# 22. Material change after verification

A material change to a verified subject invalidates the verification assertion for the changed subject.

The changed material MUST be re-verified before `verify` may apply.

An unrelated material change outside the declared verification scope MAY leave the verification assertion intact, provided the change cannot reasonably affect the verified property.

---

# 23. Non-material transformations

A verification assertion MAY survive a non-material transformation where the verified properties remain unchanged.

For example:

```text
a verified calculation in a report
may remain verified after lossless PDF conversion
```

Provenance SHOULD identify both representations.

---

# 24. Partial verification

Partial verification is permitted as an underlying AssuranceAssertion.

However, its scope MUST be explicit.

A visible `verify` token MAY be used only where the verification record clearly defines the verified scope and a reasonable reader would not thereby be given a materially false impression of broader verification.

Domain profiles MAY impose stricter display requirements for partial verification.

---

# 25. Verification evidence

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

---

# 26. Machine-readable assertion

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

---

# 27. Independence basis

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

---

# 28. Verification predicate

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

---

# 29. What `verify` does not mean

Unless separately asserted, `+AI[verify]` does NOT mean:

```text
the entire artifact is error-free
every possible claim was checked
the artifact was professionally certified
the verifier accepts release responsibility
the verifier authored the work
the artifact is legally compliant
the artifact is medically safe
the artifact has complete human review
the verification was external
the verification used no AI
```

---

# 30. Invalid uses

The following do not qualify.

### 30.1 Self-verification

A person creates a calculation and then checks that same calculation themselves.

This may be review or checking.

It is not independent verification.

### 30.2 AI self-check

An AI system generates an answer and then prompts itself to verify the answer.

This does not establish independent verification.

### 30.3 Undefined approval

A second person says:

> looks good

without a defined verification scope or method.

This does not qualify.

### 30.4 Failed verification

An independent verifier finds unresolved material errors.

`verify` MUST NOT be used until the verified subject passes the applicable criteria.

### 30.5 Verification after modification

Version 7 is verified.

Version 8 materially changes the verified calculation.

Version 8 MUST NOT inherit the assertion.

---

# 31. Canonical explanation

Where a concise explanation is required:

> **`+AI[verify]` means AI materially assisted this work, the named party accepts responsibility for releasing it, and an independent verifier successfully checked a defined scope of the work using a defined method before release.**

A shorter public explanation MAY be:

# **AI helped. Independently verified. I take responsibility.**
