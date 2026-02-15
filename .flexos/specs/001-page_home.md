001-page_home.md
---
type: spec
subtype: page
title: Wimmer EDV | IT-Consulting für ERP & Legacy-Systeme | Schleissheim
route: /
layout: home
---

### Purpose
To establish immediate credibility, showcase core expertise, and guide high-value enterprise clients directly to relevant solutions.

### Components
1.  **Hero Section**
    *   **Description:** A full-width, high-impact section at the top of the page with a compelling headline and a clear call to action.
2.  **Partner Logo Cloud**
    *   **Description:** A simple, clean section to display official partner logos, reinforcing authority and trust.
3.  **Core Expertise Pillars**
    *   **Description:** A set of three distinct cards or visual sections, each representing a primary service area. This acts as the main navigation into the service funnels.
4.  **Value Proposition Section**
    *   **Description:** A brief, text-focused section outlining the key reasons to choose Wimmer EDV.
5.  **Client Success Teaser**
    *   **Description:** A visually separated block featuring a powerful client testimonial or a pull-quote from a case study.
6.  **Call to Action (CTA) Banner**
    *   **Description:** A final, full-width section with a clear and direct call to action to encourage lead generation.

### Data Requirements
*   **Hero Section:**
    *   `headline`: "27 Jahre Erfahrung. Stabilität für Ihre kritischen IT-Systeme."
    *   `subheadline`: "Wir modernisieren Legacy-Systeme und sichern Ihre Unternehmensdaten."
    *   `cta_text`: "Unsere Expertise entdecken"
    *   `cta_link`: `/expertise`
*   **Partner Logo Cloud:**
    *   A list of partner logos, each with:
        *   `logo_image_url` (e.g., Microsoft, Veeam)
        *   `partner_name` (alt text)
*   **Core Expertise Pillars:**
    *   A collection of 3 pillar objects, each containing:
        *   `title`: (e.g., "Legacy System Modernization", "ERP Consulting", "Data Protection")
        *   `short_description`: A one-sentence summary of the service.
        *   `link`: (e.g., `/expertise/ibm-as400-iseries-consulting`, `/expertise/microsoft-dynamics-ax-consulting`, `/expertise/datensicherung-veeam`)
*   **Value Proposition Section:**
    *   `title`: "Warum Wimmer EDV?"
    *   A list of 3 value points, each with:
        *   `title`: (e.g., "Stabilität", "Tiefe Expertise", "Partnerschaft")
        *   `description`: A short paragraph explaining the point.
*   **Client Success Teaser:**
    *   `quote_text`: A verbatim quote from a client.
    *   `attribution`: Client name and/or company.
    *   `cta_text`: "Zur Fallstudie"
    *   `cta_link`: The URL to the full case study page (e.g., `/kundenerfolge/case-study-1`).
*   **CTA Banner:**
    *   `headline`: "Bereit für eine stabile IT-Zukunft?"
    *   `subtext`: "Kontaktieren Sie uns für eine unverbindliche Erstberatung."
    *   `cta_text`: "Beratung anfordern"
    *   `cta_link`: `/kontakt`

### User Interactions
*   User clicks the primary CTA in the Hero section, navigating to the `/expertise` page.
*   User clicks on one of the Core Expertise Pillar cards, navigating to the corresponding service detail page.
*   User clicks the link in the Client Success Teaser, navigating to the full case study.
*   User clicks the final CTA, navigating to the `/kontakt` page.

### States
*   **Default:** All components are loaded and visible. Standard hover/active states on all links and buttons.