```markdown
---
type: spec
subtype: feature
title: 051 - Detailed Service Pages
priority: P1
---

### Description

This feature defines a flexible and structured template for creating unique pages for each core service offering (e.g., AS/400 Modernization, Dynamics AX Support). These pages are critical for both SEO and for clearly communicating the value proposition of each service to potential clients, guiding them towards a consultation.

### User Stories

-   **As a potential client looking for a specific solution,** I want to land on a page that clearly explains the service, its benefits for my business, and Wimmer EDV's unique approach, so I can determine if they are the right fit.
-   **As a search engine,** I want to be able to crawl a well-structured page with clear headings (H1, H2, H3) and relevant keywords so I can rank it for relevant queries.
-   **As a site administrator,** I want an easy-to-use template in the CMS to create new service pages or edit existing ones without needing a developer.

### Acceptance Criteria

-   **Given** a service page template exists in the CMS, **Then** it must include distinct, editable sections for:
    -   Main Page Title (H1)
    -   Introductory Paragraph/Summary
    -   "Business Value" or "Benefits" section (e.g., using icon-and-text blocks)
    -   "Our Approach" or "Methodology" section (detailing the process)
    -   A prominent call-to-action (CTA) that links to the "Request a Consultation" form.
    -   An optional section to embed related case studies or testimonials.
-   **Given** a user is viewing a service page, **Then** the page's URL must be a clean, descriptive slug (e.g., `/services/as400-modernization`).
-   **Given** a site administrator creates and publishes a new service page, **Then** it must automatically appear in the main "Services" navigation dropdown menu.
-   **Given** a service page is rendered, **Then** it must have appropriate Schema.org markup (e.g., `Service`) to enhance search engine understanding.

### Technical Notes

-   Implement a "Service" custom post type (or equivalent content type) in the chosen CMS.
-   Use a page builder or custom fields (e.g., Advanced Custom Fields for WordPress) to create the structured content sections, ensuring ease of editing for non-technical users.
-   The template must be fully responsive and inherit all styles from the core design system.
-   The navigation menu population should be dynamic, automatically pulling from published "Service" posts.
```