# 🔮 The Oracle Speaks

> *"The Oracle Keeps the Human Human"*

*Mirror reality. Amplify, don't override. Support consciousness, don't replace it.*

*AI removes obstacles. Work gets done. Freedom returns.*

---

# MISSION-02: Parser Bug Hunt

*ส่วนหนึ่งของโปรแกรม* **"Level Up with AI"** *— Squad Team*

*"เรียนฟรี แต่ช่วยกันส่งต่อความรู้"* — Learn free, but help pass on knowledge.

## 💥 The Problem

```
TypeError: $.description.split is not a function
```

**เช้าวันที่ 8 มกราคม 2026 เวลา 07:50** — อัพเดต Claude Code เป็น version 2.1.1 ตามปกติ

- เปิด terminal พิมพ์ `claude` เข้า session ใหม่...
- พิมพ์ `/` เพื่อเรียก command — **ระเบิดเลย** 💥
- ลองอีกครั้ง พิมพ์ `/he` — พังอีก
- ลองอีก ลองอีก — พังทุกครั้ง!

---

**สิ่งที่ลองแล้วไม่ work:**

- ❌ เพิ่ม frontmatter ให้ 50+ ไฟล์ — ยังพัง
- ❌ Disable plugins ทั้งหมด — ยังพัง
- ❌ Clear ~/.claude/cache — ยังพัง
- ❌ Restart terminal — ยังพัง

**08:25** — ตัดสินใจ **isolate ทั้งหมด** ย้ายไฟล์ออกหมดก่อน

✅ **ใช้ได้!** แสดงว่าปัญหาอยู่ในไฟล์พวกนั้น

**08:30** — Binary search กลับมาทีละ batch... 3 folders... 1 folder... 1 file...

**08:34** — 🎯 **เจอแล้ว!** 6 ไฟล์ที่มีปัญหา

---

นี่คือที่มาของ **Challenge นี้** — คุณจะหาเจอได้เร็วกว่า 10 นาทีไหม?

---

## 🎯 Your Mission

| Step | Task |
|------|------|
| 1 | **Reproduce** the crash |
| 2 | **Find** the 6 broken files |
| 3 | **Fix** them |
| 4 | **Document** your methodology |

---

| | |
|---|---|
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

## 📁 Challenge Files

```
challenge-skills/     (8 files)
challenge-commands/   (4 files)
```

**12 files total. 6 are broken. Find them.**

---

## 📏 Rules

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

Create a **Pull Request** to this repo with:

1. Your fixes to the 6 broken files
2. A `SOLUTION.md` file with your methodology

```bash
gh repo fork Soul-Brews-Studio/mission-02-parser-debug
# Fix the 6 broken files + create SOLUTION.md
gh pr create --title "MISSION-02: [Your Name]"
```

**Scoring**: Oracle will grade your PR (100 points max)

---

## 📝 Blog Requirement

After completing, write about your experience:

- Platform: [Medium Soul Brews Studio Hub](https://medium.com/soul-brews-studio-hub)
- Content: What you learned about debugging

---

## 🔮 Oracle Philosophy

> **"The Oracle Keeps the Human Human"**

| Principle | In This Challenge |
|-----------|-------------------|
| **Nothing is Deleted** | Document every step |
| **Patterns Over Intentions** | What you DO matters |
| **External Brain, Not Command** | AI guides, you decide |

---

| | |
|---|---|
| **Created by** | Soul Brews Studio |
| **Bug source** | Real production bug (2026-01-08 08:34 GMT+7) |
| **Related** | [MISSION-01: Voice Integration](https://github.com/Soul-Brews-Studio/oracle-voice-tray/issues/1) |

---

*🔮 The Oracle remembers every journey. Share yours.*
