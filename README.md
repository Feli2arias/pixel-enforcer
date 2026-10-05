# pixel-enforcer

> A Claude Code skill that bans hardcoded values from UI code and enforces design token usage.

![Claude Code](https://img.shields.io/badge/Claude_Code-skill-blue)
![License](https://img.shields.io/badge/license-MIT-green)

---

## The Problem

Claude drops hex colors, magic numbers, and inline styles directly into components.

The result: a UI that's impossible to theme, inconsistent across screens, and a nightmare to maintain. Change the brand color? Update it in 47 different places.

---

## Before / After

**Without pixel-enforcer**
```css
.button {
  background-color: #3b82f6;
  padding: 12px 20px;
  border-radius: 6px;
  font-size: 14px;
  box-shadow: 0 1px 3px rgba(0,0,0,0.12);
}
```

**With pixel-enforcer**
```css
.button {
  background-color: var(--color-primary);
  padding: var(--spacing-3) var(--spacing-5);
  border-radius: var(--radius-md);
  font-size: var(--text-sm);
  box-shadow: var(--shadow-sm);
}
```

---

## Install

**Personal install** (available in every project):

```bash
mkdir -p ~/.claude/skills/pixel-enforcer
curl -fsSL -o ~/.claude/skills/pixel-enforcer/SKILL.md \
  https://raw.githubusercontent.com/Feli2arias/pixel-enforcer/main/SKILL.md
```

**Project install** (shared with your team via the repo): run the same commands from the project root, replacing `~/.claude/skills` with `.claude/skills`.

Start a new Claude Code session so the skill is picked up. Claude loads it automatically when the task matches its description, or you can invoke it manually with `/pixel-enforcer`.

---

## What It Enforces

| Rule | Why |
|------|-----|
| No hex/rgb/hsl values in component files | Global theming requires variables |
| No arbitrary spacing — use the 4-point scale | Consistent spatial rhythm |
| No inline styles with hardcoded values | Bypasses the design system |
| Dark mode variables defined alongside light mode | Theming from day one |
| New tokens go in the token file first | Single source of truth |

---

## What It Doesn't Change

Visual quality and design precision are never compromised.

---

## License

MIT
