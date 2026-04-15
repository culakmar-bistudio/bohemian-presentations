# Bohemia Presentations — Handover

## Project Purpose

This repo is a **presentation template system** for Bohemia Interactive. Each presentation is a self-contained HTML slide deck — no frameworks, no build tools, just a single HTML file per deck.

The template visual style (dark theme, Barlow/Barlow Condensed fonts, BI green accent, slide transitions) was extracted from the first presentation built here: the website strategy deck.

---

## Project Structure

```
/
├── website-strategy/          ← First presentation (bohemia.net hub strategy)
│   └── presentation.html
│
├── template/                  ← Template documentation
│   ├── STYLE-GUIDE.md         ← Colors, typography, spacing, effects
│   ├── BRANDING.md            ← How to customize per brand/topic
│   ├── LAYOUTS.md             ← 8 slide layout patterns
│   ├── COMPONENTS.md          ← Reusable UI components
│   └── SLIDE-ENGINE.md        ← Navigation, transitions, how to create new decks
│
├── archive/                   ← Old bohemia.net hub demo files (html pages, images, docs)
│   ├── index.html, dayz.html, arma.html, enfusion.html
│   ├── HANDOVER.md, starting-prompt.md
│   ├── logo-dropdown.png, primary-navigation.png
│   └── fonts/
│
├── HANDOVER.md                ← This file
└── .gitignore
```

**Convention:** Each new presentation lives in its own root-level folder (e.g., `quarterly-review/`, `arma4-reveal/`). Refer to `template/` docs for style, layout, and component guidance.

---

## Git & Deployment — CRITICAL

### GitHub Account

- **Repo:** `https://github.com/culakmar-bistudio/bohemian-presentations`
- **Owner:** `culakmar-bistudio` (Martin Baar)
- **Email:** `95048565+culakmar-bistudio@users.noreply.github.com`

### Vercel Hosting Requirement

**All commits pushed to this repo MUST come from the `culakmar-bistudio` GitHub account. No other author.**

Vercel is connected to the `culakmar-bistudio` GitHub account for deployment. If commits come from any other GitHub identity (different username, different email, bot accounts, or AI tools committing under their own name), Vercel will either fail to deploy or lose its connection to the repo.

Before committing, always verify:
```bash
git config user.name   # must be: culakmar-bistudio
git config user.email  # must be: 95048565+culakmar-bistudio@users.noreply.github.com
```

### Deployment History — Lessons Learned

This repo has been through multiple "clean slate" incidents where all files were deleted by commits made under incorrect git identities. The repo was nuked and recreated from scratch. Key takeaways:

1. **Never commit under a different git user** — always check `git config user.name` and `git config user.email` before any commit
2. **Never force push without checking** — the reflog saved us once, but don't rely on it
3. **The GitHub remote was removed and re-added during recovery** — if `git remote -v` shows no origin, re-add it:
   ```bash
   git remote add origin https://github.com/culakmar-bistudio/bohemian-presentations.git
   ```
4. **Branch protection** should be set up on the repo to prevent accidental force pushes to master

### Current State (2026-04-15)

**Local:** 2 commits on `master`, correct user (`culakmar-bistudio`) on both.

**Remote:** No remote configured. Needs to be re-added before pushing:

```bash
git remote add origin https://github.com/culakmar-bistudio/bohemian-presentations.git
git push -u origin master
```

**Next up:** Iterate on `website-strategy/presentation.html` content, then sync template docs in `template/` to match any structural/style changes discovered during that iteration.
