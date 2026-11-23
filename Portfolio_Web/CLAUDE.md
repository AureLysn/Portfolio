# AureLysn Portfolio — read this first

This folder holds the code of the **public portfolio website**. It is **not** the vault root.
Since 2026-11-14 it is part of the public `Portfolio` repository (`04_Portfolio/`), not a repository of its own.
This is the only rules file here; the former `AGENTS.md` was merged into it on 2026-11-20.

| You need | Read |
|---|---|
| The vault's operating contract | `D:\AureLysn\CLAUDE.md` |
| How to talk to Aurel (reply in Vietnamese, peer register) | `01_Origine/05_Meta/Schema/12-user-profile.md` |
| Why the site has one front page and two doors (Art · Branding) | `01_Origine/01_Identity/Portfolio_Plan/one-site-two-doors-decision.md` (private vault) |
| What may and may not appear on the site | `01_Origine/05_Meta/Schema/04-lanes.md` §1.3 (*No direct promotion from `personal` to `04_Portfolio/`*) |

None of those rules are restated here — a rule written in two places is two rules.

## Three things specific to this repository

1. **Content flows one way: vault → this repo.** Only material Aurel has approved, from
   `04_Portfolio/01_Design_Showcase/` and `02_Storage/03_Finished_Work/Design/`. Build code never reads the vault directly, never symlinks it,
   and private personal drafts are never copied here.
2. **A commit here is close to publishing.** Git keeps every draft forever, and the site is
   built from what is committed. Unfinished content carries `draft: true`.
3. **Snapshot boundary.** This folder sits inside `D:\AureLysn\04_Portfolio\Portfolio_Web`, so the vault's `snapshot`
   zips it. `node_modules/`, `.astro/` and `dist/` are excluded.
   **Anything else here is zipped every time** — keep heavy media (video, source PSDs) out of this
   tree.

## Git — core in plugin `git-guard` (named `git-chung` until 2026-11-23)

Read `git-guard:git-an-toan` before any git command. Commits are made in the `Portfolio` repository at `04_Portfolio/`.
The `Portfolio` repository works by branch → PR like every other repository (`git-an-toan` §1.3, Aurel 2026-11-14). What this folder adds:

- **Branch:** `<type>/<yyyy-mm-dd>-<viec-khong-dau>`, `type` = `feat` · `fix` · `docs` · `chore` —
  the same words the commit subjects already use. **Never commit on `main`**: everything
  goes through a PR, merged with `--merge --delete-branch`.
- **Gate before a commit:** `npm run build` must pass once `src/` holds real pages. Docs-only
  changes: read the diff.
- **After a merge:** pull the main checkout.

⚠️ The Astro template ships `CLAUDE.md` as a **hardlink** to `AGENTS.md`. Since 2026-11-20 this
folder keeps only `CLAUDE.md`. If a template update brings `AGENTS.md` back, delete it instead of
keeping two copies.

---

# Astro notes (from the template)

## Development

When starting the dev server, use background mode:
