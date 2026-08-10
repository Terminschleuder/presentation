# terminschleuder — presentation

A high-level architecture and domain walkthrough of the terminschleuder geospatial
events platform, written for an audience seeing it for the first time.

- **[`terminschleuder-overview.md`](terminschleuder-overview.md)** — the deck (~28 slides).

## How to view / present it

The deck is **Marp-formatted Markdown** — each `---` is a slide break and `#` is the
slide title. It also reads fine as a plain document.

**Option A — VS Code (easiest for editing):**
install the *Marp for VS Code* extension, open the `.md` file, and use the preview.

**Option B — export to PDF / PPTX / HTML** (no editor needed):

```bash
npx @marp-team/marp-cli@latest terminschleuder-overview.md -o slides.pdf
npx @marp-team/marp-cli@latest terminschleuder-overview.md -o slides.pptx
npx @marp-team/marp-cli@latest terminschleuder-overview.md -o slides.html
```

**Option C — just read it** on GitHub / Obsidian / any Markdown viewer. The mermaid
diagrams render on GitHub and in Obsidian out of the box.

**Option D — let CI build it for you.** Every push to `main`/`master` (and every PR
and release tag) runs [`.github/workflows/ci.yml`](.github/workflows/ci.yml), which
renders the deck to `slides.pdf` with the official Marp CLI image (Chromium bundled, so
mermaid diagrams and raw HTML render correctly) and uploads it as a **`slides` artifact**
on the Actions run — download it from the run page on GitHub.

## What's covered

- What problem it solves; the "two ways an event enters, one trust boundary" idea
- High-level architecture & the no-GIS-on-the-host deployment constraint
- Apps / project layout
- **Domain glossary** and the core data model (ERD)
- Event lifecycle; the ingestion pipeline; promotion & provenance
- **Where the data comes from** (hand-curated, ingested, the GeoNames city gazetteer, demo seed)
- **How city finding works** (`?near_city=` → centroid → `ST_DWithin` → distance-annotated)
- Proximity search correctness & performance; `near_city` vs `city`
- Authentication (JWT / API key / session → one User) & authorization/ownership
- The public read-only API surface; self-describing OpenAPI 3; the demo client
- URL routing, deployment & operations; how to explore it yourself

> Tip: the `<!-- ... -->` comments at the top of some slides are speaker notes.