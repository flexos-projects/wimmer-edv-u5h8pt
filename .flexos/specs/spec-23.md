```yaml
---
type: spec
subtype: flow
title: Primary Journey: Legacy System Leader (High-Intent Search)
trigger: User searches Google for "ibm as/400 modernisierung österreich"
---

### Trigger
A potential client, a leader in a company still operating on a legacy IBM AS/400 system, is actively searching for modernization solutions. They use Google to search for `ibm as/400 modernisierung österreich`, indicating a high intent to find a specialist in Austria.

### Steps
1.  **Entry and Validation (Landing Page: `/expertise/ibm-as400-iseries-consulting`)**
    *   **User Action**: Clicks on Wimmer EDV's search result, landing directly on the dedicated IBM AS/400 iSeries Consulting service page.
    *   **System Response**: The page loads, displaying a headline and opening paragraph that immediately confirm Wimmer EDV's specific expertise in AS/400 modernization. Key services like RPG programming and integration are prominently listed.
2.  **Evidence Gathering (Deep Dive: `/kundenerfolge/case-study-as400-integration`)**
    *   **User Action**: Scans the service page, finds a linked case study titled "Integration of AS/400 with modern logistics software," and clicks on it.
    *   **System Response**: The case study page loads, presenting details of a similar client's challenge, Wimmer EDV's solution, and the achieved results.
3.  **Initiate Contact (Conversion: `/kontakt`)**
    *   **User Action**: Having been convinced by the case study, the user navigates to the contact page, likely via the main navigation's "Kontakt" link or a prominent CTA.
    *   **System Response**: The contact page loads, displaying a detailed "Request a Consultation" form.
    *   **User Action**: Fills out the form, providing specific details about their current system and project goals.
    *   **System Response**: The form submission is processed, and a confirmation message is displayed.

### Decision Points
*   **On Landing Page**: Does the headline and initial content immediately confirm relevance and expertise?
    *   **Yes**: Proceeds to scan services and look for deeper evidence (Step 2).
    *   **No**: User bounces (Failure State).
*   **On Case Study Page**: Does the case study resonate with the user's own problems and provide a convincing solution?
    *   **Yes**: User feels confident and ready to make contact (Step 3).
    *   **No**: User may return to the service page, explore other areas, or bounce (Failure State).
*   **On Contact Page**: Is the "Request a Consultation" form clear, intuitive, and reassuring enough to warrant providing detailed information?
    *   **Yes**: User completes and submits the form (Success State).
    *   **No**: User leaves the contact page without submission (Failure State).

### Error Handling
*   **Page Not Found**: If any link leads to a 404 page, the user is presented with an error page and an option to return to the homepage or contact Wimmer EDV.
*   **Form Validation Errors**: If the user submits the contact form with invalid or missing required information, the form highlights the specific errors, preventing submission until corrected.
*   **Server Error (Form Submission)**: In the rare event of a server-side error during form submission, the user is notified that the submission failed and advised to try again or contact via alternative methods (phone/email).

### Success/Failure States
*   **Success**: The user successfully submits the "Request a Consultation" form on the `/kontakt` page, providing detailed project information.
*   **Failure**: The user leaves the site without submitting the form or initiating contact, either due to lack of relevant information, trust, or technical issues.