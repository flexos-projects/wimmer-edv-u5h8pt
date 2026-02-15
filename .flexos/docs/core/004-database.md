---
type: doc
subtype: core
title: 004-database.md - Content Model
---

This content model defines the structured data needed to power the Wimmer EDV website, ensuring content is consistent, reusable, and optimized for SEO.

### **1. Service (`service`)**
Defines a core service offering.
*   `title`: Text (e.g., "IBM AS/400 & iSeries Consulting")
*   `slug`: Text (URL-friendly version of the title)
*   `category`: Select (Legacy System Modernization, Modern IT Infrastructure)
*   `summary`: Text (Short description for overview pages)
*   `heroImage`: Image
*   `contentBlocks`: Repeater Field (Flexible content)
    *   `Rich Text`: Formatted text for detailed descriptions.
    *   `Key Features List`: List of specific offerings (e.g., "RPG Programming," "System Integration").
    *   `CallToAction`: Headline, text, button text, button link.
*   `relatedCaseStudies`: Relationship (Many-to-many link to `caseStudy` entries)

### **2. Case Study (`caseStudy`)**
Defines a client success story.
*   `title`: Text (e.g., "ERP Modernization for Leading Austrian Manufacturer")
*   `clientName`: Text (Anonymized if needed, e.g., "Führender österreichischer Maschinenbauer")
*   `slug`: Text
*   `publishDate`: Date
*   `featuredImage`: Image
*   `challenge`: Rich Text (The business problem the client faced)
*   `solution`: Rich Text (How Wimmer EDV solved the problem)
*   `results`: Rich Text (The tangible outcomes and benefits)
*   `technologies`: Tags (e.g., "Dynamics AX", "AS/400", "Veeam")
*   `testimonialQuote`: Text (A powerful quote from the client)
*   `testimonialAuthor`: Text (Name/Title of the person quoted)

### **3. Team Member (`teamMember`)**
Defines a person in the company.
*   `name`: Text (e.g., "Ing. Christian Wimmer")
*   `title`: Text (e.g., "Founder & Lead Consultant")
*   `photo`: Image
*   `bio`: Rich Text (Professional background and expertise)
*   `areasOfExpertise`: Tags (e.g., "IBM iSeries", "ERP Architecture", "RPG")

### **4. Partner (`partner`)**
Defines a technology or certification partner.
*   `name`: Text (e.g., "Veeam")
*   `logo`: Image
*   `websiteUrl`: URL
*   `partnershipLevel`: Text (e.g., "Gold ProPartner", "Microsoft Certified Partner") - Optional

### **5. Testimonial (`testimonial`)**
A standalone client quote for use throughout the site.
*   `quote`: Text (The client's statement)
*   `authorName`: Text
*   `authorTitle`: Text (e.g., "IT Director")
*   `authorCompany`: Text
*   `relatedService`: Relationship (Link to a `service` entry) - Optional

### **6. Global Settings (`settings`)**
A singleton to hold site-wide information.
*   `companyName`: Text (Wimmer Consulting GmbH)
*   `address`: Text
*   `phone`: Text
*   `email`: Text
*   `vatId (UID)`: Text
*   `companyRegisterId (FN)`: Text