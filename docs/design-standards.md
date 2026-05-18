# FSA Design Standards

Reference for applying FSA brand standards to MkDocs documentation.

---

## Colours

Extracted from the live `food.gov.uk` stylesheet (`fsa_2021` Drupal theme).

### Primary

| Role | Hex |
|---|---|
| Primary / header background | `#007c75` |
| Link hover | `#014b4c` |
| Focus / accent | `#f1c400` |
| Body text | `#000000` |
| Background | `#ffffff` |

### Secondary

| Role | Hex |
|---|---|
| Error / alert | `#e31837` |
| Dark blue | `#165c7d` |
| Warning yellow | `#fdb913` |
| Purple | `#49176d` |
| Info blue | `#007fb2` |

### UI / Tertiary

| Role | Hex |
|---|---|
| Mid green | `#6cb33f` |
| Light green | `#a9c47f` |
| Dark grey (secondary text) | `#53565a` |
| Page background | `#f0f3f5` |
| Borders | `#dee2e5` |
| Near-black body text | `#101010` |

### Hover / interactive states

| Role | Hex |
|---|---|
| Purple hover | `#2a0247` |
| Dark green hover | `#002a2a` |
| Grey hover | `#d9d9d6` |

---

## Typography

| Use | Family | Weight |
|---|---|---|
| Body | `Open Sans, sans-serif` | 400 (normal), 600 (bold) |
| Headings | `Fira Sans, sans-serif` | 700 (bold) |

Both fonts are available on Google Fonts.

---

## Logo

The FSA logo is an inline SVG — it is not served as a standalone file from `food.gov.uk`. Two versions exist in the `fsa_2021` CSS as base64 data URIs:

- **English** — dark green wordmark (`#016f51`) on transparent background
- **Welsh** — white wordmark on coloured background

The logo comprises two elements:
1. A DNA-helix / sustainability symbol (greens: `#2aa237`, `#a9c47e`, `#016f51`, `#fff`)
2. "Food Standards Agency" wordmark in `#016f51`

The logo is saved at `docs/assets/fsa-logo.svg`.

---

## Favicon

The `food.gov.uk` HTML references these paths (relative to the domain root):

```
/themes/custom/fsa_2021/dist/img/favicon/apple-touch-icon.png  (180×180)
/themes/custom/fsa_2021/dist/img/favicon/favicon-16x16.png
/themes/custom/fsa_2021/dist/img/favicon/favicon-32x32.png
/themes/custom/fsa_2021/favicon.ico
```

Save to `docs/assets/` and reference in `mkdocs.yml`:

```yaml
extra:
  favicon: assets/favicon-32x32.png
```

---

## Applying to MkDocs

The project uses `mkdocs-tech-docs-template` (a Python port of the GDS Tech Docs Template built on MkDocs Material). Override colours via `docs/stylesheets/extra.css`:

```css
/* FSA primary colour overrides */
:root {
  --md-primary-fg-color: #007c75;
  --md-primary-fg-color--light: #6cb33f;
  --md-primary-fg-color--dark: #014b4c;
  --md-accent-fg-color: #f1c400;
  --md-typeset-a-color: #007c75;
}

/* Headings */
.md-typeset h1,
.md-typeset h2,
.md-typeset h3 {
  font-family: "Fira Sans", sans-serif;
  font-weight: 700;
}

/* Body */
body {
  font-family: "Open Sans", sans-serif;
}
```

Reference in `mkdocs.yml`:

```yaml
extra_css:
  - stylesheets/extra.css
```
