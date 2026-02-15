003-page_expertise_ibm-as400-iseries-consulting.md
---
type: spec
subtype: page
title: IBM AS/400 & iSeries Experten | Wimmer EDV
route: /expertise/ibm-as400-iseries-consulting
layout: service-detail
---

### Purpose
To attract, inform, and convert potential clients who require specialized expertise in IBM AS/400 & iSeries systems by detailing the specific services offered.

### Components
1.  **Page Header**
    *   **Description:** A focused header with a title and an introductory statement that resonates with the target audience.
2.  **Service List / Feature Blocks**
    *   **Description:** A detailed breakdown of the specific services offered related to AS/400. This could be a list, a set of cards, or an accordion.
3.  **Content Block ("Our Approach")**
    *   **Description:** A flexible text and (optional) image component to explain the company's methodology and approach.
4.  **Related Case Studies Teaser**
    *   **Description:** A grid or list of cards linking to case studies that are relevant to this specific service.
5.  **Call to Action (CTA) Banner**
    *   **Description:** A prominent, page-specific CTA banner designed to capture leads.

### Data Requirements
*   **Page Header:**
    *   `title`: "IBM AS/400 & iSeries Consulting"
    *   `introduction_text`: "Ihre AS/400 ist kein Relikt, sondern ein Kraftwerk. Wir helfen Ihnen, das volle Potenzial auszuschöpfen."
*   **Service List:**
    *   A list of service items, each with:
        *   `title`: (e.g., "RPG-Programmierung", "Modernisierung & Web-Integration", "System-Integration")
        *   `description`: A paragraph detailing what the service entails.
*   **Content Block ("Our Approach"):**
    *   `title`: "Unser Ansatz"
    *   `content`: Formatted text (HTML/Markdown) explaining the company's approach to AS/400 projects.
*   **Related Case Studies Teaser:**
    *   `title`: "Erfolgsgeschichten aus der Praxis"
    *   A list of case study objects (fetched by a tag like "as400"), each with:
        *   `case_study_title`: The title of the case study.
        *   `case_study_summary`: A brief teaser.
        *   `case_study_link`: The URL to the full case study.
*   **CTA Banner:**
    *   `headline`: "Planen Sie Ihre AS/400-Zukunft"
    *   `cta_text`: "Jetzt Beratung anfordern"
    *   `cta_link`: `/kontakt`

### User Interactions
*   User clicks on a related case study to navigate to that page.
*   User clicks the CTA button to navigate to the contact page.

### States
*   **Default:** All content is visible.
*   **Empty State (Case Studies):** If no case studies are tagged for this service, the "Related Case Studies Teaser" component should not be rendered.