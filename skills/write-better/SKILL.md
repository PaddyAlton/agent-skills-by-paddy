---
name: write-better
description: Use when writing anything to be read by many people. Write concisely. Use fewer AI-isms. Condense text, retaining clarity. Take inspiration from great writers.
---

# Write Better Prose

>  "I have only made this letter longer because I have not had the time to make it shorter." (Blaise Pascal)

It takes time and effort to condense the written word, conveying the same information more transparently and in less space. This skill describes how to do it.

Use this skill to write or refine any prose that will be read by more than one person:

- RFCs (e.g. in Notion)
- Tickets (e.g. in Linear)
- Documentation in this project
- ADRs (Architecture Decision Records)
- PR descriptions

## Typical Triggers

(Usually at the end of a long 1-1 discussion)

- "Write this up as a Linear ticket"
- "Write a Notion RFC to propose this change"
- "Let's capture this in our documentation"
- "We need an ADR for this"

(Usually as a standalone request)

- "Make this Linear ticket more concise and clear for others"
- "Tidy up this RFC before I share it with our colleagues"

(As part of the delivery-of-work process)

- "Add a description for this PR"

## Core Principles

*Lead with value*
- First sentence does the work
- Don't bury the takeaway
- Readers scroll fast

*Be direct, not blunt*
- Say what you mean
- Confidence without arrogance
- Contractions are fine

*Technical, not alienating*
- Define terms when helpful
- Complex ideas deserve simple language
- Let code speak when it can

*Share what you actually know*
- Personal experience beats generic advice
- Specific examples beat abstract principles
- Acknowledge what you don't know

*Iterate, iterate*
- Write, refine, refine again
- Don't stop condensing until you have 'diamond prose': hard and precise, not fluffy; polished and clear, not just 'good enough'; high value in a small space

## Standard Practices

### Summarise first

For Tickets and RFCs, *ALWAYS* lead with a summary:

Format: 1-3 sentences that capture the 'so what'

Audience: imagine our CTO stayed up late and now we're in the middle of a triage session the next morning. The summary must be suitable for this situation. The summary may assume some background system and technical knowledge, but must grab attention in a small space. The reader must grasp the problem and any proposed solution without reading the rest of the document.

ADRs have their own format (which you should refer to) but said format starts with
a title and a description line, respecting this principle.

PRs have their own format (which you should refer to) but said format starts with summaries of the overall stack and the specific PR, respecting this principle.

### Diamond prose

Write like Hemingway, each sentence simple and load-bearing. Florid sentences may have their place elsewhere, but not here. Your prose should be grammatically correct and brief.

In the main body, structure the prose. Use headings and subheadings to break up the text. Use short paragraphs. Avoid long blocks of text.

Bullet-points, numbered lists, and checklists are good. Use them.

### Orwell's six rules

Famous writing rules from *Politics and the English Language* (George Orwell). Good for writing concisely.

1. Never use a metaphor, simile, or other figure of speech which you are used to seeing in print.
2. Never use a long word where a short one will do.
3. If it is possible to cut a word out, always cut it out.
4. Never use the passive where you can use the active.
5. Never use a foreign phrase, a scientific word, or a jargon word if you can think of an everyday English equivalent.
6. Break any of these rules sooner than say anything outright barbarous.

Amendment:

We're doing technical writing, so technical terms have their place *where they encode information concisely without loss of clarity*.

Some technical terms and acronyms are commonplace among engineers and don't need explaining: API, backend/frontend, database, HTTP, SQL, JSON, YAML, etc.

However, if a term would not be understood by a newly-joined engineer, define it on the first use. Terms specific to your industry or domain need the same care.

If there are several such terms, include a 'jargon buster' section below the executive summary, in this format:

```text
### Jargon Buster

[Term]:
[A one-line definition a new joiner would understand.]

[Related terms, e.g. two acronyms]:
- [Acronym 1]: [expansion]
- [Acronym 2]: [expansion]
[One line on what they mean together and why they matter.]
```

(Leave out terms your whole audience already knows.)

### Avoid 'AI-isms'

Banned patterns:

*Rule of three*
Grouping items in threes is a well-known technique, but overused. Vary list lengths.

BAD: "The project was innovative, comprehensive, and groundbreaking."
GOOD: "The project worked."

*Negative parallelisms*
BAD: "This is not just a tool, but a revolution." / "This is not good; it's bad."
GOOD: State what it is directly.

*em-dashes*
The em-dash `—` is often overused. Strive for a balance of punctuation markers.

Creating an 'aside': parentheses `()` and commas `,` should be used at least as often.

USE LESS: "The project — which had executive backing — changed the way we work."
USE MORE: "The project, which had executive backing, changed the way we work." / "The project (which had executive backing) changed the way we work."

Creating a 'break': semicolons `;` and colons `:` and periods `.` should be used at least as often.

USE LESS: "This work was successful — it led to a cost saving of £10,000."
USE MORE: "This work was successful: it led to a cost saving of £10,000."

USE LESS: "This technology is essential — it enables us to scale."
USE MORE: "This technology is essential; it enables us to scale." / "This technology is essential. It enables us to scale."

### Other Rules

Use British English spelling and grammar. Avoid Americanisms.

### Conclude Clearly

End with a clear conclusion. Summarise the key points and any next steps. If there are action items, make them explicit.
