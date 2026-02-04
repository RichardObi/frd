# FRD Landing Page - AI Coding Agent Instructions

This document guides AI agents in maintaining and enhancing the Fréchet Radiomics Distance (FRD) landing page website.

## Project Overview

**Purpose**: Modern, engaging landing page showcasing the FRD paper and encouraging adoption of the metric in medical imaging research.

**Tech Stack**:
- Static HTML/CSS/JavaScript (no build tools required)
- GitHub Pages deployment
- Vanilla JavaScript (no frameworks)
- Minimal dependencies for fast loading

**Key Resources**:
- Paper (Journal): https://www.sciencedirect.com/science/article/pii/S1361841526000125
- Paper (arXiv): https://arxiv.org/abs/2412.01496
- Code: https://github.com/RichardObi/frd-score
- Evaluation Framework: https://github.com/mazurowski-lab/medical-image-similarity-metrics
- Design Reference: https://langdaniel.github.io/TeNCA/ (academic, clean aesthetic)

## Architecture & Key Patterns

### Page Structure (Single-Page Application)
The landing page uses semantic HTML sections with smooth scrolling navigation:
- `#home` - Hero section with authors, institutions, and CTA buttons
- `#about` - Problem/solution description
- `#deepdive` - Technical blog-style deep dive into FRD methodology
- `#method` - Technical methodology with paper figures
- `#results` - Key findings, applications, and interactive visualizations
- `#benchmarks` - Comparative performance tables vs. FID, RadFID, etc.
- `#datasets` - Overview of validated datasets across modalities
- `#code` - Quick start and installation
- `#team` - Author affiliations and contact information
- `#faq` - Frequently asked questions
- `#citation` - BibTeX citation and publication links

**Why this approach**: Comprehensive single-page layout provides all information without navigation complexity, while maintaining fast load times and excellent SEO.

### Asset Organization
- **Images** (`static/images/`): Paper figures, diagrams, comparison plots
- **CSS** (`static/css/style.css`): Single stylesheet with CSS variables for theming
- **JS** (`static/js/main.js`): Minimal vanilla JS for navigation and UX enhancements
- **PDFs** (`static/pdf/`): Full paper, supplementary materials

**Convention**: Use descriptive filenames with hyphens (e.g., `frd-comparison-results.png`, `method-overview.png`)

### Styling System
Colors are centralized in CSS variables:
```css
:root {
    --primary-color: #1e40af;      /* Brand blue */
    --secondary-color: #7c3aed;    /* Accent purple */
    --text-dark: #1f2937;
    --text-light: #6b7280;
    --bg-light: #f9fafb;           /* Subtle background for alt sections */
    --bg-white: #ffffff;
}
```

**Pattern**: Sections alternate between white and light gray backgrounds (`section:nth-child(odd)`) to create visual separation. Modify only CSS variables for consistent theming.

## Development Workflows

### Adding Content Sections

**Task**: Add a new feature section (e.g., Applications, Benchmarks, Team)

1. **Add HTML section** in `index.html`:
   ```html
   <section id="applications" class="applications">
       <div class="container">
           <h2>Applications</h2>
           <!-- Content here -->
       </div>
   </section>
   ```

2. **Add navigation link** in navbar (keep alphabetical order):
   ```html
   <li><a href="#applications">Applications</a></li>
   ```

3. **Add CSS** in `style.css`:
   ```css
   .applications { /* section-specific styles */ }
   ```

4. **Test**: Verify smooth scrolling works and responsive layout (test at 768px breakpoint)

### Integrating Paper Figures

1. **Prepare images**: Optimize PNG/JPG (~100-200KB max per image for web)
2. **Place in** `static/images/` with descriptive name
3. **Add to HTML**:
   ```html
   <figure>
       <img src="static/images/method-overview.png" alt="FRD pipeline diagram">
       <figcaption>Figure X: Description from paper</figcaption>
   </figure>
   ```
4. **Style in CSS**: Use flexbox for responsive image grids

### Responsive Design

**Breakpoint**: 768px (tablet/mobile threshold)

Always test mobile layout:
```bash
# In browser dev tools: Toggle device toolbar (Cmd+Shift+M)
# Or resize to 375px width
```

Pattern in CSS:
```css
@media (max-width: 768px) {
    /* Adjust grid columns, font sizes, padding */
    h1 { font-size: 2.5rem; }
    .content-grid { grid-template-columns: 1fr; }
}
```

## Common Tasks & Code Patterns

### Adding Author Information
Authors and institutions are displayed in the hero section. Update in [index.html](index.html):
```html
<div class="authors">
    <p>Author1¹, Author2²³, ...</p>
</div>
<div class="institutions">
    <p class="institution-list">
        <span>¹ Institution Name</span> • ...
    </p>
</div>
```

