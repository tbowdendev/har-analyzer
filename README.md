A self-contained HAR inspection tool built for Palo Alto Networks traffic. Drop a `.har` file and explore API calls, responses, and performance signals — no backend, no install, no data leaves your browser.

## Supported Platforms

### Cortex Cloud (`*.paloaltonetworks.com`)
CSPM is fully supported. Additional modules (XSIAM, XDR, CAS, CWP, CIEM, and more) are in progress.

### Prisma Cloud (`*.prismacloud.io`)
All Prisma Cloud modules are supported. DSPM, CAS, and CWP coverage is partial — endpoint mapping continues to expand with real HAR traffic.

## Features

**Core**
- Drag-and-drop or browse to load HAR files — all processing stays in the browser
- Smart filtering: static assets, fonts, browser extensions, and Cortex background noise (notification polling, session sync, CSP reports) hidden by default
- Toggle **Full HAR View** to see every request in the file
- Endpoint grouping with lazy-rendered call details
- UUID/ID normalisation groups parametrised routes together

**Inspection**
- Per-call product-area label chip (e.g. "XQL Query", "CIEM", "Cloud Workload Protection")
- Direct link to the pan.dev API reference page for each recognized CSPM endpoint
- Response body viewer with JSON syntax highlighting and copy-to-clipboard
- Payload viewer for request bodies
- Copy request as **cURL** command
- Status code badges with hover tooltips (human-readable descriptions)
- Slow request detection (>1500 ms), error highlighting (4xx/5xx)

**Filtering & Search**
- HTTP method filter bar (GET / POST / PUT / PATCH / DELETE)
- Full-text search across URLs and response bodies
- Clickable stat cards to filter by errors or slow requests
- Legend filter bar for badge-based filtering

**Export & UI**
- Markdown summary export
- 7 themes with persisted preference (Dark Purple, Light, Cyberpunk, Sunset, Forest, PANW Orange, Prisma Cloud)
- About, Documentation (Status Codes / Features), and retro Changelog modals
- Floating utility buttons (scroll-to-top, theme picker, about)

## Usage

1. Open `har-analyzer.html` in any modern browser (double-click or drag into a tab)
2. Drop a `.har` file or click the upload zone
3. Use the stat cards, method filters, and search to narrow results
4. Click an endpoint group to expand individual calls; expand a call for full request/response detail
5. Use the product-area chip to identify which Cortex/Prisma module each call belongs to
6. Export a Markdown summary or copy individual calls as cURL

## Upcoming

- Expand Cortex Cloud module coverage — additional endpoint mapping for XSIAM, XDR, and CAS
- Expand Prisma Cloud coverage — deeper endpoint mapping for DSPM, CAS, and CWP modules
- Extend API documentation links to cover additional endpoint categories beyond CSPM
- Custom branding support — allow swapping in company-provided logos and accent colors

## Notes

- Runs fully offline — no network calls, no telemetry
- Works best on up-to-date Chrome, Edge, Firefox, or Safari
- Category mapping built from 166 normalised endpoint patterns across 14 real HAR files
