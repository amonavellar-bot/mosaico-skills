# Changelog

All notable changes to this project will be documented in this file.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
Versioning follows [Semantic Versioning](https://semver.org/).

---

## [1.1.0] — 2026-05-27

### Fixed

- `checklist-abnt.md` — added item numbers (5.X.X format) to all 146 items across 16 sections, enabling precise citations in the format required by SKILL.md; added explicit WCAG 3.3.8 cross-reference to item 5.9.16
- `patterns-web.md` — implemented complete focus trap in HTML modal (Tab/Shift+Tab cycle, ESC key, focus return to trigger); fixed `role="alert"` + `aria-live="polite"` conflict in HTML and React live region examples (changed to `role="status"`); fixed Angular custom component to use native `button[app-opcao]` selector instead of `role="button"` on host; fixed Vue accordion to use `:hidden` attribute instead of `v-show` for semantic correctness across all AT/browser combinations
- `patterns-mobile.md` — added missing `excludeSemantics: true` parameter to Flutter `Semantics` example; resolved React Native live region conflict (`accessibilityRole="alert"` removed from `accessibilityLiveRegion="polite"` context); corrected SwiftUI hint guidance to descriptive form per Apple HIG
- `ciandt-context.md` — added European Accessibility Act (EAA, Directive 2019/882) with June 2025 private-sector compliance deadline; clarified disability statistics with Censo 2022 context alongside PNS 2019 dual-methodology explanation
- `SKILL.md` — added Platform Ambiguity fallback section with instructions for detecting platform from code clues and requesting clarification when ambiguous

### Added

- `patterns-web.md` — complete React Modal focus trap component with `useFocusTrap` pattern; new SPA Routing Focus Management section with working examples for React Router, Vue Router, and Angular Router
- `patterns-mobile.md` — Quick Reference: Common Mistakes table covering all four mobile platforms (React Native, Flutter, iOS, Android)
- `wcag-quick-ref.md` — official W3C spec URL, last-reviewed date, version note for future updates

---

## [1.0.0] — 2026-05-26

### Added

- `mosaico-dev` plugin — initial release
- **Review mode**: categorized accessibility audit (Perceivable, Operable, Understandable, Robust — aligned with WCAG 2.2 principles) with before/after code, standard references, and three-tier severity labels
- **Build mode**: proactive accessibility checklist and code templates before feature development
- **Explain mode**: plain-language explanations for accessibility concepts with code examples
- `SKILL.md` — skill behavior definition with Correction Walkthrough format and tone guide
- `wcag-quick-ref.md` — complete WCAG 2.2 reference (78 success criteria, all levels)
- `checklist-abnt.md` — ABNT NBR 17225 reference (146 items across 16 sections)
- `patterns-web.md` — accessible before/after code examples for HTML, React, Vue, Angular
- `patterns-mobile.md` — accessible before/after code examples for React Native, Flutter, iOS (SwiftUI), Android (Jetpack Compose)
- `ciandt-context.md` — CI&T internal context: Oráculo da Acessibilidade, contacts, Brazilian law overview, assistive tech guide, validation tools
- Bilingual support (Portuguese and English)
