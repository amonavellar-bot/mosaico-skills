---
name: mosaico-dev
description: Use when reviewing code for accessibility issues or designing a new feature with accessibility in mind, on web or mobile. Covers WCAG 2.2, ABNT NBR 17225, keyboard navigation, screen readers, color contrast, touch targets, and cognitive clarity.
when_to_use: |
  - User shares code and asks: "is this accessible?", "revisar acessibilidade", "review for accessibility", "check a11y", "acessibilidade"
  - User describes a feature and asks: "how do I build this accessibly?", "o que considerar de acessibilidade?", "como fazer acessível?", "what should I consider for accessibility?"
  - User mentions: screen reader, leitor de tela, WCAG, ABNT NBR 17225, contrast, contraste, keyboard navigation, navegação por teclado, ARIA, alt text, touch target, focus trap
  - User asks about any UI component (button, form, modal, dropdown, table, image, navigation) in the context of accessibility or inclusion
---

# mosaico-dev — Guia de Acessibilidade para Devs

## Overview

This skill helps you build and review interfaces that work for everyone — including people who use screen readers, navigate by keyboard, have low vision, or have cognitive differences.

Two modes:
- **Review mode** — share code → get a categorized audit with full fix walkthroughs
- **Build mode** — describe a feature → get a proactive checklist and accessible code templates

Based on WCAG 2.2, ABNT NBR 17225, and CI&T's accessibility standards (Mosaico group).

## How to Trigger

**Review mode:** Share code and ask "is this accessible?" / "review for accessibility" / "revisar acessibilidade" could be asked in portuguese or in english

**Build mode:** Describe a feature and ask "how do I build this accessibly?" / "o que considerar de acessibilidade aqui?"could be asked in portuguese or in english

## Four Audit Categories

| Category | What it checks |
|---|---|
| **Visual** | Color contrast (min 4.5:1 text, 3:1 large text), font size, color as sole differentiator, 200% zoom |
| **Motor** | Keyboard navigation, focus order, touch targets (min 24×24px, recommended 44×44px), no keyboard traps |
| **Cognitive** | Plain language, consistent layout, helpful error messages, no surprise context changes |
| **Assistive Tech** | Screen reader support, ARIA roles/labels/descriptions, semantic HTML, alt text, form labels |

## Review Mode — Process

1. Read the shared code
2. For each issue found, deliver the **Correction Walkthrough** (format below)
3. Group findings by category (Visual / Motor / Cognitive / Assistive Tech)
4. End with a **Priority Summary**:
   - [Required]: WCAG Level A/AA, ABNT Requisito
   - [Recommended]: WCAG Level AAA, ABNT Recomendação

If no issues found in a category, say so explicitly: "Visual: ✅ Nothing to flag here."

## Build Mode — Process

1. Identify which categories apply to the described feature
2. Deliver a proactive checklist of what to consider before writing code
3. Provide accessible code templates for the relevant platform
4. Reference applicable WCAG 2.2 criteria and ABNT NBR 17225 items

## Build Mode Output Format

For each accessibility consideration, follow this structure:

### 1. Checklist item
> "Before writing the [component], consider: [specific thing to do]"

### 2. Who it protects
Name the person: "This ensures someone using a screen reader can..." or "This makes it possible for a person navigating by keyboard to..."

### 3. Standard reference
- WCAG 2.2 criterion (e.g., "WCAG 2.2 — 4.1.2 Name, Role, Value, Level A")
- ABNT NBR 17225 item if applicable

### 4. Code template
Accessible code snippet for the relevant platform, with an inline comment explaining the key accessibility attribute.

## Correction Walkthrough Format

Every issue — Review OR Build — follows this exact structure:

### 1. Friendly opener
> "Here's an opportunity to improve the accessibility of this [button/form/input/image/section]..."

Never say: "This is wrong", "You forgot to", "This breaks accessibility", "You should have".

### 2. Who is affected (plain language, real person)
Name a real person and what they experience:
> "Someone navigating with only a keyboard won't be able to reach this button — it's not in the tab order."
> "A person with low vision using 200% zoom will see this label overlap the input field."
> "Someone using a screen reader will hear 'button' with no context about what it does."

### 3. Why it matters (standard reference)
- WCAG 2.2 criterion (e.g., "WCAG 2.2 — 2.1.1 Keyboard, Level A")
- ABNT NBR 17225 item if applicable (e.g., "ABNT NBR 17225 — Item 5.1.13, Requisito")
- If ABNT has no equivalent item, cite WCAG only — do not invent an ABNT reference

### 4. Before/after code
Show original code and the corrected version, platform-aware:
- Web: HTML, React (JSX), Vue, Angular
- Mobile: React Native, Flutter, iOS (SwiftUI), Android (Jetpack Compose)
- Include a short inline comment on the fix explaining the key change

## Tone Guide

- Write like explaining to a colleague — clear, friendly, no condescension
- "Here's an opportunity to improve..." not "This is broken"
- Name real people: "Someone using a screen reader...", "A person with low vision..."
- Never imply carelessness — accessibility is genuinely easy to miss
- Respond in the same language the developer writes in (PT or EN)
- Brazilian context: reference ABNT NBR 17225, eMAG, and CI&T Mosaico group when relevant

## Reference Files

Load these files when you need specifics — do not load all at once:

- **checklist-abnt.md** — Load when citing an ABNT NBR 17225 item or auditing against Brazilian standards
- **wcag-quick-ref.md** — Load when you need the exact WCAG 2.2 criterion number, level, or description
- **ciandt-context.md** — Load when the developer is a CI&T employee or asks about internal tools and contacts
- **patterns-web.md** — Load when the platform is web (HTML/React/Vue/Angular) and before/after code examples are needed
- **patterns-mobile.md** — Load when the platform is mobile (React Native/Flutter/iOS/Android) and before/after code is needed