# WCAG 2.2 Quick Reference

W3C Recommendation, December 2024. 4 principles, 13 guidelines, 78 success criteria.

**Levels:** A (minimum) · AA (standard target) · AAA (enhanced)

⭐ = New in WCAG 2.2

---

## Principle 1: Perceivable

Information and user interface components must be presentable to users in ways they can perceive.

### 1.1 Text Alternatives

| Criterion | Level | Plain-language description |
|---|---|---|
| 1.1.1 Non-text Content | A | All images, buttons, icons, and other non-text content must have a text alternative (alt text, labels, or captions) so screen readers can describe them. |

### 1.2 Time-based Media

| Criterion | Level | Plain-language description |
|---|---|---|
| 1.2.1 Audio-only and Video-only (Prerecorded) | A | Provide a transcript for audio-only content and a transcript or audio description for video-only content. |
| 1.2.2 Captions (Prerecorded) | A | Add synchronized captions to all prerecorded videos that include audio so deaf users can follow along. |
| 1.2.3 Audio Description or Media Alternative (Prerecorded) | A | For prerecorded video with audio, provide either a full text transcript or an audio description of what happens visually. |
| 1.2.4 Captions (Live) | AA | Provide real-time captions for live video that includes spoken audio (like live streams or webinars). |
| 1.2.5 Audio Description (Prerecorded) | AA | Add a narrated audio track describing the visual content of prerecorded videos for blind users. |
| 1.2.6 Sign Language (Prerecorded) | AAA | Include a sign language interpretation track for all prerecorded video content that contains audio. |
| 1.2.7 Extended Audio Description (Prerecorded) | AAA | When regular audio descriptions cannot fit in the pauses of the video, pause the video to provide fuller descriptions. |
| 1.2.8 Media Alternative (Prerecorded) | AAA | Provide a complete text alternative for all prerecorded synchronized media and video-only content. |
| 1.2.9 Audio-only (Live) | AAA | Provide a real-time text alternative (like live captioning) for live audio-only content such as podcasts. |

### 1.3 Adaptable

| Criterion | Level | Plain-language description |
|---|---|---|
| 1.3.1 Info and Relationships | A | Structure and relationships conveyed visually (headings, tables, lists) must also be conveyed in code so assistive technologies understand the layout. |
| 1.3.2 Meaningful Sequence | A | When the order of content matters for understanding, the reading sequence must be correctly defined in the code. |
| 1.3.3 Sensory Characteristics | A | Do not rely solely on shape, color, size, location, or sound to give instructions (e.g., "click the green button on the right"). |
| 1.3.4 Orientation | AA | Content must not lock itself to portrait or landscape orientation unless that specific orientation is essential. |
| 1.3.5 Identify Input Purpose | AA | Form fields that collect personal information (name, email, address) must be programmatically marked so browsers and assistive tools can autofill them. |
| 1.3.6 Identify Purpose | AAA | The purpose of interface components, icons, and page regions must be identifiable in code so users can customize their experience. |

### 1.4 Distinguishable

| Criterion | Level | Plain-language description |
|---|---|---|
| 1.4.1 Use of Color | A | Never use color as the only way to convey information — always pair it with text, pattern, or another visual cue. |
| 1.4.2 Audio Control | A | If audio plays automatically for more than 3 seconds, provide a way to pause, stop, or mute it independently of system volume. |
| 1.4.3 Contrast (Minimum) | AA | Normal text must have a contrast ratio of at least 4.5:1, and large text (18pt or 14pt bold) at least 3:1 against its background. |
| 1.4.4 Resize Text | AA | Text must be resizable up to 200% without assistive technology and without losing content or functionality. |
| 1.4.5 Images of Text | AA | Use real text instead of images of text unless the specific visual appearance of the text is essential. |
| 1.4.6 Contrast (Enhanced) | AAA | Normal text must have a contrast ratio of at least 7:1, and large text at least 4.5:1 — a stricter version of 1.4.3. |
| 1.4.7 Low or No Background Audio | AAA | In prerecorded speech audio, background sounds must be at least 20 dB quieter than the foreground speech, or be removable. |
| 1.4.8 Visual Presentation | AAA | For blocks of text, users must be able to control foreground/background colors, line width, line spacing, and text alignment. |
| 1.4.9 Images of Text (No Exception) | AAA | Only use images of text for pure decoration or when the visual presentation is essential — no other exceptions. |
| 1.4.10 Reflow | AA | Content must not require horizontal scrolling on a screen width of 320 CSS pixels (equivalent to 400% zoom on a 1280px screen). |
| 1.4.11 Non-text Contrast | AA | UI components (buttons, inputs, focus indicators) and informational graphics must have a contrast ratio of at least 3:1 against adjacent colors. |
| 1.4.12 Text Spacing | AA | When users override text spacing (line height, letter spacing, word spacing, paragraph spacing), no content or functionality should be lost. |
| 1.4.13 Content on Hover or Focus | AA | Content that appears on hover or focus (tooltips, dropdowns) must be dismissible, hoverable, and persistent until dismissed. |

