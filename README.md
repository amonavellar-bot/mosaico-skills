# mosaico-skills

Accessibility skills for Claude Code — by the [CI&T Mosaico group](mailto:amon.avellar@ciandt.com).

## What is this?

A Claude Code plugin that turns your AI assistant into an accessibility-aware development partner. It audits code for accessibility issues and guides feature design across web and mobile platforms, based on WCAG 2.2 and ABNT NBR 17225.

### Plugins included

| Plugin | Description |
|---|---|
| `mosaico-dev` | Friendly accessibility guide — review, build, and explain modes for web and mobile |

---

## Installation

```bash
# 1. Register the marketplace
claude plugin marketplace add amonavellar-bot/mosaico-skills

# 2. Install the plugin
claude plugin install mosaico-dev
```

Or install locally from a cloned repo:

```bash
git clone https://github.com/amonavellar-bot/mosaico-skills.git
claude plugin marketplace add ./mosaico-skills
claude plugin install mosaico-dev
```

Verify the install:

```bash
claude plugins list
```

---

## Usage

After installation, the skill activates automatically when Claude Code detects accessibility-related intent in your prompts. No slash command needed.

### Review mode — audit existing code

Share code and ask for a review:

```
Is this button accessible?

<button onClick={handleClose}>X</button>
```

```
Revisar acessibilidade nesse formulário:

<form>
  <input type="text" placeholder="Nome" />
  <input type="email" placeholder="Email" />
  <button type="submit">Enviar</button>
</form>
```

Claude will respond with a categorized audit across four areas aligned with WCAG 2.2 principles: **Perceivable**, **Operable**, **Understandable**, and **Robust** — each issue with a before/after code fix, the applicable WCAG 2.2 / ABNT NBR 17225 reference, and a severity label ([Blocker], [Required], or [Recommended]).

### Build mode — design a feature accessibly

Describe what you're building:

```
I'm building a modal dialog with a close button and a form inside. What should I consider for accessibility?
```

```
Vou criar um dropdown de seleção de país. O que considerar de acessibilidade?
```

Claude will give you a proactive checklist and accessible code templates before you write a single line.

---

## Supported platforms

| Platform | Frameworks |
|---|---|
| Web | HTML, React (JSX), Vue, Angular |
| Mobile | React Native, Flutter, iOS (SwiftUI), Android (Jetpack Compose) |

---

## Standards covered

- **WCAG 2.2** — all 78 success criteria (Level A, AA, AAA)
- **ABNT NBR 17225** — Brazilian accessibility standard (146 items across 16 sections)
- **eMAG** — Brazilian government accessibility model

---

## Contributing

1. Fork this repository
2. Create a branch: `git checkout -b feature/your-change`
3. Make your changes following the structure below
4. Open a pull request

### Repository structure

```
mosaico-skills/
├── .claude-plugin/
│   └── marketplace.json        # marketplace registry
└── plugins/
    └── native/
        └── mosaico-dev/
            ├── .claude-plugin/
            │   └── plugin.json  # plugin metadata
            └── skills/
                └── accessibility/
                    ├── SKILL.md             # skill behavior definition
                    ├── checklist-abnt.md    # ABNT NBR 17225 reference
                    ├── wcag-quick-ref.md    # WCAG 2.2 quick reference
                    ├── ciandt-context.md    # CI&T internal context
                    ├── patterns-web.md      # web before/after code examples
                    └── patterns-mobile.md   # mobile before/after code examples
```

### Updating reference files

When WCAG or ABNT releases a new version, update the corresponding reference file and bump the version header at the top of the file.

---

## License

MIT — see [LICENSE](LICENSE)

## Maintainer

Amon Avellar — [amon.avellar@ciandt.com](mailto:amon.avellar@ciandt.com) — CI&T Mosaico group
