![GitHub Repo stars](https://img.shields.io/github/stars/michalatt/claude-skills?style=social)

# claude-skills

My workspace for Claude Code skills. Currently includes: /challenge for critical thinking, /ux-check for skill UX audits

---

## challenge

Claude is built to help — which means it tends to agree.

This skill gives it a reason to push back. Type `/challenge` at any decision point and Claude picks the hardest relevant question from a curated bank and answers it honestly.

<img width="639" height="267" alt="image" src="https://github.com/user-attachments/assets/528d15f8-6aca-4f32-905d-20423812570e" />

**Questions it picks from:**
- What's the simplest version of this?
- What am I not asking that I should be?
- What would someone who disagrees say?
- Explain it like I need to decide, not understand
- What would you do differently if you started over?

**Custom questions:** Add a `custom-questions.md` file next to `SKILL.md` with project-specific questions. Same format — question + when to pick it. The built-in 5 always stay.

**How to install:**

Copy `skills/challenge/SKILL.md` into your project under `.claude/skills/challenge/SKILL.md`

**How to use:**

Simply type /challenge in your Claude Code terminal.

---

## ux-check

Audit any Claude Code skill for UX quality. Scores it on 6 dimensions — discoverability, onboarding, user control, system status, token efficiency, and degrees of freedom — then gives the top 3 actionable suggestions.

Works in two modes: **shared** (scores all 6, out of 12) and **personal** (scores efficiency + flexibility only, out of 4).

**How to install:**

Copy `skills/ux-check/SKILL.md` into your project under `.claude/skills/ux-check/SKILL.md`

**How to use:**

Type `/ux-check` to see a list of installed skills, or `/ux-check [skill-name]` to check a specific one.
