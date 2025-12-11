---
title: "Technical Implementation Guide"
description: "Developer and SEO team technical specifications"
client: "4Corners Concrete Coatings"
reportDate: "2025-12-11"
reportType: "technical"
---

# Technical Implementation Guide

> **This document contains all technical specifications for developers and SEO team members implementing the 4Corners SEO strategy.**

---

## Priority 1: Critical (Week 1)

### 1.1 Robots.txt Configuration

Create or update `robots.txt` at the domain root:

```txt
# Primary Crawlers
User-agent: *
Allow: /
Disallow: /admin/
Disallow: /checkout/
Disallow: /*?*
Disallow: /search/
Disallow: /cart/
Disallow: /account/
Disallow: /wp-admin/
Disallow: /*.json$
Disallow: /api/

# AI/LLM Crawlers - ALLOW ALL
User-agent: GPTBot
Allow: /

User-agent: Google-Extended
Allow: /

User-agent: anthropic-ai
Allow: /

User-agent: ClaudeBot
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: Applebot-Extended
Allow: /

User-agent: CCBot
Allow: /

# Sitemap Location
Sitemap: https://www.4cornersconcretecoatings.com/sitemap.xml
```

**Verification:** Access `https://www.4cornersconcretecoatings.com/robots.txt` directly to confirm.

---

### 1.2 XML Sitemap Generation

Generate comprehensive XML sitemap at `/sitemap.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9"
        xmlns:image="http://www.google.com/schemas/sitemap-image/1.1">

  <!-- Homepage -->
  <url>
    <loc>https://www.4cornersconcretecoatings.com/</loc>
    <lastmod>2025-12-11</lastmod>
    <changefreq>weekly</changefreq>
    <priority>1.0</priority>
  </url>

  <!-- Service Pages -->
  <url>
    <loc>https://www.4cornersconcretecoatings.com/services/</loc>
    <lastmod>2025-12-11</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.9</priority>
  </url>

  <!-- Individual Service Pages - priority 0.8 -->
  <!-- Blog Posts - priority 0.6 -->
  <!-- Location Pages - priority 0.8 -->

</urlset>
```

**Requirements:**
- Include all indexable pages
- Accurate `lastmod` dates (update when content changes)
- Priority values: Homepage 1.0, Services 0.8-0.9, Blog 0.6, Utility pages 0.3
- Submit to Google Search Console and Bing Webmaster Tools

---

### 1.3 Meta Tags Implementation

**Required meta tags for EVERY page:**

```html
<head>
  <!-- Primary Meta Tags -->
  <title>[Page Title] | 4Corners Concrete Coatings</title>
  <meta name="description" content="[155 character description with keywords]">
  <meta name="robots" content="index, follow">

  <!-- Canonical URL -->
  <link rel="canonical" href="https://www.4cornersconcretecoatings.com/[current-url]">

  <!-- Open Graph / Facebook -->
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://www.4cornersconcretecoatings.com/[current-url]">
  <meta property="og:title" content="[Page Title]">
  <meta property="og:description" content="[Description]">
  <meta property="og:image" content="https://www.4cornersconcretecoatings.com/images/og-image.jpg">

  <!-- Twitter -->
  <meta property="twitter:card" content="summary_large_image">
  <meta property="twitter:url" content="https://www.4cornersconcretecoatings.com/[current-url]">
  <meta property="twitter:title" content="[Page Title]">
  <meta property="twitter:description" content="[Description]">
  <meta property="twitter:image" content="https://www.4cornersconcretecoatings.com/images/og-image.jpg">

  <!-- Geo Tags -->
  <meta name="geo.region" content="US-CO">
  <meta name="geo.placename" content="Colorado">

  <!-- Mobile -->
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="format-detection" content="telephone=yes">
</head>
```

---

### 1.4 Schema Markup - LocalBusiness (Homepage)

