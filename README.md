# CR Weekly Status Report — Topic Sorter

A single-page tool that sorts pasted team status updates under Tessa Richards' fixed
list of 17 tracked CR items, so they're easy to review and copy into the
[OG-Commercial Readiness - CR Weekly Status Report - All Items](https://reedelsevier.sharepoint.com/sites/OG-CustomerLearning/Lists/CR%20Weekly%20Status%20Report/AllItems.aspx).

Everything runs client-side in the browser — no backend, no data leaves your machine.

## Features

- Paste raw text (plain, Markdown-style `##` headers, `[Bracketed]` headers, or
  rich text copied straight from Teams/Outlook) and it's automatically grouped by topic.
- Fuzzy header matching against the fixed 17-item list, with a couple of built-in aliases
  (e.g. "NEOID LMS Access CK Student" → "NEOID LMS Access").
- Per-topic Copy buttons.
- "Copy all as Markdown" for a full sorted digest.
- "Copy as table" — produces tab-separated Topic/Update rows you can paste directly
  into the SharePoint list's grid (quick edit) view.
- Star up to 3 topics ("☆ Top 3" button on any card with content) and give each a short
  label (Launch, Risk, GTM, Milestone, etc.) to feature them in a highlights table.
- **Create Final Report (.doc)** — generates a Word-openable document formatted after the
  Commercial Readiness Status Report example: logo header, a 3-column Top 3 highlights
  table (Paper-shaded cells, matching the example exactly), updates grouped under the same
  section headers as the tracked list (with "No updates this week." for blanks), and a
  Personnel section with Time Off bullets and a Sign Off checklist. No server, no library —
  built client-side in the browser.
- Draft auto-saved to browser `localStorage` so a reload doesn't lose your paste.
- Styled to Elsevier brand standards: Vital Orange / Graphite / Ink / Sand / Paper / Action
  Blue palette, Tiempos Text + National 2 typography, and the Elsevier wordmark in the header.

## Hosting on GitHub Pages

1. Create a new GitHub repository (public, or private with GitHub Pages enabled on your plan).
2. Add `index.html` and the `fonts/` folder from this download to the repository root
   (commit and push) — the brand fonts are loaded from `fonts/` at a relative path, so that
   folder needs to travel with `index.html`. (The logo and favicon are inlined directly in
   `index.html`, so nothing else is required.)
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to `Deploy from a branch`, choose the
   `main` branch and the `/ (root)` folder, then **Save**.
5. GitHub will publish the page at `https://<your-username>.github.io/<repo-name>/`
   within a minute or two.

## Files

- `index.html` — the tool itself (the Elsevier wordmark logo and favicon are inlined inside
  it, so it needs no other file to render or to generate reports).
- `fonts/` — Tiempos Text and National 2 web fonts (Elsevier brand typefaces), referenced by
  `index.html` via `@font-face`. Required for the page's on-screen branding.
- `assets/` — the original logo/favicon source files (SVG + PNG, all lockups and colors), kept
  for reference if you need a different lockup elsewhere. Not loaded by `index.html` itself.
- `Commercial_Readiness_Status_Report_sample.doc` — a sample branded report generated from
  this tool's "Create Final Report" button.

## Notes

- The tool does not write to the SharePoint list automatically — there's no API
  connection wired up. Use the "Copy as table" button and paste into the list's
  quick-edit grid view instead.
- If you'd like it to auto-populate the list, that would require a small addition
  (e.g. the SharePoint REST API or Power Automate flow) authenticated with your
  own credentials, since a static GitHub Pages site can't hold organizational
  secrets safely.
