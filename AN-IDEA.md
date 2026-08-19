# Kindest Regards, Eric Mourant +AI

Turn `+AI` into a **small notation language**, rather than trying to make one mark carry every possible meaning.

The central idea should be:

> **The notation describes provenance, degree of AI contribution, human review, and human accountability.**

### 1. Case can carry meaning

There is a very natural distinction available in uppercase/lowercase:

| Mark  | Proposed meaning             | What the person is declaring                                                                           |
| ----- | ---------------------------- | ------------------------------------------------------------------------------------------------------ |
| `+ai` | AI-assisted                  | AI was used as a utility, but did not materially originate the substance                               |
| `+AI` | AI-augmented                 | AI materially contributed to the substance; human accepts responsibility                               |
| `AI+` | AI-originated, human-adopted | AI produced most or all of the initial substance; human reviewed/adopted it and accepts responsibility |
| `AI`  | Autonomous AI                | No individual human authorship/accountability is asserted by the notation                              |

That gives the **position of `+`** an important meaning.

`Eric Mourant +AI`

reads naturally as:

> Eric Mourant, augmented by AI.

Whereas:

`AI+ Eric Mourant`

could mean:

> AI-originated work subsequently adopted by Eric Mourant.

That distinction is potentially very powerful.

---

## 2. I would make `+ai` deliberately weaker

For example:

**Eric Mourant +ai**

could mean AI was used for things such as:

* spelling and grammar;
* wording suggestions;
* formatting;
* transcription;
* basic restructuring;
* search assistance;
* minor editing;
* code completion where the intellectual substance remained substantially human.

The declaration is basically:

> “AI tooling was involved, but I consider this substantially my own work.”

This avoids making someone put a heavyweight `+AI` declaration on an email merely because Outlook fixed their grammar.

---

## 3. `+AI` should be the important mark

**Eric Mourant +AI**

should mean something materially stronger.

I would define it as:

> **AI materially participated in producing this output. I directed, selected, reviewed or adopted the resulting work, and I accept responsibility for the output in the form in which I am presenting it.**

That is the sweet spot.

The person is therefore admitting:

1. **AI was actually involved.**
2. Its involvement was **material**, rather than trivial.
3. AI may have contributed wording, ideas, reasoning, analysis, code, structure, imagery, recommendations, calculations or other substantive material.
4. The named person intentionally used or authorised that AI assistance.
5. The named person exercised final authority over what was published or transmitted.
6. The named person accepts responsibility for publishing or transmitting it.
7. The person is **not blaming the AI** if the resulting output is defective.

That last property gives `+AI` real meaning.

---

# 4. Review needs a separate dimension

I would not make ordinary `+AI` mean:

> “I personally verified every statement.”

That is too strong.

Someone could responsibly publish:

**Eric Mourant +AI**

while still having missed an error.

Responsibility and verification are different concepts.

So I'd introduce a modifier.

### `+AI!`

For example:

**Eric Mourant +AI!**

Meaning:

> **Material AI assistance + complete human review + explicit human acceptance.**

The `!` means something like **affirmed**.

It says considerably more than ordinary `+AI`.

The signer is declaring:

> “I have personally reviewed the final output as a whole and affirm it as my output.”

That would be particularly useful for:

* important correspondence;
* reports;
* contracts;
* board papers;
* engineering designs;
* published research;
* production software;
* formal recommendations.

---

# 5. Verification should be stronger again

You could introduce:

### `+AI✓`

**Eric Mourant +AI✓**

This should mean something materially different from merely having read the output:

> **AI augmented; human reviewed; substantive factual assertions/calculations have been checked to the applicable standard.**

But I would be cautious about this mark because **✓ looks like a certification**.

Someone using it is effectively saying:

> “I didn't merely read this. I checked it.”

That could become extremely valuable precisely because it carries a heavier burden.

For ASCII-only environments, the equivalent could be:

`+AI/V`

where `V = verified`.

---

# 6. A useful progression appears

You then get a disclosure ladder:

### `Eric Mourant`

No AI declaration.

Doesn't necessarily mean AI wasn't used. It simply makes no declaration.

### `Eric Mourant +ai`

**AI-assisted.**