Add to homepage `<head>` or before closing `</body>`:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "@id": "https://www.4cornersconcretecoatings.com/#organization",
  "name": "4Corners Concrete Coatings",
  "alternateName": "4Corners Concrete",
  "url": "https://www.4cornersconcretecoatings.com",
  "logo": "https://www.4cornersconcretecoatings.com/images/logo.png",
  "image": "https://www.4cornersconcretecoatings.com/images/hero.jpg",
  "description": "Professional concrete floor coatings in Colorado including epoxy, polyaspartic, and polished concrete for residential and commercial spaces.",
  "telephone": "+1-970-292-7623",
  "email": "admin@4cornersconcretecoatings.com",
  "address": {
    "@type": "PostalAddress",
    "addressRegion": "CO",
    "addressCountry": "US"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": "40.0150",
    "longitude": "-105.2705"
  },
  "areaServed": [
    {
      "@type": "City",
      "name": "Denver",
      "sameAs": "https://en.wikipedia.org/wiki/Denver"
    },
    {
      "@type": "City",
      "name": "Boulder",
      "sameAs": "https://en.wikipedia.org/wiki/Boulder,_Colorado"
    },
    {
      "@type": "City",
      "name": "Fort Collins",
      "sameAs": "https://en.wikipedia.org/wiki/Fort_Collins,_Colorado"
    },
    {
      "@type": "City",
      "name": "Colorado Springs",
      "sameAs": "https://en.wikipedia.org/wiki/Colorado_Springs,_Colorado"
    }
  ],
  "priceRange": "$$",
  "currenciesAccepted": "USD",
  "paymentAccepted": "Cash, Credit Card, Check",
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      "opens": "08:00",
      "closes": "18:00"
    },
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": "Saturday",
      "opens": "09:00",
      "closes": "14:00"
    }
  ],
  "sameAs": [
    "https://www.facebook.com/4cornersconcretecoatings",
    "https://www.instagram.com/4cornersconcretecoatings",
    "https://www.youtube.com/@4cornersconcretecoatings"
  ],
  "hasOfferCatalog": {
    "@type": "OfferCatalog",
    "name": "Concrete Coating Services",
    "itemListElement": [
      {
        "@type": "Offer",
        "itemOffered": {
          "@type": "Service",
          "name": "Epoxy Floor Coating",
          "description": "Durable epoxy floor coatings for garages and commercial spaces"
        }
      },
      {
        "@type": "Offer",
        "itemOffered": {
          "@type": "Service",
          "name": "Polyaspartic Coating",
          "description": "Fast-curing polyaspartic coatings with UV stability"
        }
      },
      {
        "@type": "Offer",
        "itemOffered": {
          "@type": "Service",
          "name": "Polished Concrete",
          "description": "Modern polished concrete floors for residential and commercial"
        }
      }
    ]
  }
}
</script>
```

---

### 1.5 Service Page Schema

Add to each individual service page:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Service",
  "serviceType": "[Service Name - e.g., Epoxy Floor Coating]",
  "name": "[Service Name] in Colorado | 4Corners Concrete Coatings",
  "description": "[100-200 word service description]",
  "provider": {
    "@type": "LocalBusiness",
    "@id": "https://www.4cornersconcretecoatings.com/#organization"
  },
  "areaServed": {
    "@type": "State",
    "name": "Colorado"
  },
  "hasOfferCatalog": {
    "@type": "OfferCatalog",
    "name": "[Service Name] Options",
    "itemListElement": [
      {
        "@type": "Offer",
        "itemOffered": {
          "@type": "Service",
          "name": "[Specific offering]"
        }
      }
    ]
  }
}
</script>
```

---

### 1.6 FAQ Schema

Add to any page with FAQ content:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "How much does concrete floor coating cost in Colorado?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Concrete floor coating costs typically range from $3-$12 per square foot in Colorado, depending on the coating type, surface condition, and project size. Epoxy coatings average $4-$8/sq ft, while premium polyaspartic coatings range from $6-$12/sq ft. Contact us for a free estimate for your specific project."
      }
    },
    {
      "@type": "Question",
      "name": "How long does epoxy floor coating last?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Professionally applied epoxy floor coatings typically last 10-20 years with proper care. In Colorado's climate, high-quality epoxy with proper surface preparation can withstand temperature fluctuations, moisture, and road salt tracked in from vehicles."
      }
    },
    {
      "@type": "Question",
      "name": "What areas in Colorado do you serve?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "4Corners Concrete Coatings serves the entire Front Range of Colorado, including Denver, Boulder, Fort Collins, Colorado Springs, and surrounding communities. We offer free on-site estimates throughout our service area."
      }
    }
  ]
}
</script>
```

---

### 1.7 Breadcrumb Schema

Add to all pages except homepage:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Home",
      "item": "https://www.4cornersconcretecoatings.com/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Services",
      "item": "https://www.4cornersconcretecoatings.com/services/"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "[Current Page Name]",
      "item": "https://www.4cornersconcretecoatings.com/services/[current-page]/"
    }
  ]
}
</script>
```

