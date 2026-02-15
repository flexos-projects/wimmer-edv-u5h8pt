---
type: doc
subtype: core
title: 007-technical.md - Technical Architecture
---

This document outlines the technical specifications for the Wimmer EDV website redesign, prioritizing performance, SEO, and maintainability.

### 1. Core Stack

*   **Framework:** **Astro**. Chosen for its exceptional performance-by-default (zero JS on the client-side unless explicitly needed) and content-focused architecture. It is ideal for building fast, SEO-friendly marketing websites.
*   **Deployment:** **Vercel**. Provides a seamless CI/CD pipeline, automatic HTTPS, global CDN, and serverless functions for handling backend tasks like form submissions.
*   **Content Management:** **Markdown/MDX Files in Git Repository**. For this project's scale, a full-featured CMS is overkill. Content will be managed directly in the project's Git repository using Markdown files with YAML frontmatter, following the defined content model. This is simple, version-controlled, and extremely fast.

### 2. Performance Targets

The site must be exceptionally fast to establish credibility.
*   **Google Lighthouse Score:** Target >95 across all categories (Performance, Accessibility, Best Practices, SEO).
*   **Core Web Vitals:** All metrics (LCP, FID, CLS) must pass in the "Good" category.
*   **Load Time:** Largest Contentful Paint (LCP) under 1.5 seconds on a standard mobile connection.

### 3. SEO & Metadata

Technical SEO will be flawless from day one.
*   **Structured Data:** Implement `Organization` and `Service` Schema.org JSON-LD structured data across the site. Case studies will use `Article` schema. This provides rich context for search engines.
*   **Sitemap:** An `sitemap.xml` file will be automatically generated at build time to include all canonical page URLs.
*   **Robots.txt:** A correctly configured `robots.txt` will be in place to guide search engine crawlers.
*   **Meta Tags:** All pages will have unique, SEO-optimized `<title>` and `<meta name="description">` tags, as defined in the Page Architecture document.
*   **Open Graph & Twitter Cards:** Implement OG and Twitter tags for rich social media sharing previews on all pages.
*   **Canonical URLs:** All pages will have a self-referencing `rel="canonical"` link to prevent duplicate content issues.

### 4. Form Handling

*   **Implementation:** Use a Vercel Serverless Function to process form submissions.
*   **Process:**
    1.  The user submits the form.
    2.  The request is sent to the serverless function endpoint.
    3.  The function performs basic validation and spam checking (e.g., using a honeypot field).
    4.  On success, the function sends a formatted email notification to the Wimmer EDV contact email address.
    5.  The function returns a success response to the frontend, which displays a "Thank you" message.

### 5. Asset Optimization

*   **Images:** Utilize Astro's built-in `<Image>` component. This will automatically generate optimized `webp` and `avif` formats, create responsive `srcset` attributes, and lazy-load all off-screen images.
*   **CSS/JS:** All CSS and JavaScript will be bundled and minified at build time. Critical CSS will be inlined in the `<head>` for the fastest possible initial render.

### 6. Analytics & Tracking

*   **Platform:** **Google Analytics 4 (GA4)**.
*   **Implementation:** GA4 will be implemented via **Google Tag Manager (GTM)**. This allows for flexible event tracking without requiring new code deployments.
*   **Tracked Events:**
    *   "Request a Consultation" form submissions.
    *   Clicks on email addresses (`mailto:` links).
    *   Clicks on phone numbers (`tel:` links).
    *   Downloads of any future gated content (e.g., PDFs).

### 7. Language & Internationalization

*   **Primary Language:** The site will be built as a single-language site in German (`de-AT`). The `<html>` tag will be set to `lang="de-AT"`.
*   **Future-Proofing:** While not a P1 requirement, the Astro project structure will be organized to easily accommodate future language additions if necessary.