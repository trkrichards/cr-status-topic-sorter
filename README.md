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
- Star up to 3 topics ("☆ Top 3" button on any card with content) to feature them in a
  Top 3 Updates section.
- Time Off and Sign-off fields feed into the final report.
- **Download Word Report (.doc)** — generates a real Word-openable document with Top 3
  Updates, Updates by Topic (all 17, including blanks marked "No update this week"),
  Time Off, and Sign-off sections. No server, no library — built client-side in the browser.
- Draft auto-saved to browser `localStorage` so a reload doesn't lose your paste.

## Hosting on GitHub Pages

1. Create a new GitHub repository (public, or private with GitHub Pages enabled on your plan).
2. Add `index.html` from this folder to the repository root (commit and push).
3. In the repo, go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to `Deploy from a branch`, choose the
   `main` branch and the `/ (root)` folder, then **Save**.
5. GitHub will publish the page at `https://<your-username>.github.io/<repo-name>/`
   within a minute or two.

## Files

- `index.html` — the complete tool (self-contained; no build step, no dependencies).

## Notes

- The tool does not write to the SharePoint list automatically — there's no API
  connection wired up. Use the "Copy as table" button and paste into the list's
  quick-edit grid view instead.
- If you'd like it to auto-populate the list, that would require a small addition
  (e.g. the SharePoint REST API or Power Automate flow) authenticated with your
  own credentials, since a static GitHub Pages site can't hold organizational
  secrets safely.
