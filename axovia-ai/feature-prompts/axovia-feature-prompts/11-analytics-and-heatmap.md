# 11-analytics-and-heatmap.md — Analytics + Visitor Behavior

## Feature Title: Analytics Integration + Optional Heatmap Tracking

## Objective

Implement tools to monitor site performance and user behavior:

- Integrate Google Analytics (GA4) for pageviews and events
- (Optional) Integrate Hotjar / PostHog for heatmaps and recordings
- Validate with CI-friendly configuration + `.env` support

---

## Components / Files to Modify

| File                                  | Purpose                                         |
| ------------------------------------- | ----------------------------------------------- |
| `lib/services/analytics_service.dart` | Wrapper for sending events                      |
| `lib/main.dart`                       | Initialize analytics based on ENV               |
| `.env`                                | Add `GA_MEASUREMENT_ID`, `ENABLE_HEATMAPS`      |
| `firebase.json`                       | Set security headers (CSP for external scripts) |

---

## Analytics Requirements

- Track pageviews, scroll depth, button clicks (e.g. CTA, PDF download)
- Track conversion event: contact form submit
- Respect GDPR/CCPA (show cookie opt-in for EU IPs — future task)

---

## Heatmap Options (Optional + Configurable)

- Embed Hotjar or PostHog via JS injection in HTML
- Enable via `.env` toggle: `ENABLE_HEATMAPS=true`
- Use anonymized visitor ID when possible
- Disable in dev/staging automatically

---

## Agent Instructions

### Pre-Implementation

-

### Implementation

- Send custom events with `AnalyticsService.track()`
- Only init analytics on `ENV=production`
- Confirm deployment builds include JS safely (no console errors)

### Post-Implementation

-

---

## Acceptance Criteria

As a **data-driven dev**, I can:

- ✅ Track pageviews and form submissions via GA4
- ✅ Toggle analytics + heatmaps from `.env`
- ✅ Disable tracking in non-prod builds
- ✅ See visual behavior if heatmaps are active

---

## Notes

You can’t optimize what you don’t measure.\
Start with GA4 and build up to deeper insights over time.

> 📊 Watch the scroll. Feel the clicks. Learn what converts.

