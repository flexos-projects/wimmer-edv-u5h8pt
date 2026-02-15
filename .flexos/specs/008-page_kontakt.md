008-page_kontakt.md
---
type: spec
subtype: page
title: Kontakt & Beratung | Wimmer EDV
route: /kontakt
layout: default
---

### Purpose
To provide clear and multiple ways to get in touch, and to capture high-quality, pre-qualified leads through a detailed consultation request form.

### Components
1.  **Page Header**
    *   **Description:** A direct and encouraging headline to prompt user action.
2.  **Contact Info Block**
    *   **Description:** A visually separated block containing the physical address, phone number, and email address. Includes an embedded map.
3.  **Consultation Request Form**
    *   **Description:** A "High-Intent" form with specific fields designed to pre-qualify inquiries.

### Data Requirements
*   **Page Header:**
    *   `title`: "Kontaktieren Sie uns für eine unverbindliche Erstberatung"
*   **Contact Info Block:**
    *   `address`: Full company address.
    *   `google_maps_embed_url`: The URL for the embedded map iframe.
    *   `phone_number`: The company phone number.
    *   `email_address`: The company contact email.
*   **Consultation Request Form:**
    *   `form_fields`: Definition for the form fields, including:
        *   Name (Text, required)
        *   Firma (Text, optional)
        *   Email (Email, required)
        *   Telefon (Tel, optional)
        *   Aktuelles System (Text, optional, placeholder: "z.B. IBM AS/400, Dynamics AX 2012")
        *   Projektziele / Ihre Nachricht (Textarea, required)
    *   `privacy_policy_checkbox_text`: "Ich habe die <a href='/datenschutz'>Datenschutzerklärung</a> gelesen und akzeptiere sie."

### User Interactions
*   User clicks on the phone number link, triggering the device's call functionality (`tel:`).
*   User clicks on the email address link, opening the user's default email client (`mailto:`).
*   User interacts with the embedded map (zoom, pan).
*   User fills out and submits the form.
*   Form submission triggers validation on required fields.

### States
*   **Form - Default:** All fields are empty. The submit button is active.
*   **Form - Validation Error:** If the user submits without filling required fields or with an invalid email, an error message appears next to the respective fields and the form is not submitted.
*   **Form - Submitting:** After clicking submit, the button is disabled and a loading indicator (e.g., spinner) appears to provide feedback.
*   **Form - Success:** Upon successful submission, the form is hidden and replaced with a thank-you message (e.g., "Vielen Dank für Ihre Anfrage! Wir werden uns in Kürze bei Ihnen melden.").
*   **Form - Server Error:** If the submission fails due to a server or network error, a general error message is displayed near the submit button (e.g., "Ein Fehler ist aufgetreten. Bitte versuchen Sie es später erneut.").