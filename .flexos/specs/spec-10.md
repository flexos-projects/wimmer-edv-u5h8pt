```markdown
---
type: spec
subtype: feature
title: 052 - Compelling "About Us" Page
priority: P1
---

### Description

A dedicated "About Us" page designed to build trust and credibility by telling the Wimmer EDV story. It will emphasize the company's long history ("Since 1997"), stability, core philosophy, and experience, serving as a primary trust-building asset for potential clients.

### User Stories

-   **As a potential client evaluating Wimmer EDV,** I want to understand their history, values, and experience so I can feel confident in their ability to deliver on a long-term, high-value project.
-   **As a potential partner,** I want to learn about the company's background and core principles to see if our values align for a potential collaboration.
-   **As a site administrator,** I want to be able to easily update the text and images on this page through the CMS.

### Acceptance Criteria

-   **Given** the "About Us" page is created, **Then** it must contain distinct, editable sections for:
    -   A primary headline and introductory narrative.
    -   Company History / "Since 1997" story.
    -   Company Philosophy / Mission Statement.
    -   A section showcasing partner logos (re-using the partner logo component).
-   **Given** the page is designed, **Then** its layout should be engaging, potentially using a mix of text, images (e.g., office photos), and blockquotes to break up content.
-   **Given** a user is on the page, **Then** there must be a clear call-to-action (CTA), such as "Request a Consultation" or "Meet Our Team" (linking to the team page when it becomes available).
-   **Given** a user navigates to the `/about` URL, **Then** this page is displayed.

### Technical Notes

-   This can be implemented as a standard page in the CMS, but with a potentially unique layout configured via a page builder or a custom page template.
-   The partner logos section should be a reusable component that is also used on the homepage to ensure consistency and maintainability (DRY - Don't Repeat Yourself).
```