```markdown
---
type: spec
subtype: feature
title: 061 - Testimonial Integration
priority: P2
---

### Description

A system to manage and strategically display short, powerful client quotes throughout the website. Instead of being isolated on one page, testimonials will be woven into key conversion pages like the homepage and relevant service pages to provide social proof at critical points in the user journey.

### User Stories

-   **As a potential client reading a service page,** I want to see a quote from another client who used that specific service, which reassures me of its effectiveness and builds my trust.
-   **As a site administrator,** I want a central place to add and manage all testimonials, and then an easy way to select which specific ones to display on various pages across the site.

### Acceptance Criteria

-   **Given** a site administrator is in the CMS, **Then** there is a "Testimonials" management area (e.g., a custom post type).
-   **Given** the admin creates a new testimonial entry, **Then** they can input the quote text, the client's name, and their company/title.
-   **Given** an admin is editing a page (e.g., the Homepage or a Service page), **Then** they must have an interface (e.g., a custom block or a relationship field) to select and embed one or more specific testimonials on that page.
-   **Given** a testimonial is displayed on the frontend, **Then** it is visually distinct from standard body text (e.g., italicized, within a styled blockquote) and clearly attributes the quote to the person and company.

### Technical Notes

-   Create a "Testimonial" custom post type. This CPT should be non-public, meaning it won't have its own single pages or archive pages (`'publicly_queryable' => false`).
-   On pages/templates where testimonials can be added, use a relationship field (e.g., ACF Post Object field) to allow editors to pick from the list of available testimonial entries.
-   Create a reusable component/block for rendering the testimonial's markup and styling, which can be easily dropped into any page template.
```