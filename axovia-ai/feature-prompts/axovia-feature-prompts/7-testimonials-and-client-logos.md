# 7-testimonials-and-client-logos.md — Social Proof Block

## Feature Title: Testimonials & Client Trust Signals

## Objective
Add social credibility to the Axovia AI homepage:
- Display testimonials from early users or clients (real or placeholder)
- Include client logos / badges of tools / integrations
- Showcase trust and quality with visual elegance

---

## Components to Create

| Component | Purpose |
|-----------|---------|
| `TestimonialSection` | Main wrapper for the block |
| `TestimonialCard` | Individual review component with quote + name/photo |
| `ClientLogoBar` | Row of grayscale logos that animate into color on hover |
| `AutoScrollCarousel` | Optional — auto-advancing carousel of cards |

---

## Design Constraints
- Neumorphic testimonial cards with light elevation
- 3 cards visible on desktop, swipeable on mobile
- Quote text, avatar (real or AI-generated), and user title
- Logos should desaturate and brighten on hover (color reveal)

---

## Testimonial Types
- Can be user quotes, internal founder message, or product screenshots
- Allow placeholder testimonials until real ones are imported
- Include 5 minimum (loopable)

---

## Agent Instructions

### Pre-Implementation
- [ ] Load design-system + theme constants
- [ ] Confirm testimonial data format (JSON or inline)

### Implementation
- Use `ListView` or `PageView` for carousel (if used)
- Fade+scale testimonials in from bottom as they enter viewport
- Logo bar should be horizontally scrollable and responsive

### Post-Implementation
- [ ] Validate layout on mobile + desktop
- [ ] Add dummy data if real data unavailable
- [ ] Update `component-registry.md`
- [ ] Complete `post-task.md`

---

## Acceptance Criteria

As a **credibility-focused UI engineer**, I can:
- ✅ Render 3–5 testimonials in a swipeable carousel
- ✅ Animate logos and quote cards cleanly
- ✅ Use placeholders that can be updated later
- ✅ Support responsiveness and dark mode

---

## Notes
This section establishes Axovia as a trusted brand.

> 🌌 Make it feel like the future *already trusts* Axovia — even before a client clicks anything.

