# 3-ui-shell-neumorphism.md — Neumorphic Layout + Theme Engine

## Feature Title: Responsive UI Shell with Neumorphism + Theme Toggle

## Objective
Establish the global layout engine for the Axovia AI website:
- Design and implement a neumorphism-inspired UI shell
- Integrate dark/light theme toggle across all components
- Ensure all future pages follow this responsive layout

> ✨ This will define the Axovia visual identity: clean, elegant, futuristic.

---

## Components to Create

| Component | Purpose |
|-----------|---------|
| `DashboardScaffold` | Global layout wrapper: header, sidebar, content pane |
| `ThemeConstants` | Centralized color palette, spacing, fonts, and shadows |
| `ThemeController` | Theme toggle controller with persistence (localStorage) |
| `ResponsiveLayout` | Auto-switch column/row layout based on screen width |
| `AxoviaSwitch` | Custom neumorphic toggle UI for switching themes |
| `DarkLightIcon` | Adaptive icon that animates between sun/moon |

---

## Design Constraints
- Neumorphism should be **subtle**, **clean**, and **performance-friendly**
- Use soft light/shadow insets and convex shapes
- Ensure contrast meets accessibility standards (AA/AAA)
- Animation must not cause jank or frame drops on mobile

---

## Style Guidelines (ThemeConstants)
- Primary: `#6E00FF` (Axovia Purple)
- Surface: `#F0F2F5` light / `#181A1F` dark
- Text: `#111111` light / `#EEEEEE` dark
- Elevation shadows: `BoxShadow(offset: Offset(6,6), blur: 16)`
- Fonts: `Inter`, `Work Sans`
- Rounded corners: `24px`
- Border radius scale: `xs (4) sm (8) md (16) lg (24)`

---

## Feature Behavior
- Website starts in `system` theme mode
- Toggle can override with persistent preference
- All layouts are responsive:
  - Desktop: Sidebar + Header
  - Tablet: Collapsed sidebar
  - Mobile: Topbar-only layout

---

## Agent Instructions

### Pre-Implementation
- [ ] Complete `pre-task.md` fully
- [ ] Confirm no duplicate layout systems or themes exist
- [ ] Check `component-registry.md` before creating new components

### Implementation
- Use `Provider` or `Riverpod` for global state
- Write reusable, animated neumorphic widgets
- Avoid performance regressions (test in release mode)

### Post-Implementation
- [ ] Complete `post-task.md` verification
- [ ] Update `component-registry.md` with layout + theme components
- [ ] Ensure test coverage of layout logic + toggling behavior

---

## Acceptance Criteria

As a **frontend-focused AI assistant**, I can:
- ✅ Create a flexible `DashboardScaffold` with slot injection
- ✅ Implement a full-featured light/dark theme engine
- ✅ Use soft neumorphic effects that feel futuristic but fast
- ✅ Provide responsive layout shifts (desktop → mobile)
- ✅ Persist user theme preference using local storage
- ✅ Test and validate performance across screen sizes

---

## Notes
This layout and theme system will serve as the design backbone for the Axovia AI website. It must be:
- Pixel-perfect
- Lightweight and animated
- Memorable and scalable

Once complete, it will be used by all future sections: Hero, Product Cards, Calendly Form, Blog, etc.