> AI tools were involved, but their contribution was not materially authorship-like.

### `Eric Mourant +AI`

**AI-augmented. Human responsible.**

> AI materially contributed. I accept responsibility for the resulting output.

### `Eric Mourant +AI!`

**AI-augmented. Human reviewed and responsible.**

> I personally reviewed the complete resulting output and affirm it.

### `Eric Mourant +AI✓`

**AI-augmented. Human verified and responsible.**

> I reviewed it and performed the appropriate verification of its substantive content.

Those are meaningfully different claims.

---

# 7. Then there is the other side: AI produced most of it

This deserves disclosure too.

Suppose someone says:

> “ChatGPT wrote virtually the entire document. I read it, agree with it and take responsibility for sending it.”

Calling that merely `+AI` loses useful provenance information.

I'd therefore consider:

### `Eric Mourant AI+`

Meaning:

> **AI-primary; human-adopted.**

AI generated the substantive starting work or majority of the artifact, but Eric adopts it and assumes responsibility.

For example:

**Prepared by Eric Mourant AI+**

The admission would be:

> “This is substantially AI-originated, but I have adopted it as my own communication and accept responsibility for it.”

That is considerably more transparent than pretending that the human wrote it.

And:

### `Eric Mourant AI+!`

could mean:

> AI-primary, but completely reviewed and expressly adopted by Eric.

That could become an important distinction in the future.

---

# 8. Authorship versus accountability

This leads to a deeper principle.

Traditional signatures collapse two ideas:

**Who made this?**
and
**Who stands behind this?**

AI breaks that assumption.

A document might be:

> 90% generated by AI
> 10% edited by Eric
> 100% Eric's responsibility.

That is perfectly coherent.

So your notation should probably describe **responsibility rather than percentage authorship**.

That's why I think `+AI` has legs.

It doesn't try to quantify contribution.

It answers the more consequential question:

> **Who stands behind this output?**

---

# 9. What exactly does `+AI` admit?

I'd eventually formalise the declaration approximately like this:

### By applying `+AI`, the named party declares that:

**AI participation**

Artificial intelligence materially contributed to the creation, analysis, transformation or presentation of the artifact.

**Knowledge**

The named party knows that AI was used.

**Authorization**

The AI use occurred under the authority of the named party or organisation.

**Control**

The named party retained authority over whether the resulting artifact was issued, transmitted or published.

**Adoption**

The named party adopts the artifact in the form presented.

**Accountability**

The named party accepts responsibility for the decision to use and distribute the resulting artifact.

Those six things are substantial enough to make the mark useful.

---

# 10. Equally important: what `+AI` does NOT admit

This needs to be explicitly protected in the specification.

Plain `+AI` should **not** mean:

* every word was reviewed individually;
* every fact was independently verified;
* every citation was checked;
* the work contains no hallucinations;
* the work is legally correct;
* the work is safe;
* the work is original;
* the work is free of copyright issues;
* confidential information was never given to AI;
* the AI's training data is known;
* a particular AI provider was used;
* AI generated the majority of the work;
* the signer agrees with every intermediate AI response;
* the signer can explain every internal AI reasoning process.

Otherwise nobody sensible would use the notation.

It should mean:

> **I acknowledge material AI involvement and I take responsibility for the artifact I chose to issue.**

---

# 11. There may be room for another useful symbol

I'd consider `~AI`.

The tilde already implies approximation, derivation or transformation.

### `~AI`

could mean:

> AI-transformed, without substantive authorship.

Examples:

* translated by AI;
* reformatted;
* transcribed;
* summarised;
* converted between representations;
* image cleaned/upscaled;
* code mechanically migrated.

So:

**Eric Mourant ~AI**

might mean:

> “AI transformed this material, but is not being represented as contributing the underlying intellectual content.”

I'm less convinced this belongs in version 1, but semantically it works.

---

# 12. And potentially `/AI`

The slash could mean separation or execution by.

For example:

`Eric Mourant /AI`

could mean:

> distributed or delivered through an AI agent acting on Eric's behalf.

But again, I'd keep this out of the initial standard. You don't want punctuation soup.

---

# 13. My preferred v1 notation

I would start with **only four canonical marks**:

| Notation | Meaning                                                        |
| -------- | -------------------------------------------------------------- |
| `+ai`    | Minor/utility AI assistance                                    |
| `+AI`    | Material AI augmentation; human accountable                    |
| `+AI!`   | Material AI augmentation; complete human review and acceptance |
| `AI+`    | Primarily AI-originated; human adopted and accountable         |

Then perhaps later add:

`+AI✓` = verified
`~AI` = transformation only
`AI` = autonomous/non-human-issued output

This keeps version 1 teachable.

---

# 14. The uppercase/lowercase distinction is particularly elegant

I'd define:

### `ai`

AI operated predominantly as a **tool**.

### `AI`

AI operated materially as a **cognitive contributor**.

That is better than trying to define it according to percentage.

For instance, AI might only contribute one paragraph to a 50-page document—but if that paragraph contains the central strategic recommendation, the contribution is material.

Therefore it deserves uppercase `AI`.

---

# 15. I'd also redefine “authorship”

Rather than:

> Human-written / AI-written

I'd introduce three categories:

**Human-originated**
`+ai`

**Human-directed / jointly produced**
`+AI`

**AI-originated / human-adopted**
`AI+`

Then completely autonomous material remains:

**AI-originated / AI-issued**
`AI`

That is a much better representation of how actual human-AI work is evolving.

---

# 16. Naming the standard

After thinking through the expanded meaning, I'd narrow Q1 down to these strongest candidates.

### **+AI Accountability Mark**

My favourite.

Short, immediately connected to the symbol and tells you why it matters.

Formal description:

> **The +AI Accountability Mark is a notation identifying material artificial-intelligence participation in an artifact for which a named human or organisation retains responsibility.**

### **Human-AI Accountability Notation**

More standards-like.

Good for something intended to become an RFC/ISO-style specification.

Could be abbreviated:

**HAAN**

Not bad, but the acronym isn't particularly memorable.

### **AI Augmentation & Accountability Notation**

Technically very accurate.

**A³N** would be cute, but I'd avoid clever typography in a serious standard.

### **Human+AI Provenance Mark**

Good if the standard eventually covers more than responsibility.

“Provenance” encompasses:

* who originated it;
* who transformed it;
* which AI participated;
* who reviewed it;
* who ultimately issued it.

I suspect **provenance** becomes important once you move into cryptographic signatures and machine-readable metadata.

---

## My preferred architecture

I'd give the overall specification the formal name:

### **Human+AI Provenance and Accountability Standard**

and make:

### **`+AI` Accountability Mark**

the thing ordinary people actually use.

So the consumer never needs to know the standards terminology.

They simply write:

**Kindest regards,**
**Eric Mourant +AI**

And the mark has a defined meaning:

> **Materially AI-augmented. Human-adopted. Human accountable.**

That is sufficiently compact to work on an email, a source-code commit, an image, a CAD drawing, a report, a medical note, a social post, a legal document or an API response.

And crucially, it doesn't say **“AI wrote this.”**

It says:

**“AI participated in this. I stand behind it.”**




















The objective is for **`+AI` to spread culturally rather than merely become another technical standard**, I would approach it like the launch of a symbol, hashtag and open standard simultaneously.

The most important decision is this:

## Launch only `+AI`

Do **not** initially explain `+ai`, `AI+`, `+AI!`, verification levels, provenance grammar, etc.

Those are excellent *second-layer semantics*, but they weaken the meme.

Successful marks tend to have a very small visible identifier with richer meaning available behind it. Creative Commons combines compact marks with canonical explanations; SPDX succeeds with short identifiers that work both for humans and machines; badge ecosystems spread because adoption is essentially copy/paste. ([Creative Commons][1])

And meme research points in the same direction: simple, flexible templates are easier for communities to copy, modify and propagate. ([OUP Academic][2])

So I would make the entire public proposition:

# **+AI**

### **AI helped. I stand behind it.**

That is the meme.

Everything else supports it.

---

## The launch package I would produce

