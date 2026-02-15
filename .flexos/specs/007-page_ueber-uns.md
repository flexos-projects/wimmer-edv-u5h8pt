007-page_ueber-uns.md
---
type: spec
subtype: page
title: Über Wimmer EDV | IT-Beratung seit 1997
route: /ueber-uns
layout: default
---

### Purpose
To build trust and form a human connection by showcasing the company's long history, stable values, and the experienced team behind the services.

### Components
1.  **Page Header / Story Section**
    *   **Description:** A section that combines the page title with a narrative of the company's founding and history since 1997.
2.  **Philosophy / Values Section**
    *   **Description:** A content section, possibly with icons or distinct blocks, that outlines the company's core values.
3.  **Team Section**
    *   **Description:** A grid or row of profiles for the founder and key consultants, including photos and short bios.
4.  **Partners Section**
    *   **Description:** A dedicated section detailing official partner statuses, going beyond simple logos to explain the value of these partnerships.

### Data Requirements
*   **Story Section:**
    *   `title`: "Unsere Geschichte: IT-Beratung seit 1997"
    *   `content`: Formatted text (HTML/Markdown) telling the company's story.
*   **Philosophy Section:**
    *   `title`: "Unsere Philosophie"
    *   A list of values, each with:
        *   `title`: (e.g., "Langfristige Partnerschaften", "Tiefes Technisches Verständnis", "Pragmatismus")
        *   `description`: A short explanation of each value.
*   **Team Section:**
    *   `title`: "Das Team"
    *   A list of team member objects, each with:
        *   `name`: "Hans Wimmer"
        *   `title`: "Gründer & Geschäftsführer"
        *   `photo_url`: URL to a professional headshot.
        *   `bio`: A short professional biography.
*   **Partners Section:**
    *   `title`: "Unsere Partner"
    *   A list of partner objects, each with:
        *   `partner_logo_url`: URL of the partner logo.
        *   `partner_name`: "Microsoft"
        *   `description`: Text describing the partnership status and its benefits for clients.

### User Interactions
*   Standard navigation, no complex interactions on this page.

### States
*   **Default:** All content is visible. The team section might be designed to be added post-launch (P2 feature) and should gracefully not appear if no data is provided.