**Pattern**: Use superscript numbers (¹²³) for affiliation markers; separate institutions with bullets (•).

### Adding a Feature Card Grid
Used in Results section. Pattern for repeating cards:
```html
<div class="results-grid">
    <div class="result-card">
        <h3>Feature</h3>
        <p>Description</p>
    </div>
</div>
```

```css
.results-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
}

.result-card {
    border-left: 4px solid var(--primary-color);  /* Accent line */
    transition: transform 0.3s ease;              /* Hover effect */
}
```

**Convention**: Use `auto-fit` for responsive column sizing; left borders for emphasis; subtle hover transforms.

### Interactive Visualization Placeholders
For future interactive elements (charts, comparisons):
```html
<div class="interactive-viz">
    <h3>🎮 Interactive Feature</h3>
    <div class="viz-placeholder">
        <div class="viz-controls">
            <!-- Controls here -->
        </div>
        <div class="viz-canvas">
            <p>📊 Visualization will appear here</p>
        </div>
    </div>
</div>
```

**Style**: Gradient background, white text, placeholder canvas with min-height: 300px. Ready for D3.js, Plotly, or Chart.js integration.

### Code Block Display
For installation/usage code:
```html
<pre><code>pip install frd-score
from frd import compute_frd
result = compute_frd(images_1, images_2)</code></pre>
```

**Style**: Dark background (`--text-dark`), light text, monospace font (`Monaco`, fallback to `Courier New`)

### Button Styling
Two states available:
```html
<a href="#" class="btn btn-primary">Read Paper</a>
<a href="#" class="btn btn-secondary">View Code</a>
```

**Pattern**: Primary buttons are brand-colored; secondary buttons have border-only style. Both have consistent hover transitions.

## GitHub Pages Deployment

**Setup** (one-time):
1. Repository must be public
2. Settings → Pages → Source: `main` branch
3. Site publishes at `https://username.github.io/frd-website`

**Process** (on each update):
```bash
git add .
git commit -m "Update: [brief description]"
git push origin main
# Site updates automatically (check Actions tab for deployment status)
```

**Custom domain** (optional):
1. Create `CNAME` file with domain name
2. Update DNS CNAME record pointing to `username.github.io`

## Quality Standards

### Accessibility
- Use semantic HTML: `<section>`, `<nav>`, `<article>`, `<figure>`
- Include `alt` text for all images
- Sufficient color contrast (WCAG AA minimum)
- Test keyboard navigation (Tab, Enter on links)

### Performance
- Optimize images before adding (target <200KB each)
- No external libraries for basic functionality
- Use CSS for animations (not JS)
- Test page load speed (target <2s first contentful paint)

### SEO
- Descriptive `<title>` and `<meta name="description">`
- Proper heading hierarchy (h1 → h2 → h3)
- Internal anchor links for navigation
- Canonical domain set in GitHub Pages

## File References for Common Tasks

| Task | File | Section |
|------|------|---------|
| Update hero text/buttons | [index.html](index.html#L21-L30) | Hero section |
| Change brand colors | [static/css/style.css](static/css/style.css#L2-L8) | `:root` variables |
| Add responsive breakpoint | [static/css/style.css](static/css/style.css#L252-L280) | `@media` query |
| Modify navigation links | [index.html](index.html#L15-L23) | Navbar nav-links |
| Style new section | [static/css/style.css](static/css/style.css#L140-L160) | Section classes |
| Add interactivity | [static/js/main.js](static/js/main.js) | Main JavaScript file |

## Do's and Don'ts

✅ **DO**:
- Keep markup semantic and minimal
- Use CSS variables for theming
- Test on mobile (768px and 375px viewports)
- Compress images before adding
- Add `alt` text to all images
- Use consistent spacing (2rem for sections, 1rem for content)

❌ **DON'T**:
- Add heavy JavaScript frameworks (Vue, React)
- Use inline styles (always use CSS classes)
- Add hard-coded colors (always use CSS variables)
- Skip responsive testing
- Include unoptimized images (>200KB)
- Change HTML structure without updating nav links
- Modify existing color variables without approval (they establish visual identity)

## Notes for Agents

- This is a **static site** — no backend needed. No databases, no server-side code.
- The landing page should be **visually professional** but not overly complex. Reference the TeNCA design as the gold standard.
- **Paper integration** is key: figures and key results from https://arxiv.org/abs/2412.01496 should be prominently featured.
- Keep the **call-to-action clear**: readers should easily find links to the paper, code repository, and installation instructions.
- The audience is **academic researchers** in medical imaging — tone should be professional but accessible.
