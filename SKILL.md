---
name: decision-memo
description: Capture workplace decisions and conflicts as portfolio case study material and behavioral interview (BQ) stories. Use when the user describes a workplace decision, disagreement, cross-functional conflict, constraint-driven pivot, or retrospective on something that happened at work — especially when they want to preserve it as career capital for future job searches. Outputs are structured Notion memos with separate internal retrospective and outward-facing narrative layers.
---

# Decision Memo Skill

## Purpose

Designers and other knowledge workers accumulate high-signal career capital from day-to-day decisions — but most of it evaporates because it's never recorded in a retrievable form. This skill captures decisions at the moment they're fresh, in a structure that separates honest internal retrospection from polished outward narrative, so the same raw material can later feed portfolio case studies or behavioral interview stories without re-interviewing the past.

The skill exists because the gap between mid-level and senior-level positioning in interviews is rarely about *what* someone built — it's about *how* they articulate the judgment behind decisions. Mid-level narratives describe execution. Senior narratives describe tradeoffs evaluated, stakeholders navigated, and systems of judgment. This skill forces the inputs that senior narratives need.

## When to Trigger

Proactive trigger (recommended default): when the user describes any of the following, Claude should ask *"This sounds like it could be worth capturing as a decision memo — want to log it?"* and only proceed on confirmation.

- A workplace decision they made or were party to, especially one with tradeoffs
- A cross-functional disagreement or conflict
- A pivot driven by external constraint (compliance, timeline, leadership change)
- Frustration with a colleague, process, or organizational dynamic
- A retrospective phrase like "looking back," "what I learned," "I should have," "next time I'd"
- Explicit requests: "record this," "capture this," "turn this into a memo," "use this for BQ"

Do not trigger on:
- Generic venting with no decision structure
- Questions about someone else's decision they weren't involved in
- Hypotheticals not grounded in actual events

## Mode Selection

On confirmation, immediately ask the user to pick a mode:

**Full Mode** — for decisions worth a complete retrospective
- Produces: Part A (six sections) + Part B (bilingual STAR + hook questions)
- Time cost: 15–30 minutes of conversation
- Use when: the decision is high-stakes, complex, or expected to anchor a case study / primary BQ story

**Quick Capture Mode** — for preserving material before it fades
- Produces: condensed Part A (3 sections) + abbreviated Part B (bilingual STAR + 1–2 hook questions)
- Time cost: 5–10 minutes
- Use when: the user wants to get it down and decide later whether to expand
- Can be upgraded to Full Mode in a future conversation

## Workflow

### Step 1 — Listen first

Let the user tell the story in their own words before structuring anything. Do not interrupt with template questions. Take mental notes on what's missing for the selected mode.

### Step 2 — Reframing check (Full Mode only)

Before filling the template, ask: *is the decision the user described the actual decision, or is it a downstream tool choice?*

Signals that reframing is needed:
- The "decision" is a concrete artifact (e.g., "I built a version control system") rather than a strategic choice
- The user's language suggests they're describing *what they did*, not *what they chose between*
- The surrounding context describes a pattern, not an isolated event

When detected, surface the upstream decision explicitly. Example: *"The version control system sounds like the tool. The decision underneath it seems to be 'when persuasion stopped working, I switched to governance.' Does that match how you were actually thinking?"* Only proceed when the user confirms or corrects the framing.

### Step 3 — Structured interview

Walk the sections in order. For each, check what the user already covered and ask targeted questions only for the gaps. Load `INTERVIEWING.md` for the full question bank. Do not ask more than 3 questions per turn.

Critical gates that must not be skipped:

- **Options evaluated.** If the user only described the chosen path, ask what was rejected. A memo with only one option is not a decision — it's execution. If no alternatives were considered, that itself is the finding, and the memo should reflect it.
- **Stakeholder dynamics.** Who supported, who opposed, who was neutral. What did the user do to move them. What tension remained unresolved.
- **Political judgment.** Did the user make any non-design tradeoffs (preserving relationships, picking battles, conserving capital)? These belong in Part A only.

### Step 4 — Draft Part A

Write Part A in Chinese by default (user's stated preference). Be honest — if the user said "I only executed" or "I didn't fight hard enough," preserve that voice in Part A. Do not sanitize Part A for credibility; its function is truthful retrospection, not performance.

### Step 5 — Extract Part B

From Part A, extract the outward-facing narrative. Part B exists in both Chinese and English. Apply the quality checks in `QUALITY_CHECKS.md` and the translation principles in `TRANSLATION_GUIDE.md`.

Key extraction rules:
- Subject of every sentence should be the user ("I"), not the organization ("we") or opponents ("they")
- Passive voice → active voice ("it was decided" → "I weighed X and chose Y")
- "Blame" language must be removed entirely — internal truth, external neutrality
- If the user didn't have decision authority, frame what they *did* do (identified, proposed, advocated, retrospected) rather than what they didn't (couldn't decide, wasn't heard)

### Step 6 — Quality checks

Before finalizing, run the Senior Narrative Self-Check (see `QUALITY_CHECKS.md`). Surface any flagged lines to the user for confirmation rather than auto-editing.

### Step 7 — Notion publish

Follow the procedure in `NOTION_WORKFLOW.md`:
1. Determine project and resolve project prefix
2. Find or create the `Decision Memos — [Project]` index page
3. Assign next ID ([PREFIX]-NNN for Full; [PREFIX]-Q-NNN for Quick)
4. Create the memo page under the index
5. Update the index table with the new entry
6. Return the Notion URL

## Default Assumptions

- Default user profile: a knowledge worker in mid-to-senior transition, actively building portfolio and BQ material for future job searches. Phrasing defaults are tuned for product design contexts but generalize to adjacent fields (PM, research, engineering management).
- Chinese is the conversational language; English Part B is for external use (interviews, portfolio copy).
- Notion is the destination. Project prefix map is stored in `NOTION_WORKFLOW.md` and should be extended when new projects appear.

## What This Skill Is Not

- Not a journaling tool. Every memo should have a discernible decision at its core.
- Not a complaint log. Frustration is a trigger signal, but the output must be decision-structured.
- Not a portfolio writer. Portfolio case studies consume memo content but are authored separately with different rhetorical constraints.
