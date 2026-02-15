```markdown
---
type: spec
subtype: feature
title: 056 - Standard Legal Pages
priority: P1
---

### Description

Creation of the legally required "Impressum" (Imprint) and "Datenschutz" (Privacy Policy) pages. These pages are non-negotiable for legal compliance in the target market (Germany/EU). They must be easily accessible from a persistent site footer.

### User Stories

-   **As a user,** I want to easily find the company's official legal information and privacy policy to understand my rights and verify the company's legitimacy.
-   **As the site owner,** I want to ensure the site is legally compliant with German/EU regulations (like GDPR and Telemediengesetz) to avoid potential fines and legal issues.
-   **As a site administrator,** I want to be able to edit the content of these pages using the standard text editor in the CMS.

### Acceptance Criteria

-   **Given** any page on the site is viewed, **Then** the site footer must contain persistent text links for "Impressum" and "Datenschutz".
-   **Given** a user clicks the "Impressum" link, **Then** they are taken to the `/impressum` page which displays the company's legal imprint information.
-   **Given** a user clicks the "Datenschutz" link, **Then** they are taken to the `/datenschutz` page which displays the company's privacy policy.
-   **Given** these pages exist in the CMS, **Then** their content must be fully editable through a standard WYSIWYG editor.
-   **Given** these pages are rendered, **Then** they must include a `noindex` meta tag to prevent them from being indexed by search engines.

### Technical Notes

-   Create two standard pages in the CMS.
-   The client is responsible for providing the legally vetted content for these pages.
-   Use an SEO plugin or a custom function to add the `<meta name="robots" content="noindex, follow">` tag to the `<head>` of these specific pages.
```