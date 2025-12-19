# project purpose
- to teach kids numbers
- use three js

## Quick guide for AI coding agents

This repository is a small static project. The goal of this file is to give focused, actionable guidance so an AI agent (Copilot, assistant) can be productive immediately.

Key points you should know:

- Project layout (minimal)
  - `docs/index.html` — primary site entry (HTML). Most content changes live here or additional files under `docs/`.
  - `readme.md` — top-level README describing the project (use lowercase filename as present).
  - `LICENSE` — repository license file.

- Big picture & why
  - This repository contains a static documentation/site stored in `docs/`. There is no build system or package manifest present. Changes to pages are plain HTML edits and new files added under `docs/`.

- Common developer workflows (how to preview, test, and commit)
  - Preview local changes: open `docs/index.html` in a browser. On macOS: `open docs/index.html`.
  - There are no tests or build steps. Keep edits minimal, update relative links when adding files in `docs/`.
  - Commit messages: use short imperative messages (e.g., `docs: add FAQ page` or `fix: correct meta tags`).

- Project-specific conventions and patterns
  - Filenames are lowercase (e.g., `readme.md`, `docs/index.html`). Preserve casing to avoid platform-specific link breakage.
  - Prefer lightweight HTML edits — no framework scaffolding is used. Avoid introducing build tools unless requested.
  - Keep the site content self-contained under `docs/`. Use relative links (`./page.html` or `subdir/page.html`).

- Integration points & external dependencies
  - No external build, CI, or package manager files were found. Assume no Node/Python/Rust toolchain unless such files are added by humans.

- When creating or modifying files, be explicit and conservative:
  - If adding a new page, create `docs/new-page.html` and add a link from `docs/index.html`.
  - If changing site metadata (title, meta description), update `docs/index.html` directly.
  - Example: to add a “Contributing” page:
    1. Create `docs/contributing.html` with content.
    2. Add a link to `docs/index.html` (use a relative link).

- Safety and style rules for the agent
  - Do not add new tooling or CI without confirming with the human maintainer.
  - Keep changes limited to documentation and HTML unless user explicitly asks to add code or tooling.

- Files to check when you make changes (priority order)
  1. `docs/index.html` — update links, titles, or page content.
  2. `readme.md` — update high-level documentation about the project and any new workflows.
  3. `LICENSE` — do not modify unless instructed.

If anything in this file is unclear or you want additional conventions (commit hooks, branch naming, CI), tell me what to document and I will update this file.

— End of instructions
