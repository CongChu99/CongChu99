# Tech Stack: GitHub Profile README

> This is a static file project (README.md) + external SVG services + GitHub Actions automation.
> Traditional "frontend/backend/database" categories are replaced with profile-specific categories.

---

## Profile Structure

- **Format**: GitHub Flavored Markdown (GFM) with inline HTML (`<img>`, `<div>`, `<table>`, `<a>`)
- **File**: `README.md` at root of `CongChu99/CongChu99` repository
- **Size target**: < 50 KB raw markdown; total asset weight < 3 MB

---

## Widget Services

| Component | Service | Hosting | Rationale |
|---|---|---|---|
| **Header/Footer** | [capsule-render](https://github.com/kyechan99/capsule-render) | Vercel (public) | Best animated wave/gradient headers; supports `#714B67→#017E84` gradient natively |
| **Typing tagline** | [readme-typing-svg](https://github.com/DenverCoder1/readme-typing-svg) | Vercel (public) | CSS-animated SVG typing effect; configurable font, speed, colors |
| **Stats card** | [github-readme-stats](https://github.com/anuraghazra/github-readme-stats) | Public Vercel instance (self-host recommended — see note) | Live commit/star/PR/issue counts; 20+ themes |
| **Streak stats** | [github-readme-streak-stats](https://streak-stats.demolab.com) | Public instance | Current streak, longest streak, total contributions |
| **Top languages** | github-readme-stats top-langs endpoint | Same as stats card | Language breakdown by repo |
| **Trophies** | [github-profile-trophy](https://github.com/ryo-ma/github-profile-trophy) | Vercel (public) | Achievement badges; `flat` row theme |
| **Badges** | [shields.io](https://shields.io) + [devicons](https://devicons.github.io/devicon/) | shields.io CDN | Static skill badges; highly customizable colors |

> **Self-hosting note (Recommendation 4 from research)**: Fork `anuraghazra/github-readme-stats` and deploy to a free Vercel account (~15 min). Replace public instance URLs with personal deployment URL to avoid rate limiting. Not required for MVP but recommended for production reliability.

---

## Automation (GitHub Actions)

| Workflow | Action | Trigger | Purpose |
|---|---|---|---|
| `snake.yml` | [Platane/snk@v3](https://github.com/Platane/snk) | Daily cron (`0 12 * * *`) | Regenerates snake SVG from contribution graph; commits to `output/` branch |
| *(Phase 2)* `waka-readme.yml` | [waka-readme](https://github.com/athul/waka-readme) | Weekly cron | Refreshes WakaTime coding stats in README — requires WakaTime API key secret |

**Permissions required**: `contents: write` for snake workflow to commit output SVG back to repo.

**Secrets required** (Phase 2 only): `WAKATIME_API_KEY` stored in repository Secrets.

---

## Color System

All widget theme parameters must use this palette for visual consistency:

| Token | Hex | Usage |
|---|---|---|
| `primary` | `#714B67` | Odoo purple — capsule-render start color, typing SVG color |
| `secondary` | `#017E84` | Odoo teal — capsule-render end color, accent elements |
| `background` | `#0D1117` | GitHub dark background |
| `text` | `#C9D1D9` | GitHub default text |

Widget-specific parameters:
- capsule-render: `color=714B67,017E84&type=waving&height=200&section=header`
- readme-typing-svg: `color=017E84&width=600&lines=...`
- github-readme-stats theme: `theme=tokyonight` (closest to palette; or `bg_color=0D1117&title_color=714B67&text_color=C9D1D9&icon_color=017E84`)
- streak-stats: `theme=tokyonight`
- github-profile-trophy: `theme=tokyonight`

---

## Tech Badge List

Organized by the 4 domain groups defined in proposal:

### AI / ML & Tools
`Python` · `LangChain` · `OpenAI` · `Ollama` · `FastAPI` · `Jupyter`

### Odoo & ERP
`Odoo` (custom badge) · `PostgreSQL` · `XML` · `JavaScript`

### DevSecOps
`Docker` · `Kubernetes` · `Ansible` · `GitHub Actions` · `GitLab CI` · `Trivy` · `SonarQube` · `Linux` · `Nginx` · `Bash`

### Languages & General Tools
`Python` · `Git` · `VS Code` · `Ubuntu`

Badge source: shields.io (`https://img.shields.io/badge/<label>-<color>?style=for-the-badge&logo=<logo>&logoColor=white`)

---

## CI/CD

- **Pipeline**: GitHub Actions (built into profile repository)
- **Workflows**: 1 scheduled workflow for snake animation (MVP); 1 more for WakaTime (Phase 2)
- **No build process**: README.md is a static file — no compilation, no deployment pipeline

---

## Monitoring & Reliability

- **No APM**: Not applicable for a static README
- **Failure detection**: GitHub Actions sends email notifications on workflow failure by default
- **Broken image fallback**: GitHub shows alt text on broken image load — keep all `<img>` tags with descriptive `alt` attributes
- **Cache**: GitHub caches external SVGs 5–60 min. Snake animation SVG committed to repo (local reference) bypasses this

---

## Deployment Strategy

- **Strategy**: Direct commit to `main` branch of `CongChu99/CongChu99` repository
- **Environments**: Production only (GitHub profile is live immediately on commit)
- **Rollback**: `git revert` any commit; GitHub profile updates within seconds
