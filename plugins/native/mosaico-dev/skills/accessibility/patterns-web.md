# Web Accessibility Patterns

Before/after code examples for web platforms.
Based on WCAG 2.2, eMAG, W3C standards, and UK-Brazil Digital Access Programme guide.

Sources:
- Padrão Digital de Governo — Acessibilidade no Código HTML (eMAG / gov.br)
- Guia de Boas Práticas para Acessibilidade Digital (UK-Brazil Digital Access Programme, 2023)

---

## Images and Alt Text

Every image that conveys information needs an `alt` attribute. Screen readers read the `alt` value aloud; without it they may read the filename or say "image", which tells users nothing.

### ❌ Before (inaccessible)
```html
<!-- No alt — screen reader reads the filename or nothing useful -->
<img src="grafico-receita-q3.png">

<!-- Icon inside a link with no text — screen reader announces nothing -->
<a href="/relatorio"><img src="icon-download.svg"></a>
```

### ✅ After (accessible)
```html
<!-- Describe what the image communicates, not just what it looks like -->
<img src="grafico-receita-q3.png"
     alt="Gráfico de barras mostrando crescimento de receita de 40% no Q3 2024">

<!-- Icon link: alt carries the link destination -->
<a href="/relatorio">
  <img src="icon-download.svg" alt="Baixar relatório de indicadores 2024">
</a>
```

**Decorative image — tell screen readers to skip it:**
```html
<!-- Empty alt + role="presentation" means the reader skips this completely -->
<img src="divisor-decorativo.svg" alt="" role="presentation">
```

**Image with text inside it (avoid this pattern entirely):**
```html
<!-- ❌ Text in an image cannot be read by screen readers or resized by the browser -->
<img src="banner-promocao.png">

<!-- ✅ Use real HTML text; style with CSS -->
<div class="banner">
  <h2>Promoção de Aniversário</h2>
  <p>Até 50% de desconto em todos os planos</p>
</div>
```

---

## Buttons and Links

A **link** navigates somewhere. A **button** performs an action. Mixing them breaks the mental model for screen-reader users and keyboard-only users.

### ❌ Before (inaccessible)
```html
<!-- No accessible name — screen reader says "button" with no context -->
<button><img src="icon-fechar.svg"></button>

<!-- Generic link text — users cannot tell where this goes -->
<a href="/artigo-123">Saiba mais</a>
<a href="/doc.pdf">Clique aqui</a>

<!-- div used as a button — not reachable by Tab key, not announced as interactive -->
<div onclick="enviarFormulario()">Enviar</div>
```

### ✅ After (accessible)
```html
<!-- Icon-only button: aria-label provides the accessible name -->
<button aria-label="Fechar modal">
  <img src="icon-fechar.svg" alt="">
</button>

<!-- Descriptive link text: users know the destination before clicking -->
<a href="/artigo-sobre-acessibilidade">Saiba mais sobre acessibilidade digital</a>
<a href="/relatorio-2024.pdf">Baixar relatório de indicadores 2024 (PDF)</a>

<!-- Real button element: focusable, activatable with Enter/Space, correct role -->
<button type="button" onclick="enviarFormulario()">Enviar formulário</button>
```

**Button vs link — use the right semantic element:**
```html
<!-- ❌ Styled link used as a button action -->
<a href="#" onclick="toggleMenu()">Menu</a>

<!-- ✅ Button for actions, link for navigation -->
<button type="button" onclick="toggleMenu()" aria-expanded="false" aria-controls="menu-nav">
  Menu
</button>
```

---

## Forms and Labels

Every form field needs a visible `<label>` linked to its `id`. Placeholder text disappears when the user types and is never sufficient as a label.

### ❌ Before (inaccessible)
```html
<!-- No label — screen reader only announces "text input" -->
<input type="text" placeholder="Nome completo">

<!-- Label not connected to input — clicking the label does not focus the field -->
<label>E-mail</label>
<input type="email" name="email">

<!-- Required field with no indication — user does not know it is mandatory -->
<input type="text" id="cpf" required>

<!-- Error message appears far from the field — screen reader may miss it -->
<input type="text" id="cep" name="cep">
<p style="color:red">CEP inválido</p>
```

