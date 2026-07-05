# MarlonAvery.com

The cinematic personal platform of **Marlon Avery** — Applied AI executive, engineer, founder,
educator, and speaker. *Building AI. Teaching the Future.*

A scroll-driven, film-like experience built on Astro 5, where three Higgsfield-generated hero
sequences of Marlon are scrubbed by the visitor's scroll — anchored by real photography, real
projects, and real workshop content.

## Stack

- [Astro 5](https://astro.build) + Content Collections (all content is data, not hardcoded)
- Tailwind CSS v4 (design tokens in `src/styles/global.css`)
- TypeScript (strict), zero client frameworks — a few small vanilla scripts
- GitHub Pages via GitHub Actions (`.github/workflows/deploy.yml`)

## Quick start

```sh
npm install
npm run dev        # local dev server
npm run check      # astro type/diagnostic check
npm run build      # production build → dist/
```

## Deployment flow

- `main` deploys production via `.github/workflows/deploy.yml`.
- `staging` deploys preview builds via `.github/workflows/deploy-staging.yml`.
- Feature branches should open PRs into `staging`, then promote `staging` into `main`.

## Domain cutover (Webflow -> GitHub Pages)

1. In GitHub repository settings, set Pages source to **GitHub Actions**.
2. Configure production custom domain as `marlonavery.com`.
3. In your DNS provider, point apex `@` to GitHub Pages A records:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
4. Add `www` as a CNAME to `Marlona.github.io`.
5. Add `staging` as a CNAME to `Marlona.github.io`.

## Editing content

Add or edit files under `src/content/` — no component changes needed:

| Collection   | Format | Powers                                   |
| ------------ | ------ | ---------------------------------------- |
| `speaking`   | JSON   | Keynote topics on /speaking               |
| `workshops`  | JSON   | Workshop catalog, detail pages, wizard    |
| `events`     | JSON   | /events upcoming + archive, home preview  |
| `projects`   | MDX    | /projects case studies, home features     |
| `experience` | JSON   | About-page timeline                       |
| `press`      | JSON   | Planner resources on /speaking            |
| `blog`       | MDX    | Reserved for future writing section       |

## Cinematic sequences

The three hero clips live in `public/video/` and are registered in `src/data/heroClips.ts`.
See `CLAUDE.md` for the generation identity rule and the required ffmpeg encode settings
(dense keyframes for scroll-seeking). Reduced-motion visitors get poster frames instead.

## Lighthouse (production build)

Performance 99–100 · Accessibility 100 · Best Practices 100 · SEO 100
