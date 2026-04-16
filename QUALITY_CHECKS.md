# Senior Narrative Quality Checks

Run these checks after drafting Part B, before finalizing the memo. Surface flags to the user for confirmation rather than silently editing. The user's voice must remain theirs — the skill's job is to catch patterns, not rewrite.

## The Core Distinction

Mid-level narratives describe **what was done**. Senior narratives describe **what was chosen between, why, and what it revealed**. Every sentence in Part B should pass the test: *does this show judgment, or just activity?*

---

## Check 1 — Passive Voice and Agency Erasure

Flag and query:

- "We decided..." / "It was decided..." / "The team landed on..." → whose decision was it, and what did *you* do?
- "I was asked to..." / "I was given..." → what was your relationship to the ask? Did you shape it?
- "It turned out..." / "It became clear..." → who noticed? How? When?

Acceptable uses:
- When the user genuinely was not the decision-maker and the memo is honest about that (see Check 4)
- When describing genuine collective action where individual authorship isn't meaningful

---

## Check 2 — Missing Options

Scan for sentences like "I designed X" or "I built Y" that describe only the chosen path.

If no alternative appears anywhere in Part B:
- Flag: "Part B doesn't show what you chose against. Without that, this reads like execution, not decision-making."
- Fix: surface the rejected option from Part A into the Action section

A Part B without at least one "instead of" / "rather than" / "weighed against" is almost always under-pitching the user's judgment.

---

## Check 3 — Emotional Stakeholder Language

Flag any of the following in Part B:

- "PM didn't listen" / "Engineering refused" / "Leadership ignored" → reframe as priorities ("PM's priority was X; mine was Y")
- "I was frustrated" / "It was disappointing" → remove entirely; emotion belongs in Part A if anywhere
- "They made it hard" / "They blocked me" → reframe as organizational dynamics ("The org's structure created X situation")
- "Finally they agreed" / "Eventually they saw" → reframe without the adversarial arc

Rule of thumb: if a sentence would sound bitter read out loud in an interview, it's not ready for Part B.

---

## Check 4 — Honest Positioning Under Low Authority

When the user didn't have decision authority, Part B must not overclaim. Flag:

- "I led the decision to..." when user was actually the proposer
- "I convinced the team to..." when user's proposal was rejected
- Passive hedges that obscure the user's actual role

But equally, flag under-claiming:

- "I just executed" / "I only did what was asked" / "I wasn't really part of it" → if the user identified the problem, proposed alternatives, advocated internally, or extracted a methodology lesson, those are senior actions worth naming

The goal: honest framing of *what the user actually did within their authority*, not inflation and not self-erasure.

---

## Check 5 — The "Why" Test on Action

The Action section of STAR is where senior narratives live or die. Test each sentence:

- Does it say *what* was done, or *why* it was chosen?
- Is there a tradeoff named?
- Is there a stakeholder navigated?
- Is there a methodology reflected on?

If the Action is a sequence of verbs ("I researched, I prototyped, I shipped"), it's too thin. Ask the user: "What's one thing in here that wasn't obvious? What's the non-trivial judgment?"

---

## Check 6 — Result That Reflects Learning

The Result in STAR should contain two things:

1. What happened (outcome, ideally with a signal)
2. What it taught (one-sentence heuristic or shift in how the user operates)

A Result that only reports the outcome is mid-level. A Result that also names what changed in the user's future approach is senior.

---

## Check 7 — Hook Question Defensibility

For each hook question drafted, test:

- Is this a question an adversarial interviewer would actually ask, or a softball?
- Does the answer concede ground honestly, or does it sound defensive?
- Does the answer point to a transferable lesson, or just justify the past?

Good hook questions include ones the user might flinch from:
- "Do you think you failed here?"
- "Why didn't you push harder?"
- "How do you know your alternative was better?"
- "Isn't this just blaming the organization?"

If all three hook questions are comfortable, they're the wrong questions.

---

## Check 8 — Subject Consistency

Every sentence in Part B Action should have a clear subject. Flag:

- Passive constructions without actors
- Sentences that start mid-narrative ("Then the pivot happened")
- Unclear referents ("they" / "the team" without prior anchor)

Preferred structure: "I [verb] [object] because [reason]."

---

## Translation-Specific Checks (when producing English Part B)

See `TRANSLATION_GUIDE.md` for full translation principles. During quality check, additionally verify:

- English version avoids direct translation of Chinese idioms
- Self-assessment language ("Senior-level judgment...") used sparingly — once, not repeated
- Confidence register matches the user's actual voice (not inflated, not self-effacing)

---

## Surface Format

When running these checks, return flags to the user like:

> I want to flag a few things in Part B before we finalize:
>
> - **Check 2**: The Action says "I proposed Option B and it was rejected" but doesn't name what Option B competed against. Want to add the alternative?
> - **Check 3**: "Leadership ignored the usability argument" reads adversarial. Consider "Leadership prioritized business visibility over the usability case I made."
> - **Check 7**: The third hook question ("Did you learn something?") is softballed. A tougher interviewer would ask "Do you think your disagreement was actually right, or just preference?" Want to swap?
>
> Let me know which to adopt, and anything I should leave as-is.

Never auto-apply. The user's voice and judgment are the final authority.
