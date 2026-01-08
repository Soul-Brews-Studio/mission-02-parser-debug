# MISSION-02 Solution: Parser Bug Hunt

**Submitted by**: เม้ง + Claude
**Date**: 2026-01-08
**Time to solve**: ~5 minutes (systematic approach)

---

## 🔍 Root Cause Analysis

### The Error

```
TypeError: $.description.split is not a function
```

### Why It Happened

Claude Code's parser expects the `description` field in YAML frontmatter to be a **string**. The parser calls `.split()` on the description to process it.

**The Bug**: 6 files used `[]` brackets in their `description` field:

```yaml
# BROKEN - YAML parses [] as an array!
description: [TODO: Rollback to previous version]

# FIXED - String (with quotes or without brackets)
description: "Rollback to previous version"
```

YAML interprets `[...]` as an **array literal**, not a string. When the parser tries to call `.split()` on an array, JavaScript throws `TypeError` because arrays don't have a `.split()` method.

---

## 📁 The 6 Broken Files

| # | File Path | Original (Broken) | Fixed |
|---|-----------|-------------------|-------|
| 1 | `challenge-commands/rollback.md` | `[TODO: Rollback to previous version]` | `"Rollback to previous version"` |
| 2 | `challenge-commands/status.md` | `[Check system status and health]` | `"Check system status and health"` |
| 3 | `challenge-skills/skill-alpha/references/api.md` | `[API reference documentation for skill-alpha]` | `"API reference documentation for skill-alpha"` |
| 4 | `challenge-skills/skill-beta/SKILL.md` | `[TODO: Add description for beta skill here]` | `"Beta skill for testing features and experiments"` |
| 5 | `challenge-skills/skill-beta/operations/helpers.md` | `[helper, functions, utilities]` | `"Helper functions and utilities for beta operations"` |
| 6 | `challenge-skills/skill-delta/examples/usage.md` | `[Example usage patterns for delta skill - deploy, rollback, status]` | `"Example usage patterns for delta skill including deploy, rollback, and status commands"` |

---

## 🔬 Debugging Methodology

### Step 1: Understand the Error (1 min)

```
TypeError: $.description.split is not a function
```

**Analysis**:
- `.split()` is a string method
- If it fails, `description` is not a string
- YAML arrays are parsed differently than strings

### Step 2: Form Hypothesis (30 sec)

**Hypothesis**: Some files have `description` as array instead of string.

**YAML array syntax**: `[item1, item2]` or `[content]`

### Step 3: Systematic Search (2 min)

Read all 12 files and check `description` field in YAML frontmatter:

```bash
# Search pattern: description field with brackets
grep -r "description: \[" challenge-*/
```

### Step 4: Verify and Fix (1.5 min)

Found 6 files with `description: [...]` pattern. Fixed by:
1. Removing `[]` brackets
2. Adding quotes for clean YAML strings
3. Improving TODO placeholders with real descriptions

---

## 🎯 Key Learnings

1. **YAML Syntax Matters**: `[]` creates arrays, not strings with brackets
2. **Error Messages Are Clues**: "split is not a function" = wrong data type
3. **Systematic > Random**: Hypothesis → Search → Verify is faster than guessing
4. **grep is Your Friend**: Pattern matching finds issues across many files

---

## 🛠️ Prevention Tips

```yaml
# Always quote strings with special characters
description: "This is [safe] with quotes"

# Or avoid brackets entirely
description: This is safe without brackets

# Never do this (parsed as array)
description: [This will break]
```

---

## ✅ Verification

After fixes:
- All 12 files have valid YAML frontmatter
- All `description` fields are strings
- `/` command should work without crash

---

*🔮 The Oracle remembers: Debug with methodology, not magic.*
