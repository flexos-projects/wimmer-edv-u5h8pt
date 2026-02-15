```markdown
---
type: spec
subtype: database-schema
title: Schema Registry - Wimmer EDV
---

# Database Schema Registry

This document details the database schema for the Wimmer EDV content model. It includes definitions for all tables, their columns, data types, and constraints.

---

## Core Tables

### `services`
Defines a core service offering.

| Field Name           | Data Type            | Constraints/Notes                                       |
|----------------------|----------------------|---------------------------------------------------------|
| `id`                 | `BIGINT`, `SERIAL`   | Primary Key                                             |
| `title`              | `VARCHAR(255)`       | `NOT NULL`                                              |
| `slug`               | `VARCHAR(255)`       | `NOT NULL`, `UNIQUE`                                    |
| `category`           | `VARCHAR(100)`       | e.g., 'Legacy System Modernization', 'Modern IT'        |
| `summary`            | `TEXT`               | `NOT NULL`. Short description for overview pages.       |
| `hero_image_id`      | `BIGINT`             | Foreign Key to `media.id`. `NULLABLE`.                  |
| `created_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |
| `updated_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |

### `case_studies`
Defines a client success story.

| Field Name           | Data Type            | Constraints/Notes                                       |
|----------------------|----------------------|---------------------------------------------------------|
| `id`                 | `BIGINT`, `SERIAL`   | Primary Key                                             |
| `title`              | `VARCHAR(255)`       | `NOT NULL`                                              |
| `client_name`        | `VARCHAR(255)`       | `NOT NULL`. Can be anonymized.                          |
| `slug`               | `VARCHAR(255)`       | `NOT NULL`, `UNIQUE`                                    |
| `publish_date`       | `TIMESTAMPZ`         | `NOT NULL`                                              |
| `featured_image_id`  | `BIGINT`             | Foreign Key to `media.id`. `NULLABLE`.                  |
| `challenge`          | `TEXT`               | `NOT NULL`. Rich text field.                            |
| `solution`           | `TEXT`               | `NOT NULL`. Rich text field.                            |
| `results`            | `TEXT`               | `NOT NULL`. Rich text field.                            |
| `testimonial_quote`  | `TEXT`               | `NULLABLE`                                              |
| `testimonial_author` | `VARCHAR(255)`       | `NULLABLE`                                              |
| `created_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |
| `updated_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |

### `team_members`
Defines a person in the company.

| Field Name           | Data Type            | Constraints/Notes                                       |
|----------------------|----------------------|---------------------------------------------------------|
| `id`                 | `BIGINT`, `SERIAL`   | Primary Key                                             |
| `name`               | `VARCHAR(255)`       | `NOT NULL`                                              |
| `title`              | `VARCHAR(255)`       | `NOT NULL`                                              |
| `photo_id`           | `BIGINT`             | Foreign Key to `media.id`. `NULLABLE`.                  |
| `bio`                | `TEXT`               | `NULLABLE`. Rich text field.                            |
| `created_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |
| `updated_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |

### `partners`
Defines a technology or certification partner.

| Field Name           | Data Type            | Constraints/Notes                                       |
|----------------------|----------------------|---------------------------------------------------------|
| `id`                 | `BIGINT`, `SERIAL`   | Primary Key                                             |
| `name`               | `VARCHAR(255)`       | `NOT NULL`, `UNIQUE`                                    |
| `logo_id`            | `BIGINT`             | Foreign Key to `media.id`. `NULLABLE`.                  |
| `website_url`        | `VARCHAR(2048)`      | `NULLABLE`                                              |
| `partnership_level`  | `VARCHAR(255)`       | `NULLABLE`. e.g., 'Gold ProPartner'.                     |
| `created_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |
| `updated_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |

### `testimonials`
A standalone client quote for use throughout the site.

| Field Name           | Data Type            | Constraints/Notes                                       |
|----------------------|----------------------|---------------------------------------------------------|
| `id`                 | `BIGINT`, `SERIAL`   | Primary Key                                             |
| `quote`              | `TEXT`               | `NOT NULL`                                              |
| `author_name`        | `VARCHAR(255)`       | `NOT NULL`                                              |
| `author_title`       | `VARCHAR(255)`       | `NOT NULL`                                              |
| `author_company`     | `VARCHAR(255)`       | `NOT NULL`                                              |
| `related_service_id` | `BIGINT`             | Foreign Key to `services.id`. `NULLABLE`.               |
| `created_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |
| `updated_at`         | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`                             |

---

## Singleton & Settings Tables

### `settings`
A singleton table to hold site-wide information (guaranteed to have only one row).

| Field Name             | Data Type            | Constraints/Notes                   |
|------------------------|----------------------|-------------------------------------|
| `id`                   | `INTEGER`            | Primary Key, `CHECK (id = 1)`       |
| `company_name`         | `VARCHAR(255)`       | `NOT NULL`                          |
| `address`              | `TEXT`               | `NOT NULL`                          |
| `phone`                | `VARCHAR(100)`       | `NOT NULL`                          |
| `email`                | `VARCHAR(255)`       | `NOT NULL`                          |
| `vat_id`               | `VARCHAR(100)`       | `NOT NULL`                          |
| `company_register_id`  | `VARCHAR(100)`       | `NOT NULL`                          |
| `updated_at`           | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`         |

