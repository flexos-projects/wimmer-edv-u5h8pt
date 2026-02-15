006-page_kundenerfolge.md
---
type: spec
subtype: page
title: Kundenerfolge & Fallstudien | Wimmer EDV
route: /kundenerfolge
layout: default
---

### Purpose
To provide tangible proof of capabilities and results through detailed case studies, building trust and demonstrating expertise across different industries and technologies.

### Components
1.  **Page Header**
    *   **Description:** A standard page header with a title and an introductory paragraph about their partnership approach.
2.  **Filterable Case Study Grid**
    *   **Description:** A dynamic grid of case study cards that can be filtered by categories like "Branche" (Industry) or "Technologie" (Technology).

### Data Requirements
*   **Page Header:**
    *   `title`: "Kundenerfolge"
    *   `introduction_text`: A paragraph explaining their commitment to long-term partnerships and delivering measurable results.
*   **Filterable Case Study Grid:**
    *   `filter_controls`: A list of filter categories, each with a list of options.
        *   Example: `[ { name: "Branche", options: ["Produktion", "Handel"] }, { name: "Technologie", options: ["AS/400", "Dynamics AX", "Veeam"] } ]`
    *   `case_studies`: A collection of case study objects, each containing:
        *   `title`: The title of the project/case study.
        *   `client_name`: The name of the client.
        *   `thumbnail_image`: URL for a representative image.
        *   `summary`: A short one-sentence summary.
        *   `tags`: An array of tags used for filtering (e.g., `["Produktion", "AS/400"]`).
        *   `link`: The URL to the full case study detail page.

### User Interactions
*   User clicks on a filter button (e.g., "AS/400"). The grid updates (with a potential loading animation) to show only the case studies matching that filter.
*   User can select multiple filters.
*   User clicks on a case study card to navigate to the full case study detail page.

### States
*   **Default:** All case studies are visible in the grid.
*   **Filtering:** A loading state (e.g., a spinner or faded grid) is briefly shown while the grid is being re-rendered after a filter is applied.
*   **No Results:** If a filter combination results in zero matches, a message like "Keine Fallstudien für diese Auswahl gefunden." is displayed instead of an empty grid.
*   **Empty State:** If there are no case studies published at all, a message is displayed, e.g., "Weitere Fallstudien werden in Kürze veröffentlicht."