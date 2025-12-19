# project purpose

- to teach kids numbers
- use p5 js

## quick guide for AI coding agents

This repository is a small, static site. The goal of this file is to give focused, actionable guidance so an AI agent (Copilot, assistant) can be productive immediately.

key points you should know

- project layout (minimal)
  - `docs/index.html` — primary site entry (HTML). Most interactive behavior and UI live in this single file.
  - `readme.md` — top-level README describing the project.
  - `LICENSE` — repository license file.

- big picture & why
  - The project is a self-contained static page (no build system). Edits are plain HTML/JS/CSS changes under `docs/`.
  - Rendering is done with Three.js (r128 via CDN) in `docs/index.html`.

- common developer workflows (preview, test, commit)
  - Preview local changes: open `docs/index.html` in a browser. On macOS: `open docs/index.html`.
  - There are no automated tests or build steps. Keep edits minimal and self-contained.
  - Commit messages: use short imperative messages (e.g., `docs: add feature`, `fix: update grid labels`).

- project-specific conventions and patterns
  - Filenames are lowercase (e.g., `readme.md`, `docs/index.html`). Preserve casing.
  - Avoid adding build tooling, package manifests, or CI without explicit human approval.
  - Keep site content self-contained under `docs/` and use relative links.

## runtime & architecture notes (important for edits)

- the interactive page uses Three.js to create:
  - a group of "balls" (one mesh per item by default),
  - optional canvas-based textures for per-ball numeric labels,
  - grid lines and row/column labels built from Plane geometries with Canvas textures.

- performance considerations
  - Creating a CanvasTexture per ball and many individual Mesh objects is expensive. For large counts prefer one of:
    1. InstancedMesh for the balls (single geometry/material instance) + a texture atlas for labels.
    2. CSS/DOM overlay labels if exact 3D alignment isn't required.
  - When updating or removing textures and geometries, always call dispose() on geometries, materials, and textures to free GPU memory.

- current fast-mode behavior (as of recent changes)
  - The UI provides a "Balls only (fast)" toggle which is enabled by default.
  - Fast mode defaults ON and does the following:
    - hides grid lines and row/column labels,
    - disables per-ball Canvas textures,
    - renders balls as simple 2D discs (CircleGeometry) with MeshBasicMaterial (no lights/textures) to reduce load.
  - Toggling fast-mode converts existing balls between fast (2D, no textures) and normal (3D sphere + labels) rendering. The helper `setBallRenderingMode` handles disposal and recreation.

## guidance for making edits (checklist for PRs or patches)

1. If you change rendering code that creates geometries or textures, ensure you:
   - dispose() old geometries, materials, and textures when they are removed or replaced,
   - avoid creating thousands of canvas textures unless you also add an instancing/atlas strategy.

2. When adding new UI controls in `docs/index.html`:
   - add a control inside the existing `.controls` container and preserve mobile layout behavior.
   - keep controls accessible (labels with `for` attributes) and preserve existing `id` conventions.

3. Performance-first edits:
   - If the change might cause many new meshes/textures, either implement an efficient instanced approach or gate the feature behind the fast-mode toggle.

4. Small features and behavior tweaks are welcome directly in `docs/index.html`. For larger changes (new build tooling or many new files), ask the maintainer first.

## files to check when you make changes (priority order)
1. `docs/index.html` — primary interactive logic and UI.
2. `readme.md` — update high-level docs or usage notes if behavior changes.
3. `LICENSE` — do not modify unless explicitly instructed.

If anything in this file is unclear or you want additional conventions (commit hooks, branch naming, CI), tell me what to document and I will update this file.

-- end of instructions
