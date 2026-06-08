# FocusForge — ICSE Boards Study System

A gamified study tool for ICSE Class 10 students.

## 🌐 Live Website
**https://Parth-Theo.github.io/focusforge**

## Features
- ✅ Pomodoro Timer (25/45/60 min) with focus mode overlay
- ✅ Study Assistant (keyword-based ICSE topic help)
- ✅ Custom Test Generator (20/50/100 marks)
- ✅ XP & Gamification (5 levels: CADET → MAJOR)
- ✅ Subject & Chapter Management with priorities and ratings
- ✅ Streak System with multipliers
- ✅ 6 Achievements to unlock
- ✅ Admin Panel for user management
- ✅ 28-day study activity heatmap
- ✅ Backup & Restore (JSON export/import)
- ✅ Per-user state isolation
- ✅ SHA-256 password hashing

## Getting Started

1. Open the website
2. Enter the 6-digit verification code shown on screen
3. On first run, create an Admin account
4. Add subjects and chapters, then start studying!

> **Note:** This is a local profile switcher, not a real authentication system. All data lives in your browser's localStorage. For genuine multi-device sync, a backend would be needed.

## Architecture

| File | Purpose |
|------|---------|
| `index.html` | Markup (loads external CSS/JS) |
| `styles.css` | All styles, with accessibility support |
| `app.js` | Application logic, security helpers |

## Data & Privacy

- All data is stored in `localStorage` per-user (`focusforge-state-<email>`)
- Passwords are SHA-256 hashed before storage
- User-entered text is escaped to prevent XSS
- Use the **Backup** button to download your progress as JSON
- Use **Restore** to re-import from a backup file

## Security Model

This is a **static site with no server**. The login is a convenience profile switcher — it does not provide real security. Anyone with browser access can inspect localStorage. Do not store sensitive data.

## Deploy to GitHub Pages

The site is automatically deployed via GitHub Pages from the `main` branch.
