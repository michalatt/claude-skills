---
name: ux-check
description: Audit a Claude Code skill for UX quality — scores discoverability, onboarding, user control, status, efficiency, and flexibility
argument-hint: "[skill-name]"
---

You audit Claude Code skills for UX quality. You read a skill's files, score it on 6 dimensions, and give actionable suggestions.

**Note:** This evaluates the skill standalone. If a skill is designed to run inside a wrapper/parent skill, some UX (like checkpoints) may come from the parent.

## Step 1: Find the skill

If the user provided a skill name as argument, look for it in `.claude/skills/[name]/SKILL.md`.

If no argument was given:
- List all folders in `.claude/skills/`
- Show the list and ask: "Which skill do you want to check?"

If the skill isn't found, tell the user and stop.

## Step 2: Detect mode

Read the skill's SKILL.md frontmatter. Check for signals:
- **Shared signals:** has `description` with "what + when", has `argument-hint`, has keywords or detailed frontmatter
- **Personal signals:** minimal or missing frontmatter, no description, bare-bones structure

Tell the user your guess and ask them to confirm:
> "This looks like a **shared** skill (has description and argument hint). Is that right, or is it personal?"

Use their answer for scoring. Don't proceed until confirmed.

## Step 3: Read files

Read the SKILL.md fully. Then find all local file references in it (relative paths, not URLs). Read up to 5 of them (first level only, no recursion).

If more than 5 referenced files exist, note the total count — you'll mention it in the report.

## Step 4: Score

Evaluate against these 6 dimensions. Each scores 0, 1, or 2.

| # | Dimension | 0 (Missing) | 1 (Partial) | 2 (Good) |
|---|-----------|-------------|-------------|----------|
| 1 | Frontmatter & discoverability | No description, or says only what (not when) | Exists but vague, missing keywords | Third-person, clear what + when, good keywords, clear command name |
| 2 | Onboarding | Jumps straight to work, no orientation | Some context but missing what's needed from user | States what it will do AND what it needs |
| 3 | User control | No defaults shown, no pauses, guesses when unclear | Inconsistent — asks in one place, assumes in another | Defaults surfaced, pauses at critical moments, asks when ambiguous |
| 4 | System status | No progress communication | Some updates but gaps in multi-step processes | Clear communication at each key step |
| 5 | Token efficiency | Over 500 lines, everything in one file | Reasonable length but could split better | Concise main file, details in referenced files |
| 6 | Degrees of freedom | Same rigidity for safe and dangerous operations | Some variation but not well-matched to risk | Strict where fragile, flexible where creative |

**Scoring math:**
- **Shared mode:** all 6 count → X/12
- **Personal mode:** only dimensions 5-6 scored → X/4. Show dimensions 1-4 as "optional" with findings but don't count them in the total.

## Step 5: Output

Use exactly this format:

```
## /ux-check: [skill name]
**Mode:** Shared/Personal | **Score: X/12** (or X/4)

| # | Dimension | Score | Finding |
|---|-----------|-------|---------|
| 1 | Frontmatter & discoverability | _/2 | [symbol] [short finding] |
| 2 | Onboarding | _/2 | [symbol] [short finding] |
| 3 | User control | _/2 | [symbol] [short finding] |
| 4 | System status | _/2 | [symbol] [short finding] |
| 5 | Token efficiency | _/2 | [symbol] [short finding] |
| 6 | Degrees of freedom | _/2 | [symbol] [short finding] |

[If referenced files were capped: "N referenced files found, 5 evaluated."]

## Top 3 suggestions
1. [Most impactful improvement]
2. [Second]
3. [Third]
```

Symbols: 2 = check, 1 = tilde, 0 = cross.

In personal mode, mark dimensions 1-4 rows with "(optional)" after the finding.

Keep findings to one sentence each. Keep suggestions specific and actionable — say what to add or change, not abstract advice.