### ✅ After (accessible)
```html
<!-- Label linked via "for" + "id" — clicking the label focuses the field -->
<label for="nome">Nome completo</label>
<input type="text" id="nome" name="nome" autocomplete="name">

<!-- for + id connect label to input; aria-required tells assistive tech it is required -->
<label for="email">
  E-mail <span aria-hidden="true">*</span>
</label>
<input type="email" id="email" name="email" required aria-required="true"
       autocomplete="email">

<!-- Required field: visible asterisk explained by legend or footnote -->
<fieldset>
  <legend>Dados pessoais <span aria-hidden="true">* campos obrigatórios</span></legend>
  <label for="cpf">CPF <span aria-hidden="true">*</span></label>
  <input type="text" id="cpf" name="cpf" required aria-required="true"
         inputmode="numeric" autocomplete="off">
</fieldset>

<!-- Error linked to field via aria-describedby — read immediately after the label -->
<label for="cep">CEP</label>
<input type="text" id="cep" name="cep" aria-describedby="cep-erro" aria-invalid="true">
<p id="cep-erro" role="alert">CEP inválido. Use o formato 00000-000.</p>
```

**Checkbox group — use fieldset + legend:**
```html
<!-- ❌ Checkboxes without group label -->
<input type="checkbox" id="receber-email"> <label for="receber-email">E-mail</label>
<input type="checkbox" id="receber-sms"> <label for="receber-sms">SMS</label>

<!-- ✅ fieldset gives screen readers the group context -->
<fieldset>
  <legend>Receber notificações por</legend>
  <label><input type="checkbox" name="notif" value="email"> E-mail</label>
  <label><input type="checkbox" name="notif" value="sms"> SMS</label>
</fieldset>
```

---

## Headings Structure

Headings create a navigation outline that screen-reader users use to jump between sections. Never skip levels or use headings just to make text bigger.

### ❌ Before (inaccessible)
```html
<!-- ❌ Using heading only for visual size — breaks the outline -->
<h1>Nosso Portal</h1>
<h3>Últimas notícias</h3>  <!-- skipped h2 -->
<h5>Hoje no esporte</h5>   <!-- skipped h3 and h4 -->

<!-- ❌ div styled to look like a heading — screen reader ignores it -->
<div style="font-size:24px; font-weight:bold;">Resultados do trimestre</div>

<!-- ❌ Multiple h1 on the same page — confuses navigation -->
<h1>Início</h1>
...
<h1>Sobre nós</h1>
```

### ✅ After (accessible)
```html
<!-- One h1 per page, hierarchical levels, no skipped levels -->
<h1>Portal de Notícias</h1>
  <h2>Últimas notícias</h2>
    <h3>Cidades</h3>
      <h4>São Paulo</h4>
      <h4>Rio de Janeiro</h4>
    <h3>Esportes</h3>
      <h4>Futebol</h4>
        <h5>Seleção brasileira</h5>
  <h2>Sobre nós</h2>
```

**Section with nav landmark:**
```html
<!-- Use semantic landmarks so users can jump to areas -->
<header role="banner">
  <h1>Nome do Portal</h1>
</header>
<nav role="navigation" aria-label="Menu principal">
  <ul>
    <li><a href="/inicio">Início</a></li>
    <li><a href="/servicos">Serviços</a></li>
  </ul>
</nav>
<main role="main" id="conteudo-principal">
  <h2>Bem-vindo</h2>
</main>
<footer role="contentinfo">
  <!-- Informações de direitos autorais -->
</footer>
```

---

## Color Contrast

Text must have a contrast ratio of at least 4.5:1 against its background (WCAG AA). Large text (18pt+ or 14pt+ bold) needs at least 3:1. Never use color as the only way to convey information.

### ❌ Before (inaccessible)
```css
/* ❌ Light grey on white — fails WCAG AA (ratio ~2.3:1) */
.caption {
  color: #aaaaaa;
  background: #ffffff;
}

/* ❌ Error state shown only by red color */
.field-error {
  border-color: red;
}
```

