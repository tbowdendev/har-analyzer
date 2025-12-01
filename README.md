# HAR Analyzer (single-file HTML)

A self-contained HAR inspection tool that runs entirely in your browser. Drop a `.har` file and explore requests, responses, and performance signals without any backend or installs.

## Features
- Drag-and-drop or browse to load HAR files locally (no network calls).
- Smart filtering to focus on API calls; toggle Full HAR View for everything.
- Interactive stats (errors/slow) and endpoint grouping with lazy-rendered details.
- Search URLs/bodies, view responses with syntax highlighting, copy JSON.
- Markdown export summary for quick sharing.
- Theme picker (7 themes) with persisted preference; floating utility buttons.
- About, Documentation (Status Codes / Features), and retro Changelog modals.

## Getting Started
1. Open `har-analyzer.html` in any modern browser (double-click or drag into a tab).  
2. Drop a `.har` file or click the upload zone to browse.  
3. Use the stat cards, filters, and search to narrow results; click endpoints to expand calls.  
4. Switch themes via the palette button; view About/Docs/Changelog from the floating buttons.  
5. Export a summary with the “Export Summary” button when needed.

## Notes
- Runs fully offline; all processing stays in the browser.
- Works best on up-to-date Chrome/Edge/Firefox/Safari.
- If icons appear off, ensure the file is opened locally without CSP restrictions and that emoji rendering is available (used for feature icons).

## Project Layout
- `har-analyzer.html` – the entire application (UI, logic, and styles).
- `CHANGELOG.md` – release notes and history.

## Contributing
- Please reach out to me directly using the "Contact" button in Har Analyzer to discuss contributing or feature requests.
