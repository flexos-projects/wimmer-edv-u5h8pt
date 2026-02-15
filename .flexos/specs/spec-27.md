```markdown
---
type: spec
subtype: database-relationships
title: Relationship Map - Wimmer EDV
---

# Database Relationship Map

This document outlines the relationships between the tables in the Wimmer EDV database.

### 1. `services` <-> `case_studies`
*   **Type**: Many-to-Many
*   **Tables**: `services`, `case_studies`
*   **Via**: `services_case_studies` (Join Table)
*   **Description**: A service can be associated with multiple case studies, and a case study can demonstrate the application of multiple services.
    *   `services.id` <-> `services_case_studies.service_id`
    *   `case_studies.id` <-> `services_case_studies.case_study_id`

### 2. `services` -> `service_content_blocks`
*   **Type**: One-to-Many
*   **Tables**: `services`, `service_content_blocks`
*   **Description**: Each service can have multiple content blocks that make up its detailed page content. Each content block belongs to exactly one service.
    *   `services.id` (1) -> (M) `service_content_blocks.service_id`

### 3. `testimonials` -> `services`
*   **Type**: Many-to-One
*   **Tables**: `testimonials`, `services`
*   **Description**: A testimonial can be optionally linked to a specific service it relates to. A service can have multiple testimonials.
    *   `testimonials.related_service_id` (M) -> (1) `services.id`

### 4. `case_studies` <-> `tags`
*   **Type**: Many-to-Many
*   **Tables**: `case_studies`, `tags`
*   **Via**: `case_studies_tags` (Join Table)
*   **Description**: A case study can be tagged with multiple technologies (e.g., "AS/400", "Veeam"). A single technology tag can be applied to many case studies. The join is filtered by `tags.type = 'technology'`.
    *   `case_studies.id` <-> `case_studies_tags.case_study_id`
    *   `tags.id` <-> `case_studies_tags.tag_id`

### 5. `team_members` <-> `tags`
*   **Type**: Many-to-Many
*   **Tables**: `team_members`, `tags`
*   **Via**: `team_members_tags` (Join Table)
*   **Description**: A team member can have multiple areas of expertise (e.g., "RPG", "ERP Architecture"). A single expertise tag can be applied to many team members. The join is filtered by `tags.type = 'expertise'`.
    *   `team_members.id` <-> `team_members_tags.team_member_id`
    *   `tags.id` <-> `team_members_tags.tag_id`

### 6. Media Relationships (Image Assets)
The `media` table holds all image assets. Several core tables link to it via a Many-to-One relationship.
*   **Type**: Many-to-One
*   **Description**: An image in the media library can be used by an entry, but each specific image field (like `hero_image_id`) in a core table entry points to only one media asset.

*   `services.hero_image_id` -> `media.id`
*   `case_studies.featured_image_id` -> `media.id`
*   `team_members.photo_id` -> `media.id`
*   `partners.logo_id` -> `media.id`

```