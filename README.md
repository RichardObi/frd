# FRD Landing Page

A modern landing page for the **Fréchet Radiomics Distance (FRD)** paper - a versatile metric for comparing medical imaging datasets.

## Overview

This repository hosts the official landing page for the FRD project at https://richardobi.github.io/frd-website (or your custom domain).

FRD is a perceptual metric tailored for medical images that utilizes standardized, clinically meaningful, and interpretable radiomics features. It outperforms existing image distribution metrics across multiple medical imaging applications including:

- Out-of-domain (OOD) detection
- Image-to-image translation evaluation
- Unconditional image generation assessment

**Published in:** Medical Image Analysis, Volume 110, Article 103943 (2026)

## Project Structure

```
frd-website/
├── index.html              # Main landing page with 11 sections
├── README.md              # This file
├── static/
│   ├── css/
│   │   └── style.css      # Comprehensive styling with 600+ lines
│   ├── js/
│   │   └── main.js        # Navigation and interactive features
│   ├── images/            # Paper figures, diagrams, comparison plots
│   └── pdf/               # Paper PDF and supplementary materials
└── .github/
    └── copilot-instructions.md  # AI agent development guidelines
```

## Page Sections

1. **Hero**: Authors, institutions, publication badges, CTA buttons
2. **About**: Problem statement and FRD solution overview
3. **Deep Dive**: Blog-style technical walkthrough with radiomic features, algorithm steps, findings
4. **Method**: FRD pipeline with paper figures (placeholders for actual images)
5. **Results**: Key findings with performance metrics and interactive visualization placeholders
6. **Benchmarks**: Comparative tables (FRD vs. FID, RadFID, LPIPS)
7. **Datasets**: Overview of validated datasets (Brain MRI, Breast MRI, Chest X-ray, Abdominal CT/MRI)
8. **Code**: Installation, quick start, features list
9. **Team**: Institutions and collaborators across Duke, UBarcelona, Helmholtz, Yale
10. **FAQ**: 10+ common questions with detailed answers
11. **Citation**: BibTeX with journal and arXiv links

## Getting Started

### Local Development

No build process required! Simply open `index.html` in a browser or serve locally:

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx http-server

# Using Ruby
ruby -run -ehttpd . -p8000
```

Then navigate to `http://localhost:8000`

## Key Features

- **Responsive Design**: Optimized for desktop, tablet, and mobile
- **Semantic HTML**: Accessible and SEO-friendly
- **Fast Loading**: Minimal dependencies, optimized assets
- **GitHub Pages Ready**: Deploy directly from the `main` branch

## Customization

### Adding Figures from the Paper

Place figure images in `static/images/` and reference them:

```html
<img src="static/images/figure-name.png" alt="Figure description">
```

### Updating Content

Edit sections directly in `index.html`:
- **Hero section**: Main title and CTA buttons
- **About section**: Problem/solution description
- **Method section**: Technical details and figures
- **Results section**: Key findings
- **Code section**: Installation and usage
- **Citation section**: BibTeX citation

### Styling

Modify colors and layout in `static/css/style.css`:

```css
:root {
    --primary-color: #1e40af;      /* Main brand color */
    --secondary-color: #7c3aed;    /* Accent color */
}
```

## Deployment

### GitHub Pages

1. Push to a repository on GitHub
2. Go to **Settings → Pages**
3. Select `main` branch as source
4. Site will be available at `https://username.github.io/frd-website`

### Custom Domain

Add a `CNAME` file with your domain:

```bash
echo "your-domain.com" > CNAME
```

## Resources

- **Paper (Journal)**: https://www.sciencedirect.com/science/article/pii/S1361841526000125
- **Paper (arXiv)**: https://arxiv.org/abs/2412.01496
- **Code Repository**: https://github.com/RichardObi/frd-score
- **Evaluation Framework**: https://github.com/mazurowski-lab/medical-image-similarity-metrics

## Authors

**Lead Authors**: Nicholas Konz (Duke), Richard Osuala (Barcelona/Munich), Maciej A. Mazurowski (Duke)

**Contributing Institutions**: Duke University, Universitat de Barcelona, Helmholtz Munich, Technical University Munich, Yale University, King's College London

## License

MIT License - See LICENSE file for details