```html
<!-- ❌ Color-only error — colorblind users see no difference -->
<input type="text" class="field-error">
```

### ✅ After (accessible)
```css
/* ✅ Dark grey on white — passes WCAG AA (ratio ~9.7:1) */
.caption {
  color: #595959;
  background: #ffffff;
}

/* ✅ Error shown with color + icon + border change */
.field-error {
  border: 2px solid #c0392b;  /* color cue */
  background-image: url('icon-error.svg');  /* icon cue */
  padding-right: 2.5rem;
}
```

```html
<!-- ✅ Error shown with color + icon + text — three independent cues -->
<label for="senha">Senha</label>
<input type="password" id="senha" class="field-error"
       aria-describedby="senha-erro" aria-invalid="true">
<p id="senha-erro" role="alert">
  <span aria-hidden="true">⚠</span> A senha deve ter ao menos 8 caracteres.
</p>
```

**Accessible high-contrast toggle:**
```css
/* Respect user's OS preference automatically */
@media (prefers-color-scheme: dark) {
  body {
    background: #1a1a1a;
    color: #f5f5f5;
  }
  a { color: #7cb9ff; }
}
```

---

## Focus Management

Visible focus is mandatory. Removing `outline` with no replacement is one of the most common barriers for keyboard-only users.

### ❌ Before (inaccessible)
```css
/* ❌ Removes focus indicator entirely — keyboard users are lost */
* { outline: none; }
button:focus { outline: 0; }
a:focus { outline: none; }
```

```html
<!-- ❌ Modal opens but focus stays behind it — users type into hidden content -->
<button onclick="document.getElementById('modal').style.display='block'">
  Abrir configurações
</button>
<div id="modal" style="display:none">
  <button onclick="fechar()">Fechar</button>
  <p>Conteúdo do modal</p>
</div>
```

### ✅ After (accessible)
```css
/* ✅ Custom focus style that is visible and brand-consistent */
:focus-visible {
  outline: 3px solid #005fcc;
  outline-offset: 2px;
  border-radius: 2px;
}

/* ✅ Remove default only when :focus-visible is supported */
:focus:not(:focus-visible) {
  outline: none;
}
```

```html
<!-- ✅ Modal with focus trap and ESC support -->
<button id="btn-abrir" onclick="abrirModal()">Abrir configurações</button>

<div id="modal" role="dialog" aria-modal="true" aria-labelledby="modal-titulo"
     style="display:none" tabindex="-1">
  <h2 id="modal-titulo">Configurações</h2>
  <p>Conteúdo do modal</p>
  <button id="modal-primeiro-foco">Confirmar</button>
  <button onclick="fecharModal()">Fechar</button>
</div>

<script>
// Query all focusable elements inside the modal
const FOCUSABLE = 'a[href], button:not([disabled]), input, select, textarea, [tabindex]:not([tabindex="-1"])';

function abrirModal() {
  const modal = document.getElementById('modal');
  modal.style.display = 'block';
  // Move focus to the first focusable element inside the modal
  const primeiro = modal.querySelector(FOCUSABLE);
  if (primeiro) primeiro.focus();
}

function fecharModal() {
  const modal = document.getElementById('modal');
  modal.style.display = 'none';
  document.getElementById('btn-abrir').focus(); // Return focus to trigger
}

// Focus trap: keep Tab and Shift+Tab cycling within the modal
document.getElementById('modal').addEventListener('keydown', (e) => {
  if (e.key === 'Escape') { fecharModal(); return; }
  if (e.key !== 'Tab') return;

  const modal = document.getElementById('modal');
  const focusable = [...modal.querySelectorAll(FOCUSABLE)];
  const first = focusable[0];
  const last = focusable[focusable.length - 1];

  if (e.shiftKey) {
    // Shift+Tab on first element → wrap to last
    if (document.activeElement === first) { e.preventDefault(); last.focus(); }
  } else {
    // Tab on last element → wrap to first
    if (document.activeElement === last) { e.preventDefault(); first.focus(); }
  }
});
</script>
```

