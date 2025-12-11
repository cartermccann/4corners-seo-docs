---
title: "Page Speed Optimization"
description: "Complete technical guide for maximum website performance"
client: "4Corners Concrete Coatings"
reportDate: "2025-12-11"
reportType: "technical"
---

# Page Speed Optimization Guide

> **Page speed is a confirmed Google ranking factor. Faster sites rank higher and convert better. Target: Mobile 90+, Desktop 95+ on PageSpeed Insights.**

---

## Core Web Vitals Targets

| Metric | What It Measures | Target | How Google Rates |
|--------|-----------------|--------|------------------|
| **LCP** | Largest Contentful Paint | < 2.5 seconds | Good: <2.5s, Needs Improvement: 2.5-4s, Poor: >4s |
| **INP** | Interaction to Next Paint | < 200ms | Good: <200ms, Needs Improvement: 200-500ms, Poor: >500ms |
| **CLS** | Cumulative Layout Shift | < 0.1 | Good: <0.1, Needs Improvement: 0.1-0.25, Poor: >0.25 |

---

## Image Optimization

### Format Conversion

Convert all images to WebP with JPEG fallback:

```bash
# Using cwebp command line tool
cwebp -q 85 input.jpg -o output.webp

# Batch conversion (all jpg in folder)
for file in *.jpg; do cwebp -q 85 "$file" -o "${file%.jpg}.webp"; done
```

### Size Guidelines

| Image Type | Max Dimensions | Max File Size | Format |
|------------|---------------|---------------|--------|
| Hero images | 1920x1080px | 200KB | WebP |
| Gallery images | 1200x800px | 150KB | WebP |
| Thumbnails | 400x300px | 50KB | WebP |
| Blog images | 800x600px | 100KB | WebP |
| Icons | 64x64px | 5KB | SVG or WebP |

### Responsive Images

```html
<picture>
  <!-- WebP for modern browsers -->
  <source
    type="image/webp"
    srcset="
      image-400.webp 400w,
      image-800.webp 800w,
      image-1200.webp 1200w
    "
    sizes="(max-width: 600px) 400px, (max-width: 1200px) 800px, 1200px"
  >
  <!-- JPEG fallback -->
  <source
    type="image/jpeg"
    srcset="
      image-400.jpg 400w,
      image-800.jpg 800w,
      image-1200.jpg 1200w
    "
    sizes="(max-width: 600px) 400px, (max-width: 1200px) 800px, 1200px"
  >
  <!-- Default -->
  <img
    src="image-800.jpg"
    alt="Descriptive alt text"
    width="800"
    height="600"
    loading="lazy"
  >
</picture>
```

### Lazy Loading

```html
<!-- Images below the fold -->
<img src="image.jpg" loading="lazy" alt="Description">

<!-- DO NOT lazy load -->
<!-- - Hero images -->
<!-- - LCP elements -->
<!-- - Above-fold content -->
```

### Image Dimensions

**Always specify width and height** to prevent CLS:

```html
<!-- Good - prevents layout shift -->
<img src="image.jpg" width="800" height="600" alt="Description">

<!-- Bad - causes layout shift -->
<img src="image.jpg" alt="Description">
```

---

## CSS Optimization

### Critical CSS Inlining

Extract and inline CSS needed for above-fold content:

```html
<head>
  <!-- Critical CSS inline -->
  <style>
    /* Only styles needed for initial viewport */
    header { /* ... */ }
    .hero { /* ... */ }
    nav { /* ... */ }
  </style>

  <!-- Non-critical CSS deferred -->
  <link rel="preload" href="/css/main.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
  <noscript><link rel="stylesheet" href="/css/main.css"></noscript>
</head>
```

### CSS Minification

Remove whitespace, comments, and unnecessary characters:

```css
/* Before: 1.2KB */
.hero {
  background-color: #1a1a2e;
  padding: 60px 20px;
  text-align: center;
}

/* After: 800 bytes */
.hero{background-color:#1a1a2e;padding:60px 20px;text-align:center}
```