---

## Priority 2: High (Week 2)

### 2.1 Image Optimization

**Format Requirements:**
| Image Type | Format | Max Size | Dimensions |
|------------|--------|----------|------------|
| Hero images | WebP (JPEG fallback) | 200KB | 1920x1080 max |
| Gallery images | WebP (JPEG fallback) | 150KB | 1200x800 max |
| Thumbnails | WebP | 50KB | 400x300 |
| Logos | SVG or PNG | 50KB | Variable |

**Implementation:**

```html
<!-- Responsive images with WebP -->
<picture>
  <source srcset="image.webp" type="image/webp">
  <source srcset="image.jpg" type="image/jpeg">
  <img src="image.jpg"
       alt="Epoxy garage floor coating in Denver home"
       width="1200"
       height="800"
       loading="lazy"
       decoding="async">
</picture>

<!-- Hero image (above fold - no lazy loading) -->
<picture>
  <source srcset="hero.webp" type="image/webp">
  <img src="hero.jpg"
       alt="Professional concrete coating services in Colorado"
       width="1920"
       height="1080"
       fetchpriority="high">
</picture>
```

**Alt Tag Requirements:**
- Descriptive (not just "image1.jpg")
- Include location when relevant: "Epoxy garage floor coating Denver"
- Keep under 125 characters
- Don't start with "Image of" or "Picture of"

**File Naming Convention:**
```
epoxy-garage-floor-denver.webp
polished-concrete-commercial-boulder.webp
before-after-metallic-epoxy.webp
```

---

### 2.2 Lazy Loading Implementation

```html
<!-- Below-fold images -->
<img src="image.jpg" loading="lazy" alt="Description">

<!-- Iframes (maps, videos) -->
<iframe src="..." loading="lazy"></iframe>
```

**Do NOT lazy load:**
- Hero images
- Logo
- Above-fold content
- Critical LCP elements

---

### 2.3 CSS/JS Minification

**CSS:**
- Minify all CSS files
- Combine into single file where possible
- Inline critical CSS for above-fold content
- Defer non-critical CSS

```html
<!-- Critical CSS inline -->
<style>
  /* Minimal CSS for above-fold content */
</style>

<!-- Deferred CSS -->
<link rel="preload" href="styles.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
<noscript><link rel="stylesheet" href="styles.css"></noscript>
```

**JavaScript:**
- Minify all JS files
- Defer non-critical scripts
- Async load analytics and third-party scripts

```html
<!-- Defer JS -->
<script src="main.js" defer></script>

<!-- Async third-party -->
<script src="analytics.js" async></script>
```

---

### 2.4 Browser Caching Headers

Add to `.htaccess` (Apache) or server config:

```apache
# Cache static assets
<IfModule mod_expires.c>
  ExpiresActive On

  # Images
  ExpiresByType image/jpeg "access plus 1 year"
  ExpiresByType image/png "access plus 1 year"
  ExpiresByType image/webp "access plus 1 year"
  ExpiresByType image/svg+xml "access plus 1 year"

  # CSS/JS
  ExpiresByType text/css "access plus 1 month"
  ExpiresByType application/javascript "access plus 1 month"

  # Fonts
  ExpiresByType font/woff2 "access plus 1 year"
  ExpiresByType font/woff "access plus 1 year"

  # HTML
  ExpiresByType text/html "access plus 0 seconds"
</IfModule>

# GZIP Compression
<IfModule mod_deflate.c>
  AddOutputFilterByType DEFLATE text/html text/css application/javascript application/json
</IfModule>
```

---

### 2.5 Core Web Vitals Targets

| Metric | Target | How to Achieve |
|--------|--------|----------------|
| **LCP** (Largest Contentful Paint) | < 2.5s | Optimize hero image, preload fonts, fast server |
| **INP** (Interaction to Next Paint) | < 200ms | Minimize JS, defer non-critical scripts |
| **CLS** (Cumulative Layout Shift) | < 0.1 | Set image dimensions, reserve space for dynamic content |

**Testing Tools:**
- Google PageSpeed Insights
- WebPageTest.org
- Chrome DevTools Lighthouse

---

## Priority 3: Important (Week 3-4)

### 3.1 New Page Creation

**Service Pages to Create:**