---

## ARIA Roles and Labels

Use native HTML elements first. Add ARIA only when native elements are not enough. A `div` or `span` used as an interactive element has no role, no keyboard support, and no accessible name by default.

### ❌ Before (inaccessible)
```html
<!-- ❌ div used as button — not focusable, not announced as interactive -->
<div class="btn-primary" onclick="salvar()">Salvar</div>

<!-- ❌ Custom dropdown with no ARIA — screen reader does not know it is a listbox -->
<div class="dropdown">
  <div onclick="toggleDropdown()">Selecione um estado ▾</div>
  <div class="dropdown-list">
    <div onclick="select('SP')">São Paulo</div>
    <div onclick="select('RJ')">Rio de Janeiro</div>
  </div>
</div>

<!-- ❌ Dynamic alert with no live region — screen reader misses the update -->
<div id="alerta"></div>
<script>
  document.getElementById('alerta').textContent = 'Arquivo salvo com sucesso';
</script>
```

### ✅ After (accessible)
```html
<!-- ✅ Real button element — focus, keyboard, role all handled natively -->
<button type="button" onclick="salvar()">Salvar</button>

<!-- ✅ Native select — accessible out of the box -->
<label for="estado">Estado</label>
<select id="estado" name="estado">
  <option value="">Selecione um estado</option>
  <option value="SP">São Paulo</option>
  <option value="RJ">Rio de Janeiro</option>
</select>

<!-- ✅ role="status" + aria-live="polite" — announces non-urgent updates without interrupting the user -->
<!-- Use role="alert" (assertive) only for critical errors that must interrupt immediately -->
<div id="alerta" role="status" aria-live="polite" aria-atomic="true"></div>
<script>
  // Inserting text triggers an announcement without stealing focus
  document.getElementById('alerta').textContent = 'Arquivo salvo com sucesso';
</script>
```

**Toggle button with state:**
```html
<!-- ✅ aria-pressed reflects current state to screen readers -->
<button type="button" id="btn-contraste" aria-pressed="false"
        onclick="toggleContraste(this)">
  Alto contraste
</button>
<script>
function toggleContraste(btn) {
  const isOn = btn.getAttribute('aria-pressed') === 'true';
  btn.setAttribute('aria-pressed', String(!isOn));
  document.body.classList.toggle('alto-contraste', !isOn);
}
</script>
```

**Expandable section (accordion):**
```html
<!-- ✅ aria-expanded tells users whether section is open or closed -->
<button type="button" aria-expanded="false" aria-controls="secao-1-conteudo"
        onclick="toggleSecao(this, 'secao-1-conteudo')">
  O que é acessibilidade digital?
</button>
<div id="secao-1-conteudo" hidden>
  <p>Acessibilidade digital garante que todas as pessoas possam usar produtos digitais.</p>
</div>
<script>
function toggleSecao(btn, targetId) {
  const expanded = btn.getAttribute('aria-expanded') === 'true';
  btn.setAttribute('aria-expanded', String(!expanded));
  document.getElementById(targetId).hidden = expanded;
}
</script>
```

---

## Keyboard Navigation

Every interactive element must be reachable and operable with the keyboard alone. Mouse-only event handlers (mouseover, click without keyboard equivalent) lock out users who cannot use a pointer device.

### ❌ Before (inaccessible)
```html
<!-- ❌ Custom card clickable only by mouse — no Tab stop, no keyboard event -->
<div class="card" onclick="abrirDetalhe(1)">
  <h3>Produto A</h3>
  <p>Ver detalhes</p>
</div>

<!-- ❌ Submenu opens only on mouseover — keyboard users never see it -->
<ul>
  <li onmouseover="mostrarSubmenu('sub1')">
    Serviços
    <ul id="sub1" style="display:none">
      <li><a href="/consultoria">Consultoria</a></li>
    </ul>
  </li>
</ul>

<!-- ❌ Skip-to-content link hidden with display:none — not reachable by Tab -->
<a href="#conteudo" style="display:none">Ir para o conteúdo principal</a>
```

