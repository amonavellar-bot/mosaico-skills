# mosaico-dev

Accessibility skill for Claude Code — CI&T Mosaico group.

Audits code for accessibility issues and guides feature design on web and mobile platforms, based on WCAG 2.2 and ABNT NBR 17225.

## Skills

| Skill | Invocation | Description |
|---|---|---|
| `mosaico-dev` | `/mosaico-dev:mosaico-dev` | Accessibility audit (review mode) and proactive checklist (build mode) |

## Usage

The skill activates automatically when Claude detects accessibility-related intent. No slash command needed.

**Review mode** — share code and ask for a review:
```
Revisar acessibilidade nesse componente:
<button onClick={handleClose}>X</button>
```

**Build mode** — describe a feature before building it:
```
I'm building a modal with a form inside. What should I consider for accessibility?
```

## Platforms supported

- **Web:** HTML, React (JSX), Vue, Angular
- **Mobile:** React Native, Flutter, iOS (SwiftUI), Android (Jetpack Compose)

## Standards

- WCAG 2.2 (78 success criteria — Level A, AA, AAA)
- ABNT NBR 17225:2024 (146 items across 16 sections)
- eMAG (Brazilian government accessibility model)

## Maintainer

Amon Avellar — [amon.avellar@ciandt.com](mailto:amon.avellar@ciandt.com) — CI&T Mosaico group
