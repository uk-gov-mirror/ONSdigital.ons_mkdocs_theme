# Project Plan: ONS → FSA Theme Rebrand

**Project:** Rebrand `ons_mkdocs_theme` as `fsa_mkdocs_theme`  
**Author:** james.westwood@food.gov.uk  
**Date:** 2026-05-13  

---

## Objective

Replace all ONS branding, colours, fonts, metadata, and references throughout the MkDocs theme with FSA brand standards, and rename the Python package from `ons_mkdocs_theme` to `fsa_mkdocs_theme`.

---

## FSA Design Standards Summary

### Colours
| Role | Hex |
|---|---|
| Primary / header background | `#007c75` |
| Dark / hover / footer | `#014b4c` |
| Footer meta background | `#002a2a` |
| Accent / focus | `#f1c400` |
| Body text | `#101010` |
| Links | `#007c75` |
| Link hover | `#014b4c` |
| Nav link hover | `#f1c400` |

### Typography
| Use | Family | Weight |
|---|---|---|
| Body | `Open Sans, sans-serif` | 400 / 600 |
| Headings (h1–h4) | `Fira Sans, sans-serif` | 700 |

---

## Phase 1 — Rename Folder and Package

**Tasks:**
1. Run `git mv ons_mkdocs_theme/ fsa_mkdocs_theme/` to rename the theme directory while preserving git history.
2. Copy `fsa-logo.svg` from `C:\repos\ladataproject_etl\docs\assets\fsa-logo.svg` into `fsa_mkdocs_theme/assets/images/fsa-logo.svg`.

**Files affected:**
- `ons_mkdocs_theme/` (entire directory → `fsa_mkdocs_theme/`)

---

## Phase 2 — Package Build Config

**Tasks:**
3. Update `setup.cfg`:
   - `name`: `ons_mkdocs_theme` → `fsa_mkdocs_theme`
   - `author`: `Keilan Evans, ONS` → remove / blank
   - `author_email`: → `james.westwood@food.gov.uk`
   - `description`: replace ONS references with FSA
   - `url`: remove (no public repo URL)
   - `[options.package_data]` key: `ons_mkdocs_theme` → `fsa_mkdocs_theme`
4. Update `MANIFEST.in`: `ons_mkdocs_theme` → `fsa_mkdocs_theme`

**Files affected:**
- `setup.cfg`
- `MANIFEST.in`

---

## Phase 3 — MkDocs Config

**Tasks:**
5. Update `mkdocs.yml`:
   - `site_name`: `ONS MkDocs Theme` → `FSA MkDocs Theme`
   - Remove `repo_name` and `repo_url`
   - `custom_dir`: `ons_mkdocs_theme` → `fsa_mkdocs_theme`
   - `logo`: `assets/images/logo.svg` → `assets/images/fsa-logo.svg`
   - `copyright`: replace ONS link/text with FSA (`food.gov.uk`)
   - Remove `social` link (pointed to ONS GitHub)
   - `watch` path: `ons_mkdocs_theme/` → `fsa_mkdocs_theme/`
6. Update `fsa_mkdocs_theme/mkdocs_theme.yml`:
   - Font `text: Roboto` → `Open Sans`

**Files affected:**
- `mkdocs.yml`
- `fsa_mkdocs_theme/mkdocs_theme.yml`

---

## Phase 4 — CSS Rebrand

**Tasks:**
7. Update `fsa_mkdocs_theme/assets/stylesheets/main.css`:
   - Add Google Fonts `@import` for Open Sans and Fira Sans after `@charset` declaration
   - Update `:root` CSS variables:

| Variable | From | To |
|---|---|---|
| `--font-color` | `#222222` | `#101010` |
| `--font-family` | `'Helvetica', sans-serif` | `'Open Sans', sans-serif` |
| `--links-color` | `#00796b` | `#007c75` |
| `--links-hover-color` | `#a8bd3a` | `#014b4c` |
| `--logo-header-nav-font-color` | `#003d59` | `#014b4c` |
| `--header-nav-background-color` | `#003d59` | `#007c75` |
| `--title-font-color` | `#003d59` | `#014b4c` |
| `--top-nav-links-hover-color` | `#a8bd3a` | `#f1c400` |
| `--footer-background-color` | `#263238` | `#014b4c` |

   - Add `font-family: 'Fira Sans', sans-serif; font-weight: 700;` to the `.md-typeset h1–h4` rule

**Files affected:**
- `fsa_mkdocs_theme/assets/stylesheets/main.css`

---

## Phase 5 — Docs Content

**Tasks:**
8. Update `docs/setup.md`:
   - `pip install ons_mkdocs_theme` → `pip install fsa_mkdocs_theme`
   - Folder creation and `git clone` instructions
9. Update `docs/creating-your-site.md` line 43: theme name in YAML code example
10. Update `docs/building-your-site.md` line 4: page title frontmatter
11. Update `docs/contributing/reporting-a-bug.md` and `docs/contributing/reporting-a-docs-issue.md`: remove/genericise ONSdigital issue tracker URLs

**Files affected:**
- `docs/setup.md`
- `docs/creating-your-site.md`
- `docs/building-your-site.md`
- `docs/contributing/reporting-a-bug.md`
- `docs/contributing/reporting-a-docs-issue.md`

---

## Phase 6 — README

**Tasks:**
12. Update `README.md`:
    - Logo `<img>` `src` attribute
    - All body text references to "ONS MkDocs Theme"
    - `pip install ons_mkdocs_theme` → `fsa_mkdocs_theme`
    - `git clone` URL → remove or update

**Files affected:**
- `README.md`

---

## Phase 7 — GitHub Issue Templates

**Tasks:**
13. Update `.github/ISSUE_TEMPLATE/bug_issue.yml`: replace all `onsdigital.github.io/ons_mkdocs_theme` and `ONSdigital/ons_mkdocs_theme` URLs
14. Update `.github/ISSUE_TEMPLATE/documentation_issue.yml`: same

**Files affected:**
- `.github/ISSUE_TEMPLATE/bug_issue.yml`
- `.github/ISSUE_TEMPLATE/documentation_issue.yml`

---

## Verification Checklist

- [ ] `pip install -e .` installs the package as `fsa_mkdocs_theme`
- [ ] `mkdocs serve` renders site title as "FSA MkDocs Theme"
- [ ] Header background is `#007c75`, footer is `#014b4c`
- [ ] FSA logo renders (not the ONS logo)
- [ ] Headings use Fira Sans; body text uses Open Sans
- [ ] No remaining ONS references: `grep -r "ons_mkdocs_theme\|ONSdigital\|ons\.gov" --include="*.py" --include="*.yml" --include="*.yaml" --include="*.cfg" --include="*.md" --include="*.css" .`