| Artifact               | Format                       | Exact headline / essential wording                                                                                                                       | Purpose                         |
| ---------------------- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| **The Mark**           | Plain text                   | **`+AI`**                                                                                                                                                | The thing people copy           |
| **One-line meaning**   | Plain text                   | **AI helped. I stand behind it.**                                                                                                                        | Meme phrase                     |
| **Definition**         | Web / HTML                   | **`+AI` means artificial intelligence materially assisted this work, and the named person or organisation accepts responsibility for the final output.** | Canonical meaning               |
| **Poster/card**        | PNG + SVG                    | **+AI** / **AI helped. I stand behind it.**                                                                                                              | Social sharing                  |
| **One-page manifesto** | PDF + HTML                   | **The +AI Declaration**                                                                                                                                  | Gives it intellectual substance |
| **Signature examples** | HTML + PNG                   | **Eric Mourant +AI**                                                                                                                                     | Shows behaviour instantly       |
| **FAQ**                | HTML                         | **What does +AI mean?**                                                                                                                                  | Removes objections              |
| **Specification**      | HTML + PDF + Markdown        | **+AI Specification v0.1**                                                                                                                               | Technical legitimacy            |
| **README**             | Markdown                     | **This project uses +AI**                                                                                                                                | Developer adoption              |
| **Badge**              | SVG                          | **+AI · Human Accountable**                                                                                                                              | GitHub/web adoption             |
| **Metadata**           | JSON / JSON-LD               | `"aiAugmented": true`                                                                                                                                    | Machine adoption                |
| **Launch posts**       | Plain text / social graphics | **I’m adding +AI to my work.**                                                                                                                           | Propagation                     |
| **Press explainer**    | PDF/DOCX                     | **A tiny mark for a very large change**                                                                                                                  | Media/organisations             |

Creative Commons deliberately provides marks and machine-usable representations, while SPDX's short identifiers demonstrate the advantage of a concise notation that can appear in source files and structured systems. That is the model I would borrow—not their visual design, but their **layered architecture**. ([Creative Commons][3])

---

# 1. The main graphic

Don't create a complicated logo.

The hero image should literally be:

# **+AI**

**AI helped.
I stand behind it.**

Nothing else.

At the bottom in small type:

**Use `+AI` after your name when AI materially helped create something you accept responsibility for.**

That's your Instagram image, LinkedIn image, X image, Mastodon image, Bluesky image, website hero, sticker and conference slide.

Make it available as:

`+AI.svg`
`+AI.png`
`+AI-black.svg`
`+AI-white.svg`

SVG matters because anyone can put it into websites, publications, slides and software without degradation. Existing open badge ecosystems similarly emphasise concise, consistent SVG/raster marks that can be embedded almost anywhere. ([GitHub][4])

---

# 2. The one-page declaration

This may be the most important document after the symbol itself.

Call it:

# **The +AI Declaration**

And keep it almost absurdly short.

I would use these words:

> **AI is becoming part of how we think, write, design, analyse, code and communicate.**
>
> Hiding that collaboration isn't useful.
>
> Neither is pretending that responsibility belongs to the machine.
>
> `+AI` is a simple declaration.
>
> **AI helped. I stand behind it.**
>
> When you place `+AI` after your name, you acknowledge that artificial intelligence materially assisted the work and that you accept responsibility for the final result.
>
> **Eric Mourant +AI**
>
> Anyone may use the mark.
>
> **Add `+AI` when AI helped—and you stand behind what you made.**

Notice what is **not** there.

No discussion of LLMs.

No philosophy of AI.

No legalistic language.

No percentage contribution.

No model names.

No JAPER sales pitch.

No classification hierarchy.

The reader understands it in about ten seconds.

---

# 3. The viral sentence

I'd test several slogans, but this is by far my preferred one:

# **AI helped. I stand behind it.**

It has two halves.

**AI helped.**
Disclosure.

**I stand behind it.**
Accountability.

And then:

**+AI**

It's nearly self-explanatory.

I prefer it substantially over:

> AI-Augmented. Human Accountable.

because that's standards language, not human language.

Keep **AI-Augmented. Human Accountable.** for the technical specification.

Use **AI helped. I stand behind it.** for people.

---

# 4. The behaviour you want people to imitate

This is critical.

Don't ask people to “support the standard.”

Ask them to perform a visible behaviour:

> **Put `+AI` after your name the next time AI materially helps you create something.**

