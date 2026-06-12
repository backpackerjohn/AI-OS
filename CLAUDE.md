# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

`AI-OS` is a workspace/knowledge base, not a conventional software application. It organizes design and planning artifacts for projects. There is **no build system, no package manager, no dependencies, no test suite, and no CI** — artifacts are self-contained files meant to be opened or read directly.

Because there is nothing to build or install, "running" an artifact means opening the HTML file in a browser (e.g. `open` / `xdg-open` the file, or load it via `file://`). There are no commands to lint, compile, or test.

## Directory convention

Content is nested under a `Projects/` tree with this shape:

```
AI-OS/Projects/<Project Name>/<Workstream or Feature>/<artifacts>
```

The repository root contains a single top-level folder `AI-OS/` (same name as the repo) which holds `Projects/`. Folder names use spaces and Title Case (e.g. `Dealership CRM`, `Browser Customer Input Wireframe and Planning`); preserve this style and quote paths in shell commands.

Currently the only project is **Dealership CRM**, with one workstream containing a paired spec + wireframe (see below).

## The spec + wireframe pairing (core convention)

A feature is typically captured as **two complementary files that must be kept in sync**:

1. A **spec markdown** (e.g. `desktop-adding-customer-unsold-page.md`) — describes *structure and layout only*: what sections exist, how they are arranged, and what content each holds. By the spec's own stated rule, it **does not describe behavior or functionality**. Selection/animation/sync behavior is documented narratively but the spec is the source of truth for *layout and field inventory*.
2. A **wireframe HTML** (e.g. `customer-detail-wireframe.html`) — a single self-contained file (inline `<style>` + inline `<script>`, no external assets or libraries) that realizes the spec as an interactive grayscale prototype. This is the source of truth for *behavior*.

When changing one, update the other so they don't drift. If you add a field or section to the wireframe, reflect it in the spec's field inventory, and vice versa. Note the two can legitimately differ in depth — e.g. the wireframe's lien sub-section carries more fields (bank address, per-diem, 20-day payoff) than the spec's summary lists; treat the wireframe as authoritative for exact fields.

## Wireframe conventions (HTML prototypes)

These prototypes follow a deliberate, consistent design language. Match it when editing or adding wireframes.

- **Grayscale only.** The palette is defined once as CSS custom properties in `:root` (`--ink`, `--line`, `--fill`, `--field`, `--muted`, etc.). Use these variables rather than hardcoding colors. The look is intentionally a low-fidelity wireframe (dotted grid page background, "browser chrome" frame, placeholder text in italics).
- **Reusable primitives** are plain CSS classes, not components: `.label` (uppercase field label), `.field` (input box; `input.field` for editable, plain `<div class="field">` for read-only placeholder), `.row`/`.stack` (flex layout), `.card`/`.card-head`/`.card-body`, `.chip`/`.val-chip`, `.tile` (bento sidebar tiles), `.opt` (multi-select option), `.yn-chip` (Yes/No pair).
- **No frameworks.** All interactivity is vanilla JS in a single `<script>` at the end of the file, organized as small IIFEs per feature (pickers, sidebar collapse, interview overlay, Yes/No pairs, field sync).

### Data-attribute behavior contracts

Behavior is wired through `data-*` attributes rather than per-element JS. When adding fields/controls, reuse these patterns:

- `data-sync="<key>"` — **two-way field linking.** All inputs sharing a key mirror each other's value on input, and feed the live sidebar summary tiles. This is how the Interview overlay, the main cards, and the sidebar (`Customer Trade`, `Payment Goals`) stay in sync. To link a new field across views, give every instance the same `data-sync` key.
- `data-group="<name>"` (on `.opt`) — multi-select toggles that populate the matching sub-section of the `Customer Wants` sidebar tile (`vehicle`, `features`).
- `data-target="<id>"` with `data-default="yes|no"` (on `.yn` Yes/No pairs) and `data-target` + optional `data-invert="true"` (on `.toggle` switches) — show/hide a region by element id. `data-invert` flips the sense (used by "Paying Cash" to *hide* finance fields when on).
- `data-auto="today"` — input auto-populated with the current date on load.
- The sidebar summary tiles use `.mini-row[data-for="<sync-key>"]` rows that reveal themselves only when the corresponding synced field has a value; the special key `pay-range` is composed from `pay-min`/`pay-max`.

## Git workflow

- Active development branch for current work: `claude/claude-md-docs-1tvpi9`. Develop, commit, and push there; do not push to `main` without explicit permission.
- Push with `git push -u origin <branch-name>`; retry on network errors with exponential backoff.
- Do **not** open a pull request unless explicitly asked.
