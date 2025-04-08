# 9-downloadable-pdf-section.md — PDF Downloads Area

## Feature Title: Downloadable Pitch Decks & PDF Library

## Objective
Give visitors easy access to downloadable PDFs:
- Show pitch decks, whitepapers, technical overviews
- Allow direct downloads and previews (responsive)
- Track engagement optionally via analytics or function ping

---

## Components to Create

| Component | Purpose |
|-----------|---------|
| `PdfDownloadSection` | Section wrapper for listing PDFs |
| `PdfCard` | Title, preview, download/view buttons |
| `PdfPreviewModal` | In-browser modal preview using iframe viewer |
| `DownloadTrackerService` | Firebase Cloud Function to log PDF downloads (optional)

---

## Content Requirements
- Support 3–5 PDFs minimum
- Titles: "Axovia Flow Framework", "Feature Prompt Examples", "Agentic System Designs"
- Show file size and document type icon
- Preview opens fullscreen iframe viewer (PDF.js or native)

---

## UI Behavior
- Cards animate into view
- On mobile, stacked vertical layout with large tap zones
- Downloads show loading state then browser save popup

---

## Agent Instructions

### Pre-Implementation
- [ ] Confirm `.env` has `PDF_STORAGE_PATH` or similar
- [ ] Ensure test PDFs are stored in Firebase Storage (emulated in dev)

### Implementation
- Use signed URLs from Firebase Storage (or emulator equivalent)
- Use Dart `http` or Storage SDK to access files
- Modal preview should scale and not crash mobile browsers

### Post-Implementation
- [ ] Validate mobile and desktop experience
- [ ] Add unit tests for tracker and download service
- [ ] Register PDF components in `component-registry.md`
- [ ] Complete `post-task.md`

---

## Acceptance Criteria

As a **marketing-oriented AI web dev**, I can:
- ✅ Display beautiful PDF cards with preview + download options
- ✅ Show PDF content inside a modal viewer
- ✅ Track or ping Firebase on download (optional analytics)
- ✅ Ensure responsive behavior across all devices

---

## Notes
This feature gives investors and leads something to take with them.
It should feel high-end, like a portfolio in their pocket.

> 🔖 Make these files feel like **artifacts of innovation.**

