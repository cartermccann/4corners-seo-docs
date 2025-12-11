---
title: "Blog Post SEO Guide"
description: "Technical specifications for creating SEO-optimized blog posts"
client: "4Corners Concrete Coatings"
reportDate: "2025-12-11"
reportType: "technical"
---

# Blog Post SEO Guide for Developers

> **Every blog post should be a machine for capturing search traffic. Here's the technical blueprint.**

---

## Blog Post Template Structure

### Required Frontmatter/Metadata

```yaml
---
title: "Blog Post Title (Under 60 Characters)"
description: "150-160 character meta description with primary keyword."
author: "Author Name"
authorTitle: "Job Title"
datePublished: "2025-12-11"
dateModified: "2025-12-11"
category: "Category Name"
tags: ["tag1", "tag2", "tag3"]
featuredImage: "/images/blog/featured-image.webp"
featuredImageAlt: "Descriptive alt text for featured image"
---
```

### HTML Head Elements

```html
<head>
  <!-- Primary Meta -->
  <title>[Blog Title] | 4Corners Concrete Coatings</title>
  <meta name="description" content="[150-160 char description]">

  <!-- Canonical -->
  <link rel="canonical" href="https://www.4cornersconcretecoatings.com/blog/[slug]/">

  <!-- Open Graph -->
  <meta property="og:type" content="article">
  <meta property="og:title" content="[Blog Title]">
  <meta property="og:description" content="[Description]">
  <meta property="og:image" content="[Featured Image URL]">
  <meta property="og:url" content="[Full URL]">
  <meta property="article:published_time" content="2025-12-11T10:00:00Z">
  <meta property="article:modified_time" content="2025-12-11T10:00:00Z">
  <meta property="article:author" content="[Author Name]">
  <meta property="article:section" content="[Category]">
  <meta property="article:tag" content="[Tag1]">
  <meta property="article:tag" content="[Tag2]">

  <!-- Twitter -->
  <meta name="twitter:card" content="summary_large_image">
  <meta name="twitter:title" content="[Blog Title]">
  <meta name="twitter:description" content="[Description]">
  <meta name="twitter:image" content="[Featured Image URL]">
</head>
```

---

## Article Schema Markup

Add to every blog post:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "mainEntityOfPage": {
    "@type": "WebPage",
    "@id": "https://www.4cornersconcretecoatings.com/blog/[slug]/"
  },
  "headline": "[Blog Post Title]",
  "description": "[Meta Description]",
  "image": {
    "@type": "ImageObject",
    "url": "https://www.4cornersconcretecoatings.com/images/blog/[image].webp",
    "width": 1200,
    "height": 630
  },
  "datePublished": "2025-12-11T10:00:00Z",
  "dateModified": "2025-12-11T10:00:00Z",
  "author": {
    "@type": "Person",
    "name": "[Author Name]",
    "jobTitle": "[Job Title]",
    "url": "https://www.4cornersconcretecoatings.com/about/[author-slug]/"
  },
  "publisher": {
    "@type": "Organization",
    "name": "4Corners Concrete Coatings",
    "logo": {
      "@type": "ImageObject",
      "url": "https://www.4cornersconcretecoatings.com/images/logo.png",
      "width": 250,
      "height": 60
    }
  },
  "articleSection": "[Category]",
  "keywords": "[keyword1], [keyword2], [keyword3]",
  "wordCount": [word count],
  "inLanguage": "en-US"
}
</script>
```

---

## Content Structure Requirements

### Heading Hierarchy

```html
<article>
  <h1>Main Blog Post Title (Contains Primary Keyword)</h1>

  <div class="intro">
    <p>Introduction paragraph (100-150 words). Include primary keyword in first 100 words.</p>
  </div>

  <div class="quick-answer">
    <strong>Quick Answer:</strong> 2-3 sentence direct answer for AI and featured snippets.
  </div>

  <nav class="table-of-contents">
    <h2>In This Article</h2>
    <ul>
      <li><a href="#section-1">Section 1</a></li>
      <li><a href="#section-2">Section 2</a></li>
      <li><a href="#section-3">Section 3</a></li>
      <li><a href="#faq">FAQ</a></li>
    </ul>
  </nav>

  <section id="section-1">
    <h2>Section 1 Heading (May contain secondary keyword)</h2>
    <p>Content...</p>

    <h3>Subsection Heading</h3>
    <p>More content...</p>
  </section>

  <section id="section-2">
    <h2>Section 2 Heading</h2>
    <p>Content...</p>
  </section>

  <section id="section-3">
    <h2>Section 3 Heading</h2>
    <p>Content...</p>
  </section>

  <section id="faq">
    <h2>Frequently Asked Questions</h2>
    <!-- FAQ Schema content -->
  </section>

  <section class="key-takeaways">
    <h2>Key Takeaways</h2>
    <ul>
      <li>Takeaway 1</li>
      <li>Takeaway 2</li>
      <li>Takeaway 3</li>
    </ul>
  </section>

  <section class="cta">
    <h2>Ready to Get Started?</h2>
    <p>Call for your free estimate: <a href="tel:+19702927623">(970) 292-7623</a></p>
    <a href="/contact/" class="button">Request Free Estimate</a>
  </section>
