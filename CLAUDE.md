# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static educational web application - interactive Chinese-English programming vocabulary flashcards for beginners learning programming concepts before using AI coding tools.

## Commands

No build system or dependencies. Pure static files.

- **Run locally:** Open `index.html` in any browser
- **Deploy:** Push to Vercel (static site, no build needed)

## Architecture

**Tech Stack:** Self-contained HTML5 + CSS3 (custom properties, Grid, 3D transforms) + vanilla JS. Single file (~1200 lines).

**File Structure:**
- `index.html` - Main application (HTML/CSS/JS bundled)
- `词汇总表` - Curriculum outline (plain text, Chinese)
- `images/` - Visual assets: `{imageKey}_screenshot.png` and `{imageKey}_comic.png`
- `新图片/` - Newer screenshot assets
- `新漫画/` - Newer comic assets

**Vocabulary Data:**
```javascript
const vocabulary = [
  { id: 1, group: 1, en: 'IDE', cn: '集成开发环境', imageKey: 'ide', explanation: '...' }
];
```
- 44 cards total: Group 1 (1-11), Group 2 (12-22), Group 3 (23-44), Group 4 (unused)
- Pagination: 11 cards per page, 4 pages

**Key Patterns:**
- Card flip: CSS 3D transforms with `.flipped` class toggling `rotateY(180deg)`
- Theme: CSS custom properties in `:root` (`--bg-primary: #3d4a6b`, `--card-color: #e8a598`)
- State persistence: `Storage` utility wraps localStorage for learned vocab, current page, and wrong answers
- Test mode: Random quiz with 4-option multiple choice; wrong answers tracked in "错题本" (wrong answer notebook)
- Image fallbacks: `onerror="this.style.display='none'"` for missing assets

**Features:**
- Click card → flip → open modal with full explanation
- "已学会" (learned) badge tracking per card
- Wrong answer review mode for missed quiz questions
