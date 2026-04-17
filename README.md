# 🔍 HAR Analyzer

> A self-contained HAR inspection tool built for Palo Alto Networks traffic. Drop a `.har` file and explore API calls, responses, and performance signals — **no backend, no install, no data leaves your browser.**

![HTML](https://img.shields.io/badge/HTML-Single%20File-orange?logo=html5&logoColor=white)
![Platform](https://img.shields.io/badge/platform-Browser-brightgreen?logo=googlechrome&logoColor=white)
![No Install](https://img.shields.io/badge/install-none%20required-success)
![Offline](https://img.shields.io/badge/offline-fully%20supported-blue)
![PANW](https://img.shields.io/badge/Palo%20Alto%20Networks-Support%20Tool-FF6600?logo=paloaltosoftware&logoColor=white)

---

## 🌐 Supported Platforms

| Platform | Domain | Coverage |
|---|---|---|
| **Cortex Cloud** | `*.paloaltonetworks.com` | CSPM fully supported. XSIAM, XDR, CAS, CWP, CIEM in progress. |
| **Prisma Cloud** | `*.prismacloud.io` | All core modules supported. DSPM, CAS, and CWP coverage expanding. |

---

## ✨ Features

**📂 Core**
- Drag-and-drop or browse to load HAR files — all processing stays in the browser
- Smart filtering: static assets, fonts, browser extensions, and Cortex background noise hidden by default
- Toggle **Full HAR View** to see every request in the file
- Endpoint grouping with lazy-rendered call details
- UUID/ID normalisation groups parametrised routes together

**🔬 Inspection**
- Per-call product-area label chip (e.g. `XQL Query`, `CIEM`, `Cloud Workload Protection`)
- Direct link to the [pan.dev](https://pan.dev) API reference page for each recognized CSPM endpoint
- Response body viewer with JSON syntax highlighting and copy-to-clipboard
- Payload viewer for request bodies
- Copy request as **cURL** command
- Status code badges with hover tooltips
- Slow request detection (>1500 ms), error highlighting (4xx/5xx)

**🔎 Filtering & Search**
- HTTP method filter bar (GET / POST / PUT / PATCH / DELETE)
- Full-text search across URLs and response bodies
- Clickable stat cards to filter by errors or slow requests
- Legend filter bar for badge-based filtering

**🎨 Export & UI**
- Markdown summary export
- 3 themes with persisted preference — Cortex Cloud, Prisma Cloud, PANW Orange
- Theme-matched favicon and header logo that swap automatically
- About, Documentation (Status Codes / Features / Roadmap), and retro Changelog modals
- Floating utility buttons (scroll-to-top, theme picker, about)

---

## 🚀 Usage

1. Open `har-analyzer.html` in any modern browser (double-click or drag into a tab)
2. Drop a `.har` file or click the upload zone
3. Use the stat cards, method filters, and search to narrow results
4. Click an endpoint group to expand individual calls; expand a call for full detail
5. Use the product-area chip to identify which Cortex/Prisma module each call belongs to
6. Export a Markdown summary or copy individual calls as cURL

---

## 🗺️ Roadmap

| Priority | Item | Status |
|---|---|---|
| 1 | Prisma Cloud endpoint coverage — DSPM, CAS, CWP | 🔄 In Progress |
| 2 | Cortex Cloud endpoint coverage — XSIAM, XDR, CAS | 🔄 In Progress |
| 3 | Extended API documentation links beyond CSPM | 📋 Planned |

---

## 📝 Notes

- ✅ Runs fully offline — no network calls, no telemetry
- ✅ Works best on up-to-date Chrome, Edge, Firefox, or Safari
- ✅ Category mapping built from **166 normalised endpoint patterns** across **14 real HAR files**