---

## Principle 2: Operable

User interface components and navigation must be operable.

### 2.1 Keyboard Accessible

| Criterion | Level | Plain-language description |
|---|---|---|
| 2.1.1 Keyboard | A | All functionality must be usable with a keyboard alone — nothing should require a mouse or specific gesture path. |
| 2.1.2 No Keyboard Trap | A | If you can move keyboard focus into a component, you must also be able to move it out using only the keyboard. |
| 2.1.3 Keyboard (No Exception) | AAA | All functionality must be operable by keyboard without exception — a stricter version of 2.1.1 with no path-dependency loophole. |
| 2.1.4 Character Key Shortcuts | A | If single-character keyboard shortcuts are used, users must be able to turn them off, remap them, or they must only activate when the component has focus. |

### 2.2 Enough Time

| Criterion | Level | Plain-language description |
|---|---|---|
| 2.2.1 Timing Adjustable | A | If a time limit is set by the content, users must be able to turn it off, extend it, or the time limit must be at least 20 hours. |
| 2.2.2 Pause, Stop, Hide | A | Any moving, blinking, or auto-updating content that lasts more than 5 seconds must have a mechanism to pause, stop, or hide it. |
| 2.2.3 No Timing | AAA | The content does not use time limits except for real-time events and non-interactive synchronized media. |
| 2.2.4 Interruptions | AAA | Users can postpone or suppress any interruption (alerts, updates) except emergency notices. |
| 2.2.5 Re-authenticating | AAA | When a session expires, users can re-authenticate and continue their activity without losing any data they entered. |
| 2.2.6 Timeouts | AAA | Warn users about inactivity timeouts that could cause data loss, unless data is preserved for more than 20 hours. |

### 2.3 Seizures and Physical Reactions

| Criterion | Level | Plain-language description |
|---|---|---|
| 2.3.1 Three Flashes or Below Threshold | A | Content must not flash more than 3 times per second, or it must stay below the general and red flash thresholds to avoid triggering seizures. |
| 2.3.2 Three Flashes | AAA | No content flashes more than 3 times per second — a stricter version of 2.3.1 with no threshold exceptions. |
| 2.3.3 Animation from Interactions | AAA | Motion animations triggered by user interaction can be disabled, unless the animation is essential. |

### 2.4 Navigable

