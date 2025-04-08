# 6-product-sections-agent-showcase.md — Product Sections + Agentic Showcase

## Feature Title: Axovia Products + Agentic Systems Showcase

## Objective
Create beautiful, scrollable product sections that highlight Axovia’s key offerings:
- AI Agentic Systems as SaaS
- No-Code Development Tools
- Business Efficiency Software
- Chrome Extensions

Each product should be showcased in a modular and reusable card system.

---

## Components to Create

| Component | Purpose |
|-----------|---------|
| `ProductShowcaseSection` | Section wrapper with heading and layout grid |
| `AgentProductCard` | Modular card for each product feature |
| `HoverInteractionWrapper` | Shared hover/scale animation wrapper |
| `ProductCategoryTabs` | Optional segmented control to filter content |

---

## Product Categories

1. **Agentic Systems**
   - LangGraph agents
   - Orchestrator-Worker patterns
   - Social media automation agents

2. **No-Code Tools**
   - UI builders, prompt chains, page creation tools

3. **Business Software**
   - Analytics dashboards, time-saving workflows, custom CRMs

4. **Chrome Extensions**
   - Lightweight tools powered by Axovia AI APIs

---

## Visual Style
- Use neumorphic cards with soft outer shadows
- Include icon, short description, and "Learn More" or "Demo" button
- Grid layout should auto-wrap and animate in
- Cards should be animated into view via scroll triggers

---

## Agent Instructions

### Pre-Implementation
- [ ] Confirm layout shell is ready and `ThemeConstants` is used
- [ ] Check `component-registry.md` for reusable layout components

### Implementation
- Use Flutter `GridView`, `Wrap`, or `SliverGrid`
- Implement animation with `flutter_staggered_animations` or similar
- Each card must be < 280ms total entry time (performance budget)

### Post-Implementation
- [ ] Add 90%+ test coverage for layout + responsiveness
- [ ] Validate filter tab logic and empty-state behavior (if used)
- [ ] Update `component-registry.md` and `codebase-structure.md`
- [ ] Run post-task.md completion process

---

## Acceptance Criteria

As a **frontend agent**, I can:
- ✅ Display Axovia's main product categories in beautiful modular cards
- ✅ Ensure full mobile and desktop responsiveness
- ✅ Animate cards into view with performance-safe transitions
- ✅ Allow optional filtering via tabs
- ✅ Provide CTA paths from each card

---

## Notes
This is the “what we offer” section. It should make every product feel polished, exciting, and high-tech.

Cards will later link to subpages, demos, or lead forms.

> 🤖 Let each agent card feel like you're inviting someone to interact with real, living software intelligence.

