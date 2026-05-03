# Changelog

All notable changes to this project are documented here. The app is a single-file HTML utility, so version bumps are tied to UI/UX fixes and feature polish.

## 1.4.5
- **Security: response bodies, request URLs, and `mimeType` strings are now HTML-escaped** before rendering. Previously, a HAR file that contained `<script>` or attribute-breakout HTML in any of those fields could execute when the corresponding endpoint group was expanded, breaking the "no data leaves the browser" guarantee.
- **Search now matches literal text** instead of treating dots, slashes, and other regex metacharacters as wildcards. The `escapeRegExp` helper was double-escaping its replacement string, so searches containing `.`, `/`, `?`, `(`, etc. silently returned zero hits.
- **Endpoint groups with many calls no longer clip.** Expanded groups grow to fit their full content via JS-managed `max-height`; the previous CSS cap of `10000px` with `overflow: hidden` made every call past ~12 unreachable in 1.4 (cards got taller in 1.4, the cap got hit faster).
- **Copy cURL / Copy JSON now work in Firefox older than v113** and any browser without `window.event`. The button is now passed explicitly via `this` in the inline `onclick`; previously the fallback path silently swallowed a `ReferenceError` and left the button stuck.
- **Copy buttons no longer flicker on rapid double-click.** The pending revert timer is cancelled before scheduling a new one.
- **cURL output now properly escapes single quotes** in URLs and header values (`postData` was already escaped). Curl output for a request to a URL containing `'` is now valid shell.
- **`FileReader.onerror` handler.** If reading the file itself fails (unreadable disk, permission error), the spinner is cleared and a clear error is shown instead of leaving the UI hung.
- **Malformed HAR entries are filtered, not fatal.** Entries missing required fields (`request`, `request.url`, `response.content`) are skipped at parse time rather than failing the whole file. If every entry is malformed, a clear error is shown.
- **Sequential view: invalid `startedDateTime` sorts to the end** of the list, instead of being treated as Unix epoch 1970 and pushed to the top.
- **Negative or unknown request times are shown as `n/a`** instead of `-1ms`.
- **Clear button now resets the Highlight matches checkbox** alongside the rest of the state.
- **Stat cards (Total / Errors / Slow / Endpoints) all reflect the active filter together.** Clicking the Errors card now narrows every count to only matching entries; previously only Endpoints narrowed and the rest stayed at the pre-filter values.
- **Status 0 (network failure) counts as an error.** HAR entries with a status of 0 — blocked, CORS-rejected, DNS-failed, or aborted before any response — are now classified as errors, matched by the Errors filter, badged in red, and documented in the Status Codes tab.
- **Filtered/Full and Grouped/Sequential toggle buttons keep their active gradient in both states.** Previously the gradient only showed in the default state, making the button look disabled in the alternate state.
- **File picker now rejects non-`.har` files** with a clear error message, matching the existing drag-and-drop validation. Both checks are now case-insensitive (`.HAR` works on Windows).
- **Documentation Features tab** now lists all 1.4 features (Inline Headers, Sequential Layout, Per-Call Timestamps, Export Summary & Copy with HTTP/HTTPS support).
- **Accessibility:** icon-only floating buttons (theme picker, about, scroll-to-top) now have `aria-label` and `title` attributes so screen readers and tooltips announce them properly.

## 1.4
- **Request and Response headers** are now displayed inline on every API call card. Collapsible sections (collapsed by default) reveal a name/value table for each. Trace-ID-style headers (`x-trace-id`, `x-request-id`, `x-correlation-id`, `x-amzn-requestid`, `cf-ray`, etc.) are visually highlighted so they're easy to spot.
- **Sequential layout mode.** New toggle in the controls bar — 📚 Grouped ↔ ⏱ Sequential. Sequential view sorts entries by `startedDateTime` and renders them as a flat chronological list. Honors all existing filters (errors, slow, method, search). Caps at 500 entries with a "refine filters to see more" banner for very large HARs.
- **Explicit start timestamps** on every API call card. Local time formatted as `HH:MM:SS.mmm` next to the existing duration. Hover the timestamp to see the full ISO string for paste into log tools.
- **Clipboard buttons fixed for HTTP deployments.** Copy cURL, Copy JSON, and Export Summary previously silently failed when the tool was hosted on plain HTTP, because the modern Clipboard API only works in secure contexts. Added a `document.execCommand('copy')` fallback so they work everywhere.

