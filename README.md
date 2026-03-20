![GitHub Repo stars](https://img.shields.io/github/stars/michalatt/claude-skills?style=social)

# claude-skills

My workspace for Claude Code skills. Currently includes: /challenge for critical thinking, /ux-check for skill UX audits

---

## challenge

Claude is built to help — which means it tends to agree.

This skill gives it a reason to push back. Type `/challenge` at any decision point and Claude picks the hardest relevant question from a curated bank and answers it honestly.

<img width="769" height="284" alt="image" src="https://github.com/user-attachments/assets/12bfaca1-31a0-45e3-83da-8510faeb8b4e" />


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

Skills are the new UI — but most skill authors focus on "does it work?" and skip "is it clear to the user?". Type `/ux-check` and it reads your skill, scores it on 6 UX dimensions, and tells you exactly what to fix.

Scores on: discoverability, onboarding, user control, system status, token efficiency, and degrees of freedom. Top 3 actionable suggestions included.

<img width="741" height="510" alt="image" src="https://github.com/user-attachments/assets/0c7f64d4-6280-4f90-832a-a612f7a13a7d" />


Works in two modes: **shared** (scores all 6, out of 12) and **personal** (scores efficiency + flexibility only, out of 4).

**How to install:**

Copy `skills/ux-check/SKILL.md` into your project under `.claude/skills/ux-check/SKILL.md`

**How to use:**

Type `/ux-check` to see a list of installed skills, or `/ux-check [skill-name]` to check a specific one.
