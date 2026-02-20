# Ecosystem Microsite — Agency Character Select

## What This Is
An interactive microsite that presents a portfolio of 6 agencies as a retro pixel-art "character select" screen — like a fighting game roster. Each agency is a "character" with unique stats, abilities, and client logos. Built as a signature piece for prospective clients and partners.

## The 6 Agencies
1. **Compound** (Red) — The Storyteller — Web3 Content for Founders
2. **Reply Guys** (Yellow) — The Connector — Strategic Replies on X & LinkedIn
3. **Prospr3** (Purple) — The Inventor — Innovation Studio for Experiences
4. **Dreamy** (Blue) — The Architect — UI/UX Studio for the Web
5. **Curator** (Pink) — The Strategist — Cinematic Brand Campaigns
6. **Web3Clipping** (Green) — The Editor — 550+ Clippers Platform

## Architecture
This is currently a static HTML/CSS/JS single-page site served via Express.

```
ecosystem-microsite/
├── public/
│   └── index.html          # The full app — all HTML, CSS, JS in one file
├── server.js                # Express static file server
├── package.json
├── Dockerfile
├── railway.toml
├── .gitignore
└── CLAUDE.md
```

## Layout Structure
- **Top bar**: Title "SELECT YOUR AGENCY" with version and location
- **Left panel** (280px): Brand info, key metrics (custom per agency), 3 abilities (TCG card style), client grid
- **Center stage**: Large pixel sprite on a glowing disc platform, hero name treatment, ambient glow in brand color
- **Bottom bar**: 6 selector cards with face portraits, agency name, class, and number. Clicking selects that agency.

## Key Technical Details
- Pixel art sprites are drawn programmatically on `<canvas>` using `fillRect` — no image assets needed
- Full body sprites (32x48 grid) display on center stage, face portraits (16x16 grid) in the bottom selector bar
- Each agency has a unique accent color that cascades through the entire UI when selected
- Keyboard navigation: arrow keys cycle agencies, 1-6 for quick select
- CRT scanline overlay and pixel grid background for retro feel
- Fonts: Press Start 2P (headings), Silkscreen (labels), Space Mono (body text)

## Design Decisions — DO NOT CHANGE
- Background is near-black (#050508) for maximum contrast and readability
- Text hierarchy: primary (#f0f0f5), secondary (#b8b8d0), dim (#7a7a9a), muted (#3e3e58)
- Stats use real metrics not abstract power bars (e.g. "10M+ Impressions", "550+ Clippers")
- Bottom bar keeps full card layout with face image + name + class (not portrait-only)
- Scanline opacity is subtle (0.02) — enough to feel retro without hurting readability

## Deployment — Railway
- Dockerfile and railway.toml are pre-configured
- Server listens on `process.env.PORT` (Railway sets this automatically)
- No build step needed — it's static files served by Express
- Health check on `/`

## Deploy Commands
```bash
# Initialize git and push to Railway
git init
git add .
git commit -m "Initial: ecosystem microsite v1"

# Option A: Railway CLI
railway login
railway init
railway up

# Option B: Connect GitHub repo in Railway dashboard
# Push to GitHub, then link in Railway → New Project → Deploy from GitHub
```

## Future Enhancements (not for this deploy)
- Replace programmatic pixel sprites with hand-drawn pixel art PNGs from a commissioned artist
- Add Sanity CMS for modular brand/case study management
- Add click-through to individual brand deep-dive pages with case studies
- Add sound effects on character selection
- Add idle sprite animations
- Migrate to Next.js when CMS integration is needed