## 1.3
- **Cortex Cloud theme:** black header bar with a 2px green bottom border, green-600 accent, flat slate surfaces, no glass morphism, no animated gradient background.
- **Prisma Cloud theme:** black header bar with a 2px cyan bottom border, cyan-600 accent, flat slate surfaces, Prisma Cloud branding.
- **PANW Orange theme:** black header bar with a 2px orange bottom border, orange-600 accent, flat slate surfaces, dedicated PANW logo, and a "Cloud Support Tool" subtitle.
- **Theme system trimmed:** removed legacy themes (Dark Purple, Light, Cyberpunk, Sunset, Forest); the picker now ships with just Cortex Cloud, Prisma Cloud, and PANW Orange.
- **Default theme is Cortex Cloud.** Invalid or stale saved themes fall back cleanly instead of failing silently.
- **Auto-detection:** loading a HAR file detects whether it contains Cortex (`paloaltonetworks.com`) or Prisma (`prismacloud.io`) traffic and switches to the matching theme.
- **Dynamic header** — logo and subtitle swap between Cortex Cloud / Prisma Cloud / PANW Orange / default based on the active theme.
- **Theme-matched favicon** — the browser tab icon swaps to match the active theme (green / cyan / orange).
- **About modal icon** — now displays the active theme's logo instead of a static mark.

## 1.2
- **API documentation links:** every API call card now shows a direct link to the relevant pan.dev CSPM endpoint reference page.
- Path normalization and progressive fallback — calls with specific resource IDs (alert IDs, account IDs, UUIDs) resolve to the correct parent endpoint doc.
- Correct slug generation for versioned paths (`v2`, `v3` → `v-2`, `v-3`) matching pan.dev URL conventions.

## 1.1
- **Cortex Cloud noise filtering:** background requests (notification polling, UI persistent storage, XSOAR session sync, CSP violation reports) are now suppressed in filtered view.
- **Cortex Cloud product-area labels:** every API call card shows a module chip (XQL Query, CIEM, Cloud Security, Cloud Workload Protection, Code Security, Vuln Management, API Security, Data Classification, AI Copilot, Asset Inventory, Contextual Search, XSOAR Automation, XSOAR Incident, XSOAR Case, XSOAR Playbook, and more).
- Category mapping built from real HAR traffic — 166 normalized endpoint patterns captured across 14 HAR files.
- **Legend bar filters:** clicking any badge in the legend bar now filters results to that badge type (2xx, 3xx, 4xx, 5xx, slow, empty, no response).
- **Payload viewer:** request body content is now viewable inline on each API call card with JSON syntax highlighting.
- **Tooltip arrow fix:** status badge tooltips now display with correct arrow positioning across all themes.

## 1.0.0
- Added HTTP method filter bar (GET, POST, PUT, PATCH, DELETE toggle buttons).
- Added "Copy as cURL" button on every API call card for quick endpoint reproduction.
- Added hover tooltips on status badges showing human-readable descriptions (e.g., "404 — Not Found").
- Added always-visible status/badge legend bar below the stats dashboard.
- Replaced `alert()` error handling with a styled error modal and added HAR validation guards.
- Added in-app feedback form modal (Google Form embed, replacing mailto link).
- Removed alpha disclaimer; updated to stable release status.

## 1.0.0-rc.2
- Added "EMPTY" badge for API calls that return 2xx with no response body.
- Empty response count displayed in endpoint group headers.
- Fixed broken icons (stopwatch/document) in API call details.
- Fixed domain allowlist filter to stop excluding empty 200 responses.
- Added EMPTY badge documentation to the Documentation modal.

## 1.0.0-rc.1
- Fixed the documentation modal backdrop/stacking and ensured About → Documentation/Changelog buttons open their modals.
- Constrained and centered the upload zone to stop it from covering the page layout.
- Restored feature icons in the Documentation → Features tab.

## 1.0.0-beta.3
- Polished UI for floating buttons so they no longer overlap modals.
- Updated About modal version display and refined interactions.

## 1.0.0-beta.2
- Smoothed expand/collapse animation timing.
- Slowed transition speed for clearer visual feedback.
- Improved rendering logic to prevent layout jumps.

## 1.0.0-beta.1
- Major performance improvement with lazy rendering of API calls.
- Added debounced search for smoother filtering.
- Reduced memory usage for large HAR files and cleaned the codebase.

## 0.8.4a
- Added the Documentation modal with tabbed Status Codes and Features.
- Documented badge colors/meanings and app capabilities.
- Improved About modal layout.

## 0.7.4a
- Added “NO RESPONSE” badge for failed requests with empty bodies and improved error visibility.

## 0.7.3a
- Added theme-aware background gradients and refined PANW Orange/Prisma Cloud themes.
- Saved theme preferences to localStorage.
- Completed the theme system (7 themes).

## 0.7.2a
- Added theme picker UI and palette button.

## 0.6.2a
- Added smart domain allowlist filtering and interactive stat-card filtering.
- Fixed error display to show all errors regardless of content-type.

## 0.6.1a
- Added floating scroll-to-top button and About modal.
- Added terminal-style changelog modal.
- General UI polish.

## 0.6.0a
- Full rebuild with core features and smart filtering for API calls.
- Interactive stat cards and bug fixes.

## 0.5.0a
- Added endpoint grouping and collapsible sections.

## 0.4.0a
- Added search and response body viewing with syntax highlighting.

## 0.3.0a
- Added statistics dashboard, error/slow detection, improved filtering.

## 0.2.0a
- Initial HAR parsing with request/response display and basic UI.

## 0.1.0a
- Initial release with file upload support.
