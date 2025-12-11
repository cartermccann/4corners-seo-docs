# Comcreate SEO Report Template

A beautiful, professional SEO report template powered by Astro. Simply add your markdown files and deploy to Vercel to share polished SEO reports with clients.

## Features

- Modern, professional dark theme with Comcreate branding
- Fully responsive design
- Lightning-fast static site generation
- Card grid layout for easy navigation
- Custom markdown styling for beautiful reports
- SEO-optimized metadata
- Easy deployment to Vercel

## Quick Start

### 1. Use This Template

Click "Use this template" on GitHub to create your own repository, or clone it:

```bash
git clone [repository-url] client-name-seo-report
cd client-name-seo-report
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Add Your SEO Report Content

Add your markdown files to `src/content/docs/`. Each file will automatically appear as a card on the homepage.

**Example file:** `src/content/docs/executive-summary.md`

```markdown
---
title: "Executive Summary"
description: "Overview of SEO strategy and recommendations"
client: "Client Name"
reportDate: "2025-12-10"
reportType: "audit"
---

# Executive Summary

Your content here...
```

### 4. Preview Locally

```bash
npm run dev
```

Visit `http://localhost:4321` to see your report.

### 5. Deploy to Vercel

```bash
npm run build
```

Then push to GitHub and connect to Vercel (see DEPLOYMENT.md for details).

## Project Structure

```
/
├── public/              # Static assets (logos, favicons)
│   ├── logo.png        # Comcreate logo (appears in header)
│   ├── wide-logo.png   # Wide logo (appears in footer)
│   └── favicon.ico
├── src/
│   ├── components/      # Reusable components
│   ├── content/
│   │   └── docs/       # ADD YOUR MARKDOWN FILES HERE
│   ├── layouts/         # Page layouts
│   ├── pages/          # Route pages
│   └── styles/
│       └── global.css   # Comcreate brand styling
└── README.md
```

## Adding Content

### Basic Markdown File

Create a new `.md` file in `src/content/docs/`:

```markdown
---
title: "Technical SEO Audit"
description: "Comprehensive technical analysis"
---

# Technical SEO Audit

## Section 1

Your content...
```

### Optional Frontmatter Fields

```yaml
---
title: "Page Title"                    # Required for card display
description: "Short description"       # Shows on homepage card
client: "Client Name"                  # Optional: Client identifier
reportDate: "2025-12-10"              # Optional: Report date
reportType: "audit"                    # Optional: audit, monthly, quarterly, strategy, technical, content
category: "Technical"                  # Optional: For organization
tags: ["seo", "technical", "audit"]   # Optional: For filtering
---
```

### Supported Markdown Features

- **Headings**: `#`, `##`, `###`, etc.
- **Lists**: Bulleted and numbered
- **Tables**: Full markdown table support
- **Code blocks**: Syntax highlighting
- **Blockquotes**: For callouts
- **Images**: `![alt](image-url)`
- **Links**: Internal and external

### Example Content Structure

```markdown
# Technical Audit

## Core Web Vitals

| Metric | Score | Status |
|--------|-------|--------|
| LCP    | 2.1s  | Pass   |
| FID    | 45ms  | Pass   |
| CLS    | 0.05  | Pass   |

## Action Items

- [ ] Fix mobile usability issues
- [ ] Optimize images
- [ ] Add schema markup

## Code Example

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Company Name"
}
```
```

## Customization

### Update Client Information

Edit `src/components/Footer.astro` to update contact information:

```astro
<p class="footer-contact">
  <a href="tel:+16199550105">(619) 955-0105</a>
  <a href="mailto:sales@comcreate.org">sales@comcreate.org</a>
</p>
```

### Customize Colors

Edit `src/styles/global.css` to change brand colors:

```css
:root {
  --color-primary: #3b82f6;       /* Main brand color */
  --color-accent-cyan: #06b6d4;   /* Cyan accent */
  --color-accent-purple: #a855f7; /* Purple accent */
}
```

### Replace Logos

Replace these files in the `public/` folder:
- `logo.png` - Square logo (shows in header)
- `wide-logo.png` - Wide logo (shows in footer)
- `favicon.ico` - Browser tab icon

## Development Commands

| Command | Action |
|---------|--------|
| `npm install` | Install dependencies |
| `npm run dev` | Start dev server at `localhost:4321` |
| `npm run build` | Build for production to `dist/` |
| `npm run preview` | Preview production build locally |

## Deployment

See [DEPLOYMENT.md](DEPLOYMENT.md) for detailed deployment instructions to Vercel.

### Quick Deploy

1. Push your repository to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Import your GitHub repository
4. Vercel auto-detects Astro and deploys
5. Share the generated URL with your client

## Template Workflow

### For Each New Client Report:

1. Clone this repository or create from template
2. Update repository name to `client-name-seo-report`
3. Clear `src/content/docs/` folder
4. Add your client's SEO report markdown files
5. Test locally with `npm run dev`
6. Build with `npm run build`
7. Deploy to Vercel
8. Share the live URL with client

## Support

For issues or questions about this template:
- Email: sales@comcreate.org
- Phone: (619) 955-0105

## License

© Comcreate - San Diego, CA
