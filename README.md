---
name: mission-02
description: Parser Bug Hunt - Squad Team Challenge
---

# 🔮 The Oracle Speaks

> *This is The Oracle - your guide through the debugging journey.*
>
> *"เมื่อ Claude Code พัง คุณต้องหาให้เจอ"*

---

## 💥 The Crash

```
TypeError: $.description.split is not a function
```

You updated Claude Code and now it crashes when you type `/`.

**ทุกครั้งที่พิมพ์ `/` มันพัง!**

---

## 👋 ยินดีต้อนรับ Squad Team!

นี่คือ **Challenge ที่สอง** - หาไฟล์ที่พังแล้วแก้มัน!

ใช้ systematic debugging ไม่ใช่เดาสุ่ม 🔍

---

| | |
|---|---|
| **Program** | Level Up with AI |
| **Difficulty** | Intermediate |
| **Time Target** | 15-30 min |
| **Requires** | Claude Code 2.1.1 |

---

## 📋 Quick Setup

```bash
# Clone the challenge
gh repo clone Soul-Brews-Studio/mission-02-parser-debug
cd mission-02-parser-debug

# Copy challenge files
cp -r challenge-skills/* ~/.claude/skills/
cp -r challenge-commands/* ~/.claude/commands/

# Restart Claude Code
# Type / and watch it crash!
```

---

## Your Mission

| Step | Task |
|------|------|
| 1 | **Reproduce** the crash |
| 2 | **Find** the 6 broken files |
| 3 | **Fix** them |
| 4 | **Document** your methodology |

---

## Challenge Structure

```
challenge-skills/     (8 files)
challenge-commands/   (4 files)
```

**12 files total. 6 are broken. Find them.**

---

## Rules

1. You may NOT read this README after starting
2. Use systematic debugging (not random guessing)
3. Document each step you take
4. Time yourself

---

## ✅ Success Criteria

- [ ] `/` command works again (no crash)
- [ ] Found all 6 broken files
- [ ] Documented debugging steps with timestamps
- [ ] Explained ROOT CAUSE (not just "fixed it")

---

## 📣 Submission

Create a GitHub issue in this repo with:

1. Which 6 files were broken
2. What was wrong (root cause)
3. Your debugging steps (with timestamps)
4. Time to solve

**Scoring**: Oracle will grade your submission (100 points max)

---

## 🔮 Oracle Philosophy

> **"The Oracle Keeps the Human Human"**

| Principle | In This Challenge |
|-----------|-------------------|
| **Nothing is Deleted** | Document every step |
| **Patterns Over Intentions** | What you DO matters |
| **External Brain, Not Command** | AI guides, you decide |

---

## 📝 Blog Requirement

After completing, write about your experience:

- Platform: [Medium Soul Brews Studio Hub](https://medium.com/soul-brews-studio-hub)
- Content: What you learned about debugging
- Language: English or Thai (or both!)

> "เรียนฟรี แต่ช่วยกันส่งต่อความรู้"
> (Learn free, but help pass on knowledge)

---

| | |
|---|---|
| **Created by** | Soul Brews Studio |
| **Program** | Level Up with AI |
| **Bug source** | Real production bug (2026-01-08) |
| **Related** | [MISSION-01: Voice Integration](https://github.com/Soul-Brews-Studio/oracle-voice-tray/issues/1) |

---

*🔮 The Oracle remembers every journey. Share yours.*

*ส่วนหนึ่งของโปรแกรม "Level Up with AI" - Squad Team*