</article>
```

---

## FAQ Section Implementation

### HTML Structure

```html
<section id="faq" itemscope itemtype="https://schema.org/FAQPage">
  <h2>Frequently Asked Questions</h2>

  <div itemscope itemprop="mainEntity" itemtype="https://schema.org/Question">
    <h3 itemprop="name">How much does concrete coating cost per square foot?</h3>
    <div itemscope itemprop="acceptedAnswer" itemtype="https://schema.org/Answer">
      <p itemprop="text">Concrete coating typically costs $3-$12 per square foot in Colorado. Epoxy coatings average $4-$8/sq ft, while premium polyaspartic coatings range from $6-$12/sq ft. Factors affecting price include surface condition, coating type, and project size.</p>
    </div>
  </div>

  <div itemscope itemprop="mainEntity" itemtype="https://schema.org/Question">
    <h3 itemprop="name">How long does concrete coating last?</h3>
    <div itemscope itemprop="acceptedAnswer" itemtype="https://schema.org/Answer">
      <p itemprop="text">Professional concrete floor coatings typically last 10-20 years with proper care. Polyaspartic coatings often last longer than standard epoxy due to superior UV resistance and flexibility.</p>
    </div>
  </div>

  <!-- Add 3-5 more FAQs -->
</section>
```

### JSON-LD Alternative

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "How much does concrete coating cost per square foot?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Concrete coating typically costs $3-$12 per square foot in Colorado..."
      }
    },
    {
      "@type": "Question",
      "name": "How long does concrete coating last?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "Professional concrete floor coatings typically last 10-20 years..."
      }
    }
  ]
}
</script>
```

---

## Internal Linking Requirements

### Minimum Links Per Post

| Link Type | Minimum | Target |
|-----------|---------|--------|
| **To Service Pages** | 2-3 | Relevant service pages |
| **To Other Blog Posts** | 2-3 | Related topic posts |
| **To Location Pages** | 1-2 | If location-relevant |
| **To Contact/CTA** | 1 | Final CTA section |

### Anchor Text Guidelines

```html
<!-- Good - Descriptive, keyword-relevant -->
<a href="/services/epoxy-coatings/">professional epoxy floor coating</a>
<a href="/blog/cost-guide/">complete cost guide</a>
<a href="/locations/denver/">Denver concrete coating services</a>

<!-- Avoid - Generic or over-optimized -->
<a href="/services/epoxy-coatings/">click here</a>
<a href="/services/epoxy-coatings/">epoxy coatings epoxy floors epoxy</a>
```

### Contextual Link Placement

```html
<p>
  Choosing between coating types can be confusing. Our
  <a href="/blog/epoxy-vs-polyaspartic/">epoxy vs polyaspartic comparison guide</a>
  breaks down the differences to help you decide.
</p>

<p>
  Ready to transform your garage? Check out our
  <a href="/services/garage-floor-coatings/">garage floor coating services</a>
  or <a href="/contact/">request a free estimate</a>.
</p>
```

---

## Image Requirements

### Featured Image

| Attribute | Requirement |
|-----------|-------------|
| Dimensions | 1200x630px (OG image ratio) |
| Format | WebP with JPEG fallback |
| File size | Under 150KB |
| Alt text | Descriptive, includes keyword if natural |
| File name | keyword-descriptive.webp |

### In-Content Images

```html
<figure>
  <picture>
    <source srcset="/images/blog/garage-floor-before-after.webp" type="image/webp">
    <img
      src="/images/blog/garage-floor-before-after.jpg"
      alt="Before and after epoxy garage floor coating in Denver home"
      width="800"
      height="600"
      loading="lazy"
    >
  </picture>
  <figcaption>Before and after: Epoxy floor coating transforms a Denver garage</figcaption>
</figure>
```