### ✅ After (accessible)
```html
<!-- ✅ Card as a button or link — focusable, keyboard-activatable -->
<article class="card">
  <h3><a href="/produto/1">Produto A</a></h3>
  <p>Ver detalhes</p>
</article>

<!-- ✅ Submenu keyboard-accessible via click/Enter -->
<nav aria-label="Menu principal">
  <ul>
    <li>
      <button type="button" aria-expanded="false" aria-haspopup="true"
              onclick="toggleSubmenu(this, 'sub1')">
        Serviços
      </button>
      <ul id="sub1" hidden>
        <li><a href="/consultoria">Consultoria</a></li>
      </ul>
    </li>
  </ul>
</nav>

<!-- ✅ Skip link visible on focus — first Tab press reveals it -->
<a href="#conteudo-principal" class="skip-link">
  Ir para o conteúdo principal
</a>
```

```css
/* Skip link is off-screen until focused */
.skip-link {
  position: absolute;
  top: -3rem;
  left: 0;
  background: #005fcc;
  color: #fff;
  padding: 0.5rem 1rem;
  z-index: 9999;
  transition: top 0.1s;
}
.skip-link:focus {
  top: 0;  /* Slides into view when Tab is pressed */
}
```

**Touch-target minimum size (44×44px):**
```css
/* ✅ Enhanced tap target (44×44px) — WCAG 2.5.5 Level AAA and iOS/Android HIG recommendation
   Note: WCAG 2.5.8 Level AA requires only 24×24px minimum; 44×44px is the preferred safe target */
button,
a,
[role="button"] {
  min-height: 44px;
  min-width: 44px;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}
```

---

## React Patterns

### 1. Accessible button with loading state

```jsx
import { useState } from 'react';

// ❌ Before: div used as button, no loading feedback
function SaveButtonBad({ onSave }) {
  return (
    <div className="btn" onClick={onSave}>
      Salvar
    </div>
  );
}

// ✅ After: real <button>, aria-busy communicates loading state
function SaveButton({ onSave }) {
  const [loading, setLoading] = useState(false);

  async function handleClick() {
    setLoading(true);
    await onSave();
    setLoading(false);
  }

  return (
    <button
      type="button"
      onClick={handleClick}
      disabled={loading}
      aria-busy={loading}           // Announces "busy" to screen readers
      aria-label={loading ? 'Salvando…' : 'Salvar'}
    >
      {loading ? 'Salvando…' : 'Salvar'}
    </button>
  );
}
```

### 2. Accessible form field with error

```jsx
// ❌ Before: no label association, no error feedback
function EmailFieldBad() {
  return (
    <div>
      <input type="email" placeholder="Digite seu e-mail" />
      <span style={{ color: 'red' }}>E-mail inválido</span>
    </div>
  );
}

// ✅ After: label linked by htmlFor/id, error linked by aria-describedby
function EmailField({ value, onChange, error }) {
  const fieldId = 'email-field';
  const errorId = 'email-field-error';

  return (
    <div>
      <label htmlFor={fieldId}>
        E-mail <span aria-hidden="true">*</span>
      </label>
      <input
        type="email"
        id={fieldId}
        value={value}
        onChange={onChange}
        aria-required="true"
        aria-invalid={!!error}            // Tells screen reader the field has an error
        aria-describedby={error ? errorId : undefined}
        autoComplete="email"
      />
      {error && (
        // role="alert" (assertive) is correct here — a form error requires immediate announcement
        <p id={errorId} role="alert">
          {error}
        </p>
      )}
    </div>
  );
}
```

### 3. Focus management after modal open/close