**Tools:**
- cssnano (npm)
- clean-css (npm)
- Online: cssnano.co

### Remove Unused CSS

Audit and remove CSS that isn't used:

```bash
# Using PurgeCSS
npx purgecss --css styles.css --content index.html --output cleaned.css
```

---

## JavaScript Optimization

### Script Loading Strategies

```html
<!-- Critical JS - load immediately -->
<script src="critical.js"></script>

<!-- Non-critical JS - defer (best for most scripts) -->
<script src="main.js" defer></script>

<!-- Third-party/analytics - async -->
<script src="analytics.js" async></script>
```

**When to use each:**

| Strategy | Behavior | Best For |
|----------|----------|----------|
| Default | Blocks rendering | Critical inline scripts only |
| `defer` | Downloads in parallel, executes after HTML parsed | Main site JS |
| `async` | Downloads in parallel, executes immediately when ready | Analytics, third-party |

### JS Minification

```javascript
// Before: 2KB
function calculateTotal(items) {
  let total = 0;
  for (let i = 0; i < items.length; i++) {
    total += items[i].price;
  }
  return total;
}

// After: 150 bytes
function calculateTotal(t){let e=0;for(let l=0;l<t.length;l++)e+=t[l].price;return e}
```

**Tools:**
- Terser (npm)
- UglifyJS (npm)

### Code Splitting

Only load JS needed for current page:

```javascript
// Dynamic import for features not needed immediately
button.addEventListener('click', async () => {
  const module = await import('./calculator.js');
  module.showCalculator();
});
```

---

## Font Optimization

### Font Display Strategy

```css
@font-face {
  font-family: 'CustomFont';
  src: url('/fonts/custom.woff2') format('woff2');
  font-display: swap; /* Shows fallback font immediately, swaps when loaded */
  font-weight: 400;
}
```

### Preload Critical Fonts

```html
<head>
  <link rel="preload" href="/fonts/primary.woff2" as="font" type="font/woff2" crossorigin>
</head>
```

### Limit Font Weights

Only load weights you actually use:

```css
/* Bad - loading all weights */
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;200;300;400;500;600;700;800;900');

/* Good - only weights needed */
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
```

### Self-Host Fonts

Download and host fonts locally for better performance:

```
/fonts/
  roboto-regular.woff2
  roboto-bold.woff2
```

---

## Server Optimization

### Enable Compression

**.htaccess (Apache):**

```apache
<IfModule mod_deflate.c>
  # Compress HTML, CSS, JavaScript, Text, XML and fonts
  AddOutputFilterByType DEFLATE application/javascript
  AddOutputFilterByType DEFLATE application/json
  AddOutputFilterByType DEFLATE application/xml
  AddOutputFilterByType DEFLATE text/css
  AddOutputFilterByType DEFLATE text/html
  AddOutputFilterByType DEFLATE text/javascript
  AddOutputFilterByType DEFLATE text/plain
  AddOutputFilterByType DEFLATE text/xml
  AddOutputFilterByType DEFLATE font/woff2
  AddOutputFilterByType DEFLATE image/svg+xml
</IfModule>
```

**Nginx:**

```nginx
gzip on;
gzip_types text/plain text/css application/json application/javascript text/xml application/xml image/svg+xml;
gzip_min_length 1000;
```

### Browser Caching

**.htaccess:**

```apache
<IfModule mod_expires.c>
  ExpiresActive On

  # Images - cache for 1 year
  ExpiresByType image/jpeg "access plus 1 year"
  ExpiresByType image/png "access plus 1 year"
  ExpiresByType image/webp "access plus 1 year"
  ExpiresByType image/svg+xml "access plus 1 year"
  ExpiresByType image/gif "access plus 1 year"

  # Fonts - cache for 1 year
  ExpiresByType font/woff "access plus 1 year"
  ExpiresByType font/woff2 "access plus 1 year"

  # CSS/JS - cache for 1 month
  ExpiresByType text/css "access plus 1 month"
  ExpiresByType application/javascript "access plus 1 month"

  # HTML - no cache (always fresh)
  ExpiresByType text/html "access plus 0 seconds"
</IfModule>
```

