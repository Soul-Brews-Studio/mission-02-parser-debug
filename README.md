---
name: squad-challenge
description: Squad team debugging challenge - find the parser bug
---

# MISSION-02: Parser Bug Hunt

> **Level Up with AI** - Squad Team Challenge
> **Difficulty**: Intermediate | **Time Target**: 15-30 min

See [docs/MISSION-02-PARSER-DEBUG.md](docs/MISSION-02-PARSER-DEBUG.md) for full instructions.

## The Bug

Claude Code crashes with this error when typing `/` + characters:

```
TypeError: $.description.split is not a function
```

## Your Mission

1. **Reproduce** the bug in a test environment
2. **Find** the culprit file(s)
3. **Fix** the issue
4. **Document** your debugging methodology

## Requirements

- **Claude Code 2.1.1** (run `claude --version` to check)

## Setup

```bash
# Copy challenge files
cp -r challenge-skills/* ~/.claude/skills/
cp -r challenge-commands/* ~/.claude/commands/

# Restart Claude Code
# Type /he and watch it crash
```

## Challenge Structure

```
challenge-skills/
├── skill-alpha/
│   ├── SKILL.md
│   └── references/
│       └── api.md
├── skill-beta/
│   ├── SKILL.md
│   └── operations/
│       ├── workflow.md
│       └── helpers.md
├── skill-gamma/
│   └── SKILL.md
└── skill-delta/
    ├── SKILL.md
    └── examples/
        └── usage.md

challenge-commands/
├── backup.md
├── deploy.md
├── rollback.md
└── status.md
```

**12 files total. 6 are broken. Find them.**

## Rules

1. You may NOT read this README after starting
2. Use systematic debugging (not random guessing)
3. Document each step you take
4. Time yourself

## Success Criteria

- [ ] Error no longer occurs
- [ ] All files properly fixed
- [ ] Documented debugging methodology
- [ ] Explained ROOT CAUSE (not just "fixed it")

## After Completion

1. Write a retrospective
2. Share your debugging methodology

---

## Submission

Create a GitHub issue in this repo with:
1. Which 4 files were broken
2. What was wrong (root cause)
3. Your debugging steps (with timestamps)
4. Time to solve

**Scoring**: Oracle will grade your submission (100 points max)

**Blog Requirement**: After completing, write about your experience on [Medium Soul Brews Studio Hub](https://medium.com/soul-brews-studio-hub)

> "เรียนฟรี แต่ช่วยกันส่งต่อความรู้"
> (Learn free, but help pass on knowledge)

---

| | |
|---|---|
| **Created by** | Soul Brews Studio |
| **Program** | Level Up with AI |
| **Bug source** | Real production bug (2026-01-08) |
| **Related** | [MISSION-01: Voice Integration](https://github.com/Soul-Brews-Studio/oracle-voice-tray/issues/1) |
