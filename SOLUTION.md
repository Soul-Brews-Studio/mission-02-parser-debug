# SOLUTION: MISSION-02 Parser Bug Hunt

**Submitted by:** BoBoatYogi (with Claude Opus 4.5)
**Date:** 2026-01-08
**Time to solve:** ~5 minutes

---

## Root Cause

**Error:** `TypeError: $.description.split is not a function`

**Root Cause:** YAML frontmatter `description: [text]` is parsed as an **array**, not a string.

In YAML:
- `description: text` → string
- `description: "text"` → string (explicit)
- `description: [text]` → **array with one element** (bug!)

When Claude Code's parser calls `description.split()`, it fails because `.split()` is a string method, not available on arrays.

---

## Methodology

### Step 1: Understand the Error (12:11:00)

```
TypeError: $.description.split is not a function
```

Key insight: `.split()` is a string method. If it fails, `description` is NOT a string.

### Step 2: Targeted Search (12:11:30)

```bash
grep -r "description:" --include="*.md" | grep "\["
```

Found pattern: `description: [...]` — square brackets in YAML = array!

### Step 3: Identify All Broken Files (12:12:00)

Read all 12 markdown files in parallel to confirm 6 broken ones.

### Step 4: Apply Fix (12:14:00)

```yaml
# Before (BROKEN - parsed as array)
description: [Some text here]

# After (FIXED - parsed as string)
description: "Some text here"
```

### Step 5: Verify (12:15:00)

```bash
grep -r "description: \[" --include="*.md" | wc -l
# Result: 0 (no more YAML arrays)
```

---

## The 6 Broken Files

| # | File | Original (Broken) | Fixed |
|---|------|-------------------|-------|
| 1 | `challenge-commands/rollback.md` | `[TODO: Rollback to previous version]` | `"TODO: Rollback to previous version"` |
| 2 | `challenge-commands/status.md` | `[Check system status and health]` | `"Check system status and health"` |
| 3 | `challenge-skills/skill-alpha/references/api.md` | `[API reference documentation for skill-alpha]` | `"API reference documentation for skill-alpha"` |
| 4 | `challenge-skills/skill-beta/SKILL.md` | `[TODO: Add description for beta skill here]` | `"TODO: Add description for beta skill here"` |
| 5 | `challenge-skills/skill-beta/operations/helpers.md` | `[helper, functions, utilities]` | `"helper, functions, utilities"` |
| 6 | `challenge-skills/skill-delta/examples/usage.md` | `[Example usage patterns for delta skill - deploy, rollback, status]` | `"Example usage patterns for delta skill - deploy, rollback, status"` |

---

## Key Lessons

### 1. Error Messages Tell You the Type Mismatch

`X.split is not a function` = X is not a string. Check what X actually is.

### 2. YAML Syntax Matters

- `[item1, item2]` = array
- `"[item1, item2]"` = string with brackets
- `item1, item2` = string (commas are just text)

### 3. Grep Before Reading

Instead of opening every file, use `grep` to filter candidates first.

### 4. Binary Search for "One of N Files"

When you know "one of these files is broken":
1. Remove all → test → works?
2. Add half back → test → crashes?
3. Narrow down to affected half
4. Repeat until found

---

## Prevention

For teams writing YAML frontmatter:

1. **Lint your markdown** - Use a YAML validator
2. **Avoid brackets** - Unless you want an array
3. **Use quotes** - When in doubt, quote your strings
4. **Test after creation** - Run the parser on new files

---

🤖 Generated with [Claude Code](https://claude.com/claude-code)

Co-Authored-By: Claude Opus 4.5 <noreply@anthropic.com>