| Page URL | Primary Keyword | Title Tag |
|----------|----------------|-----------|
| `/services/patio-coatings/` | concrete patio coatings | Patio Concrete Coatings Colorado \| 4Corners |
| `/services/pool-deck-coatings/` | pool deck coatings | Pool Deck Coatings Colorado \| 4Corners |
| `/services/driveway-coatings/` | concrete driveway coating | Driveway Concrete Coatings \| 4Corners |
| `/services/garage-floor-coatings/` | garage concrete coating | Garage Floor Coatings Colorado \| 4Corners |
| `/services/commercial-coatings/` | commercial concrete coatings | Commercial Concrete Coatings \| 4Corners |

**Location Pages to Create:**

| Page URL | Primary Keyword | Title Tag |
|----------|----------------|-----------|
| `/locations/denver/` | concrete coatings denver | Denver Concrete Coatings \| 4Corners |
| `/locations/boulder/` | concrete coatings boulder | Boulder Concrete Coatings \| 4Corners |
| `/locations/fort-collins/` | concrete coatings fort collins | Fort Collins Concrete Coatings \| 4Corners |
| `/locations/colorado-springs/` | concrete coatings colorado springs | Colorado Springs Concrete Coatings \| 4Corners |

---

### 3.2 Internal Linking Structure

**Link Distribution:**
- Homepage links to all main service pages
- Each service page links to 2-3 related services
- Blog posts link to relevant service pages
- Location pages link to services available in that area
- All pages link back to homepage

**Anchor Text Guidelines:**
- Use descriptive, keyword-rich anchor text
- Vary anchor text (don't always use exact match)
- Natural language preferred

```html
<!-- Good -->
<a href="/services/epoxy-coatings/">epoxy floor coating services</a>
<a href="/services/epoxy-coatings/">professional epoxy coatings</a>
<a href="/services/epoxy-coatings/">learn more about our epoxy options</a>

<!-- Avoid -->
<a href="/services/epoxy-coatings/">click here</a>
<a href="/services/epoxy-coatings/">epoxy coatings</a> (exact match every time)
```

---

### 3.3 301 Redirect Map

If URLs change or pages are consolidated:

```apache
# .htaccess redirects
Redirect 301 /old-page/ https://www.4cornersconcretecoatings.com/new-page/
Redirect 301 /services/old-service/ https://www.4cornersconcretecoatings.com/services/new-service/
```

**Rules:**
- Always use 301 (permanent) for SEO
- Redirect to most relevant page
- Avoid redirect chains (A→B→C)
- Update internal links to point directly to new URL

---

### 3.4 404 Error Handling

Create custom 404 page with:
- Helpful message
- Search functionality
- Links to main pages
- Contact information

```html
<!-- 404.html -->
<h1>Page Not Found</h1>
<p>Sorry, we couldn't find that page. Here are some helpful links:</p>
<ul>
  <li><a href="/">Home</a></li>
  <li><a href="/services/">Our Services</a></li>
  <li><a href="/contact/">Contact Us</a></li>
</ul>
```

---

## Ongoing Technical Maintenance

### Weekly Tasks
- [ ] Check Google Search Console for crawl errors
- [ ] Monitor Core Web Vitals scores
- [ ] Verify no new 404 errors
- [ ] Check mobile usability issues

### Monthly Tasks
- [ ] Full site crawl with Screaming Frog or similar
- [ ] Update sitemap if new pages added
- [ ] Review page speed scores
- [ ] Check for broken links
- [ ] Verify schema markup validity (schema.org validator)

### Quarterly Tasks
- [ ] Full technical SEO audit
- [ ] Review and update meta descriptions
- [ ] Check competitor technical implementations
- [ ] Evaluate new schema opportunities

---

## Testing & Validation Tools

| Tool | Purpose | URL |
|------|---------|-----|
| Google Search Console | Indexing, errors, performance | search.google.com/search-console |
| Google PageSpeed Insights | Core Web Vitals, speed | pagespeed.web.dev |
| Schema.org Validator | Schema markup validation | validator.schema.org |
| Mobile-Friendly Test | Mobile usability | search.google.com/test/mobile-friendly |
| Rich Results Test | Schema preview | search.google.com/test/rich-results |
| Screaming Frog | Full site crawl | screamingfrog.co.uk |

---

*This technical guide should be referenced throughout implementation. Update as needed when specifications change.*
