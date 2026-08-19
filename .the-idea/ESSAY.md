# +AI — Human + AI Responsibility Notation

## 1. Purpose

`+AI` is a compact notation indicating that a named human or organisation used artificial intelligence in producing, analysing, transforming, or communicating an output, while **retaining responsibility for the final result**.

The core principle is:

> **AI assisted. Human accepted responsibility.**

`+AI` identifies augmentation rather than autonomous authorship.

---

## 2. Primary notation

### `Name +AI`

Example:

**Eric Mourant +AI**

Meaning:

* Eric Mourant is the accountable author or sender.
* Artificial intelligence materially assisted the work.
* Eric Mourant reviewed or directed the resulting output.
* Eric Mourant accepts responsibility for the communication or artifact.

`+AI` does **not** mean that the named person is an AI, represents an AI system, or delegated responsibility to an AI.

---

## 3. Formal definition

### `+AI`

**Human-directed, AI-augmented, human-accountable.**

An output MAY carry the `+AI` notation when:

1. AI materially contributed to its creation, analysis, transformation, formulation, or presentation.
2. A human or accountable organisation directed or authorised the work.
3. The accountable party has accepted the resulting output.
4. Responsibility for the output remains with the named human or organisation.

The notation SHOULD NOT be used where an AI system operates autonomously without meaningful human acceptance of the resulting output.

---

## 4. Responsibility principle

The defining feature of `+AI` is **responsibility**, not simply AI involvement.

AI involvement alone is insufficient.

Therefore:

**AI used + human responsibility = `+AI`**

By attaching `+AI`, the signer effectively states:

> I used artificial intelligence as part of producing this output. I have accepted the resulting output and retain responsibility for it.

---

## 5. Universal usage

The notation is designed to work across communication and digital artifacts.

### Email

Kindest regards,
**Eric Mourant +AI**

### Documents

**Author:** Eric Mourant +AI

### Reports

Prepared by **JAPER Technology +AI**

### Social media

— Eric Mourant +AI

### Articles

By **Eric Mourant +AI**

### Source code

```text
Author: Eric Mourant +AI
```

### Git commits

```text
Eric Mourant +AI
```

### Software documentation

```text
Maintainer: Eric Mourant +AI
```

### Presentations

**Eric Mourant +AI**

### Legal or commercial correspondence

**Prepared and approved by Eric Mourant +AI**

### Images and creative work

**Eric Mourant +AI**

### Research

**Eric Mourant +AI**

### Machine-readable metadata

```json
{
  "author": "Eric Mourant",
  "ai_augmented": true,
  "human_accountability": true
}
```

---

## 6. Recommended notation hierarchy

A small family of marks could distinguish different responsibility models.

### `+AI`

**Human accountable, AI augmented**

The recommended standard.

Example:

**Eric Mourant +AI**

---

### `AI→Human`

**AI generated or initiated, subsequently reviewed and accepted by a human**

Useful where provenance matters more than brevity.

Example:

**AI→Eric Mourant**

---

### `AI`

**Autonomous AI output**

No human authorship or individual acceptance should be inferred.

Example:

**JAPER Agent AI**

---

### `Human`

Optional notation indicating intentionally non-AI-assisted work where that distinction matters.

Example:

**Eric Mourant · Human**

This would normally be unnecessary.

---

## 7. Preferred terminology

The recommended expansion of `+AI` is:

### Human + AI, Human Responsible

Alternative descriptive phrase:

### AI-Augmented · Human Accountable

The word **responsible** is preferable to terms such as *verified*, *approved*, or *checked*, because those terms may imply factual verification beyond what the signer intends.

Responsibility means the named party accepts ownership of the output.

---

## 8. What `+AI` does not certify

`+AI` does not inherently certify that:

* every statement is factually correct;
* every AI-generated element has been independently verified;
* no errors remain;
* the content originated primarily from the human;
* a particular AI model or provider was used;
* confidential information was or was not supplied to an AI system.

It identifies **augmentation and accountability**, not perfection.

---

## 9. Visual form

The canonical form should remain extremely simple:

**`+AI`**

Recommended presentation:

**Eric Mourant +AI**

Permitted alternatives where typography requires:

`Eric Mourant +AI`

`Eric Mourant · +AI`

`Eric Mourant | +AI`

The canonical symbol itself should remain `+AI` so that it survives plain text, email, source code, databases, filenames, metadata and machine processing.

---

## 10. Why the plus sign

The `+` has useful semantic properties.

It represents:

**Human + Artificial Intelligence**

rather than:

**Human replaced by Artificial Intelligence**

It also naturally communicates augmentation:

**existing capability + additional capability**

The notation therefore describes the relationship without assigning authorship to the AI.

---

## 11. Organisational use

Organisations may use the notation in exactly the same way.

**JAPER Technology +AI**

Meaning:

> JAPER Technology used artificial intelligence in producing this output and accepts organisational responsibility for the resulting artifact or communication.

An organisation may also identify an accountable individual:

**JAPER Technology**
**Eric Mourant +AI**

---

## 12. Optional expanded disclosure

Where additional transparency is appropriate:

**Eric Mourant +AI**
*AI-augmented. Human responsible.*

Or:

**Eric Mourant +AI**
*Artificial intelligence assisted in producing this communication. I accept responsibility for the final content.*

The expanded statement should remain optional. The objective of the notation is to make routine disclosure practical enough to become habitual.

---

## 13. Machine-readable representation

A future interoperability specification could define:

```json
{
  "augmentation": {
    "ai": true,
    "accountability": "human",
    "responsible_party": "Eric Mourant"
  }
}
```

A compact representation could be:

```json
{
  "provenance": "+AI"
}
```

For cryptographically signed artifacts, the `+AI` declaration could eventually form part of signed provenance metadata.

---

## 14. Proposed standard statement

### +AI Declaration

> The `+AI` notation indicates that artificial intelligence materially assisted in producing or processing an output and that the person or organisation identified alongside the notation accepts responsibility for the resulting output.

Canonical syntax:

**`<Responsible Party> +AI`**

Example:

**Eric Mourant +AI**

---

## 15. Governing principle

The notation should remain governed by one simple test:

### Who is responsible?

If the answer is the named human or organisation, and AI materially assisted the work:

### `+AI`
