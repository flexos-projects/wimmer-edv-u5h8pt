```markdown
---
type: spec
subtype: feature
title: 059 - "Our Team" Page/Section
priority: P2
---

### Description

This feature introduces the founder and key consultants, adding a crucial human element to the digital presence. A dedicated page or a section on the "About Us" page will feature professional photos and biographies, showcasing the depth of the team's expertise and building personal trust with prospective clients.

### User Stories

-   **As a potential client,** I want to see the people I might be working with to gauge their experience and feel more connected to the company, not just a faceless brand.
-   **As a job applicant,** I want to learn about the key team members to get a better sense of the company culture and the experts I could be working with.
-   **As a site administrator,** I want a simple system to add new team members, update their bios, or remove them if they leave the company.

### Acceptance Criteria

-   **Given** the site navigation, **Then** there is a link to an "Our Team" page (or it is a clearly-labeled section on the "About Us" page).
-   **Given** the team page/section is viewed, **Then** it displays a professional grid or list of team members.
-   **Given** each team member's profile, **Then** it must include:
    -   A professional headshot photo.
    -   Full Name.
    -   Job Title.
    -   A short biography detailing their expertise and experience.
-   **Given** a site administrator is in the CMS, **Then** there is a dedicated interface (e.g., a "Team Member" custom post type) to manage team profiles independently.

### Technical Notes

-   Implement a "Team Member" custom post type with custom fields for Title, Bio, and Photo.
-   Create a page template that queries and displays all published "Team Member" posts. This page should not be paginated unless the team is very large.
-   Ensure images are uniformly sized (e.g., square or 4:3 ratio) via image processing rules or guidelines for the administrator to maintain a clean layout.
```