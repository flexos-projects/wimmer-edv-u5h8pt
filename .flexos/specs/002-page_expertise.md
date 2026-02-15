002-page_expertise.md
---
type: spec
subtype: page
title: Unsere Expertise | IT-Consulting & Lösungen | Wimmer EDV
route: /expertise
layout: default
---

### Purpose
To serve as a clear, organized hub for all service offerings, allowing users to easily navigate to the specific solution they are interested in.

### Components
1.  **Page Header**
    *   **Description:** A standard page header with a title and an introductory paragraph.
2.  **Service Grid**
    *   **Description:** A categorized grid of cards, where each card represents a specific service. The grid is visually divided by category.

### Data Requirements
*   **Page Header:**
    *   `title`: "Unsere Expertise"
    *   `introduction_text`: A paragraph introducing the company's consulting philosophy and approach to solving client problems.
*   **Service Grid:**
    *   A list of service category objects, each containing:
        *   `category_title`: (e.g., "Legacy System Modernization", "Moderne IT-Infrastruktur")
        *   A list of service items within that category, each with:
            *   `service_title`: (e.g., "IBM AS/400 & iSeries Consulting")
            *   `service_description`: A brief summary of the service.
            *   `service_link`: The URL to the detailed service page (e.g., `/expertise/ibm-as400-iseries-consulting`).

### User Interactions
*   User clicks on any service card in the grid to navigate to the corresponding service detail page.

### States
*   **Default:** The page loads with the introduction and the full grid of services visible. Standard hover/active states on service cards.