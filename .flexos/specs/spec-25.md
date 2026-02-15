```yaml
---
type: spec
subtype: flow
title: Return Visitor / Referral Journey
trigger: User directly navigates to wimmer-edv.at
---

### Trigger
A user has previously heard of Wimmer EDV, possibly through a colleague's recommendation, an offline event, or a previous brief interaction. Their primary goal is to verify the company's legitimacy and find direct contact information. They type `wimmer-edv.at` directly into their browser.

### Steps
1.  **Initial Validation (Homepage Scan)**
    *   **User Action**: Types `wimmer-edv.at` into the browser and presses enter.
    *   **System Response**: The Wimmer EDV homepage loads.
    *   **User Action**: The user quickly scans the professional design, primary expertise areas (e.g., AS/400, Veeam), and prominent partner logos (e.g., IBM, Veeam). This visual check validates the referral and reinforces professionalism.
2.  **Contact Information Retrieval (Contact Page: `/kontakt`)**
    *   **User Action**: With validation confirmed, the user's primary goal is to find contact details. They click the prominently displayed "Kontakt" button in the main navigation.
    *   **System Response**: The `/kontakt` page loads, clearly displaying Wimmer EDV's phone number, email address, physical address, and potentially a contact form.
3.  **Action Initiation (Email or Phone Call)**
    *   **User Action**: The user either copies the provided email address to send an email from their client or taps the phone number (on mobile) to initiate a direct call.
    *   **System Response**: (External) The user's email client opens with the address pre-filled, or their phone's dialer opens with the number pre-filled.

### Decision Points
*   **On Homepage**: Does the professional design, clear expertise, and partner logos immediately validate the company's credibility and the referral?
    *   **Yes**: User proceeds to find contact information (Step 2).
    *   **No**: User might feel the referral was misguided, leading to a bounce (Failure State).
*   **On Contact Page**: Is the contact information clearly laid out, easy to find, and actionable?
    *   **Yes**: User can quickly identify and use their preferred contact method (Step 3).
    *   **No**: User might get frustrated and abandon the attempt to contact (Failure State).

### Error Handling
*   **Website Unavailable**: If `wimmer-edv.at` fails to load, the user will see a browser error (e.g., "This site can't be reached"). This is a critical failure.
*   **Incorrect Contact Information**: If the email address is invalid or the phone number is incorrect/unresponsive, the user will experience frustration and be unable to complete their action.
*   **Page Not Found**: While less likely for a direct navigation, if the `/kontakt` link is broken, the user would encounter a 404, hindering their goal.

### Success/Failure States
*   **Success**: The user successfully obtains and uses Wimmer EDV's contact information (initiates an email or phone call).
*   **Failure**: The user leaves the site without making contact, either due to issues with site accessibility, lack of clear contact information, or failure to validate the company.
```