---

## Supporting & Relational Tables

### `media`
Stores information about uploaded assets like images.

| Field Name   | Data Type            | Constraints/Notes                   |
|--------------|----------------------|-------------------------------------|
| `id`         | `BIGINT`, `SERIAL`   | Primary Key                         |
| `file_path`  | `VARCHAR(2048)`      | `NOT NULL`. Path to file in storage.|
| `alt_text`   | `VARCHAR(255)`       | `NULLABLE`. For accessibility.      |
| `mime_type`  | `VARCHAR(100)`       | `NOT NULL`                          |
| `file_size`  | `INTEGER`            | `NOT NULL`. Size in bytes.          |
| `created_at` | `TIMESTAMPZ`         | `NOT NULL`, `DEFAULT NOW()`         |

### `service_content_blocks`
Stores the flexible content blocks for the `services` table.

| Field Name    | Data Type            | Constraints/Notes                                       |
|---------------|----------------------|---------------------------------------------------------|
| `id`          | `BIGINT`, `SERIAL`   | Primary Key                                             |
| `service_id`  | `BIGINT`             | Foreign Key to `services.id`. `NOT NULL`.               |
| `block_type`  | `VARCHAR(100)`       | `NOT NULL`. e.g., 'RichText', 'KeyFeaturesList', 'CTA'. |
| `content`     | `JSONB`              | `NOT NULL`. Stores the block's data.                    |
| `sort_order`  | `INTEGER`            | `NOT NULL`, `DEFAULT 0`. For ordering blocks.           |

### `tags`
A central table for all tags (e.g., technologies, areas of expertise).

| Field Name | Data Type            | Constraints/Notes                           |
|------------|----------------------|---------------------------------------------|
| `id`       | `BIGINT`, `SERIAL`   | Primary Key                                 |
| `name`     | `VARCHAR(100)`       | `NOT NULL`                                  |
| `slug`     | `VARCHAR(100)`       | `NOT NULL`                                  |
| `type`     | `VARCHAR(50)`        | `NOT NULL`. e.g., 'technology', 'expertise'.|
|            |                      | `UNIQUE` constraint on (`name`, `type`).    |

### `services_case_studies` (Join Table)
Links `services` and `case_studies` in a many-to-many relationship.

| Field Name      | Data Type | Constraints/Notes                                           |
|-----------------|-----------|-------------------------------------------------------------|
| `service_id`    | `BIGINT`  | Foreign Key to `services.id`.                               |
| `case_study_id` | `BIGINT`  | Foreign Key to `case_studies.id`.                           |
|                 |           | Primary Key on (`service_id`, `case_study_id`).             |

### `case_studies_tags` (Join Table)
Links `case_studies` and `tags` (where type is 'technology').

| Field Name      | Data Type | Constraints/Notes                                           |
|-----------------|-----------|-------------------------------------------------------------|
| `case_study_id` | `BIGINT`  | Foreign Key to `case_studies.id`.                           |
| `tag_id`        | `BIGINT`  | Foreign Key to `tags.id`.                                   |
|                 |           | Primary Key on (`case_study_id`, `tag_id`).                 |

### `team_members_tags` (Join Table)
Links `team_members` and `tags` (where type is 'expertise').

| Field Name      | Data Type | Constraints/Notes                                           |
|-----------------|-----------|-------------------------------------------------------------|
| `team_member_id`| `BIGINT`  | Foreign Key to `team_members.id`.                           |
| `tag_id`        | `BIGINT`  | Foreign Key to `tags.id`.                                   |
|                 |           | Primary Key on (`team_member_id`, `tag_id`).                |

```