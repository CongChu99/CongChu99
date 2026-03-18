# Spec: GitHub Profile README

## ADDED Requirements

---

### Requirement: Animated Header Banner

Full-width wave animation at the top of the README using capsule-render. Applies `#714B67 → #017E84` gradient. Creates immediate visual impact and brand identity.

**Priority**: MUST

#### Scenario: Header renders with gradient wave animation
- **GIVEN** a visitor opens `github.com/CongChu99`
- **WHEN** the profile page loads
- **THEN** a full-width animated wave banner appears at the top with purple-to-teal gradient, at least 150px tall, and the animation loops continuously

#### Scenario: Header renders in both light and dark GitHub themes
- **GIVEN** a visitor viewing the profile in GitHub dark mode
- **WHEN** the page loads
- **THEN** the header gradient is visible and the wave animation runs without the image appearing broken or invisible

#### Scenario: Header fails to load (third-party service down)
- **GIVEN** capsule-render Vercel instance is temporarily unavailable
- **WHEN** the profile page loads
- **THEN** GitHub displays the alt text "Header" as fallback — profile remains readable without the image

---

### Requirement: Animated Typing Tagline

Rotating animated typing SVG below the header that cycles through the developer's 4 identity statements.

**Priority**: MUST

#### Scenario: Tagline cycles through all identity lines
- **GIVEN** a visitor on the profile page
- **WHEN** the typing animation completes one cycle
- **THEN** the following lines have appeared in sequence:
  1. `Python Tech Lead 🐍`
  2. `DevSecOps Engineer 🔐`
  3. `Odoo Developer & ERP Architect 🏗️`
  4. `AI Tools Builder 🤖`
  5. `Building business automation on Odoo & Linux`
- **AND** the animation loops back to line 1

#### Scenario: Tagline color matches color system
- **GIVEN** the README is rendered
- **WHEN** the typing SVG loads
- **THEN** the text color is `#017E84` (Odoo teal) on transparent background

---

### Requirement: Bio Section

Short personal summary paragraph that establishes niche expertise and context for technical and non-technical visitors.

**Priority**: MUST

#### Scenario: Bio communicates 4 specializations within 5 sentences
- **GIVEN** a visitor reading the bio section
- **WHEN** they read the bio paragraph
- **THEN** Python Tech Lead, DevSecOps, Odoo ERP, and AI Tools expertise are all mentioned
- **AND** the bio is no longer than 5 sentences

---

### Requirement: Tech Stack Badges — 4 Domain Groups

Visual skill badges organized into 4 clearly labeled domain groups. Each group is a distinct section with a heading.

**Priority**: MUST

#### Scenario: All 4 domain groups are present
- **GIVEN** a visitor on the profile page
- **WHEN** they scroll to the Tech Stack section
- **THEN** they see 4 labeled groups: "AI / ML & Tools", "Odoo & ERP", "DevSecOps", "Languages & Tools"
- **AND** each group contains at least 4 badge images

#### Scenario: Odoo badge renders correctly
- **GIVEN** Odoo is not in the standard shields.io logo registry
- **WHEN** the Odoo badge is embedded
- **THEN** it displays using a custom badge URL with `Odoo` label, `#714B67` color, and no broken icon
- **OR** uses a shields.io custom badge with hex color matching the Odoo brand

#### Scenario: Badges render in both light and dark mode
- **GIVEN** `style=for-the-badge` and `logoColor=white` are set on all badges
- **WHEN** the profile loads in dark mode
- **THEN** all badge text and icons are visible (no white-on-white or invisible elements)

---

### Requirement: GitHub Stats Cards

Live stats card and streak card displayed side-by-side showing GitHub activity for `CongChu99`.

**Priority**: MUST

#### Scenario: Stats card displays current GitHub metrics
- **GIVEN** the README embeds the github-readme-stats URL for username `CongChu99`
- **WHEN** the stats card loads
- **THEN** it shows: total stars earned, total commits (current year), total PRs, total issues, and contribution rank

#### Scenario: Streak card displays contribution streak
- **GIVEN** the README embeds the streak-stats URL for username `CongChu99`
- **WHEN** the streak card loads
- **THEN** it shows: current streak days, longest streak days, total contributions count

#### Scenario: Cards are displayed side-by-side on desktop
- **GIVEN** the cards are wrapped in an HTML table or centered div with `<img>` side-by-side
- **WHEN** viewed on desktop GitHub (>768px)
- **THEN** stats card and streak card appear horizontally aligned, not stacked vertically