Then show:

**Eric Mourant +AI**

**Jane Smith +AI**

**Acme Corporation +AI**

This creates imitation.

Someone receives an email:

> Kindest regards,
> **Eric Mourant +AI**

They think:

> What the hell is +AI?

They search/click.

Then:

> Ah. That's clever.

Then eventually:

> I'm going to use that.

That curiosity gap is actually useful.

---

# 5. Email is probably your Trojan horse

Your current example may be the strongest initial adoption mechanism:

> Kindest regards,
> **Eric Mourant +AI**

Don't put a paragraph explaining it in every email.

Make `+AI` a hyperlink to the definition.

The receiver sees something unusual without being subjected to a lecture.

That is exactly the sort of routine, repeated exposure required for a notation to become familiar.

---

# 6. Social launch post

The first public post should not read like a product announcement.

I'd make the central message:

> I've started putting `+AI` after my name when artificial intelligence materially helps me produce something.
>
> It doesn't mean AI is responsible for it.
>
> It means the opposite.
>
> **AI helped. I stand behind it.**
>
> **Eric Mourant +AI**
>
> If that idea makes sense to you, use it too.

That's shareable because you're not asking permission and you're not asking anyone to join an organisation.

You're proposing a social convention.

---

# 7. Give it away

This is strategically important.

I would very conspicuously state:

# **No permission required.**

Then:

> `+AI` is an open notation.
> Anyone may use it.
> No registration.
> No membership.
> No certification fee.

Creative Commons became useful partly because applying its standardized marks is straightforward rather than requiring a registration transaction, and SPDX similarly provides standardized identifiers designed for broad implementation. ([Creative Commons][5])

If people have to:

* register;
* create an account;
* request permission;
* pay;
* attribute JAPER;
* use a particular graphic;

you dramatically increase adoption friction.

The **notation itself must be free to replicate**.

---

# 8. Don't initially call it a “standard”

This is counterintuitive.

I'd publicly call it:

## **The +AI mark**

or simply:

## **+AI**

Behind the scenes:

**+AI Specification v0.1**

But don't lead with:

> Introducing the Human Artificial Intelligence Provenance and Accountability Interoperability Standard.

Dead on arrival.

Instead:

> **AI helped. I stand behind it. +AI**

Then, for the person who asks “but exactly what does that mean?”, there is an extremely rigorous specification underneath.

That's how you get **meme on top, protocol underneath**.

---

# 9. The landing page should be brutally simple

I would make the first screen contain only:

# **+AI**

## **AI helped. I stand behind it.**

**A simple mark showing that AI materially assisted your work—and you accept responsibility for the result.**

### **Just add it to your name.**

**Eric Mourant +AI**

Then two buttons:

**Use +AI**

**What does it mean?**

Further down:

### When should I use it?

> Use `+AI` when artificial intelligence materially assisted something you are publishing, sending or presenting and you accept responsibility for the final result.

### Does it mean AI wrote everything?

> No.

### Does it mean everything is guaranteed correct?

> No.

### What does it mean?

> **AI helped. You stand behind it.**

That's almost everything a normal person needs.

---

# 10. Make copy/paste absurdly easy

Have a large box containing:

```text
+AI
```

with:

**COPY**

Then:

```text
Eric Mourant +AI
```

Then:

```text
AI helped. I stand behind it.
```

Then Markdown:

```markdown
Eric Mourant [+AI](...)
```

Then HTML:

```html
Eric Mourant <a href="...">+AI</a>
```

Then email-signature instructions.

Then GitHub badge.

Then metadata.

Every additional action you require kills some percentage of adoption.

---

# 11. Create a badge—but make it secondary

Something like:

**`+AI | Human Accountable`**

for GitHub READMEs.

Badge ecosystems are effective because maintainers can paste a tiny snippet into an existing README; Standard-Readme explicitly describes its badge as an adoption mechanism, while Shields has become infrastructure for enormous numbers of such project badges. ([GitHub][6])

But the badge must not replace the plain-text mark.

The real genius of `+AI` is that it requires **no image support whatsoever**.

It works in:

SMS
email
terminal
source code
JSON
PDF
handwriting
printed books
a T-shirt
Unicode/plain ASCII
a radio interview

