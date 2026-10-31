<div align="center">

<!-- Logo -->
<img src="public/bo-creation-logo.png" alt="BO Creation" width="120" />

# Personal Portfolio — Oussema Bouchahwa

**Full-stack engineer · Visual director · Sfax, Tunisia**

[![Next.js](https://img.shields.io/badge/Next.js-16.3.4-black?logo=next.js&logoColor=white)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-v4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Supabase-4169E1?logo=postgresql&logoColor=white)](https://supabase.com/)
[![Prisma](https://img.shields.io/badge/Prisma-6-2D3748?logo=prisma&logoColor=white)](https://www.prisma.io/)
[![Cloudinary](https://img.shields.io/badge/Cloudinary-Media_CDN-3448C5?logo=cloudinary&logoColor=white)](https://cloudinary.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

</div>

---

## Overview

This is my personal portfolio site — built to show engineering work alongside visual production.  
No template. Designed from scratch around a dark cinematic aesthetic, custom CMS, and a Cloudinary-backed media vault.

**Stack:** Next.js 16 (App Router) · PostgreSQL + Prisma · Tailwind CSS v4 · Framer Motion + GSAP · Cloudinary

---

## Screenshots

> _Screenshots below show the live site. Replace with actual captures after local setup._

| Section | Preview |
|---------|---------|
| **Hero** | Full-screen dark entry with grain overlay, ambient cursor glow, GSAP split-text reveal |
| **Work** | Project grid with Cloudinary images, live tech tags, edit button (admin mode) |
| **Visuals** | Masonry media vault — travel photos from Route Insolite + Midjourney work |
| **Admin Dashboard** | CMS panel at `/admin` — Projects, Experience, Certifications, Media, Messages |

---

## Features

### Portfolio Sections (8)
- **Hero** — name reveal animation, BO Creation watermark, ambient cursor glow, live Sfax clock
- **About** — bio + tech manifesto terminal easter egg (type `ob` + Enter)
- **Work** — project cards with Cloudinary image/video, tech stack tags, live URLs, GitHub links
- **Skills** — animated skill meter bars grouped by category
- **Experience** — vertical timeline with role, company, dates, description
- **Certifications** — credential cards with issuer, date, optional credential URL
- **Visuals** — masonry grid for travel photography (Route Insolite) and Midjourney generative work
- **Contact** — form with real-time message delivery + live Sfax timezone clock

### Admin CMS (`/admin`)
- Projects manager — create, edit, delete with direct Cloudinary image/video upload
- Experience editor — ordered timeline entries
- Certifications manager — with credential link + logo upload
- **Media Vault** — upload and manage images/videos directly to Cloudinary
- Messages inbox — view contact form submissions from the database

### Technical
- **Cloudinary CDN** — all media (images, videos) uploaded and served via Cloudinary
- **Graceful DB fallback** — static defaults served when Supabase is offline (zero crash)
- **`prefers-reduced-motion`** compliant — parallax, split-text, ambient glow all disabled on request
- **Shared animation tokens** — `src/lib/motion.ts` defines `EASE`, `DUR`, `EASE_GSAP` used across GSAP and Framer Motion
- **BO Creation brand** — logo in preloader, nav, hero watermark, admin sidebar, favicon
- **`next/image`** — optimized image delivery for all Cloudinary assets
- Turbopack dev server, TypeScript strict mode, zero build errors

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | Next.js 16.3.4 (App Router + Turbopack) |
| Language | TypeScript 5 (strict) |
| Styling | Tailwind CSS v4 |
| Animation | Framer Motion 13, GSAP 3 |
| Database | PostgreSQL via Supabase |
| ORM | Prisma v6 |
| Media CDN | Cloudinary |
| Fonts | Space Grotesk, JetBrains Mono |
| Deployment | Vercel (recommended) |

---

## Project Structure

```
src/
├── app/
│   ├── (site)/               # Public portfolio pages
│   │   ├── page.tsx          # Home — fetches DB, falls back to defaults
│   │   ├── HomeClient.tsx    # Client shell with section routing
│   │   └── layout.tsx
│   ├── admin/                # CMS dashboard (protected)
│   │   ├── projects/         # ProjectForm, ProjectsManager
│   │   ├── experience/       # ExperienceForm
│   │   ├── certificates/     # CertForm
│   │   ├── media/            # MediaVaultClient
│   │   └── messages/
│   └── api/
│       └── upload/           # Cloudinary upload endpoint
├── components/               # Section components (Hero, Work, Skills, …)
├── lib/
│   ├── motion.ts             # Shared animation tokens (EASE, DUR)
│   ├── uploadToCloudinary.ts # Client-side Cloudinary helper
│   └── data/
│       └── defaults.ts       # Static fallback data (DB offline)
├── backend/
│   └── db/
│       └── client.ts         # Prisma client singleton
└── styles/
    └── globals.css           # CSS variables, color tokens, grain overlay
```

---

## Getting Started

### Prerequisites
- Node.js 20+
- PostgreSQL database (Supabase recommended)
- Cloudinary account (free tier works)

### Setup

```bash
# 1. Clone
git clone https://github.com/OussEmabouchahwa/Personal-Portfolio-Website.git
cd Personal-Portfolio-Website

# 2. Install
npm install

# 3. Environment
cp .env.example .env
# Fill in your Supabase + Cloudinary credentials

# 4. Database
npx prisma generate
npx prisma db push   # creates tables in your Supabase project

# 5. Dev server
npm run dev
# → http://localhost:3000
```

### Admin Dashboard
Navigate to `/admin` to manage content (projects, experience, certifications, media, messages).  
Admin is currently open — add authentication middleware before deploying publicly.

---

## Environment Variables

Copy `.env.example` to `.env` and fill in your values.  
**Never commit `.env` — it is already excluded by `.gitignore`.**

| Variable | Description |
|----------|-------------|
| `DATABASE_URL` | Supabase pooled connection string |
| `DIRECT_URL` | Supabase direct connection (for migrations) |
| `NEXT_PUBLIC_SUPABASE_URL` | Your Supabase project URL |
| `CLOUDINARY_CLOUD_NAME` | Cloudinary cloud name |
| `CLOUDINARY_API_KEY` | Cloudinary API key |
| `CLOUDINARY_API_SECRET` | Cloudinary API secret (server-only) |
| `NEXT_PUBLIC_CLOUDINARY_CLOUD_NAME` | Cloud name for client-side upload widget |

---

## About

**Oussema Bouchahwa** — Software engineering student at IPSAS, Sfax, Tunisia.  
Backend/full-stack work: PostgreSQL, Prisma, Next.js.  
Visual side: travel photography and direction at [Route Insolite](https://www.instagram.com/route.insolite/), generative work with Midjourney.

📧 oussema.bouchahwa@ipsas.tn  
🔗 [LinkedIn](https://www.linkedin.com/in/bouchahwa-oussema-0216b3264/)  
💻 [GitHub](https://github.com/OussEmabouchahwa)

---

## License

[MIT](LICENSE) — use the structure freely, but don't copy my personal content (bio, photos, projects).
