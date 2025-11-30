<!-- Copilot instructions tailored for the Inside Rail Quarto site -->
# Inside Rail — Copilot Instructions

This repository is a Quarto-based static website. The guidance below is concise, actionable, and specific to this codebase so you can be immediately productive.

**Big Picture:**
- **Project type:** Quarto website (`_quarto.yml` sets `project.type: website`). The source content is `.qmd` files (root and per-section subfolders) and the generated site lives in `_site/`.
- **Primary sections:** `tennis/`, `racing/`, `nfl/` — each contains an `index.qmd` and posts (e.g., `tennis/post1-first-strike.qmd`).
- **Static assets:** `site_libs/` contains vendored JS/CSS (Bootstrap, Quarto runtime). `styles.css` at project root is the project’s custom CSS and is referenced from `_quarto.yml` under `format.html.css`.

**Build / Preview / Publish (Windows PowerShell):**
- Install Quarto locally (required): https://quarto.org/docs/get-started/
- Build site: `quarto render` (from repo root). This regenerates `_site/` and `search.json`.
- Live preview: `quarto preview` (starts a local server and watches for changes).
- Important: treat `_site/` as generated output — do not edit files directly there.

**Authoring conventions & patterns to follow:**
- Post files: create new posts as `.qmd` in the appropriate section folder (e.g., `tennis/new-post.qmd`). Follow front-matter used in `tennis/post1-first-strike.qmd` (YAML keys: `title`, `description`, `date`, `categories`). Date format: `YYYY-MM-DD`.
- Navigation: `_quarto.yml` controls the site navbar; links in the navbar reference source `.qmd` files (e.g., `tennis/index.qmd`). Update `_quarto.yml` to add/remove top-level nav items.
- Styling: add project-level CSS rules in `styles.css`. `_quarto.yml` already references this file.
- Vendor assets: `site_libs/` contains third-party libraries. Prefer updating Quarto or upstream packages rather than editing vendored files unless necessary.

**Patterns & examples from this repo:**
- Home page: `index.qmd` contains the site's introduction and links to sections.
- Tennis series: `tennis/post1-first-strike.qmd` demonstrates the preferred metadata structure, callouts, and how to link between posts using relative links (e.g., `[Post title](post1-first-strike.qmd)`).
- Callouts and styling: uses Quarto callouts (example class `.callout-note`) and project CSS customizations in `styles.css` (see the `.callout-note` rules).

**Editing guidance for AI code agents:**
- When adding content, create a `.qmd` with front-matter and place it in the correct section folder. Update `tennis/index.qmd` or `_quarto.yml` if you want it discoverable from the nav.
- Do not edit `_site/` files; instead run `quarto render` to regenerate output. If you must inspect generated HTML to debug rendering, regenerate and open `_site/<path>/index.html`.
- Keep changes minimal and localized: CSS edits in `styles.css`, content in `.qmd` files, layout changes via `_quarto.yml`.

**Common quick tasks & commands**
- Build once: `quarto render`
- Serve locally and watch: `quarto preview`
- Linting / diagnostics: Quarto provides warnings during render; fix front-matter YAML and Markdown/Quarto syntax if seen.

**Repository-specific gotchas**
- Navigation entries in `_quarto.yml` point to source `.qmd` files, not `_site` HTML. Fix broken nav links by checking file paths relative to the repo root.
- The `search.json` in `_site/` is generated — update by rebuilding the site.
- The CSS at project root is intentionally minimal and used to override the Quarto theme; prefer small, targeted rules to avoid unexpected global changes.

If anything here is unclear or you want instructions tailored for a specific automation (CI build, GitHub Pages publish, or content-generation scripts), tell me which target and I will expand or modify these instructions.