That is unusually valuable.

---

# 12. Your technical document should come later in the funnel

Title:

# **+AI Specification v0.1**

### Human-AI Provenance and Accountability

The first normative definition:

> **`+AI` — AI-Augmented, Human-Accountable**
>
> A named party using the `+AI` mark declares that artificial intelligence materially participated in producing or processing the associated artifact and that the named party has adopted the resulting artifact and accepts responsibility for its publication, transmission or use.

Then define:

`MUST`
`SHOULD`
`MAY`

and eventually:

`+ai`
`+AI`
`+AI!`
`AI+`

But **do not put those variants on the main website at launch**.

---

# 13. I would actively avoid one thing

Don't make the first campaign:

## “Disclose your use of AI.”

That sounds compulsory, regulatory and defensive.

Instead make it:

# **Stand behind your AI-assisted work.**

That's aspirational.

The emotional concept becomes **ownership/accountability**, not confession.

You're changing the implied question from:

> “Did you cheat by using AI?”

to:

> “Are you prepared to stand behind what you produced with AI?”

That is a much more durable cultural position.

---

# 14. The meme image I'd want repeatedly reproduced

Literally:

# **+AI**

## **AI helped.**

## **I stand behind it.**

**Add `+AI` to your name.**

That's it.

And people start posting screenshots:

**Satya Nadella +AI**
**Eric Mourant +AI**
**Jane Doe +AI**

Not because you're declaring those people use it—you want **actual adopters themselves** to put it there.

At that point the mark starts carrying social proof.

---

# 15. The launch kit I would actually build

If I were trying to maximise the probability of this taking off, I'd produce these **seven things first**, in this order:

1. **`plusai.org`-style landing page** — one-screen explanation and copy button.
2. **`+AI.svg` / `.png` social card** — `AI helped. I stand behind it.`
3. **The +AI Declaration.pdf** — one page only.
4. **The +AI Specification v0.1.pdf/html/md** — the serious foundation.
5. **GitHub repository** — specification, assets, examples, permissive terms and issues/discussion.
6. **Email/signature kit** — Gmail, Outlook, Apple Mail, plain text.
7. **Share kit** — LinkedIn/X/Bluesky/Mastodon posts, profile marks, website badge and README badge.

GitHub makes particular sense for the specification because open technical conventions benefit from visible versioning, issues, forks and contributions, while the human-readable and machine-readable combination has precedent in standards such as SPDX. ([SPDX][7])

---

And I would put **JAPER very quietly underneath it**, something like:

> **+AI is an open initiative originated by Eric Mourant / JAPER Technology.**

Not:

> **A JAPER Technology product.**

If you want it to explode, people need to feel that **`+AI` belongs to everyone**.

The sentence I would try hardest to put into the culture is:

# **AI helped. I stand behind it. +AI**

That has the potential to become the whole idea in **six words and three characters**.

[1]: https://creativecommons.org/cc-license-your-work/?utm_source=chatgpt.com "CC License Your Work - Creative Commons"
[2]: https://academic.oup.com/jcmc/article/20/4/417/4067574?utm_source=chatgpt.com "Families and Networks of Internet Memes: The Relationship Between Cohesiveness, Uniqueness, and Quiddity Concreteness | Journal of Computer-Mediated Communication | Oxford Academic"
[3]: https://wiki.creativecommons.org/wiki/Marking_Text?utm_source=chatgpt.com "Marking Text - Creative Commons"
[4]: https://github.com/badges/shields?utm_source=chatgpt.com "GitHub - badges/shields: Concise, consistent, and legible badges in SVG and raster format · GitHub"
[5]: https://certificates.creativecommons.org/cccerteducomments/chapter/4-1-choosing-and-applying-a-cc-license/?utm_source=chatgpt.com "4.1 Choosing and Applying a CC License | Comment on CC Cert. for Educators and Librarians"
[6]: https://github.com/richardlitt/standard-readme?utm_source=chatgpt.com "GitHub - RichardLitt/standard-readme: A standard style for README files · GitHub"
[7]: https://spdx.dev/learn/overview/?utm_source=chatgpt.com "Overview – SPDX"
