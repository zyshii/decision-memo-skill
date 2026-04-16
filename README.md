# Decision Memo Skill

A Claude skill for turning day-to-day workplace decisions into durable career capital — structured, retrievable, and ready to power portfolio case studies and behavioral interview stories.

**TL;DR: 既然改变不了煞笔同事，那就把煞笔同事蒸馏成自己跳槽的资本**

## Why This Exists

Knowledge workers make dozens of meaningful decisions a year: tradeoffs navigated, stakeholders managed, constraints accepted. Most of this material is lost because it's never recorded in a form that survives past the week it happened. By the time job search comes around, memory has smoothed over the sharp edges — the specific alternatives weighed, the political judgments made, the assumptions that turned out to be wrong. What's left is execution narrative, not judgment narrative.

The gap between mid-level and senior-level positioning in design (and most knowledge work) is rarely about *what* someone built. It's about how they articulate the judgment behind decisions. Senior narratives name tradeoffs, alternatives, and systems of thinking. Mid-level narratives describe sequences of actions. This skill forces the inputs that senior narratives need, at the moment the inputs are fresh enough to be accurate.

## How It Works

When the user describes a workplace decision, conflict, or pivot, the skill offers to capture it as a structured memo. On confirmation, it runs a guided retrospective interview and produces a Notion document in two layers:

- **Part A — Internal Retrospective**: honest, unfiltered. Stakeholder dynamics, political judgments, unresolved tensions, things that went wrong. Written in the user's primary language (Chinese, in the original use case).

- **Part B — Outward Narrative**: extracted from Part A. A STAR-format behavioral interview story plus anticipated hook questions, in both the user's language and English. Sanitized of company-specific detail and emotional residue; preserves decision logic.

The two layers are deliberately separate. Part A is for the user's memory. Part B is for a future interviewer or portfolio reader. The same raw material feeds both, but the rhetorical constraints are different, so the texts are different.

## Two Modes

**Full Mode** — for high-stakes decisions. Six-section retrospective plus bilingual STAR and hook questions. 15–30 minutes of conversation.

**Quick Capture Mode** — for preserving material before it fades. Condensed three-section version plus bilingual STAR and a hook question or two. 5–10 minutes. Can be upgraded to Full Mode later without re-interviewing.

## Design Principles Behind the Skill

**Reframing before templating.** The first thing users describe is often a tool choice, not a decision. ("I built a version control system.") The actual decision sits one level up. ("When persuasion stopped working, I switched to governance.") The skill surfaces this upstream framing before filling any template — because senior narratives are built on strategic judgments, not tool choices.

**No decision without alternatives.** A memo that only describes the chosen path isn't a decision memo, it's an execution memo. The skill treats "what did you rule out?" as a non-skippable gate. If the user genuinely had no alternatives, that itself is the finding and the memo should reflect it.

**Honest internal, neutral external.** Part A preserves voice — including frustration, self-criticism, and political calculation. Part B strips both adversarial framing and self-erasure. The goal is truthful framing of what the user actually did within their actual authority, not inflation and not performative modesty.

**Translation, not transliteration.** The English Part B is re-authored for English-speaking interviewers, not word-for-word translated. Register, hedging density, sentence structure, and vocabulary all shift. Voice is preserved; idiom is not.

**Quality checks surface, don't auto-edit.** The skill flags potential issues (passive voice, missing alternatives, emotional stakeholder language) and asks the user to confirm. The user's voice and judgment are the final authority.

## File Structure

```
decision-memo/
├── SKILL.md              Main skill definition: triggers, modes, workflow
├── TEMPLATE_FULL.md      Full mode template (bilingual Part B)
├── TEMPLATE_QUICK.md     Quick capture template
├── INTERVIEWING.md       Structured interview question bank by section
├── QUALITY_CHECKS.md     Senior-level narrative quality gates
├── TRANSLATION_GUIDE.md  Chinese-to-English Part B principles
└── NOTION_WORKFLOW.md    Notion publishing procedure
```

## Installation

### Option 1 — CLI (fastest)

Clone the repo directly:

```bash
git clone https://github.com/zyshii/decision-memo-skill.git
```

Or download just the skill files without git history:

```bash
curl -L https://github.com/zyshii/decision-memo-skill/archive/refs/heads/main.tar.gz | tar -xz
```

Or download a zip:

```bash
curl -LO https://github.com/zyshii/decision-memo-skill/archive/refs/heads/main.zip
unzip main.zip
```

Once downloaded, upload the files to your Claude Project's knowledge base, or pass them to Claude Code / API as part of your context.

### Option 2 — GitHub web interface

1. Click the green **Code** button above, then **Download ZIP**
2. Unzip locally
3. In Claude's web interface, create or open a project
4. Upload the skill files to the project's knowledge base

### Option 3 — Manual paste (lowest fidelity)

Paste the contents of `SKILL.md` into any Claude conversation as an initial message to activate the behavior for that session. Works for one-off use but loses the multi-file structure.

## Customization

This skill was originally built for a product designer navigating mid-to-senior transition, with Notion as the primary workspace and Chinese as the conversational language. The patterns generalize to other knowledge work, but several things are worth customizing:

- **Language defaults** in `SKILL.md` and `TEMPLATE_FULL.md`. Swap Chinese for another primary language if needed. The English Part B logic is independent of the primary language choice.
- **Project prefix table** in `NOTION_WORKFLOW.md`. Replace the example projects with your own.
- **Domain vocabulary** in `TRANSLATION_GUIDE.md`. The translation examples lean toward design and product contexts. Extend or replace for other domains.
- **BQ question categories** in `INTERVIEWING.md`. The question bank assumes behavioral interview format common in tech hiring. Adjust for other interview cultures.

## Why Open-Source

I'm a product designer, and this skill was built for my own job search. I'm publishing it because the underlying idea — that senior-level narratives require senior-level inputs, captured at the moment they exist — seems useful to anyone doing knowledge work through the mid-to-senior career gap.

If you adapt this for your own use, I'd be curious to see what changes. Issues and PRs welcome.

## License

MIT. Use it, fork it, adapt it.

---

*Built in collaboration with Claude. The skill's design itself went through the decision memo process — which is probably the most on-brand testing methodology available.*
