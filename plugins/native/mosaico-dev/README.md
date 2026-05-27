# mosaico-dev

Accessibility skill for Claude Code — CI&T Mosaico group.

Audits code for accessibility issues, guides feature design on web and mobile platforms, and explains accessibility concepts — based on WCAG 2.2 and ABNT NBR 17225.

## Skills

| Skill | Manual invocation | Description |
|---|---|---|
| `accessibility` | `/mosaico-dev:accessibility` | Accessibility audit (review mode), proactive checklist (build mode), and concept explanations (explain mode) |

## Installation

```bash
# 1. Register the marketplace
claude plugin marketplace add amonavellar-bot/mosaico-skills

# 2. Install the plugin
claude plugin install mosaico-dev
```

Or locally from a cloned repo:

```bash
git clone https://github.com/amonavellar-bot/mosaico-skills.git
claude plugin marketplace add ./mosaico-skills
claude plugin install mosaico-dev
```

## Usage

**The skill activates automatically.** Claude detects accessibility-related intent in your prompts and triggers the skill without any command — just write naturally in Portuguese or English.

If you need to invoke it explicitly:

```
/mosaico-dev:accessibility
```

**Review mode** — share code and ask for a review:
```
Revisar acessibilidade nesse componente:
<button onClick={handleClose}>X</button>
```

**Build mode** — describe a feature before building it:
```
I'm building a modal with a form inside. What should I consider for accessibility?
```

**Explain mode** — ask a concept question:
```
O que é focus trap e quando devo usar?
```
```
What is ARIA and when should I reach for it?
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

**Output** — categorized audit, 6 issues found:

---

### Perceivable

Here's an opportunity to improve the accessibility of this `<div>` container.

**Who is affected:** Someone with low vision will have trouble reading — the text color `#aaa` on white background has a contrast ratio of 2.3:1, well below the required 4.5:1.

> WCAG 2.2 — 1.4.3 Contrast (Minimum), Level AA
> ABNT NBR 17225 — Item 5.11.3, Requisito

```jsx
// Before
<div style={{ color: '#aaa', background: '#fff' }}>

// After — contrast ratio now 7:1
<div style={{ color: '#555', background: '#fff' }}>
```

Here's an opportunity to improve the accessibility of this `<img>`.

**Who is affected:** Someone using a screen reader will hear the filename announced ("logo.png") instead of a meaningful description, or nothing at all.

> WCAG 2.2 — 1.1.1 Non-text Content, Level A

```jsx
// Before
<img src="logo.png" />

// After — logo conveys brand identity, so it gets a descriptive alt
<img src="logo.png" alt="Mosaico logo" />

// If the image were purely decorative, use alt="" to tell screen readers to skip it:
// <img src="logo.png" alt="" />
```

---

### Operable

Here's an opportunity to improve the accessibility of this close `<div>`.

**Who is affected:** Someone navigating by keyboard cannot reach or activate this element — `<div>` elements are not in the tab order and don't respond to Enter or Space.

> WCAG 2.2 — 2.1.1 Keyboard, Level A
> ABNT NBR 17225 — Item 5.1.13, Requisito

```jsx
// Before
<div onClick={() => alert('close')}>X</div>

// After — <button> is focusable, keyboard-operable, and announces its role to screen readers
<button type="button" aria-label="Fechar" onClick={() => alert('close')}>X</button>
```

---

### Understandable

Here's an opportunity to improve the accessibility of these `<input>` fields.

**Who is affected:** Someone with a cognitive disability — or anyone who pauses mid-form — loses the field label as soon as they start typing, because placeholders disappear on input.

> WCAG 2.2 — 1.3.1 Info and Relationships, Level A

```jsx
// Before
<input type="text" placeholder="Digite seu email" />

// After — visible <label> persists while the user types
<label htmlFor="email">Email</label>
<input id="email" type="email" placeholder="ex: nome@empresa.com" />
```

---

### Robust

Here's an opportunity to improve the accessibility of this form structure.

**Who is affected:** Someone using a screen reader won't be able to identify this as a form landmark, and pressing Enter to submit won't work — there's no `<form>` element wrapping the inputs.

> WCAG 2.2 — 1.3.1 Info and Relationships, Level A

```jsx
// Before
<div onClick={() => console.log('login')} style={{ background: '#ccc', padding: 8 }}>
  Entrar
</div>

// After — semantic <form> + <button type="submit"> enable keyboard submission and screen reader landmark
<form onSubmit={handleLogin}>
  ...
  <button type="submit">Entrar</button>
</form>
```

---

**Priority Summary**

| Severity | Issues |
|---|---|
| [Blocker — Level A] | Missing alt text · `<div>` as close button · `<div>` as submit button · No `<form>` element · Placeholders as sole labels |
| [Required — Level AA] | Low contrast (#aaa on white) |

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
