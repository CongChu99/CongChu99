# Proposal: GitHub Profile README

## Why

Most developers with deep niche expertise — Odoo ERP, DevSecOps, AI tooling — look identical on GitHub to a student who wrote two Hello World scripts. A blank profile page wastes the strongest professional signal a technical developer has: a live, always-on portfolio that recruiters, clients, and collaborators visit directly.

The opportunity is specific: a Python Tech Lead with DevSecOps + Odoo + AI tools expertise has a rare combination of skills that is extremely valuable but invisible on a default GitHub profile. Building a high-quality, animated, brand-consistent README converts the profile from a dead link to an active brand asset — working 24/7 to attract the right opportunities.

Research verdict: **Build**. Zero cost, ~1 day of focused work, entirely free OSS tooling available. The ROI is clear given the niche positioning goal.

## What Changes

The GitHub profile page (`github.com/CongChu99`) transforms from a default user page into a branded, animated, self-updating portfolio. Visitors immediately see:

- A colorful animated header communicating Python Tech Lead + DevSecOps + Odoo identity
- Organized skill badges grouped by domain (AI/ML, Odoo/ERP, DevSecOps, Fullstack)
- Live GitHub activity stats and contribution visualization
- GitHub Actions workflows proving DevOps competency through the profile itself

## Capabilities

### New Capabilities

- `animated-header`: Full-width wave banner with Odoo-inspired purple-teal gradient, rendered via capsule-render
- `typing-tagline`: Rotating animated text cycling through role identifiers (Python Tech Lead | DevSecOps Engineer | Odoo Developer | AI Tools Builder)
- `bio-section`: Short personal summary (3–5 sentences) positioning niche expertise clearly
- `skill-badges`: Visual tech stack organized in 4 domain groups — AI/ML, Odoo & ERP, DevSecOps, Languages & Tools
- `github-stats-cards`: Live stats card (commits, stars, PRs, issues) + streak stats card displayed side-by-side
- `top-languages-card`: Language distribution card from github-readme-stats
- `snake-animation`: Contribution graph snake animation auto-updated daily via GitHub Actions
- `trophies-row`: GitHub achievement trophies (commits, PRs, stars, followers) row from github-profile-trophy
- `social-links`: Badge-style links to LinkedIn, contact email, and relevant professional profiles
- `animated-footer`: Matching capsule-render footer wave, mirroring header colors

## Scope

### In Scope

- `README.md` file for the `CongChu99/CongChu99` profile repository
- Animated header and footer (capsule-render)
- Typing animation tagline (readme-typing-svg)
- About/bio paragraph (manual markdown)
- Tech stack badges organized by 4 domains (shields.io + devicons)
- GitHub stats card + streak stats (github-readme-stats + streak-stats)
- Top languages card (github-readme-stats)
- Snake contribution animation (Platane/snk via GitHub Actions — `snake.yml` workflow)
- GitHub Trophies row (github-profile-trophy)
- Social/contact links section
- Color system: `#714B67` + `#017E84` palette applied consistently across all widgets
- Cross-theme verification (GitHub light + dark mode)

### Out of Scope (Non-Goals)

- Spotify Now Playing widget (personal, not professional signal; OAuth maintenance overhead)
- Blog post auto-update workflow (no confirmed blog source)
- WakaTime coding activity (requires account setup; add as Phase 2 if WakaTime account is created)
- Custom hand-crafted SVG animations (high effort, not proportional to impact)
- Mobile-optimized HTML layout (GitHub markdown rendering on mobile is acceptable without custom layout)
- Automated profile content AI-generation (out of scope for this project)

## Success Criteria

- Profile page loads in < 3 seconds with all widgets rendering (no broken image placeholders)
- All 4 skill badge domains are visible and correctly categorized without horizontal scrolling on desktop
- Stats cards display live GitHub data (commits, streak, top languages) for username `CongChu99`
- Snake animation SVG updates automatically on a daily schedule via GitHub Actions without manual intervention
- Profile reads coherently in both GitHub light mode and dark mode — no invisible text, no color clashes
- A technical visitor can identify the developer's 4 specializations (Python, DevSecOps, Odoo, AI) within 10 seconds of viewing
- GitHub Actions `snake.yml` workflow passes with `contents: write` permission and commits output SVG successfully

## Impact

**Competitors positioned against**: Generic "fullstack Python developer" profiles that lack niche domain differentiation. GitHub profile template generators (profileme.dev, rahuldkjain) produce output that doesn't address Odoo or DevSecOps niche identity.

**Audience served**: Technical recruiters at ERP/consulting firms, DevSecOps hiring managers, Odoo freelance clients, and developer community peers evaluating technical credibility.

**Ecosystem dependencies**: capsule-render (Vercel), readme-typing-svg (Vercel), github-readme-stats (public Vercel instance or self-hosted), github-readme-streak-stats (Vercel), github-profile-trophy (Vercel), shields.io, Platane/snk (GitHub Actions).
