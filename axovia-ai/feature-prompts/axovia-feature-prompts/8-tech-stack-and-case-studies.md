# 8-tech-stack-and-case-studies.md — Tech Stack + Case Study Block

## Feature Title: Tech Stack Highlight + Case Study Carousel

## Objective
Show off the elite technologies behind Axovia AI and share real-world case studies:
- Display logos of used technologies
- Feature real or simulated project case studies with results
- Reinforce credibility, performance, and innovation

---

## Components to Create

| Component | Purpose |
|-----------|---------|
| `TechStackBar` | Grid of tech badges (Firebase, Flutter, LangGraph, Python, etc.) |
| `CaseStudySection` | Container for all case study cards |
| `CaseStudyCard` | Modular card showing company, tech used, outcome |
| `ScrollRevealSection` | Reusable wrapper for entrance animation on scroll |

---

## Content Sources
- Pull logos from CDNs or local assets (SVGs)
- Include 3–5 case studies with:
  - Company Name (real or fake)
  - Problem / Solution / Result (short summary)
  - Agent pattern used (if relevant)
  - Tech stack badges inline

---

## Design Goals
- Stack bar must be **simple, dense, and immediately impressive**
- Case Study cards have neumorphic styling with strong CTA
- Cards animate up + fade on scroll into view
- Mobile must stack vertically and remain tappable

---

## Agent Instructions

### Pre-Implementation
- [ ] Confirm brand colors from `ThemeConstants`
- [ ] Check for tech logos in `assets/` or preload as needed

### Implementation
- Prefer local asset caching (no external calls on deploy)
- Responsive font scaling for tech tag labels
- Auto-wrap the tech grid on small viewports

### Post-Implementation
- [ ] Validate layout and transitions
- [ ] Add 90%+ test coverage for responsiveness and layout
- [ ] Register components in `component-registry.md`
- [ ] Complete `post-task.md`

---

## Acceptance Criteria

As a **tech-branding UI engineer**, I can:
- ✅ Display a responsive grid of all major tech used by Axovia
- ✅ Feature beautiful case studies with measurable value shown
- ✅ Ensure dark/light themes and mobile UX are solid
- ✅ Animate each block as user scrolls down

---

## Notes
This section is about **engineering pride** and business proof.

> 🔎 Let the code speak for itself — but also *show the wins*.

