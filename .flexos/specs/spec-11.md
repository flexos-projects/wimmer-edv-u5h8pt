```markdown
---
type: spec
subtype: feature
title: 053 - High-Intent "Request a Consultation" Form
priority: P1
---

### Description

A detailed contact form strategically designed to pre-qualify leads for high-value consulting services. By asking for more than just a name and email, the form gathers essential project context upfront, enabling the Wimmer EDV team to have more productive initial conversations and filter for serious inquiries.

### User Stories

-   **As a serious potential client,** I want to provide detailed information about my project so that Wimmer EDV understands my needs before our first call.
-   **As a member of the Wimmer EDV sales team,** I want to receive form submissions with rich context about the prospect's company and project goals so I can prepare effectively for the consultation.
-   **As a site administrator,** I want form submissions to be reliably delivered to a specific email address and securely stored in the website's backend as a backup.

### Acceptance Criteria

-   **Given** the "Request a Consultation" form is displayed, **Then** it must include the following fields:
    -   Full Name (text, required)
    -   Company Name (text, required)
    -   Business Email (email, required, with format validation)
    -   Phone Number (tel, optional)
    -   Company Size (dropdown/select: e.g., 1-10, 11-50, 51-200, 200+)
    -   Current System (text, e.g., AS/400, Dynamics AX, Other)
    -   Project Goals / How can we help? (textarea, required)
    -   Privacy Policy Consent (checkbox, required).
-   **Given** a user submits the form with missing or invalid data, **Then** clear, inline error messages must appear next to the respective fields without the page reloading.
-   **Given** a user successfully submits the form, **Then** an on-page "Thank You" message must replace the form, and an automated confirmation email is sent to their address.
-   **Given** a submission is successful, **Then** an email notification containing all submitted data must be sent to a designated Wimmer EDV email address.
-   **Given** a submission is successful, **Then** the form entry must be saved in the CMS backend.

### Technical Notes

-   Use a robust and reliable forms plugin or library (e.g., Gravity Forms for WordPress, or a headless form service like Formspree).
-   Implement both client-side (JavaScript) and server-side validation to ensure data integrity.
-   Implement an anti-spam measure, such as a honeypot field or Google reCAPTCHA v3, to minimize junk submissions.
```