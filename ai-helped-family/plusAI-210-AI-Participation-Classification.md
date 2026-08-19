# +AI-210 AI Participation Classification

**Status:** Draft
**Version:** 0.1.0
**Identifier:** `+AI-210`
**Dependencies:** `+AI-001`, `+AI-020`
**Related specifications:** `+AI-100`, `+AI-220`, `+AI-520`

---

# 1. Purpose

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

---

# 2. Design principle

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

### Materiality

> Did AI materially affect the artifact or release?

### Production role

> What substantive role did AI play in producing the resulting artifact?

### Operational mode

> How did the AI participate operationally?

The dimensions MUST NOT be collapsed into a single numerical authorship score.

---

# 3. Normative terminology

The terms **MUST**, **MUST NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are normative as defined by `+AI-001`.

---

# 4. Classification object

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

---

# 5. No authorship percentages

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

---

# 6. Materiality dimension

The materiality dimension has two canonical values:

```text
incidental
material
```

These values concern whether AI participation materially affected the relevant artifact, activity or release.

---

# 7. Incidental participation

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

Incidental participation alone does not satisfy the material-AI-participation condition required by `+AI-100`.

---

# 8. Material participation

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

---

# 9. Materiality is contextual

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

---

# 10. Production-role dimension

Where materiality is `material`, a production role MAY be classified as:

```text
minor
collaborative
primary
```

These classifications describe the role AI played in producing the substantive result.

They MUST NOT be treated as numerical bands.

---

# 11. Minor material participation

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

---

# 12. Minor versus incidental

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

---

# 13. Collaborative participation

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

---

# 14. Primary AI participation

`primary` means AI constituted the principal substantive production mechanism for the artifact or for the defined scope being classified.

Indicators may include:

* AI generated the initial substantive artifact from which the released artifact substantially derives;
* AI performed the central analytical or generative work;
* human participation principally consisted of direction, selection, correction, review or adoption;
* replacing the AI contribution would effectively require recreating the substantive artifact or central result.

No quantitative threshold is required.

---

# 15. Primary does not mean exclusive

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

---

# 16. Primary-production test

The recommended test is:

> **Was AI the principal mechanism by which the substantive artifact or classified scope came into existence?**

Where the answer is yes:

```text
production_role = primary
```

may be appropriate.

The detailed visible `primary` extension is reserved to `+AI-220`.

---

# 17. Scope

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

---

# 18. Operational-mode dimension

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

---

# 19. Direct participation

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

---

# 20. Agentic participation

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

---

# 21. Agentic does not mean autonomous

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

Autonomous release is governed by `+AI-530`.

---

# 22. Agentic participation and authority

Agentic classification concerns operational behaviour.

It does not state:

```text
who authorised the Agent
whether its actions were within authority
whether it had release authority
whether a human adopted the result
whether the release was autonomous
```

Those matters are represented separately through `+AI-020` authority, adoption and release relationships.

---

# 23. Mixed operational mode

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

---

# 24. Classification combinations

Examples include:

### 24.1 Material, minor, direct

```json
{
  "materiality": "material",
  "production_role": "minor",
  "operational_mode": "direct"
}
```

### 24.2 Material, collaborative, direct

```json
{
  "materiality": "material",
  "production_role": "collaborative",
  "operational_mode": "direct"
}
```

### 24.3 Material, primary, direct

```json
{
  "materiality": "material",
  "production_role": "primary",
  "operational_mode": "direct"
}
```

### 24.4 Material, collaborative, agentic

```json
{
  "materiality": "material",
  "production_role": "collaborative",
  "operational_mode": "agentic"
}
```

### 24.5 Material, primary, agentic

```json
{
  "materiality": "material",
  "production_role": "primary",
  "operational_mode": "agentic"
}
```

---

# 25. Classification is not responsibility

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

---

# 26. Classification is not quality

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

---

# 27. Classification and `+AI`

Where:

```text
materiality = material
```

and the requirements of `+AI-100` are otherwise satisfied, the canonical `+AI` declaration may apply.

Where:

```text
materiality = incidental
```

incidental participation alone does not establish the material-AI-participation predicate required by `+AI`.

---

# 28. Visible notation

This specification defines participation semantics but deliberately minimises visible notation.

The base condition:

```text
materiality = material
```

is represented by the canonical `+AI` declaration where the accountability requirements of `+AI-100` also apply.

The visible token:

```text
primary
```

is reserved to `+AI-220`.

Agent-related visible notation is reserved to `+AI-520`.

This specification does not define a canonical visible token for `collaborative`.

---

# 29. Minor visible declaration

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

---

# 30. Machine-readable classification

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

---

# 31. Classification evidence

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

---

# 32. Classification procedure

A classifier SHOULD determine participation in the following order.

### Step 1 — Determine materiality

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

### Step 2 — Determine production role

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

### Step 3 — Determine operational mode

Ask whether material AI activity was principally:

```text
direct
agentic
mixed
```

### Step 4 — Declare scope

State whether the classification applies to:

```text
the complete artifact
or
a defined subset/activity
```

---

# 33. Borderline classifications

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

---

# 34. Multiple AI systems

A single ArtifactVersion MAY involve multiple AI Systems or Agents with different participation classifications.

Example:

```text
Model A:
    minor, direct

Agent B:
    primary, agentic
```

An aggregate artifact-level classification MAY also be supplied.

The aggregate classification MUST NOT erase more detailed per-actor classifications where those classifications are relevant to a governing profile.

---

# 35. Classification across versions

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

---

# 36. Autonomous releases

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

---

# 37. Provenance integration

A `+AI-410` provenance record SHOULD use the classifications defined by this specification rather than inventing implementation-specific percentage scales.

Material AI Activities SHOULD identify their applicable participation properties where known.

---

# 38. Conformance

A participation classification conforms where:

1. its subject is identifiable;
2. its scope is explicit or unambiguously the complete artifact;
3. its materiality value conforms to this specification;
4. any production-role value conforms to this specification;
5. any operational-mode value conforms to this specification;
6. no numerical authorship threshold is presented as the normative basis of classification;
7. no classification is represented as implying responsibility, quality or correctness.

---

# 39. Canonical distinctions

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

---

# 40. Canonical principle

The fundamental rule is:

# **Classify what AI did, not what percentage of the artifact looks AI-generated.**

Participation is determined by substantive causal role, not arithmetic authorship.