| Criterion | Level | Plain-language description |
|---|---|---|
| 2.4.1 Bypass Blocks | A | Provide a way (like skip links) to bypass repeated blocks of content (like navigation menus) that appear on every page. |
| 2.4.2 Page Titled | A | Every web page must have a descriptive title that identifies its topic or purpose. |
| 2.4.3 Focus Order | A | When navigating by keyboard, the focus order must follow a logical sequence that preserves meaning and operability. |
| 2.4.4 Link Purpose (In Context) | A | The purpose of each link must be clear from the link text alone or from the link text plus its surrounding context. |
| 2.4.5 Multiple Ways | AA | Provide more than one way to find a page within a site (e.g., search, site map, navigation) — unless the page is a step in a process. |
| 2.4.6 Headings and Labels | AA | Headings and form labels must clearly describe the topic or purpose of the content they relate to. |
| 2.4.7 Focus Visible | AA | Any keyboard-operable interface must have a visible keyboard focus indicator so users can see where they are. |
| 2.4.8 Location | AAA | Provide information about the user's current location within a set of pages (e.g., breadcrumbs, highlighted nav item). |
| 2.4.9 Link Purpose (Link Only) | AAA | Every link's purpose must be clear from the link text alone, without needing surrounding context. |
| 2.4.10 Section Headings | AAA | Use section headings to organize content — any block of content should be reachable and identifiable via a heading. |
| ⭐ 2.4.11 Focus Not Obscured (Minimum) | AA | When a component receives keyboard focus, it must not be completely hidden behind other author-created content (like sticky headers or cookie banners). |
| ⭐ 2.4.12 Focus Not Obscured (Enhanced) | AAA | When a component receives keyboard focus, no part of it is hidden by author-created content — a stricter version of 2.4.11. |
| ⭐ 2.4.13 Focus Appearance | AAA | The keyboard focus indicator must meet minimum size (2px perimeter) and contrast (3:1 ratio) requirements so it is clearly visible. |

### 2.5 Input Modalities

| Criterion | Level | Plain-language description |
|---|---|---|
| 2.5.1 Pointer Gestures | A | Any functionality that requires multi-finger or path-based gestures (like pinch-zoom or swipe) must also be achievable with a simple single tap or click. |
| 2.5.2 Pointer Cancellation | A | For any action triggered by a single pointer, users must be able to cancel it (e.g., by moving away before releasing) to prevent accidental activation. |
| 2.5.3 Label in Name | A | For buttons and links that have a visible text label, the accessible name in code must include that visible text so voice control users can activate them. |
| 2.5.4 Motion Actuation | A | Any feature controlled by shaking or tilting a device must also be operable through the UI, and motion control must be able to be turned off. |
| 2.5.5 Target Size (Enhanced) | AAA | Interactive targets (buttons, links) must be at least 44×44 CSS pixels unless an equivalent accessible alternative is provided. |
| 2.5.6 Concurrent Input Mechanisms | AAA | Content must not prevent users from switching between input methods (mouse, keyboard, touch, voice) at any time. |
| ⭐ 2.5.7 Dragging Movements | AA | Any action that requires dragging (like sliders or reordering) must also be achievable without dragging using a single pointer. |
| ⭐ 2.5.8 Target Size (Minimum) | AA | Interactive targets must be at least 24×24 CSS pixels, or spaced so their hit areas do not overlap with adjacent targets. |

---

## Principle 3: Understandable

Information and the operation of the user interface must be understandable.

### 3.1 Readable

| Criterion | Level | Plain-language description |
|---|---|---|
| 3.1.1 Language of Page | A | The default human language of every page must be programmatically set (e.g., `lang="en"` in HTML) so screen readers pronounce content correctly. |
| 3.1.2 Language of Parts | AA | When a page contains passages in a different language than the default, those passages must be marked with the correct language code. |
| 3.1.3 Unusual Words | AAA | Provide a way to identify definitions for unusual words, idioms, or jargon used on the page (e.g., a glossary or inline definition). |
| 3.1.4 Abbreviations | AAA | Provide a way to find the full form or meaning of abbreviations, such as by expanding them on first use or providing a glossary. |
| 3.1.5 Reading Level | AAA | When content requires reading ability beyond lower secondary education level, provide a simplified summary or alternative version. |
| 3.1.6 Pronunciation | AAA | When the meaning of a word is ambiguous without knowing its pronunciation, provide a way to identify the correct pronunciation. |

### 3.2 Predictable

| Criterion | Level | Plain-language description |
|---|---|---|
| 3.2.1 On Focus | A | Moving keyboard focus to a component must not trigger any unexpected change of context — focus alone should not submit forms or navigate pages. |
| 3.2.2 On Input | A | Changing a form field's value (like selecting a dropdown option) must not automatically trigger a context change unless the user was warned first. |
| 3.2.3 Consistent Navigation | AA | Navigation menus and repeated elements that appear on multiple pages must appear in the same relative order on every page. |
| 3.2.4 Consistent Identification | AA | Components that have the same function across multiple pages must be labeled and identified consistently throughout the site. |
| 3.2.5 Change on Request | AAA | Context changes (like opening new windows or submitting forms) must only happen when the user explicitly requests them. |
| ⭐ 3.2.6 Consistent Help | A | If help mechanisms (like a chat button, phone number, or FAQ link) appear on multiple pages, they must appear in the same location relative to other page content. |