```jsx
import { useEffect, useRef } from 'react';

// ✅ Modal that moves focus in on open and back on close
function Modal({ isOpen, onClose, title, children }) {
  const closeButtonRef = useRef(null);
  const triggerRef = useRef(null);

  useEffect(() => {
    if (isOpen) {
      // Move focus to the close button when modal opens
      closeButtonRef.current?.focus();
    }
  }, [isOpen]);

  function handleClose() {
    onClose();
    // Return focus to whatever triggered the modal
    triggerRef.current?.focus();
  }

  function handleKeyDown(e) {
    if (e.key === 'Escape') handleClose();
  }

  if (!isOpen) return null;

  return (
    <div
      role="dialog"
      aria-modal="true"
      aria-labelledby="modal-title"
      onKeyDown={handleKeyDown}
    >
      <h2 id="modal-title">{title}</h2>
      {children}
      <button ref={closeButtonRef} type="button" onClick={handleClose}>
        Fechar
      </button>
    </div>
  );
}
```

### 4. Live region for dynamic notifications

```jsx
import { useState } from 'react';

// ✅ aria-live region announces status without disrupting the user
function Notification() {
  const [message, setMessage] = useState('');

  async function handleSave() {
    await saveData();
    setMessage('Dados salvos com sucesso.');
    // Clear after a few seconds so repeated saves are announced again
    setTimeout(() => setMessage(''), 4000);
  }

  return (
    <>
      <button type="button" onClick={handleSave}>Salvar</button>

      {/* role="status" + aria-live="polite": waits for screen reader to finish current sentence */}
      <div role="status" aria-live="polite" aria-atomic="true"
           className="sr-only">
        {message}
      </div>
    </>
  );
}
```

```css
/* Screen-reader-only utility — visually hidden but announced by AT */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

---

## Vue Patterns

### 1. Accessible icon-only button

```vue
<!-- ❌ Before: icon with no accessible name -->
<template>
  <button @click="fechar">
    <img src="icon-x.svg">
  </button>
</template>

<!-- ✅ After: aria-label names the button for screen readers -->
<template>
  <button type="button" :aria-label="labelFechar" @click="fechar">
    <img src="icon-x.svg" alt="">  <!-- alt="" because button label covers it -->
  </button>
</template>

<script setup>
const labelFechar = 'Fechar modal';
function fechar() { /* ... */ }
</script>
```

### 2. Form with reactive validation

```vue
<template>
  <form @submit.prevent="enviar" novalidate>
    <div>
      <label for="nome">Nome completo</label>
      <input
        id="nome"
        v-model="nome"
        type="text"
        :aria-invalid="!!erros.nome"
        :aria-describedby="erros.nome ? 'nome-erro' : undefined"
        required
        aria-required="true"
      />
      <p v-if="erros.nome" id="nome-erro" role="alert">
        {{ erros.nome }}
      </p>
    </div>
    <button type="submit">Enviar</button>
  </form>
</template>

<script setup>
import { ref, reactive } from 'vue';

const nome = ref('');
const erros = reactive({});

function enviar() {
  if (!nome.value.trim()) {
    erros.nome = 'Nome é obrigatório.';
    return;
  }
  delete erros.nome;
  // submit logic
}
</script>
```

### 3. Disclosure widget (accordion)

```vue
<template>
  <div>
    <button
      type="button"
      :aria-expanded="aberto"
      :aria-controls="conteudoId"
      @click="aberto = !aberto"
    >
      {{ titulo }}
    </button>
    <!-- :hidden removes the element from the accessibility tree when closed -->
    <!-- v-show (display:none) also hides from AT in most browsers, but :hidden -->
    <!-- is semantically explicit and guaranteed across all screen reader/browser combos -->
    <div :id="conteudoId" :hidden="!aberto">
      <slot />
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({ titulo: String });
const conteudoId = `accordion-${Math.random().toString(36).slice(2)}`;
const aberto = ref(false);
</script>
```

---

## Angular Patterns

### 1. Custom focusable component

```typescript
// ❌ Before: div with click handler — not keyboard accessible
// <div (click)="selecionar()">Opção A</div>

// ✅ After: selector targets a native <button> element — no role, tabindex, or keyboard
// listener needed because <button> handles all of that natively.
// Usage: <button app-opcao (selecionado)="onSelecionado()">Opção A</button>
import { Component, Output, EventEmitter, HostBinding, HostListener } from '@angular/core';

