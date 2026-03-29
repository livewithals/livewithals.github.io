# Narula's ALS Diary — Jekyll Site
## livewithals.com | Sidebar Layout

---

## Folder Structure

```
livewithals/
│
├── _config.yml              ← Site settings + NAVIGATION MENU
├── Gemfile                  ← Ruby dependencies
│
├── _layouts/
│   ├── default.html         ← Standard page (sidebar + hero + content)
│   └── research.html        ← Research pages (adds citation metadata bar)
│
├── _includes/
│   ├── head.html            ← <head>, fonts, MathJax toggle
│   ├── sidebar.html         ← Dark left sidebar (auto-built from _config.yml)
│   └── footer.html          ← Footer + JS for sidebar/dropdown
│
├── _sass/
│   ├── _variables.scss      ← ← CHANGE COLOURS / FONTS HERE
│   └── main.scss            ← All styles
│
├── assets/
│   ├── css/style.scss       ← CSS entry point (don't edit)
│   └── images/              ← ← ALL PHOTOS GO HERE
│       ├── hero-about.jpg
│       ├── hero-story.jpg
│       ├── hero-hacks.jpg
│       └── ... (one hero per page)
│
└── _pages/                  ← ← YOUR CONTENT IS HERE
    ├── about.md
    ├── our-als-story.md
    ├── caregiving-hacks.md
    ├── diet-pattern.md
    ├── faq.md
    └── ... (one .md file per page)
```

---

## Day-to-Day Editing

### Edit existing content
Open any file in `_pages/` and edit. Pure Markdown — no HTML knowledge needed.

### Add a new section
```markdown
## New Section Heading

Your content here.

### Subsection

Even more content...
```

### Add a new page

1. Create `_pages/new-topic.md`:
```markdown
---
layout: default
title: "Your Page Title"
permalink: /new-topic/
eyebrow: Optional subtitle above title
hero_image: hero-new-topic.jpg   ← optional, delete line if no hero
---

Your content here in Markdown...
```

2. Add to navigation in `_config.yml`:
```yaml
navigation:
  - title: "New Topic"
    url: "/new-topic/"
```

3. Add hero image to `assets/images/hero-new-topic.jpg`

That's it — sidebar updates automatically!

### Remove a page
Delete its entry from `_config.yml` navigation. The .md file can stay.

### Change the hero image on a page
Edit the page's frontmatter:
```markdown
hero_image: your-photo.jpg    ← must be in assets/images/
```
Remove the line entirely to show no hero image.

---

## LaTeX / Math Equations

Add `math: true` to any page's frontmatter:
```markdown
---
layout: default
title: My Page
math: true        ← this loads MathJax
---

Inline: The correction is $\Delta V = 84$ ml.

Block equation:
$$
C_{rs} = \frac{V_{T,\text{measured}}}{P_\text{plateau} - \text{PEEP}}
$$
```

---

## Callout Boxes

```html
<!-- Disclaimer (orange-left-border) -->
<div class="disclaimer-box">
Please consult a physician. <a href="/disclaimer/">Read full disclaimer.</a>
</div>

<!-- Tip (green-left-border) -->
<div class="tip-box">
<p><strong>Tip:</strong> Keep Ambu bag within arm's reach at all times.</p>
</div>

<!-- Warning (red-left-border) -->
<div class="warning-box">
<p><strong>Important:</strong> Sterile technique is essential.</p>
</div>

<!-- Pull quote (memoir style) -->
<div class="pull-quote">
<p>A meaningful sentence that deserves emphasis.</p>
</div>

<!-- Finding box (research pages) -->
<div class="finding-box">
<h4>Key Finding</h4>
<p>84 mL average overestimation per breath.</p>
</div>
```

---

## Adding Images to Content

Save image to `assets/images/` then:

```markdown
<!-- Simple inline image -->
![Caption](/assets/images/photo.jpg)

<!-- Styled figure with caption -->
<figure class="photo">
  <img src="/assets/images/photo.jpg" alt="Description">
  <figcaption>Your caption here</figcaption>
</figure>

<!-- Two photos side by side -->
<div class="photo-pair">
  <figure class="photo">
    <img src="/assets/images/photo1.jpg" alt="Left">
    <figcaption>Left caption</figcaption>
  </figure>
  <figure class="photo">
    <img src="/assets/images/photo2.jpg" alt="Right">
    <figcaption>Right caption</figcaption>
  </figure>
</div>
```

---

## Hero Images

Each page can have a full-width hero photo at the top (like the current Google Sites layout). 

- Save photo as e.g. `assets/images/hero-about.jpg`
- Set in page frontmatter: `hero_image: hero-about.jpg`
- Recommended size: 1400×500px or wider, landscape orientation
- The image is darkened automatically so it doesn't overpower the page title

---

## Changing Colours or Fonts

Open `_sass/_variables.scss`:

```scss
$red:         #b41e1e;    // ← Accent colour (headings, links, sidebar highlights)
$sidebar-bg:  #1e1e1e;    // ← Sidebar background
$cream:       #faf7f2;    // ← Page background

$font-display: 'Cormorant Garamond', Georgia, serif;  // ← Elegant heading font
$font-body:    'EB Garamond', Georgia, serif;          // ← Body text font
$font-ui:      'Josefin Sans', sans-serif;             // ← Nav, labels, captions
```

---

## Deployment to GitHub Pages

### Step 1 — Install (one time only)
```bash
gem install bundler jekyll
cd livewithals
bundle install
```

### Step 2 — Preview locally
```bash
bundle exec jekyll serve
# Open http://localhost:4000
```

### Step 3 — Push to GitHub
```bash
git init
git add .
git commit -m "Initial site"
git remote add origin https://github.com/YOUR_USERNAME/livewithals.git
git push -u origin main
```

### Step 4 — Enable GitHub Pages
GitHub repo → Settings → Pages → Source: Deploy from branch → main

### Step 5 — Connect livewithals.com
At your domain registrar, add DNS records:
```
Type    Name    Value
A       @       185.199.108.153
A       @       185.199.109.153
A       @       185.199.110.153
A       @       185.199.111.153
CNAME   www     YOUR_USERNAME.github.io
```
GitHub Pages Settings → Custom domain: `www.livewithals.com` → Save

Wait ~30 minutes → livewithals.com is live ✓

---

*Maintained by Harsh Kumar Narula — livewithals.com*
