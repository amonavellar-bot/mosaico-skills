# Changelog — mosaico-dev

## [1.1.0] — 2026-05-27

### Fixed

- `checklist-abnt.md` — item numbers (5.X.X) added to all 146 items; WCAG 3.3.8 cross-reference added to item 5.9.16
- `patterns-web.md` — HTML modal focus trap complete; `role="alert"` + `aria-live` conflict resolved; Angular native `button` selector; Vue accordion uses `:hidden`
- `patterns-mobile.md` — Flutter `excludeSemantics: true` added; React Native live region conflict resolved; SwiftUI hint guidance corrected per Apple HIG
- `ciandt-context.md` — EAA 2019/882 added with June 2025 deadline; IBGE Censo 2022 statistics added alongside PNS 2019 with dual-methodology context
- `SKILL.md` — Platform Ambiguity fallback section added

### Added

- `patterns-web.md` — React Modal with complete focus trap; SPA Routing Focus Management (React Router, Vue Router, Angular Router)
- `patterns-mobile.md` — Quick Reference: Common Mistakes table (all four platforms)
- `wcag-quick-ref.md` — official W3C URL, last-reviewed date, version note

---

## [1.0.0] — 2026-05-26

### Added

- Review mode: categorized audit (Perceivable, Operable, Understandable, Robust — aligned with WCAG 2.2 principles) with Correction Walkthrough format and three-tier severity labels
- Build mode: proactive checklist and code templates before feature development
- Explain mode: plain-language explanations for accessibility concepts with code examples
- `SKILL.md` — skill behavior, tone guide, and reference file manifest
- `wcag-quick-ref.md` — WCAG 2.2 reference (78 success criteria, all levels)
- `checklist-abnt.md` — ABNT NBR 17225:2024 reference (146 items, 16 sections)
- `patterns-web.md` — before/after code examples for HTML, React, Vue, Angular
- `patterns-mobile.md` — before/after code examples for React Native, Flutter, iOS, Android
- `ciandt-context.md` — CI&T internal context, tools, contacts, and legal overview
- Bilingual support (Portuguese and English)
