# CLAUDE.md — Project Guide

Context file for Claude Code sessions in this repo. Read this before making changes.

## What this project is

A landing page for **Infinity Automation Group (IAG)** — Joe's AI agent business
(early-stage; he also runs a real estate wholesaling/fix & flip operation, documented
in `about-me.md`, but THIS repo is the AI business — treat them as separate contexts).

The site sells custom AI agents and automations to small/mid-size businesses:
voice/chat agents, workflow automation, lead generation, content AI.

## About the owner (critical)

- **Joe does not code and does not want to learn.** Never hand him code to run or
  steps that require a terminal. Do the work end-to-end: edit, verify, commit, push.
- **Minimize permission prompts.** He explicitly asked not to be asked for permission
  except when truly necessary.
- **Communication style** (from `about-me.md`): short, direct, plain English. No hype,
  no jargon, no fluff. Lead with the bottom line. Cut every word that doesn't carry signal.
- **Verify visually.** After changing the page, render it in a headless browser and send
  him a screenshot — that's how he reviews work (see "How to verify" below).
- Contact email everywhere on the site: **joe.snow03@gmail.com**

## Branding rules

- Full company name: **Infinity Automation Group**
- **Use the full name ONLY in the site header/nav logo** (and the legal copyright line
  in the footer). Everywhere else abbreviate to **IAG** or **Infinity**.
- Tagline: **"Where the possibilities are endless"** — currently in the hero badge pill,
  footer description, and footer bottom line.
- Logo mark: an **∞ symbol** on an orange gradient rounded square.
- Earlier placeholder name was "Emberline" — if any trace of it ever reappears, remove it.

## Folder structure

```
/
├── index.html     # The entire website — HTML, CSS, and JS in one self-contained file
├── README.md      # Non-coder instructions: how to view, publish (GitHub Pages), customize
├── about-me.md    # Joe's bio, working style, and instructions for Claude (uploaded by Joe)
└── CLAUDE.md      # This file
```

**Everything is intentionally in one `index.html` file** — no build tools, no frameworks,
no dependencies, no npm. Keep it that way unless Joe asks otherwise. The page must work
by double-clicking the file or hosting it as a static file (GitHub Pages).

## Design system (in `:root` CSS variables at the top of index.html)

**Theme: dark background with warm orange accents** — Joe's explicit choice.

- Background: `--bg: #100c08` (near-black warm brown), `--bg-soft: #181210` for
  alternating sections, `--bg-card: #1f1813` / `--bg-card-2: #261d16` for cards
- Accent: `--orange: #ff8c3b`, `--orange-soft: #ffb077`, `--orange-deep: #e06a1b`,
  with `--ember` (12% orange) for subtle fills and `--line` (14% orange) for borders
- Text: `--text: #f7f1ea` (warm white), `--text-dim: #b8aa9c`, `--text-faint: #8a7d70`
- Success/live indicators: `--green: #4ade80`

**Fonts** (Google Fonts):
- **Inter** (400–800) — all body text and headings
- **Fraunces** (600, italic) — used via `.serif` / `em` for italic accent words inside
  headlines (e.g., "Run *With* Your Business") and the big step numbers

**Layout patterns:**
- Max content width 1180px (`.container`)
- Sticky blurred header
- Hero: two columns — text left, animated "agent dashboard" mockup right with white
  floating stat cards (modeled on reference screenshots Joe liked: Auteron/Quantilus style)
- Alternating section backgrounds (`section` / `.section-soft`)
- Cards with hover lift, orange-tinted borders, 16–24px radius
- Scroll-triggered fade-in via `.reveal` class + IntersectionObserver (the only JS)
- Fully responsive; nav links hide on mobile

## Page sections (top to bottom)

1. **Header/nav** — full company name + ∞ logo, anchor links, CTA button
2. **Hero** — tagline pill, headline, subtext, two CTAs, trust badges, dashboard mockup
   (`#` top)
3. **Services** (`#services`) — 6 cards: Voice & Chat Agents, Workflow Automation,
   Lead Generation & Sales, Content & Marketing AI, Custom AI Systems, Managed & Monitored
4. **How It Works** (`#how`) — 4 numbered steps: Discovery Call → Automation Audit →
   Build & Launch → Manage & Improve
5. **Results** (`#results`) — 4 big stats (30+ hrs saved, 3× faster response, 24/7, 40% costs)
6. **Industries** (`#industries`) — 8 use-case tiles (home services, clinics, real estate,
   professional services, e-commerce, contractors, agencies, startups)
7. **Testimonials** — 3 quote cards (placeholder clients)
8. **FAQ** (`#faq`) — 6 native `<details>` accordions
9. **CTA** (`#contact`) — discovery-call box, mailto button to joe.snow03@gmail.com
10. **Footer** — IAG logo, link columns, copyright with full legal name

## Git workflow

- Work happens on branch `claude/eloquent-pasteur-1f2sms` (or whatever branch the
  session designates). Joe sometimes uploads files via the GitHub web UI directly to
  the branch — **always `git pull --rebase` before pushing.**
- Commit and push without asking; Joe expects completed work, not proposals.
- Don't create pull requests unless asked.

## How to verify changes

Render the page headless and send Joe screenshots (he reviews visually, not in code):

```bash
# Playwright is installed in /tmp (package.json + node_modules); script at /tmp/shot.js
# uses the cached browser at:
#   /opt/pw-browsers/chromium_headless_shell-1194/chrome-linux/headless_shell
# (npx playwright install fails in this sandbox — use the cached executable path)
cd /tmp && node shot.js   # writes /tmp/hero.png and /tmp/fullpage.png
```

Note: `/tmp` is wiped between sessions — recreate the script from this recipe if missing.

## Content placeholders still to replace (ask Joe when relevant)

- Testimonials are fictional placeholders (Marcus J., Sarah L., David R.)
- Stats in the Results section are aspirational, not measured
- No real domain yet; contact is a personal Gmail
- `about-me.md` could feed a future "About" section — Joe hasn't asked for one yet