### 3.3 Input Assistance

| Criterion | Level | Plain-language description |
|---|---|---|
| 3.3.1 Error Identification | A | When a form input error is detected, the specific field with the error must be identified and the error described to the user in text. |
| 3.3.2 Labels or Instructions | A | Form fields and controls must have clear labels or instructions so users know what to enter or how to interact with them. |
| 3.3.3 Error Suggestion | AA | When a form error is detected and a fix is known, suggest a correction to the user unless doing so would compromise security. |
| 3.3.4 Error Prevention (Legal, Financial, Data) | AA | For pages that involve legal commitments, financial transactions, or data deletion, submissions must be reversible, checkable, or confirmable. |
| 3.3.5 Help | AAA | Context-sensitive help is available so users can get assistance relevant to the task they are performing. |
| 3.3.6 Error Prevention (All) | AAA | For any form submission, provide a way to review, confirm, and correct information before finalizing — extends 3.3.4 to all forms. |
| ⭐ 3.3.7 Redundant Entry | A | Information a user has already provided in the same process must be auto-populated or selectable — users should not have to type the same information twice. |
| ⭐ 3.3.8 Accessible Authentication (Minimum) | AA | Authentication steps must not require cognitive function tests (like puzzles or memorizing passwords) unless an alternative method or assistive mechanism is provided. |
| ⭐ 3.3.9 Accessible Authentication (Enhanced) | AAA | Authentication steps must not require any cognitive function test at all, unless an alternative non-cognitive authentication method is available — stricter than 3.3.8. |

---

## Principle 4: Robust

Content must be robust enough to be interpreted by a wide variety of user agents, including assistive technologies.

### 4.1 Compatible

| Criterion | Level | Plain-language description |
|---|---|---|
| 4.1.1 Parsing (Obsolete and removed) | — | This criterion was removed in WCAG 2.2. It originally required well-formed HTML, but assistive technologies no longer need to parse HTML directly. |
| 4.1.2 Name, Role, Value | A | All user interface components must expose their name, role (what type of element it is), and current value/state in code so assistive technologies can interact with them. |
| 4.1.3 Status Messages | AA | Status messages (like "Item added to cart" or "3 errors found") must be programmatically conveyed so screen readers can announce them without the message receiving focus. |

---

## Summary by Level

| Level | Count | Purpose |
|---|---|---|
| A | 30 | Minimum baseline — must pass to avoid blocking users |
| AA | 20 | Standard target for most legal and policy requirements |
| AAA | 28 | Enhanced accessibility — recommended where feasible |

**Note:** 4.1.1 Parsing is obsolete and removed, leaving 78 active criteria.

---

## New in WCAG 2.2 (9 criteria ⭐)

| Criterion | Level | Summary |
|---|---|---|
| ⭐ 2.4.11 Focus Not Obscured (Minimum) | AA | Focused element not completely hidden |
| ⭐ 2.4.12 Focus Not Obscured (Enhanced) | AAA | No part of focused element is hidden |
| ⭐ 2.4.13 Focus Appearance | AAA | Focus indicator meets size and contrast requirements |
| ⭐ 2.5.7 Dragging Movements | AA | Dragging actions have single-pointer alternative |
| ⭐ 2.5.8 Target Size (Minimum) | AA | Touch targets at least 24×24 CSS pixels |
| ⭐ 3.2.6 Consistent Help | A | Help mechanisms appear in consistent location |
| ⭐ 3.3.7 Redundant Entry | A | Previously entered data is auto-populated |
| ⭐ 3.3.8 Accessible Authentication (Minimum) | AA | No cognitive puzzles required for login |
| ⭐ 3.3.9 Accessible Authentication (Enhanced) | AAA | Stricter — no cognitive tests unless alternative exists |