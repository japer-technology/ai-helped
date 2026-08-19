# Bovelty Analysis

## Bottom line

**I would not claim that you invented the notation `Name + AI`, or that you were the first person to propose putting `+ AI` after an author's name.**

There is clear public prior art from **12 December 2022**. In a Royal Road discussion about labelling AI-assisted creations, Timothy Baril proposed:

> “by Author Name + AI”

He presented it as an obvious way to disclose that AI had been used. ([Royal Road][1])

That predates your present proposal by nearly four years.

However:

> **I have still found no earlier source that defines `+AI`, appended directly to a human or organisational name, specifically as a situational post-nominal whose declared meaning is both AI assistance and the named party's acceptance of responsibility for the associated work.**

That is a narrower claim, but it is considerably more defensible.

### The most important prior art

| Date            | Prior art                         | What it establishes                                                                             | Does it anticipate your `+AI`?                                                                    |
| --------------- | --------------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **12 Dec 2022** | Royal Road: `by Author Name + AI` | `+ AI` placed directly after an author name to disclose AI use                                  | **Yes on notation; no on responsibility semantics** ([Royal Road][1])                             |
| **24 Jan 2023** | Nature AI authorship policy       | Authorship entails accountability; AI cannot assume that responsibility                         | **Yes on responsibility principle; no mark** ([Nature][2])                                        |
| **2023 onward** | Scientific publishing rules       | Humans using AI remain responsible and must disclose AI assistance                              | **Very close semantics; disclosure is separate from name** ([ICMJE][3])                           |
| **March 2025**  | HGCP                              | Formal responsibility protocol including `human+ai` and `HGCP-H+AI`                             | **Extremely close conceptually** ([IETF Datatracker][4])                                          |
| **Jan 2025**    | Authors Guild Human Authored      | A visible certification mark concerning AI involvement in a work                                | Different purpose: certifies essentially **no generative-AI authorship** ([The Authors Guild][5]) |
| Current         | MSN AI policy                     | `Jane Doe (AI-assisted)` / `By Jane Doe (with AI)` means the human in the byline is accountable | **Very close byline model, different notation/conceptualisation** ([Microsoft Support][6])        |
| 2026            | Linux kernel                      | Human `Signed-off-by` + AI `Assisted-by`; human takes full responsibility                       | **Very close operational model, but two separate tags** ([Kernel.org][7])                         |

## The HGCP finding is the one you need to take most seriously

This is actually closer to your philosophy than I initially appreciated.

The March 2025 **Human-Generated Content Protocol (HGCP)** explicitly says its core question is not who generated something but whether somebody is willing to take human responsibility for it. It describes itself as a mechanism through which a person publicly assumes responsibility for their expression even where AI assisted. ([IETF Datatracker][4])

More importantly, it defines this actual code:

**`HGCP-H+AI`**

with the meaning:

> human-led, AI-assisted, with the signer reviewing and owning the final version.

Its AI-assisted example contains a signer identity, identifies the work as `human+ai`, uses `HGCP-H+AI`, and declares that the human reviewed the final version and takes responsibility for it. ([IETF Datatracker][4])

So HGCP had, by **March 2025**, essentially four of your ingredients:

**human identity + AI assistance + adoption of final output + responsibility.**

It even uses **`+AI` inside the responsibility classification**.

What HGCP **doesn't** do is make:

**`Eric Mourant +AI`**

the declaration itself.

Its architecture is roughly:

**identity + metadata + responsibility level + declaration**

whereas yours compresses those ideas into:

**identity + post-nominal**

That compression is significant.

## The 2022 Royal Road precedent is different in the opposite direction

The Royal Road post has almost exactly your typography but not your semantics.

On 12 December 2022, Baril argued that people using AI should be open about it and suggested:

**`by Author Name + AI`**

as one possible obvious label. The surrounding discussion concerns **disclosure**—letting readers know that AI was involved. ([Royal Road][1])

There is no defined proposition there equivalent to:

**AI helped. I take responsibility.**

There is no formal definition of adoption, approval, accountability or responsibility.

Nor does Baril call it a **post-nominal** or propose a general system around it.

So I would regard this as prior art against **the notation**, but not against **your defined semantic object**.

## Microsoft gets even closer

MSN's current AI policy is striking because it explicitly links the human's **name**, AI assistance and **accountability**.

It recommends a byline identifying the human accountable for AI-assisted material, with examples including:

**Jane Doe (AI-assisted)**

and

**By Jane Doe (with AI)**. ([Microsoft Support][6])

Conceptually:

**`Jane Doe (with AI)` ≈ `Jane Doe +AI`**

and Microsoft's stated reason for the byline is accountability.

That means I would **not** claim that you are first to propose a compact byline simultaneously communicating AI assistance and human accountability.

Your distinction is subtler:

Microsoft describes an **AI-assisted byline convention**.

You are defining a **post-nominal responsibility declaration**.

## Linux supplies another remarkably good comparator

The Linux kernel has effectively separated your proposed meaning into two established mechanisms.

