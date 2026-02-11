<div align="center">

```
                        _
 _ __  ___ _ __   ___  __| | ___  ___
| '_ \/ __| '_ \ / _ \/ _` |/ _ \/ __|
| | | \__ \ | | | (_) | (_| |  __/\__ \
|_| |_|___/_| |_|\___/ \__,_|\___||___/
```

### The ultimate hub for Network State events, jobs, content creators, VCs, and tooling.

**Built for the decentralized future.**

[![Website](https://img.shields.io/badge/Website-nsnodes.com-blue?style=for-the-badge)](https://nsnodes.com)
[![Telegram](https://img.shields.io/badge/Telegram-Join%20Community-26A5E4?style=for-the-badge&logo=telegram)](https://t.me/+RwyXfj5VsXk2NmE1)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)

</div>

---

## What is nsnodes?

nsnodes is your one-stop destination for everything in the **Network State ecosystem**. We aggregate and organize the resources, opportunities, and communities shaping the decentralized future.

> *"Sovereignty starts with a shared idea."*

## Features

| Feature | Description |
|---------|-------------|
| **Events Dashboard** | Real-time Network State events, conferences, and meetups worldwide |
| **Jobs Board** | Opportunities in the Network State ecosystem—full-time, contract, and volunteer |
| **Content Creators** | Thought leaders, podcasters, and influencers shaping the movement |
| **VC Directory** | Crypto-native venture capital firms and their investment thesis |
| **Societies Database** | Network State societies, DAOs, and governance experiments |
| **Open Source Tooling** | GitHub repos and tools building the ecosystem infrastructure |
| **Community Hubs** | Dedicated pages for Argentina, Edge City, Network School & more |

## Tech Stack

<div align="center">

![Next.js](https://img.shields.io/badge/Next.js_15-black?style=flat-square&logo=next.js)
![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel)

</div>

## Repositories

### Platform

| Repository | Description |
|------------|-------------|
| [**nsnodes-interface**](https://github.com/nsnodes/nsnodes-interface) | Main web application — the nsnodes platform |

### Data Collection

| Repository | Description |
|------------|-------------|
| [**events**](https://github.com/nsnodes/events) | Event aggregation from Luma.com, Sola.day, and other sources |
| [**x-sync**](https://github.com/nsnodes/x-sync) | X/Twitter data collection for tracked Network State accounts |
| [**farcaster-sync**](https://github.com/nsnodes/farcaster-sync) | Farcaster cast collection from the NS community |
| [**newsletters-sync**](https://github.com/nsnodes/newsletters-sync) | Substack and Paragraph newsletter fetcher |

### Analysis & Content

| Repository | Description |
|------------|-------------|
| [**digest**](https://github.com/nsnodes/digest) | Weekly [Nodes Digest](https://nsnodes.substack.com) newsletter generator |
| [**social-gdp**](https://github.com/nsnodes/social-gdp) | Social graph GDP analysis for Farcaster and X/Twitter |
| [**balaji_x_topics**](https://github.com/nsnodes/balaji_x_topics) | Topic analysis of Balaji's Twitter discourse |

### Architecture

```
Data Collection          Database          Frontend
─────────────────        ────────          ────────
x-sync ─────────┐
farcaster-sync ─┼───▶ Supabase ───▶ nsnodes-interface
newsletters-sync┤                         │
events ─────────┘                         ▼
                                    digest (weekly)
social-gdp ─────▶ Analysis ◀────────────┘
```

## Get Involved

We're building in public and welcome contributions from the community.

- **Explore** → [nsnodes.com](https://nsnodes.com)
- **Join the conversation** → [Telegram](https://t.me/+RwyXfj5VsXk2NmE1)
- **Contribute** → Fork it, improve it, ship it

## License

All projects are released under the [MIT License](LICENSE) unless otherwise specified.

---

<div align="center">

**Building the infrastructure for the decentralized future**

</div>