### Content Delivery Network (CDN)

Use a CDN like Cloudflare, AWS CloudFront, or Vercel Edge for:
- Static assets (images, CSS, JS, fonts)
- Global edge caching
- Automatic compression
- DDoS protection

---

## Resource Hints

### Preconnect to Required Origins

```html
<head>
  <!-- Preconnect to Google Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

  <!-- Preconnect to analytics -->
  <link rel="preconnect" href="https://www.google-analytics.com">

  <!-- DNS prefetch for external resources -->
  <link rel="dns-prefetch" href="https://maps.googleapis.com">
</head>
```

### Preload Critical Resources

```html
<head>
  <!-- Preload hero image (LCP element) -->
  <link rel="preload" as="image" href="/images/hero.webp" type="image/webp">

  <!-- Preload critical font -->
  <link rel="preload" as="font" href="/fonts/main.woff2" type="font/woff2" crossorigin>

  <!-- Preload critical CSS -->
  <link rel="preload" as="style" href="/css/critical.css">
</head>
```

---

## Third-Party Scripts

### Audit All Third-Party Scripts

Common performance killers:
- Chat widgets
- Analytics (multiple)
- Social media embeds
- Advertising scripts
- CRM integrations

### Best Practices

1. **Load async or defer** - Never block rendering
2. **Lazy load when possible** - Chat widgets on scroll/click
3. **Remove duplicates** - Only one analytics platform
4. **Consider alternatives** - Lighter versions of heavy tools

```html
<!-- Lazy load chat widget -->
<script>
  window.addEventListener('scroll', () => {
    if (!window.chatLoaded) {
      const script = document.createElement('script');
      script.src = 'https://chat-widget.js';
      script.async = true;
      document.body.appendChild(script);
      window.chatLoaded = true;
    }
  }, { once: true });
</script>
```

---

## Testing & Monitoring

### Tools to Use

| Tool | Purpose | URL |
|------|---------|-----|
| PageSpeed Insights | Core Web Vitals, recommendations | pagespeed.web.dev |
| GTmetrix | Detailed waterfall analysis | gtmetrix.com |
| WebPageTest | Multi-location testing | webpagetest.org |
| Chrome DevTools | Network, Performance tabs | Built into Chrome |
| Lighthouse | Full audit | Built into Chrome DevTools |

### Testing Checklist

- [ ] Test on mobile (PageSpeed mobile score)
- [ ] Test on slow 3G connection
- [ ] Test with cache disabled
- [ ] Test from different locations
- [ ] Test all page types (home, service, blog)

### Ongoing Monitoring

Set up alerts for:
- Core Web Vitals regression
- Page load time increases
- New third-party scripts added
- Image size increases

---

## Quick Wins Checklist

**Immediate impact (do first):**

- [ ] Convert images to WebP format
- [ ] Add width/height to all images
- [ ] Enable GZIP compression
- [ ] Set up browser caching
- [ ] Defer non-critical JavaScript
- [ ] Preload hero image
- [ ] Preconnect to external domains

**Medium effort:**

- [ ] Inline critical CSS
- [ ] Lazy load below-fold images
- [ ] Minify CSS and JavaScript
- [ ] Self-host fonts
- [ ] Set up CDN
- [ ] Remove unused CSS/JS

**Requires development:**

- [ ] Implement responsive images
- [ ] Code splitting for JavaScript
- [ ] Service worker for caching
- [ ] Progressive Web App features

---

## Performance Budget

Set limits to prevent regression:

| Resource Type | Budget |
|---------------|--------|
| Total page weight | < 1.5MB |
| JavaScript | < 300KB |
| CSS | < 100KB |
| Images per page | < 500KB |
| Fonts | < 100KB |
| Third-party scripts | < 200KB |

---

*Test after every change. Small improvements compound into significant gains.*