#### Scenario: Card theme matches color system
- **GIVEN** `theme=tokyonight` or custom hex parameters are set
- **WHEN** cards render
- **THEN** background approximates `#0D1117`, title color approximates `#714B67`, icon color approximates `#017E84`

---

### Requirement: Top Languages Card

Language distribution card showing the developer's most-used languages by repository.

**Priority**: MUST

#### Scenario: Top languages card renders for CongChu99
- **GIVEN** the README embeds the top-langs URL for username `CongChu99`
- **WHEN** the card loads
- **THEN** Python is displayed as the dominant language
- **AND** the card uses `layout=compact` for space efficiency

---

### Requirement: Snake Contribution Animation (GitHub Actions)

Daily auto-updated snake SVG animation generated from the contribution graph via GitHub Actions.

**Priority**: SHOULD

#### Scenario: Snake workflow runs on schedule
- **GIVEN** `.github/workflows/snake.yml` is committed with `schedule: cron: '0 12 * * *'`
- **WHEN** the daily cron triggers
- **THEN** the Platane/snk action generates a dark-mode snake SVG
- **AND** the action commits the SVG to the `output` branch at path `github-contribution-grid-snake-dark.svg`
- **AND** the workflow exits with status `success`

#### Scenario: Snake SVG renders in README
- **GIVEN** the snake SVG is committed and the README references it via local path from the output branch
- **WHEN** a visitor views the profile
- **THEN** the snake animation plays on the contribution graph
- **AND** the snake image is not a broken placeholder

#### Scenario: Snake workflow fails silently
- **GIVEN** the workflow fails due to permissions issue
- **WHEN** the GitHub Actions run fails
- **THEN** GitHub sends a failure notification email to the repository owner
- **AND** the previous SVG remains in place (no broken image — last successful SVG persists)

---

### Requirement: Social / Contact Links

Badge-style links to professional profiles and contact options.

**Priority**: SHOULD

#### Scenario: Social links section contains minimum required links
- **GIVEN** the social section is in the README
- **WHEN** a visitor views it
- **THEN** at minimum a LinkedIn badge-link and a contact email badge are visible
- **AND** each link opens in a new tab (`target="_blank"`)

---

### Requirement: GitHub Trophies Row

Row of achievement trophies from github-profile-trophy for username `CongChu99`.

**Priority**: MAY

#### Scenario: Trophies row renders
- **GIVEN** the trophy URL is embedded with `username=CongChu99&theme=tokyonight&row=1&column=6`
- **WHEN** the profile loads
- **THEN** up to 6 trophy icons are displayed in a single horizontal row
- **AND** the trophy theme matches the color system

---

### Requirement: Animated Footer

Bottom wave banner mirroring the header, completing the visual frame of the profile.

**Priority**: MUST

#### Scenario: Footer mirrors header gradient with section=footer
- **GIVEN** capsule-render is embedded at the bottom with `section=footer&type=waving&color=017E84,714B67` (reversed gradient)
- **WHEN** the visitor scrolls to the bottom
- **THEN** a wave animation appears matching the header style
- **AND** the gradient direction is reversed (teal-to-purple) to create a visual bookend effect

---

### Requirement: Cross-Theme Visual Verification

The complete README must render correctly in both GitHub light and dark themes with no broken elements.

**Priority**: MUST

#### Scenario: No broken images in dark mode
- **GIVEN** the complete README is committed
- **WHEN** viewed in GitHub dark mode (Settings → Appearance → Dark)
- **THEN** all badge images, stats cards, header, footer, and typing SVG render without broken image placeholders

#### Scenario: No invisible text in light mode
- **GIVEN** `style=for-the-badge&logoColor=white` badges with dark label colors
- **WHEN** viewed in GitHub light mode
- **THEN** all badge labels are readable — no white text on white background

---

### Requirement: GitHub Actions Permissions Configuration

The profile repository must grant the snake workflow permission to commit generated files.

**Priority**: MUST

#### Scenario: Snake workflow has write permission
- **GIVEN** `permissions: contents: write` is set in `snake.yml`
- **WHEN** the workflow runs and generates the SVG
- **THEN** the action successfully commits to the `output` branch without a `403 Permission denied` error

#### Scenario: Repository Actions settings allow workflows
- **GIVEN** the `CongChu99/CongChu99` repository Settings → Actions → General
- **WHEN** the snake workflow is triggered for the first time
- **THEN** it runs without being blocked by "Workflow permissions" settings