@Component({
  selector: 'button[app-opcao]', // restrict to native <button> elements only
  template: `<ng-content></ng-content>`,
})
export class OpcaoComponent {
  @Output() selecionado = new EventEmitter<void>();
  ativo = false;

  // aria-pressed is the only ARIA attribute needed — role and keyboard are native
  @HostBinding('attr.aria-pressed') get ariaPressed() { return this.ativo; }

  @HostListener('click') onClick() { this.ativar(); }

  private ativar() {
    this.ativo = !this.ativo;
    this.selecionado.emit();
  }
}
```

### 2. Accessible form with reactive validation

```typescript
// app-form.component.ts
import { Component } from '@angular/core';
import { FormBuilder, Validators, ReactiveFormsModule } from '@angular/forms';
import { CommonModule } from '@angular/common';

@Component({
  selector: 'app-contato-form',
  standalone: true,
  imports: [ReactiveFormsModule, CommonModule],
  template: `
    <form [formGroup]="form" (ngSubmit)="enviar()" novalidate>
      <div>
        <!-- label + htmlFor equivalent via for attribute -->
        <label for="email-campo">
          E-mail <span aria-hidden="true">*</span>
        </label>
        <input
          id="email-campo"
          type="email"
          formControlName="email"
          [attr.aria-invalid]="emailInvalido"
          [attr.aria-describedby]="emailInvalido ? 'email-erro' : null"
          aria-required="true"
          autocomplete="email"
        />
        <p *ngIf="emailInvalido" id="email-erro" role="alert">
          Por favor, informe um e-mail válido.
        </p>
      </div>
      <button type="submit" [disabled]="form.invalid" [attr.aria-busy]="enviando">
        {{ enviando ? 'Enviando…' : 'Enviar' }}
      </button>
    </form>
  `
})
export class ContatoFormComponent {
  enviando = false;

  form = this.fb.group({
    email: ['', [Validators.required, Validators.email]]
  });

  get emailInvalido(): boolean {
    const ctrl = this.form.get('email');
    return !!(ctrl?.invalid && ctrl?.touched);
  }

  constructor(private fb: FormBuilder) {}

  async enviar() {
    if (this.form.invalid) return;
    this.enviando = true;
    // await submitToApi(this.form.value);
    this.enviando = false;
  }
}
```

### 3. Live announcement service

```typescript
// a11y-announcer.service.ts
import { Injectable } from '@angular/core';

@Injectable({ providedIn: 'root' })
export class A11yAnnouncerService {
  private region: HTMLElement;

  constructor() {
    // Create a visually hidden aria-live region once, reuse across the app
    this.region = document.createElement('div');
    this.region.setAttribute('aria-live', 'polite');
    this.region.setAttribute('aria-atomic', 'true');
    this.region.style.cssText =
      'position:absolute;width:1px;height:1px;overflow:hidden;clip:rect(0,0,0,0)';
    document.body.appendChild(this.region);
  }

  // Call this anywhere to announce text to screen readers
  announce(message: string): void {
    this.region.textContent = '';
    setTimeout(() => { this.region.textContent = message; }, 50);
  }
}

// Usage in a component:
// this.announcer.announce('Relatório exportado com sucesso.');
```

---

## Quick Reference: Common Mistakes

| Mistake | Fix |
|---|---|
| `<img>` without `alt` | Add `alt="description"` or `alt=""` for decorative images |
| Generic link text ("clique aqui") | Use descriptive text: "Baixar relatório 2024" |
| `div`/`span` as button | Use `<button type="button">` |
| Input without `<label for="...">` | Link every input to a label via `for` + `id` |
| `outline: none` on focus | Replace with a custom visible `:focus-visible` style |
| Error only shown in red | Add icon + text message near the field |
| Heading levels skipped | Follow h1→h2→h3 hierarchy without gaps |
| Mouse-only events | Pair `click` + keyboard handler, or use native elements |
| `display:none` on skip link | Use off-screen CSS, visible on `:focus` |
| Hard-coded font height in px | Use relative units (`rem`, `em`) so browser zoom works |