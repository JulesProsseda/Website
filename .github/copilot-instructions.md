**Purpose**: Short, actionable guidance for AI coding agents working on this repository (a small static portfolio site).

- **Project type**: Plain static site — HTML files live in the repository root, CSS in `style.css`, and images/fonts under `assets/`.
- **How the site runs**: No build system. Preview by opening files in a browser or run a local static server: `python3 -m http.server 8000` from the repo root.

**Key files & patterns (examples)**
- `index.html`, `about.html`, `portfolio.html`, `Contact.HTML` — top-level pages. Note: `Contact.HTML` uses an uppercase extension in the repo, while links use `contact.html`.
- `style.css` — single stylesheet. Notice CSS variables at the top (e.g. `--primary-color`) and layout rules for `nav`, `div.home`, `div.contact`, `div.portfolio`.
- `assets/fonts/Irish_Grover/` — bundled font files. When adding fonts, prefer `assets/...` paths and add an `@font-face` rule in `style.css`.
- Image files referenced from HTML/CSS (e.g. `header.png`, `ghoul.png`, `monkey.png`, `self.jpg`) live in repo root or `assets/`.

**Project-specific conventions & gotchas**
- Case sensitivity: Development currently on macOS (case-insensitive filesystem), but remote hosts may be case-sensitive. `Contact.HTML` (capitalized) vs `contact.html` (link targets) is a likely source of runtime 404s on some servers — avoid renaming without confirming.
- Path escaping: `style.css` contains `background-image: url('self\\ portrait.jpg');` which mixes backslash escaping and a space in a filename. Prefer safe filenames (no spaces) and consistent POSIX-style paths when fixing.
- Single global stylesheet: Keep visual changes centralized in `style.css`. Agents should update CSS selectors like `div.contact`, `div.home`, and `figcaption` rather than editing inline styles across pages.
- Repeated nav pattern: Navigation markup is duplicated across pages (same order/links). When updating navigation, update all pages to keep them synchronized.

**What an AI agent should do first (practical checklist)**
1. Read `index.html`, `Contact.HTML`, and `style.css` to understand markup and CSS conventions used here.
2. Avoid renaming files in-place that change case or include spaces without asking — point out where case/spacing is inconsistent.
3. When adding fonts or images, place them under `assets/` and reference with relative paths (e.g. `assets/fonts/...`, `assets/images/...`).
4. For local testing use: `python3 -m http.server 8000` then open `http://localhost:8000`.

**Examples to cite when making edits**
- Keep `nav` structure stable: `<nav aria-label="Primary Navigation"> ... <ul> <li><a href="index.html">Home</a></li> ...` — update every page if changing order.
- Adjust visual styles in `style.css`: change `--primary-color` or `nav ul { gap: 34px; }` rather than changing spacing via inline attributes.
- Fix path issues: replace `background-image: url('self\\ portrait.jpg');` with `background-image: url('self-portrait.jpg');` and rename file accordingly (but mention case/space changes in PR description).

**Behavior when merging or creating this file**
- If a `.github/copilot-instructions.md` already exists, preserve any repository-specific rules and merge new findings under a clear **Project-specific conventions** section. Do not delete maintainers' instructions.

**Developer workflow notes (for PRs)**
- No tests in repo; keep changes focused and small. When editing multiple pages (nav, headers), include a short checklist in the PR describing which files were changed and why.
- Recommend running a local static server when previewing visual changes.

**If anything is unclear**: Ask the repository owner (Jules) for deployment targets (GitHub Pages, Netlify, etc.) and whether filenames must remain case-preserved for historical reasons.

---
Request: review these instructions and tell me if you'd like additional project details (deploy target, desired image/font paths, or a preferred filename normalization rule). 
