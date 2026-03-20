![GitHub Repo stars](https://img.shields.io/github/stars/michalatt/claude-skills?style=social)

# claude-skills

My workspace for Claude Code skills. Currently includes: /challenge for critical thinking

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
