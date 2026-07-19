# Genome Neighborhood Viewer

An interactive, single-file HTML tool for visualizing genome neighborhood diagrams from EFI-GNT (Genome Neighborhood Tool) SQLite output. Load a `.sqlite` file, adjust layout/label/color options with live sliders, and export the result as PNG or SVG.

## Usage

1. Open `genome_neighborhood_viewer.html` in a web browser (double-click it, or drag it into a browser window).
2. Drop your `.sqlite` file onto the dropzone (or click to browse).
3. Adjust the controls in the sidebar — the diagram redraws live.
4. Click **Download PNG** or **Download SVG** to export.

No installation, build step, or command line needed.

## Dependencies

- **A modern web browser** — Chrome, Firefox, Edge, or Safari (roughly anything from the last 5 years). No plugins or extensions required.
- **[sql.js](https://sql.js.org/) v1.10.3** — SQLite compiled to WebAssembly, used to read the `.sqlite` file directly in the browser. This loads automatically from a CDN (`cdn.jsdelivr.net/npm/sql.js@1.10.3`) the first time the page opens.
  - **Requires internet access on first load** to fetch the sql.js library (~1 MB of JS + WASM). Most browsers cache it afterward, so subsequent loads work offline until the cache is cleared.
  - If you're behind a firewall/proxy that blocks `cdn.jsdelivr.net`, the page will fail to initialize — the status line will say "Loading SQL engine…" indefinitely.

Nothing else is required — no Python, no npm, no server. All rendering, data parsing, and export happens client-side in the browser; no data ever leaves your machine.

## Notes
- Expects the EFI-GNT SQLite schema (`attributes` and `neighbors` tables with `rel_start`/`rel_stop`/`direction`/`family`/`color`/`desc`/`accession` columns). Should not be a problem, if downloaded from EFI-GNT.
