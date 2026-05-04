---
name: agent-friendly-ux
description: Ensures websites are optimized for AI agent navigation and interaction. Use when creating or modifying any web page, component, or layout — especially interactive elements, forms, buttons, links, and navigation. Also use when the user asks to audit, review, or check any existing website for AI agent friendliness. Based on https://web.dev/articles/ai-agent-site-ux
author: Julia Logan, Head of SEO at AICT Media (https://aictmedia.com)
---

# Agent-Friendly Website UX

**Author:** Julia Logan, Head of SEO at [AICT Media](https://aictmedia.com)

AI agents are a new class of website visitor. They navigate on behalf of humans using screenshots, raw HTML, and the accessibility tree — not a monitor. Every site we build must send clean signals across all three channels.

These rules apply to every web artifact (react-vite, data-visualization, landing pages, dashboards, etc.).

## Core Principles

Everything that makes a site agent-friendly also makes it better for humans. Agent-readiness is a recommitment to well-structured, accessible, semantic web foundations.

## Rules

### 1. Use Semantic HTML for Interactive Elements

Always use `<button>` for actions and `<a>` for navigation. Never use styled `<div>` or `<span>` as clickable elements.

```tsx
// CORRECT
<button onClick={handleSubmit}>Submit</button>
<a href="/products">View Products</a>

// WRONG — agents cannot reliably identify these as interactive
<div onClick={handleSubmit} className="btn">Submit</div>
<span onClick={navigate} className="link">View Products</span>
```

If a non-semantic element must be interactive (rare), always add `role` and `tabindex`:

```tsx
<div role="button" tabIndex={0} onClick={handleAction}>Action</div>
```

### 2. Ensure Stable, Consistent Layouts

Agents that take screenshots get confused by shifting layouts. Keep interactive elements in predictable, consistent positions across similar pages.

- Place primary actions (Add to Cart, Submit, Save) in the same relative position across pages of the same type.
- Avoid layouts where key buttons jump to different locations based on content length, category, or viewport shifts.
- Prefer fixed/sticky positioning for critical navigation and action elements.

### 3. Eliminate Ghost Elements and Transparent Overlays

Agents may discard elements that appear covered or invisible in visual analysis.

- Do not place transparent overlays on top of interactive elements.
- Avoid invisible elements that capture clicks (e.g., expanded hit areas via transparent absolutely-positioned elements covering other content).
- If a modal or overlay is not active, remove it from the DOM or set `display: none` / `visibility: hidden` — do not leave it as a transparent layer.

### 4. Label All Form Inputs

Use the `for` attribute on `<label>` tags (or `htmlFor` in React) to explicitly link labels to inputs. This lets agents understand the purpose of each field.

```tsx
// CORRECT
<label htmlFor="email">Email Address</label>
<input id="email" type="email" name="email" />

// WRONG — agent cannot determine what this input is for
<input type="email" placeholder="Enter email" />
```

For inputs without visible labels, use `aria-label`:

```tsx
<input type="search" aria-label="Search products" placeholder="Search..." />
```

### 5. Ensure Interactive Elements Are Large Enough

Any interactive element required for the user journey must have a visible area larger than 8 square pixels. This prevents visual analysis from filtering it out.

- Minimum recommended touch/click target: 44x44px for primary actions, 24x24px minimum for secondary actions.
- Icon-only buttons must have sufficient padding or explicit sizing.

### 6. Use `cursor: pointer` for Clickable Elements

`cursor: pointer` is a strong signal for actionability in visual analysis. Apply it to all interactive custom elements.

```css
[role="button"], .clickable {
  cursor: pointer;
}
```

Native `<button>` and `<a>` elements already have appropriate cursor behavior by default — do not override them.

### 7. Make All Actions Visible in the Interface

Every action a user (or agent) can take should be clearly reflected in the UI. Avoid hidden functionality that requires:

- Complex hover sequences to reveal controls
- Gesture-only interactions with no visible affordance
- Actions only accessible through keyboard shortcuts with no UI counterpart

If an action exists, it should have a visible, discoverable element in the interface.

### 8. Write Clean, Structured HTML

Agents parse the DOM to understand element relationships. Clean structure helps.

- Use proper heading hierarchy (`h1` > `h2` > `h3`) — do not skip levels.
- Group related content in semantic containers (`<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`).
- Use `<form>` elements to wrap form fields.
- Use list elements (`<ul>`, `<ol>`) for lists of items, navigation menus.

### 9. Provide Meaningful ARIA When Needed

When native semantics are insufficient, add ARIA attributes:

- `aria-label` for elements whose purpose isn't clear from visible text.
- `aria-expanded` for toggleable elements (dropdowns, accordions).
- `aria-hidden="true"` for decorative elements that should be ignored.
- `aria-live` regions for dynamic content updates (toasts, status messages).

### 10. Ensure State Changes Are Reflected in the DOM

When an element changes state (selected, disabled, expanded, loading), reflect it in attributes agents can read:

```tsx
<button disabled={isLoading} aria-busy={isLoading}>
  {isLoading ? "Saving..." : "Save"}
</button>

<details open={isExpanded}>
  <summary>More info</summary>
  ...
</details>
```

## Quick Checklist

Before delivering any web page or component, verify:

- [ ] All clickable elements use `<button>` or `<a>` (or have `role` + `tabindex`)
- [ ] All form inputs have associated `<label>` elements (via `htmlFor`/`for`) or `aria-label`
- [ ] Interactive elements have visible area > 8 sq px (prefer 44x44px for primary actions)
- [ ] No transparent overlays covering interactive elements
- [ ] Layout is stable — key actions don't shift position across similar pages
- [ ] Page uses semantic HTML structure (`nav`, `main`, `section`, `article`, `footer`)
- [ ] Dynamic states reflected via DOM attributes (`disabled`, `aria-expanded`, `aria-busy`)
- [ ] All user actions have visible UI affordances (no hidden-only interactions)
- [ ] Custom interactive elements use `cursor: pointer`
- [ ] Heading hierarchy is correct and sequential

## Auditing an Existing Website

Use this workflow when the user asks to review, audit, or check any website (external or in-project) for AI agent friendliness.

### Audit Process

1. **Gather the page content.** Use the appropriate tools depending on the target:
   - **External URL:** Take a screenshot (`type: external_url`) for visual analysis. Use `webFetch` with `extractContent: true` to get the HTML/text structure.
   - **In-project page:** Take a screenshot (`type: app_preview`) for visual analysis. Read the source files directly.

2. **Visual analysis (from screenshot).** Look for:
   - Layout stability — are key actions in consistent, predictable positions?
   - Interactive element sizing — any buttons/links that look too small to detect?
   - Ghost elements — any transparent overlays or invisible layers covering content?
   - Hidden actions — any functionality that only appears on hover or via gestures?

3. **Structural analysis (from HTML/source).** Check for:
   - **Semantic HTML:** Are interactive elements using `<button>`, `<a>`, `<input>`, `<select>`? Or are `<div>`/`<span>` elements being used as buttons/links without `role` and `tabindex`?
   - **Form labeling:** Do all `<input>`, `<textarea>`, and `<select>` elements have an associated `<label>` (via `for`/`htmlFor`) or `aria-label`?
   - **Heading hierarchy:** Does the page follow `h1` > `h2` > `h3` without skipping levels?
   - **Semantic containers:** Does the page use `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>` appropriately?
   - **ARIA attributes:** Are dynamic elements (dropdowns, modals, accordions) using `aria-expanded`, `aria-hidden`, `aria-live` where needed?
   - **State reflection:** Are disabled/loading/selected states reflected in DOM attributes (`disabled`, `aria-busy`, `aria-selected`)?
   - **Cursor styles:** Do custom interactive elements set `cursor: pointer`?

4. **Produce the audit report.** Organize findings into three severity levels:

### Audit Report Format

```markdown
# Agent-Friendly UX Audit: [Site/Page Name]

## Score: X/10

## Critical Issues (blocks agent interaction)
- [Issue]: [Description + location on page]
  - **Fix:** [Specific recommendation]

## Warnings (degrades agent performance)
- [Issue]: [Description + location on page]
  - **Fix:** [Specific recommendation]

## Suggestions (improves agent experience)
- [Issue]: [Description + location on page]
  - **Fix:** [Specific recommendation]

## What's Working Well
- [Positive finding]
```

### Severity Definitions

- **Critical:** Agent cannot complete a key task — e.g., a primary action uses a non-semantic element with no role, form inputs have no labels, or interactive elements are covered by overlays.
- **Warning:** Agent can likely work around it but may fail — e.g., small click targets, inconsistent layout positions, hover-only actions, missing ARIA states.
- **Suggestion:** Best-practice improvements — e.g., adding semantic containers, improving heading hierarchy, adding `cursor: pointer` to custom elements.

### Common Patterns to Flag

| Pattern | Severity | Recommendation |
|---------|----------|----------------|
| `<div onClick={...}>` without `role="button"` | Critical | Use `<button>` or add `role="button" tabIndex={0}` |
| `<input>` without `<label>` or `aria-label` | Critical | Add `<label htmlFor="...">` or `aria-label` |
| Transparent overlay covering buttons | Critical | Remove overlay or set `pointer-events: none` on it |
| Click target < 24x24px | Warning | Increase padding or min-width/min-height |
| Actions only visible on hover | Warning | Show controls by default, or provide visible toggle |
| Missing `aria-expanded` on dropdown trigger | Warning | Add `aria-expanded={isOpen}` |
| No `<main>` landmark | Suggestion | Wrap primary content in `<main>` |
| Skipped heading level (h1 to h3) | Suggestion | Add missing h2 level |
| No `cursor: pointer` on custom clickable | Suggestion | Add `cursor: pointer` in CSS |