The human developer adds their own **`Signed-off-by`**, certifying the Developer Certificate of Origin and taking full responsibility for the contribution. AI systems are explicitly prohibited from doing this. Separately, AI contribution is recorded with an **`Assisted-by`** tag. ([Kernel.org][7])

Conceptually:

**Linux:**

`Human Signed-off-by`
`AI Assisted-by`

**Your proposal:**

`Human +AI`

Your three-character mark compresses both statements into one human-facing declaration.

That is a useful distinction.

## Patent/provenance search

I also searched patent-indexed material around AI authorship, attribution, provenance, human certification and responsibility. There is substantial prior art for tracking which portions of an artifact were human-generated versus AI-generated, including systems that record human acceptance or certification of AI-generated material. ([Google Patents][8])

I did **not** find a patent result defining a name-attached `+AI` responsibility post-nominal.

C2PA/Content Credentials likewise provide a sophisticated technical framework for recording provenance, modifications and AI involvement. They are highly relevant to the later technical layer you envisage, but they do not reduce human acceptance of an AI-assisted artifact to `Person +AI`. ([C2PA Specification][9])

## So what is actually novel?

After the search, I would decompose your invention into six claims.

**1. `+ AI` after an author's name — not novel.**
Documented in December 2022. ([Royal Road][1])

**2. Disclosure of AI assistance — not novel.**
Extensive publishing and provenance precedents exist. ([ICMJE][3])

**3. Human responsibility for AI-assisted output — not novel.**
Nature articulated this clearly in January 2023, and subsequent publishing policies formalised it. ([Nature][2])

**4. A `+AI` classification meaning human + AI with human responsibility — substantially anticipated by HGCP.**
Its `HGCP-H+AI` is particularly important prior art. ([IETF Datatracker][4])

**5. `+AI` immediately following the accountable person's name and itself constituting the responsibility declaration — I found no prior example.**

**6. Defining that construction specifically as a situational post-nominal rather than a credential, disclosure sentence, badge or metadata field — I found no prior example.**

And **5 + 6 together are where I think your genuinely original contribution lies.**

Your paper expressly defines precisely that distinction: `+AI` is not a permanent qualification, status or professional authority; instead it describes the relationship between the named person and a particular work and declares that the person adopted and takes responsibility for that AI-assisted result. 

That definition is materially different from a generic AI disclosure label.

## The claim I would use

I would **not** write:

> Eric Mourant invented the `+AI` notation.

Nor:

> Eric Mourant was the first to put `+AI` after a person's name.

The 2022 evidence defeats both.

I would use something closer to:

> **As far as publicly searchable prior art has established, Eric Mourant's `+AI` proposal is the first to define `+AI`, when appended to a human or organisational name, as a situational post-nominal declaring both material AI assistance and the named party's acceptance of responsibility for the associated work.**

An even safer academic formulation is:

> **No earlier proposal has been identified that defines `+AI` specifically as a situational responsibility post-nominal: a mark appended to the accountable party's name to declare that AI materially assisted the associated work and that the named party has adopted and accepts responsibility for its release.**

I prefer the second. It makes an **evidence-based novelty statement** rather than trying to prove an absolute historical negative.

### One change I would make to your article

Your sentence saying that `+AI` “may represent the beginning of an entirely new class of post-nominal” is still supportable. 

But the strongest intellectual contribution is **not the plus sign**.

It is the semantic transformation:

**AI disclosure → accountable human declaration**

and the structural transformation:

**disclosure label → situational responsibility post-nominal**

That is the territory I would stake out explicitly.

[1]: https://www.royalroad.com/forums/thread/124784?page=1 "Ethically, if you're using AI, your creation should be labelled as such | Royal Road"
[2]: https://www.nature.com/articles/d41586-023-00191-1?utm_source=chatgpt.com "Tools such as ChatGPT threaten transparent science; here are our ground rules for their use | Nature"
[3]: https://www.icmje.org/recommendations/browse/artificial-intelligence/ai-use-by-authors.html?utm_source=chatgpt.com "ICMJE | Recommendations | Preparing a Manuscript for Submission to a Medical Journal"
[4]: https://datatracker.ietf.org/doc/draft-taoqiwen-hgcp/00/ "draft-taoqiwen-hgcp-00 - HGCP: A Voluntary Signing Framework for Human Expression in the Age of AI"
[5]: https://authorsguild.org/news/ag-launches-human-authored-certification-to-preserve-authenticity-in-literature/?utm_source=chatgpt.com "Authors Guild Launches \"Human Authored\" Certification to Preserve Authenticity in Literature - The Authors Guild"
[6]: https://support.microsoft.com/en-us/msn/partner-hub/msn-ai-content-policy "MSN AI content policy | Microsoft Support"
[7]: https://kernel.org/doc/html/next/process/coding-assistants.html "AI Coding Assistants — The Linux Kernel documentation"
[8]: https://patents.google.com/patent/US20260099327A1/en?utm_source=chatgpt.com "US20260099327A1 - Auditable authorship attribution with automatically applied authorship tokens - Google Patents"
[9]: https://spec.c2pa.org/specifications/specifications/2.2/explainer/Explainer.html?utm_source=chatgpt.com "C2PA and Content Credentials Explainer :: C2PA Specifications"