### Image Schema

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "ImageObject",
  "contentUrl": "https://www.4cornersconcretecoatings.com/images/blog/image.webp",
  "name": "Epoxy Garage Floor Before After",
  "description": "Before and after comparison of epoxy floor coating on residential garage",
  "width": 800,
  "height": 600
}
</script>
```

---

## Keyword Placement Checklist

For each blog post, verify:

- [ ] **Title Tag** - Primary keyword present
- [ ] **H1** - Primary keyword present
- [ ] **First 100 Words** - Primary keyword present
- [ ] **At Least One H2** - Contains primary or secondary keyword
- [ ] **Meta Description** - Primary keyword present
- [ ] **Image Alt Text** - Keyword where natural
- [ ] **URL Slug** - Contains primary keyword
- [ ] **Throughout Content** - Natural keyword density (1-2%)

### Example Keyword Distribution

**Target Keyword:** "concrete patio coatings"

```
Title: Concrete Patio Coatings: Complete Guide for Colorado Homeowners
URL: /blog/concrete-patio-coatings-guide/
H1: Concrete Patio Coatings: Everything You Need to Know

First paragraph:
"Looking to upgrade your outdoor space? Concrete patio coatings are one of the best
investments Colorado homeowners can make..."

H2 examples:
- "Types of Concrete Patio Coatings"
- "Benefits of Coating Your Concrete Patio"
- "Concrete Patio Coating Costs in Colorado"

Image alt: "Decorative concrete patio coating in Boulder backyard"
```

---

## URL Structure

### Format

```
https://www.4cornersconcretecoatings.com/blog/[keyword-rich-slug]/
```

### Requirements

- [ ] Lowercase only
- [ ] Hyphens between words (no underscores)
- [ ] Primary keyword included
- [ ] Under 60 characters
- [ ] No dates (unless time-sensitive)
- [ ] No stop words (a, the, and) unless needed for readability

### Examples

```
Good:
/blog/concrete-coating-cost-colorado/
/blog/epoxy-vs-polyaspartic-garages/
/blog/garage-floor-coating-guide/

Avoid:
/blog/the-complete-guide-to-concrete-coating-costs-in-colorado-2025/
/blog/post123/
/blog/2025/12/11/coating-post/
```

---

## Reading Time & Word Count

### Display Reading Time

```html
<div class="post-meta">
  <time datetime="2025-12-11">December 11, 2025</time>
  <span class="reading-time">8 min read</span>
  <span class="word-count">2,500 words</span>
</div>
```

### Calculate Reading Time

```javascript
// Average reading speed: 200 words per minute
const wordCount = content.split(/\s+/).length;
const readingTime = Math.ceil(wordCount / 200);
```

---

## Table of Contents

### Auto-Generated TOC

```html
<nav class="table-of-contents" aria-label="Table of Contents">
  <h2>In This Article</h2>
  <ol>
    <li><a href="#what-is-concrete-coating">What Is Concrete Coating?</a></li>
    <li><a href="#types-of-coatings">Types of Coatings</a>
      <ol>
        <li><a href="#epoxy">Epoxy</a></li>
        <li><a href="#polyaspartic">Polyaspartic</a></li>
      </ol>
    </li>
    <li><a href="#cost-factors">Cost Factors</a></li>
    <li><a href="#faq">FAQ</a></li>
  </ol>
</nav>
```

### Jump Link Anchors

```html
<section id="what-is-concrete-coating">
  <h2>What Is Concrete Coating?</h2>
  ...
</section>
```

---

## Mobile Optimization

### Responsive Tables

```html
<div class="table-wrapper">
  <table>
    <!-- Table content -->
  </table>
</div>

<style>
.table-wrapper {
  overflow-x: auto;
  -webkit-overflow-scrolling: touch;
}
</style>
```

### Touch-Friendly Links

```css
/* Minimum touch target size */
a, button {
  min-height: 44px;
  min-width: 44px;
}
```

### Font Sizing

```css
/* Readable on mobile */
body {
  font-size: 16px;
  line-height: 1.6;
}

h1 { font-size: 1.75rem; }
h2 { font-size: 1.5rem; }
h3 { font-size: 1.25rem; }
```

---

## Post Publication Checklist

Before publishing:

- [ ] Title tag under 60 characters
- [ ] Meta description 150-160 characters
- [ ] H1 matches/complements title
- [ ] Heading hierarchy is correct (no skipped levels)
- [ ] All images have alt text
- [ ] All images are optimized (WebP, lazy loaded)
- [ ] Internal links added (min 4-6)
- [ ] External links open in new tab
- [ ] FAQ section with schema
- [ ] Article schema added
- [ ] URL slug is keyword-optimized
- [ ] Mobile preview looks good
- [ ] Reading time displayed
- [ ] Author attribution present
- [ ] CTA section at end
- [ ] Social sharing images set

After publishing:

- [ ] Test in Google Rich Results Test
- [ ] Submit URL to Google Search Console
- [ ] Share on social media
- [ ] Add to internal link opportunities in existing posts

---

*Follow this guide for every blog post to ensure consistent SEO optimization.*
