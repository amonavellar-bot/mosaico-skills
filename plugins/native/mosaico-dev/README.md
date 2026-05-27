# mosaico-dev

Accessibility skill for Claude Code — CI&T Mosaico group.

Audits code for accessibility issues and guides feature design on web and mobile platforms, based on WCAG 2.2 and ABNT NBR 17225.

## Skills

| Skill | Invocation | Description |
|---|---|---|
| `accessibility` | `/mosaico-dev:accessibility` | Accessibility audit (review mode) and proactive checklist (build mode) |

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

## Example

**Input** — an inaccessible React login form:

```jsx
export function LoginForm() {
  return (
    <div style={{ color: '#aaa', background: '#fff' }}>
      <div onClick={() => alert('close')}>X</div>
      <input type="text" placeholder="Digite seu email" />
      <input type="password" placeholder="Digite sua senha" />
      <div onClick={() => console.log('login')} style={{ background: '#ccc', padding: 8 }}>
        Entrar
      </div>
      <img src="logo.png" />
    </div>
  );
}
```

Prompt: `Revisar acessibilidade nesse componente:`

**Output** — categorized audit with 6 issues found:

```
### Visual
Issue 1 — Low contrast: #aaa on #fff = 2.3:1 (required: 4.5:1)
WCAG 2.2 — 1.4.3 Contrast (Minimum), Level AA
ABNT NBR 17225 — Seção 11, Requisito

### Motor
Issue 2 — <div> as close button: not keyboard reachable, no Enter/Space support
WCAG 2.2 — 2.1.1 Keyboard, Level A

Issue 3 — <div> as submit button: same problem
WCAG 2.2 — 2.1.1 Keyboard, Level A / 4.1.2 Name, Role, Value, Level A

### Cognitive
Issue 4 — Placeholders as labels: disappear on type, no persistent label
WCAG 2.2 — 1.3.1 Info and Relationships, Level A

### Assistive Tech
Issue 5 — <img> with no alt: screen reader announces filename
WCAG 2.2 — 1.1.1 Non-text Content, Level A

Issue 6 — No <form> element: no form landmark, Enter-to-submit broken
WCAG 2.2 — 1.3.1 Info and Relationships, Level A
```

Each issue includes a before/after code fix and a Priority Summary
([Required] vs [Recommended]) at the end.

---

## Platforms supported

- **Web:** HTML, React (JSX), Vue, Angular
- **Mobile:** React Native, Flutter, iOS (SwiftUI), Android (Jetpack Compose)

## Standards

- WCAG 2.2 (78 success criteria — Level A, AA, AAA)
- ABNT NBR 17225:2024 (146 items across 16 sections)
- eMAG (Brazilian government accessibility model)

## Maintainer

Amon Avellar — [amon.avellar@ciandt.com](mailto:amon.avellar@ciandt.com) — CI&T Mosaico group
