# Third-party notices

This project is licensed under the Apache License 2.0 — see [LICENSE](LICENSE).
The deck itself is plain Markdown (`terminschleuder-overview.md`) with no
runtime dependencies; the only third-party software involved is the tooling
that renders it.

## Tooling

| Tool | Where used | License | Upstream |
| --- | --- | --- | --- |
| Marp CLI | CI (`.github/workflows/ci.yml`) renders the deck to PDF via the official `ghcr.io/marp-team/marp-cli` image; local export: `npx @marp-team/marp-cli@latest terminschleuder-overview.md -o slides.pdf --html` | MIT | https://github.com/marp-team/marp-cli |

## Notes

- Marp CLI bundles Marpit (MIT) and renders diagrams (mermaid) natively; see
  its own third-party notices for the full toolchain list.
- No third-party code is distributed with this repo — the PDF in the GitHub
  Release is the rendered output of the Markdown source.