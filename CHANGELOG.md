# Changelog

All notable changes to this project are documented here. The app is a single-file HTML utility, so version bumps are tied to UI/UX fixes and feature polish.

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
