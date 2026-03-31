A self-contained HAR inspection tool built for Palo Alto Networks traffic. Drop a `.har` file and explore API calls, responses, and performance signals — no backend, no install, no data leaves your browser.

## Supported Platforms

### Cortex Cloud (`*.paloaltonetworks.com`)
| Module | Coverage |
|---|---|
| XDR — Incidents, Alerts | `/api/webapp/incident*`, `/api/webapp/alerts` |
| XSIAM — Cases, XQL, XSOAR | `/api/webapp/case*`, `/api/webapp/xql`, `/xsoar/*` |
| CSPM — Cloud Security | `/api/cloudsec/v1` |
| CIEM | `/api/ciem/v1` |
| CAS — Code Security | `/api/cas/v1`, `/api/cas/v2` |
| CWP / Runtime | `/api/cwp/bff` |
| Vuln Management | `/api/uvm/v1`, `/api/webapp/uvm`, `/api/v1/vulnerabilities` |
| ASM | `/api/webapp/asm` |
| API Security | `/api/apisec` |
| AI Copilot | `/api/v1/agentix` |
| Asset Inventory | `/api/webapp/data-platform/unified-asset-inventory` |
| Contextual Search | `/api/webapp/data-platform/contextual-search-graph` |
| Data Classification (DSPM) | `/api/data-classification-settings` |
| Asset Network | `/api/v1/asset-network` |
| Cloud Onboarding | `/api/webapp/cloud_onboarding` |

### Prisma Cloud (`*.prismacloud.io`)
| Module | Coverage |
|---|---|
| CSPM | All API traffic from Prisma Cloud domain |
| CAS — Code Security | `/api/cas/v1`, `/api/cas/v2` |
| CWP / Runtime | `/api/cwp/bff` |
| Data Classification (DSPM) | `/api/data-classification-settings` |
| CIEM | `/api/ciem/v1` |

## Features

**Core**
- Drag-and-drop or browse to load HAR files — all processing stays in the browser
- Smart filtering: static assets, fonts, browser extensions, and Cortex background noise (notification polling, session sync, CSP reports) hidden by default
- Toggle **Full HAR View** to see every request in the file
- Endpoint grouping with lazy-rendered call details
- UUID/ID normalisation groups parametrised routes together

**Inspection**
- Per-call product-area label chip (e.g. "XQL Query", "CIEM", "Cloud Workload Protection")
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

## Notes

- Runs fully offline — no network calls, no telemetry
- Works best on up-to-date Chrome, Edge, Firefox, or Safari
- Category mapping built from 166 normalised endpoint patterns across 14 real HAR files
