# Narula's ALS Diary — Minimal Mistakes Jekyll Theme
## livewithals.com

---

## Quick answers

### LaTeX / Math equations
Write equations anywhere in any `.md` file — no extra config needed:
```markdown
Inline: The tidal volume is $V_T = 450$ ml.

Block:
$$
\Delta V_T = \int_0^{T_e} \left[ \dot{V}_1 - \dot{V}_2 \right] d\tau
$$
```
MathJax loads on every page automatically via `_includes/head/custom.html`.

### Add a new page
1. Create `_pages/new-topic.md`:
```markdown
---
layout: single
title: "New Topic"
permalink: /new-topic/
sidebar:
  nav: "main"
toc: true
---
Your content here...
```
2. Add to `_data/navigation.yml`:
```yaml
main:
  - title: "New Topic"
    url: /new-topic/
```

### Add a section / subsection
Just use Markdown headings:
```markdown
## Section (appears in TOC automatically)
### Subsection
#### Sub-subsection
```

### Change theme skin
In `_config.yml`:
```yaml
minimal_mistakes_skin: "dark"
# Options: default | dark | contrast | mint | sunrise | aqua | neon | plum
```

### Change accent colour
In `assets/css/main.scss`, find:
```scss
$als-red: #b41e1e;
```
Change to any hex colour. Affects: headings, links, nav highlights, pull quotes.

### Callout boxes
```html
<div class="notice--als-disclaimer">Disclaimer text here.</div>
<div class="notice--als-tip">Tip text here.</div>
<div class="notice--als-warning">Warning text here.</div>
<div class="notice--als-finding">
  <h4>Key Finding</h4>
  <p>Finding text here.</p>
</div>
```

### Pull quote
```html
<div class="pull-quote">
<p>A meaningful sentence.</p>
</div>
```

### Hero image on a page
Add to frontmatter:
```yaml
header:
  overlay_image: /assets/images/your-photo.jpg
  overlay_filter: 0.4   # 0.0 = no darkening, 1.0 = fully black
```
Save photo in `assets/images/`.

### Table of contents
`toc: true` in frontmatter → automatic TOC from headings.
`toc: false` → no TOC.

---

## Deploy to GitHub Pages (no Ruby needed locally)

1. Create GitHub repo
2. Upload all these files
3. Settings → Pages → Source: **GitHub Actions**
4. Done — site builds automatically in ~2 minutes
