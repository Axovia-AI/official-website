# 4-hero-section-and-branding.md — Hero Section + Brand Identity

## Feature Title: Homepage Hero Section and Brand Anchor

## Objective
Create the first visual impression of Axovia AI:
- Bold hero section with logo, name, and tagline
- Engaging CTA button (e.g. "Book a Demo")
- Animated, responsive branding block
- Establish Axovia AI’s voice as elite, modern, and agentic

---

## Components to Create

| Component | Purpose |
|-----------|---------|
| `HeroSection` | Main section for intro text, logo, animation, CTA |
| `AnimatedTitleText` | Animated headline that types or pulses |
| `BrandLogoGlow` | Axovia brand logo with glow + hover pulse |
| `PrimaryCTAButton` | Stylized button linked to booking or contact page |

---

## Visual Guidelines
- Use neumorphic container as a base
- Axovia purple highlight (`#6E00FF`) with gradient fade-in
- Hero height: 75–85% viewport height on desktop
- Responsive font sizing with `MediaQuery`
- Scroll-down arrow on mobile

---

## Behavior
- On page load, title animates in (slide or fade+type)
- Logo pulses subtly when hovered
- CTA scrolls to Contact section or opens modal
- Should animate in under 1.5 seconds (no long delays)

---

## Agent Instructions

### Pre-Implementation
- [ ] Confirm `2-ui-shell-neumorphism.md` is complete
- [ ] Confirm `ThemeConstants` is being used for styling
- [ ] Load `design-system.md` for fonts, radius, shadow spacing

### Implementation
- Wrap everything in `DashboardScaffold`
- All sizing must be responsive with `LayoutBuilder`
- Use `flutter_animate` or implicit animations (no frame drops)

### Post-Implementation
- [ ] Add full unit tests for text, layout, and responsiveness
- [ ] Add screenshot tests for light and dark themes
- [ ] Update `component-registry.md`
- [ ] Complete `post-task.md` and push

---

## Acceptance Criteria

As a **branding-oriented UI engineer**, I can:
- ✅ Render a beautiful hero section with animation and clean layout
- ✅ Display the Axovia AI brand in both light and dark themes
- ✅ Provide a working CTA button that scrolls or opens modal
- ✅ Make it mobile-optimized and animated without lag
- ✅ Ensure theme toggle still works with Hero styling

---

## Notes
This is the first impression of Axovia.ai — the "above the fold" experience that must:
- Communicate confidence
- Invite interaction
- Radiate visual precision

> ⚠️ If this section doesn't look elite — stop and redesign before continuing the site.

