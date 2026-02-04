# CLAUDE.md

This file provides guidance to Claude Code when working across the NSNodes organization repositories.

## Organization Overview

NSNodes aggregates Network State ecosystem data—events, social posts, newsletters—into a unified platform at [nsnodes.com](https://nsnodes.com). The architecture follows a collector → database → frontend pattern.

## Repository Map

### Platform (Frontend)

| Repo | Tech | Purpose |
|------|------|---------|
| `nsnodes-interface/` | Next.js 15, React 19, Tailwind v4 | Main web app at nsnodes.com |

### Data Collectors (Feed into Supabase)

| Repo | Tech | Purpose | Schedule |
|------|------|---------|----------|
| `events/` | Node.js, Playwright | Scrapes Luma.com, Sola.day events | GitHub Actions (polling/daily/weekly) |
| `x-sync/` | TypeScript | Collects tweets from ~95 tracked accounts | Scheduled via scripts |
| `farcaster-sync/` | TypeScript | Collects Farcaster casts | Scheduled |
| `newsletters-sync/` | Python | Fetches Substack/Paragraph posts | Cron on Hetzner (bi-hourly) |

### Analysis & Content Generation

| Repo | Tech | Purpose |
|------|------|---------|
| `digest/` | Shell + Claude | Generates weekly Nodes Digest newsletter |
| `social-gdp/` | TypeScript + Python | GDP-style metrics for social graphs |
| `balaji_x_topics/` | Static | Topic analysis visualization |

## Data Flow

```
┌─────────────────────────────────────────────────────────────┐
│                     DATA COLLECTION                         │
├─────────────────────────────────────────────────────────────┤
│  x-sync          → tweets from tracked accounts             │
│  farcaster-sync  → casts from NS community                  │
│  newsletters-sync → articles from 13+ newsletters           │
│  events          → events from Luma, Sola, etc.             │
└──────────────────────────┬──────────────────────────────────┘
                           ▼
                    ┌─────────────┐
                    │  Supabase   │  (Production PostgreSQL)
                    │  (shared)   │
                    └──────┬──────┘
                           │
          ┌────────────────┼────────────────┐
          ▼                ▼                ▼
   ┌─────────────┐  ┌─────────────┐  ┌─────────────┐
   │  nsnodes-   │  │   digest    │  │ social-gdp  │
   │  interface  │  │  (weekly)   │  │ (analysis)  │
   └─────────────┘  └─────────────┘  └─────────────┘
         │                │
         ▼                ▼
    nsnodes.com    nsnodes.substack.com
```

## Database

All collectors write to a shared **Supabase** instance. Key tables:

- Events from `events/`
- Tweets/posts from `x-sync/`, `farcaster-sync/`
- Newsletter articles from `newsletters-sync/`

Connection requires `SUPABASE_URL` and `SUPABASE_SERVICE_ROLE_KEY` in `.env`.

## Which Repo to Look At

| Task | Repo |
|------|------|
| UI changes, new pages, frontend bugs | `nsnodes-interface/` |
| Event scraping, new event sources | `events/` |
| Twitter/X data collection | `x-sync/` |
| Farcaster data collection | `farcaster-sync/` |
| Newsletter fetching | `newsletters-sync/` |
| Weekly digest generation | `digest/` |
| Social graph analysis | `social-gdp/` |
| Database schema changes | Check migrations in respective repos |

## Common Commands

### nsnodes-interface
```bash
npm run dev      # Dev server (Turbopack)
npm run build    # Production build
npm run lint     # ESLint
```

### events
```bash
npm run luma:events   # Scrape Luma events
npm run sola:events   # Scrape Sola events
npm run list:events   # List all events
```

### digest
```bash
./scripts/fetch-weekly-data.sh          # Pull week's data
./scripts/run-digest.sh -e rigorous     # Generate digest
```

### newsletters-sync
```bash
uv run python fetch_newsletters.py
```

## Environment Setup

Most repos need a `.env` file with Supabase credentials:

```bash
SUPABASE_URL=https://your-project.supabase.co
SUPABASE_SERVICE_ROLE_KEY=your-key
```

Some repos (like `x-sync`) also need platform-specific auth tokens.

## Notes

- The `doc/` folder is local-only (not a git repo)
- Each repo has its own `.git` — these are separate repositories, not a monorepo
- `digest/` pulls from sibling repos for user lists (see its README for paths)
