```markdown
---
type: config
subtype: design-patterns
title: Component Patterns
---

This document serves as a "recipe book" for building pages on the Wimmer EDV website, ensuring consistency while allowing for creative flexibility. Each pattern describes its purpose, includes Tailwind/CSS classes, a brief HTML structure, notes on responsiveness, animation, and 2-3 variations to choose from.

---

## Section Wrapper

The `SectionWrapper` is the foundational container for all major page sections. It establishes consistent maximum width, horizontal padding, and vertical spacing, and controls background treatment to create visual rhythm.

-   **Purpose:** Ensures consistent page structure, spacing, and background rhythm across the entire site. It's the "DNA" of every page.
-   **Tailwind/CSS Classes:**
    ```css
    .SectionWrapper {
        @apply py-24 lg:py-32; /* Generous vertical padding */
    }
    .SectionWrapper > .Container {
        @apply mx-auto max-w-7xl px-6 md:px-8; /* Content max-width and horizontal padding */
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <section class="SectionWrapper bg-surface-50">
      <div class="Container">
        <!-- Content of your section goes here -->
        <h2 class="text-4xl font-semibold text-primary-600 mb-6">Section Title</h2>
        <p class="text-lg text-surface-800">Section content...</p>
      </div>
    </section>
    ```
-   **Responsive Behavior:**
    -   Vertical padding (`py-24`/`py-32`) scales with screen size.
    -   Horizontal padding (`px-6`/`md:px-8`) adjusts for mobile vs. larger screens.
    -   `max-w-7xl` ensures content doesn't stretch too wide on very large displays.
-   **Animation/Interaction:**
    -   The wrapper itself has no direct animation.
    -   Inner content (e.g., headings, cards) can use scroll-reveal animations (see "Utility Patterns").
-   **Variations:**

    1.  **Default Canvas:**
        -   **Classes:** `bg-surface-50`
        -   **Notes:** The primary off-white background, providing a clean and premium canvas. Use for most sections.
    2.  **Subtle Contrast:**
        -   **Classes:** `bg-surface-100`
        -   **Notes:** A very light grey background to provide subtle visual separation from adjacent sections, creating a gentle rhythm.
    3.  **Bordered Separation:**
        -   **Classes:** `bg-surface-50 border-b border-surface-200`
        -   **Notes:** Use when a clear, crisp division between specific sections is desired, for example, before a footer or a major CTA.

---

## Hero Variants

Hero sections are the critical first impression. They immediately set the tone and communicate the page's core message.

-   **Purpose:** Captures attention, presents the main heading, and often includes a primary call-to-action.
-   **HTML Structure Sketch (General):**
    ```html
    <section class="HeroVariant flex items-center justify-center min-h-[60vh] md:min-h-[80vh] relative overflow-hidden">
      <div class="Container relative z-10 text-center">
        <h1 class="text-5xl md:text-6xl font-bold font-poppins mb-6 leading-tight">Your Bold Headline Here</h1>
        <p class="text-xl md:text-2xl font-inter text-opacity-80 mb-8 max-w-3xl mx-auto">Concise, impactful sub-headline supporting your main message.</p>
        <a href="#" class="Button Button--primary">Primary Call to Action</a>
      </div>
      <!-- Optional: Scroll indicator -->
      <a href="#next-section" aria-label="Scroll down" class="absolute bottom-8 animate-bounce text-surface-50 z-20">
        <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"></path></svg>
      </a>
    </section>
    ```
-   **Responsive Behavior:**
    -   Headlines (`text-5xl`/`text-6xl`) and sub-headlines (`text-xl`/`text-2xl`) adjust.
    -   Layouts (e.g., Split Hero) stack vertically on mobile.
    -   Images/videos should be `object-cover` and `w-full h-full` to adapt.
-   **Animation/Interaction:**
    -   **Entrance:** Content (headline, sub-headline, button) should fade up slightly on page load (`opacity-0 translate-y-4` to `opacity-100 translate-y-0` with `transition-all duration-700 ease-out`).
    -   **Scroll Indicator:** Subtle `animate-bounce` on the scroll arrow.
    -   **Backgrounds:** Subtle parallax or low-opacity animation for abstract graphics (if applicable).
-   **Variations:**

    1.  **Impact (Full-Viewport):**
        -   **Classes:** `min-h-screen bg-primary-600 text-surface-50` (or `bg-cover bg-center` with `GradientOverlay` on `img` or `video` background).
        -   **Notes:** A powerful, immersive hero. Uses a large `h1` (`text-6xl font-bold`). Ideal for brand-defining pages.
        -   **HTML Sketch:**
            ```html
            <section class="HeroVariant min-h-screen flex items-center justify-center relative bg-primary-600 text-surface-50 overflow-hidden">
              <!-- Optional: Abstract background graphic -->
              <div class="absolute inset-0 z-0 opacity-20" style="background-image: url('/abstract-bg.svg'); background-size: cover; background-position: center;"></div>
              <div class="Container relative z-10 text-center reveal-on-load">
                <h1 class="text-5xl md:text-6xl font-bold font-poppins mb-6 leading-tight">Transforming Business Through Intelligent IT Solutions</h1>
                <p class="text-xl md:text-2xl font-inter text-surface-50/90 mb-8 max-w-3xl mx-auto">From strategic consulting to robust implementation, we empower your digital future with precision and trust.</p>
                <a href="/contact" class="Button Button--primary reveal-on-load--delay">Get a Free Consultation</a>
              </div>
              <!-- Scroll indicator (use utility pattern) -->
              <a href="#next-section" aria-label="Scroll down" class="absolute bottom-8 animate-bounce text-surface-50 z-20">...</a>
            </section>
            ```
    2.  **Split Layout:**
        -   **Classes:** `flex flex-col md:flex-row items-center bg-surface-50 py-24 md:py-32`
        -   **Notes:** Divides the hero into two columns: one for content, one for imagery or a compelling graphic. Effective for conveying specific offerings.
        -   **HTML Sketch:**
            ```html
            <section class="HeroVariant flex flex-col md:flex-row items-center py-24 md:py-32 bg-surface-50 overflow-hidden">
              <div class="Container md:grid md:grid-cols-2 gap-16 items-center">
                <div class="md:order-1 text-center md:text-left mb-10 md:mb-0 reveal-on-load">
                  <h1 class="text-4xl md:text-5xl font-semibold font-poppins mb-4 leading-tight text-primary-600">Precision IT, Designed for Your Success</h1>
                  <p class="text-lg md:text-xl font-inter text-surface-800 mb-8">We deliver bespoke IT infrastructure and software solutions tailored to your unique challenges and growth ambitions.</p>
                  <a href="/services" class="Button Button--primary reveal-on-load--delay">Explore Our Expertise</a>
                </div>
                <div class="md:order-2 reveal-on-load--delay-fast">
                  <img src="/hero-abstract-graphic.svg" alt="Abstract network graphic" class="w-full h-auto rounded-xl shadow-lg" />
                </div>
              </div>
            </section>
            ```
    3.  **Minimal (Text-Centered):**
        -   **Classes:** `text-center bg-primary-600 text-surface-50 py-24 md:py-32` (can also use `bg-surface-50` with `text-primary-600`)
        -   **Notes:** Focuses entirely on the headline and a strong CTA, with a clean background. Great for inner pages or secondary landing pages.
        -   **HTML Sketch:**
            ```html
            <section class="HeroVariant flex items-center justify-center py-24 md:py-32 bg-gradient-to-br from-primary-600 to-primary-800 text-surface-50 overflow-hidden">
              <div class="Container relative z-10 text-center reveal-on-load">
                <h1 class="text-4xl md:text-5xl font-bold font-poppins mb-6 leading-tight">Driving Innovation, Delivering Results</h1>
                <p class="text-lg md:text-xl font-inter text-surface-50/90 mb-8 max-w-2xl mx-auto">Leverage our strategic IT insights to gain a competitive edge and optimize your operations.</p>
                <a href="/about" class="Button Button--primary reveal-on-load--delay">Learn More About Us</a>
              </div>
            </section>
            ```

---

## Content Blocks

These are the workhorses of content presentation, making up the majority of page layouts.

### Text + Image

-   **Purpose:** Pairs descriptive text with a supporting visual to enhance understanding.
-   **Tailwind/CSS Classes:**
    ```css
    .ContentBlock {
        @apply py-20 lg:py-28; /* Inherits SectionWrapper padding if directly inside */
    }
    .ContentBlock__text {
        @apply text-lg text-surface-800 leading-relaxed;
    }
    .ContentBlock__image-wrapper {
        @apply rounded-xl shadow-lg overflow-hidden;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <section class="SectionWrapper bg-surface-50">
      <div class="Container">
        <div class="ContentBlock grid grid-cols-1 md:grid-cols-2 gap-16 items-center">
          <div class="ContentBlock__text reveal-on-scroll">
            <h2 class="text-3xl font-semibold font-poppins text-primary-600 mb-4">Strategic IT Partnership</h2>
            <p class="mb-4">We don't just implement technology; we integrate solutions that align with your business objectives, ensuring long-term success and measurable ROI.</p>
            <p>Our collaborative approach means we're an extension of your team, providing expert guidance every step of the way.</p>
          </div>
          <div class="ContentBlock__image-wrapper reveal-on-scroll--delay">
            <img src="/abstract-data-flow.svg" alt="Abstract data flow graphic" class="w-full h-auto object-cover" />
          </div>
        </div>
      </div>
    </section>
    ```
-   **Responsive Behavior:**
    -   Uses a `grid grid-cols-1 md:grid-cols-2` to stack content and image vertically on mobile, then side-by-side on larger screens.
    -   Images are fluid (`w-full h-auto`).
-   **Animation/Interaction:**
    -   Each block (text and image) should fade up and translate slightly on scroll into view (`reveal-on-scroll` utility).
-   **Variations:**

    1.  **Image Right (Default):**
        -   **Classes:** `md:grid-cols-2` (text left, image right).
    2.  **Image Left:**
        -   **Classes:** `md:grid-cols-2 md:grid-flow-col-dense` (use `md:order-2` on text, `md:order-1` on image to swap).
        -   **HTML Sketch:** Add `md:order-2` to text div and `md:order-1` to image div.
    3.  **Centered Text, Flanking Graphics (2 small images):**
        -   **Classes:** `grid grid-cols-1 lg:grid-cols-3 gap-8 items-center`
        -   **Notes:** Content is `lg:col-span-1` or `lg:col-span-2` centered, with abstract visuals in the remaining columns. Good for conceptual messages.
        -   **HTML Sketch:** (requires more complex grid setup, ensure central text block has max-width)
            ```html
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 items-center text-center">
              <div class="lg:order-1 reveal-on-scroll">
                  <img src="/graphic-left.svg" alt="Left graphic" class="w-2/3 mx-auto lg:w-full h-auto" />
              </div>
              <div class="lg:order-2 reveal-on-scroll ContentBlock__text">
                  <h2 class="text-3xl font-semibold font-poppins text-primary-600 mb-4">Innovative Solutions</h2>
                  <p class="max-w-2xl mx-auto">Leveraging cutting-edge technology to build the future of your enterprise infrastructure.</p>
              </div>
              <div class="lg:order-3 reveal-on-scroll--delay">
                  <img src="/graphic-right.svg" alt="Right graphic" class="w-2/3 mx-auto lg:w-full h-auto" />
              </div>
            </div>
            ```

### Feature Grid (Icon + Heading + Text)

-   **Purpose:** Presents multiple features, services, or benefits in a clear, digestible grid format.
-   **Tailwind/CSS Classes:**
    ```css
    .FeatureGrid {
        @apply grid gap-8;
    }
    .FeatureCard {
        @apply p-8 bg-surface-50 rounded-lg shadow-md text-center reveal-on-scroll;
        @apply transition-all duration-300 ease-in-out hover:shadow-xl hover:-translate-y-1; /* Card hover effect */
    }
    .FeatureCard__icon {
        @apply text-accent-500 w-12 h-12 mb-4 mx-auto; /* Icon sizing and color */
    }
    .FeatureCard__heading {
        @apply text-xl font-medium font-poppins text-primary-600 mb-2;
    }
    .FeatureCard__text {
        @apply text-base font-inter text-surface-800;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <section class="SectionWrapper bg-surface-100">
      <div class="Container">
        <h2 class="text-4xl font-semibold font-poppins text-primary-600 text-center mb-12 reveal-on-scroll">Our Core Capabilities</h2>
        <div class="FeatureGrid grid-cols-1 md:grid-cols-2 lg:grid-cols-3">
          <div class="FeatureCard reveal-on-scroll">
            <svg class="FeatureCard__icon" fill="currentColor" viewBox="0 0 24 24"><!-- Icon SVG --></svg>
            <h3 class="FeatureCard__heading">Cloud Infrastructure</h3>
            <p class="FeatureCard__text">Scalable and secure cloud solutions tailored for optimal performance.</p>
          </div>
          <!-- More FeatureCards -->
        </div>
      </div>
    </section>
    ```
-   **Responsive Behavior:**
    -   Uses `grid-cols-1 md:grid-cols-2 lg:grid-cols-3` (or `lg:grid-cols-4`) to adapt column count.
-   **Animation/Interaction:**
    -   Each `FeatureCard` should have a scroll-reveal animation, possibly staggered.
    -   `FeatureCard` hover effect: subtle lift and shadow increase.
-   **Variations:**

    1.  **3-Column Grid:**
        -   **Classes:** `lg:grid-cols-3`
        -   **Notes:** Standard and versatile, fits most content types well.
    2.  **4-Column Grid:**
        -   **Classes:** `lg:grid-cols-4`
        -   **Notes:** For more compact features or when you have many items. Reduces individual card prominence.
    3.  **2-Column with Larger Cards:**
        -   **Classes:** `md:grid-cols-2 lg:grid-cols-2`
        -   **Notes:** Provides more space for text and icons, giving each feature greater emphasis.

### Stats/Numbers Bar

-   **Purpose:** Visually highlights key achievements or impressive figures, often with an animated count-up for impact.
-   **Tailwind/CSS Classes:**
    ```css
    .StatsBar {
        @apply py-16 bg-surface-100; /* Background for the bar */
    }
    .StatItem {
        @apply text-center reveal-on-scroll; /* Animation class */
    }
    .StatItem__number {
        @apply text-5xl md:text-6xl font-bold font-poppins text-accent-500 mb-2;
    }
    .StatItem__label {
        @apply text-lg font-medium font-inter text-surface-800;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <section class="SectionWrapper StatsBar">
      <div class="Container">
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
          <div class="StatItem">
            <div class="StatItem__number" data-count="98">0</div>
            <p class="StatItem__label">Client Satisfaction</p>
          </div>
          <div class="StatItem">
            <div class="StatItem__number" data-count="15">0</div>
            <p class="StatItem__label">Years Experience</p>
          </div>
          <div class="StatItem">
            <div class="StatItem__number" data-count="250">0</div>
            <p class="StatItem__label">Projects Completed</p>
          </div>
          <div class="StatItem">
            <div class="StatItem__number" data-count="24">0</div>
            <p class="StatItem__label">Global Partners</p>
          </div>
        </div>
      </div>
    </section>
    ```
-   **Responsive Behavior:**
    -   Uses `grid-cols-2 md:grid-cols-4` to adapt column count based on screen size.
-   **Animation/Interaction:**
    -   **Count-up:** A JavaScript Intersection Observer should trigger a smooth count-up animation for each `.StatItem__number` when it enters the viewport. `data-count` attribute holds the target value.
    -   Scroll reveal for the whole `.StatItem`.
-   **Variations:**

    1.  **Standard (4 Stats):**
        -   **Classes:** `grid-cols-2 md:grid-cols-4`, `bg-surface-100`, `text-accent-500` for numbers.
    2.  **Accent Background:**
        -   **Classes:** `bg-primary-600`, `text-surface-50` for numbers and labels.
        -   **Notes:** Creates a stronger, more assertive visual block.
    3.  **With Icon:**
        -   **HTML Sketch:** Add a small SVG icon (`w-8 h-8 text-accent-500 mb-2 mx-auto`) above the number.
        -   **Notes:** Adds an extra layer of visual storytelling to each stat.

### Testimonial

-   **Purpose:** Builds trust and credibility through direct client endorsements.
-   **Tailwind/CSS Classes:**
    ```css
    .Testimonial {
        @apply py-20 lg:py-28;
    }
    .Testimonial__quote {
        @apply text-3xl font-semibold font-poppins text-primary-600 mb-6;
    }
    .Testimonial__attribution {
        @apply text-lg font-medium font-inter text-surface-800;
    }
    .Testimonial__role {
        @apply text-base text-surface-700;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <section class="SectionWrapper bg-surface-50">
      <div class="Container max-w-4xl mx-auto text-center reveal-on-scroll">
        <p class="Testimonial__quote">“Wimmer EDV transformed our IT infrastructure, making it more robust and efficient. Their precision and expertise are unmatched.”</p>
        <cite class="Testimonial__attribution block">Anna Müller, <span class="Testimonial__role">CTO, Tech Solutions GmbH</span></cite>
        <!-- Optional: star rating -->
        <div class="flex justify-center mt-4 text-accent-500">
            <!-- SVG stars here -->
        </div>
      </div>
    </section>
    ```
-   **Responsive Behavior:**
    -   The entire block typically centers and takes full width on mobile.
-   **Animation/Interaction:**
    -   Scroll-reveal animation for the quote and attribution.
-   **Variations:**

    1.  **Single Card (Default):**
        -   **Classes:** Centered, `max-w-4xl mx-auto`, `bg-surface-50` or `bg-surface-100`.
        -   **Notes:** A prominent, standalone quote.
    2.  **Dark Background:**
        -   **Classes:** `bg-primary-600 text-surface-50`. Adjust quote color to `text-surface-50`.
        -   **Notes:** Creates a strong visual emphasis, makes the testimonial stand out.
    3.  **With Avatar:**
        -   **HTML Sketch:** Add an `img` (`w-16 h-16 rounded-full mx-auto mb-4`) above the quote for the client's portrait.
        -   **Notes:** Personalizes the testimonial and adds a human touch.

### CTA Banner

-   **Purpose:** A highly visible, distinct section designed to prompt a specific user action.
-   **Tailwind/CSS Classes:**
    ```css
    .CTABanner {
        @apply py-20 bg-accent-500 text-surface-50; /* Primary accent background */
    }
    .CTABanner__heading {
        @apply text-4xl font-semibold font-poppins mb-4 leading-tight;
    }
    .CTABanner__subtext {
        @apply text-xl font-inter opacity-90 max-w-3xl;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <section class="SectionWrapper CTABanner">
      <div class="Container flex flex-col md:flex-row items-center justify-between text-center md:text-left gap-8 reveal-on-scroll">
        <div class="flex-grow">
          <h2 class="CTABanner__heading">Ready to Elevate Your IT Strategy?</h2>
          <p class="CTABanner__subtext mx-auto md:mx-0">Connect with our experts today to discuss your unique challenges and discover tailored solutions.</p>
        </div>
        <a href="/contact" class="Button Button--white-outline reveal-on-scroll--delay">Start a Project</a>
      </div>
    </section>
    ```
-   **Responsive Behavior:**
    -   Uses `flex-col md:flex-row` to stack text and button vertically on mobile, then side-by-side on larger screens.
    -   Text aligns center on mobile, left on desktop (`text-center md:text-left`).
-   **Animation/Interaction:**
    -   Scroll-reveal for the entire banner.
    -   Button hover effect (e.g., scale up or background change).
-   **Variations:**

    1.  **Accent Background (Default):**
        -   **Classes:** `bg-accent-500 text-surface-50`, with a `Button--white-outline` (see Button variations).
        -   **Notes:** High contrast, highly visible, and action-oriented.
    2.  **Primary Background:**
        -   **Classes:** `bg-primary-600 text-surface-50`, with a `Button--white-outline`.
        -   **Notes:** Conveys stability and trust while still prompting action. Good for less urgent CTAs.
    3.  **With Subtle Illustration:**
        -   **HTML Sketch:** Add a small abstract graphic (`w-24 h-24 absolute right-0 top-1/2 -translate-y-1/2 opacity-30`) positioned subtly in the corner or behind the text.
        -   **Notes:** Adds visual interest without distracting from the CTA.

### FAQ Accordion

-   **Purpose:** Presents common questions and answers in a collapsible format, saving space and improving readability.
-   **Tailwind/CSS Classes:**
    ```css
    .AccordionWrapper {
        @apply w-full max-w-3xl mx-auto;
    }
    .AccordionItem {
        @apply border border-surface-200 rounded-lg overflow-hidden mb-4 reveal-on-scroll;
    }
    .AccordionItem[open] summary {
        @apply bg-surface-100;
    }
    .AccordionItem summary {
        @apply flex justify-between items-center p-6 cursor-pointer text-xl font-medium font-poppins text-primary-600;
        @apply transition-all duration-300 ease-in-out;
    }
    .AccordionItem summary::after { /* Chevron icon */
        content: url('data:image/svg+xml;utf8,<svg class="w-6 h-6 transform transition-transform duration-300" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>');
    }
    .AccordionItem[open] summary::after {
        content: url('data:image/svg+xml;utf8,<svg class="w-6 h-6 transform transition-transform duration-300 rotate-180" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"></path></svg>');
    }
    .AccordionItem__content {
        @apply px-6 pb-6 text-lg font-inter text-surface-800 leading-relaxed;
        /* For smooth height transition, typically needs JS, or a max-height trick */
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <section class="SectionWrapper bg-surface-50">
      <div class="Container">
        <h2 class="text-4xl font-semibold font-poppins text-primary-600 text-center mb-12 reveal-on-scroll">Frequently Asked Questions</h2>
        <div class="AccordionWrapper">
          <details class="AccordionItem">
            <summary>What IT services do you offer?</summary>
            <div class="AccordionItem__content">
              <p>We offer a comprehensive range of services including cloud infrastructure, network security, custom software development, IT consulting, and managed services.</p>
            </div>
          </details>
          <details class="AccordionItem">
            <summary>How do you ensure data security?</summary>
            <div class="AccordionItem__content">
              <p>Security is paramount. We implement multi-layered security protocols, conduct regular audits, and adhere to industry best practices and compliance standards.</p>
            </div>
          </details>
          <!-- More AccordionItems -->
        </div>
      </div>
    </section>
    ```
-   **Responsive Behavior:**
    -   Stacks vertically by default.
-   **Animation/Interaction:**
    -   **Open/Close:** The `summary` click triggers the `details` element's native open/close. For a smooth height transition, a JavaScript solution or a CSS `max-height` trick (e.g., `max-height: 0; transition: max-height 0.3s ease-in-out;` and `max-height: 500px;` on `[open]`) would be needed.
    -   **Chevron Icon:** Rotates on open/close (`rotate-180`).
    -   Scroll reveal for each `AccordionItem`.
-   **Variations:**

    1.  **Individual Items (Default):**
        -   **Classes:** Each `details` element is a separate `AccordionItem` with its own border and shadow.
    2.  **Grouped Within a Card:**
        -   **HTML Sketch:** Wrap the `AccordionWrapper` in a `Card` component (e.g., `bg-surface-100 p-8 rounded-xl shadow-lg`). Remove `border` and `shadow` from individual `AccordionItem` if desired, or keep `border-b` for internal separation.
        -   **Notes:** Groups related FAQs visually within a single, larger container.
    3.  **Subtle Background for Open State:**
        -   **Classes:** `AccordionItem[open] summary { @apply bg-surface-100; }` (already in default).
        -   **Notes:** Provides a clear visual cue when an item is expanded.

---

## Navigation

Crucial for user experience, navigation must be intuitive, responsive, and visually consistent.

### Header

-   **Purpose:** Provides site identity (logo), primary navigation links, and key calls-to-action.
-   **Tailwind/CSS Classes:**
    ```css
    .Header {
        @apply fixed top-0 left-0 w-full z-50 py-4 md:py-6 transition-all duration-300 ease-in-out;
    }
    .Header--transparent {
        @apply bg-transparent;
    }
    .Header--solid {
        @apply bg-primary-600 shadow-md;
    }
    .Header__logo {
        @apply h-8 md:h-10 text-surface-50; /* Adjust height and ensure SVG is styled correctly */
    }
    .Header__nav-link {
        @apply text-surface-50 hover:text-accent-500 font-medium font-poppins text-lg relative group;
        /* Animated underline setup */
        @apply after:block after:absolute after:bottom-0 after:left-0 after:w-0 after:h-0.5 after:bg-accent-500 after:transition-all after:duration-300 group-hover:after:w-full;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <header class="Header Header--transparent">
      <div class="Container flex items-center justify-between">
        <a href="/" aria-label="Wimmer EDV Home">
          <img src="/logo-white.svg" alt="Wimmer EDV Logo" class="Header__logo">
        </a>
        <nav class="hidden md:block">
          <ul class="flex space-x-8">
            <li><a href="/services" class="Header__nav-link group">Services</a></li>
            <li><a href="/about" class="Header__nav-link group">About Us</a></li>
            <li><a href="/contact" class="Header__nav-link group">Contact</a></li>
          </ul>
        </nav>
        <a href="/contact" class="Button Button--white-outline hidden md:block">Get a Quote</a>
        <button class="MobileMenu-trigger md:hidden text-surface-50">
          <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16m-7 6h7"></path></svg>
        </button>
      </div>
    </header>
    ```
-   **Responsive Behavior:**
    -   Main navigation links (`ul`) and CTA button (`Button`) hide on mobile (`hidden md:block`).
    -   A burger icon (`MobileMenu-trigger`) appears on mobile (`md:hidden`).
-   **Animation/Interaction:**
    -   **Scroll Behavior:** JavaScript listener adds/removes `Header--solid` class (or directly `bg-primary-600 shadow-md`) when `window.scrollY > X`.
    -   **Link Hover:** `Header__nav-link` uses a clever `::after` pseudo-element to create an animated underline effect on hover.
    -   **Button Hover:** Standard button hover animation (see "Button Hierarchy").
-   **Variations:**

    1.  **Default:** Logo left, main navigation links (Services, About, Contact) in the middle, primary CTA button right.
    2.  **Simple:** Logo left, a single primary CTA button right. Navigation links only available via mobile menu.
    3.  **Center Nav:** Logo left, main navigation links centered in their own block, CTA button right. Requires a slightly different flex/grid setup.

### Mobile Menu

-   **Purpose:** Provides accessible navigation on small screens.
-   **Tailwind/CSS Classes:**
    ```css
    .MobileMenu {
        @apply fixed inset-0 bg-primary-900 z-50 flex flex-col justify-center items-center text-center;
        @apply transition-transform duration-300 ease-in-out transform translate-x-full opacity-0; /* Hidden by default */
    }
    .MobileMenu--open {
        @apply translate-x-0 opacity-100; /* Visible state */
    }
    .MobileMenu__close-button {
        @apply absolute top-6 right-6 text-surface-50;
    }
    .MobileMenu__nav-link {
        @apply text-3xl font-poppins font-medium text-surface-50 py-4 hover:text-accent-500 transition-colors duration-200;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <div id="mobile-menu" class="MobileMenu" aria-hidden="true">
      <button class="MobileMenu__close-button">
        <svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
      </button>
      <nav>
        <ul class="space-y-4">
          <li><a href="/services" class="MobileMenu__nav-link">Services</a></li>
          <li><a href="/about" class="MobileMenu__nav-link">About Us</a></li>
          <li><a href="/contact" class="MobileMenu__nav-link">Contact</a></li>
        </ul>
      </nav>
      <a href="/contact" class="Button Button--primary mt-8">Get a Quote</a>
    </div>
    ```
-   **Responsive Behavior:**
    -   Hidden by default (`translate-x-full opacity-0`), revealed via JavaScript by toggling `MobileMenu--open`.
-   **Animation/Interaction:**
    -   **Open/Close:** Triggered by the burger icon. Menu slides in (`translate-x-0`) and fades in (`opacity-100`).
    -   **Burger Icon:** The icon itself should animate into an 'X' shape when opened (requires CSS transitions on the SVG paths or a dedicated library).
-   **Variations:**

    1.  **Full Overlay (Fade & Slide Right):**
        -   **Classes:** `translate-x-full opacity-0` for hidden, `translate-x-0 opacity-100` for open.
        -   **Notes:** Menu slides in from the right edge and fully covers the screen.
    2.  **Drawer (Right):**
        -   **Classes:** Same as above, but with `md:hidden` to ensure it only appears on mobile.
        -   **Notes:** A common pattern, feels natural for touch devices.
    3.  **Drawer (Left):**
        -   **Classes:** `transform -translate-x-full opacity-0` for hidden, `translate-x-0 opacity-100` for open.
        -   **Notes:** Similar to right drawer but slides from the left.

### Footer

-   **Purpose:** Contains secondary navigation, legal information, social media links, and optionally a newsletter signup.
-   **Tailwind/CSS Classes:**
    ```css
    .Footer {
        @apply bg-primary-950 text-surface-400 py-16 lg:py-20;
    }
    .Footer__heading {
        @apply text-lg font-poppins font-medium text-surface-50 mb-4;
    }
    .Footer__link {
        @apply text-base font-inter hover:text-accent-500 transition-colors duration-200 block mb-2;
    }
    .Footer__social-icon {
        @apply w-6 h-6 text-surface-400 hover:text-accent-500 transition-colors duration-200;
    }
    .Footer__legal-text {
        @apply text-sm text-surface-600 mt-8 text-center;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <footer class="Footer">
      <div class="Container">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8 pb-12 border-b border-primary-800">
          <div>
            <img src="/logo-white.svg" alt="Wimmer EDV Logo" class="h-8 mb-4">
            <p class="text-sm">Precision IT solutions for a complex world.</p>
          </div>
          <div>
            <h3 class="Footer__heading">Services</h3>
            <ul>
              <li><a href="/services/cloud" class="Footer__link">Cloud Computing</a></li>
              <li><a href="/services/security" class="Footer__link">Cybersecurity</a></li>
              <li><a href="/services/dev" class="Footer__link">Software Development</a></li>
            </ul>
          </div>
          <div>
            <h3 class="Footer__heading">Company</h3>
            <ul>
              <li><a href="/about" class="Footer__link">About Us</a></li>
              <li><a href="/careers" class="Footer__link">Careers</a></li>
              <li><a href="/contact" class="Footer__link">Contact</a></li>
            </ul>
          </div>
          <div>
            <h3 class="Footer__heading">Connect</h3>
            <div class="flex space-x-4 mt-4">
              <a href="#" aria-label="LinkedIn" class="Footer__social-icon"><!-- LinkedIn SVG --></a>
              <a href="#" aria-label="Twitter" class="Footer__social-icon"><!-- Twitter SVG --></a>
            </div>
            <!-- Optional: Newsletter signup form -->
            <form class="mt-6">
                <input type="email" placeholder="Your email" class="w-full p-3 rounded-lg bg-primary-800 border border-primary-700 text-surface-50 focus:outline-none focus:ring-2 focus:ring-accent-500">
                <button type="submit" class="Button Button--primary mt-3 w-full">Subscribe</button>
            </form>
          </div>
        </div>
        <p class="Footer__legal-text">&copy; 2023 Wimmer EDV. All rights reserved. <a href="/privacy" class="hover:text-accent-500">Privacy Policy</a></p>
      </div>
    </footer>
    ```
-   **Responsive Behavior:**
    -   Uses `grid-cols-1 md:grid-cols-4` to stack columns vertically on mobile and display in a grid on larger screens.
-   **Animation/Interaction:** None on the footer itself. Links and buttons have standard hover effects.
-   **Variations:**

    1.  **Multi-Column:** Logo/brand description, 2-3 columns of navigation links, social media, and a newsletter signup.
    2.  **Simple:** Logo, minimal links (e.g., Privacy, Terms), social media, and copyright information.
    3.  **Accent Top Border:**
        -   **Classes:** Add `border-t-4 border-accent-500` to the `Footer` element.
        -   **Notes:** A subtle visual pop at the top of the footer to distinguish it.

---

## Cards

The `Card` pattern is a versatile, reusable component for displaying diverse content such as services, team members, blog posts, or project highlights.

-   **Purpose:** Groups related information visually, creating clear content blocks and adding structure.
-   **Tailwind/CSS Classes:**
    ```css
    .Card {
        @apply bg-surface-50 rounded-lg shadow-md p-6 overflow-hidden;
        @apply transition-all duration-300 ease-in-out; /* Base for hover effects */
    }
    .Card--hover-lift {
        @apply hover:shadow-xl hover:-translate-y-1; /* Lift effect */
    }
    .Card__image {
        @apply w-full h-48 object-cover rounded-md mb-4;
    }
    .Card__title {
        @apply text-xl font-medium font-poppins text-primary-600 mb-2;
    }
    .Card__description {
        @apply text-base font-inter text-surface-800 leading-relaxed;
    }
    ```
-   **HTML Structure Sketch (General):**
    ```html
    <div class="Card Card--hover-lift reveal-on-scroll">
      <img src="/card-image.jpg" alt="Description" class="Card__image" />
      <div class="CardContent">
        <h3 class="Card__title">Service / Project Title</h3>
        <p class="Card__description">A brief description of the service or project, highlighting key benefits or features.</p>
        <a href="#" class="Button Button--link mt-4">Learn More</a>
      </div>
    </div>
    ```
-   **Responsive Behavior:**
    -   Cards typically adapt to their grid container. Images inside should be `w-full h-auto` or `h-X object-cover`.
-   **Animation/Interaction:**
    -   **Hover Effect:** `Card--hover-lift` class for a subtle upward translation (`-translate-y-1`) combined with an increased shadow (`shadow-xl`).
    -   **Scroll Reveal:** Individual cards should animate into view using the `reveal-on-scroll` utility.
-   **Variations:**

    1.  **Image Top (Default):**
        -   **Classes:** `Card`, `Card__image` at the top.
        -   **Notes:** Most common layout, suitable for services, blog posts, or generic content where the image introduces the topic.
        -   **HTML Sketch:** (See general sketch above)
    2.  **Image Left (Horizontal):**
        -   **Classes:** `flex flex-col sm:flex-row items-start p-4`. Image `w-full sm:w-1/3 h-32 sm:h-auto object-cover rounded-md sm:mr-4 mb-4 sm:mb-0`. Text content `flex-grow`.
        -   **Notes:** Good for lists of items where images are secondary, like team members or small product listings.
        -   **HTML Sketch:**
            ```html
            <div class="Card Card--hover-lift flex flex-col sm:flex-row items-start p-4 reveal-on-scroll">
              <img src="/person-avatar.jpg" alt="Team member" class="w-full sm:w-1/3 h-32 sm:h-auto object-cover rounded-md sm:mr-4 mb-4 sm:mb-0" />
              <div class="flex-grow">
                <h3 class="Card__title">John Doe</h3>
                <p class="text-sm font-inter text-surface-700 mb-2">Lead Cloud Architect</p>
                <p class="Card__description text-sm">John specializes in building resilient and scalable cloud infrastructures.</p>
              </div>
            </div>
            ```
    3.  **Background Image Overlay:**
        -   **Classes:** `relative text-surface-50 p-6 md:p-8 rounded-xl overflow-hidden min-h-[250px] shadow-lg Card--hover-lift`. Image as `background-image` on parent `div` or `absolute inset-0 z-0` positioned. Use `GradientOverlay` for readability.
        -   **Notes:** Visually striking, best for hero cards or categories where the image sets a strong mood.
        -   **HTML Sketch:**
            ```html
            <div class="Card Card--hover-lift relative text-surface-50 rounded-xl overflow-hidden min-h-[250px] shadow-lg reveal-on-scroll">
              <img src="/data-network.jpg" alt="Network operations" class="absolute inset-0 w-full h-full object-cover z-0" />
              <div class="absolute inset-0 z-10 GradientOverlay--primary-dark"></div> <!-- Utility gradient overlay -->
              <div class="relative z-20 p-6 md:p-8 flex flex-col justify-end h-full">
                <h3 class="Card__title text-surface-50">Advanced Cybersecurity</h3>
                <p class="Card__description text-surface-50/90">Protect your assets with robust, multi-layered security protocols.</p>
                <a href="#" class="Button Button--white-outline mt-4 self-start">View Details</a>
              </div>
            </div>
            ```

---

## Forms

Forms are essential for interaction; consistent styling ensures usability and a professional appearance.

### Input Styling

-   **Purpose:** Defines the look and feel for all form input fields (text, email, textarea, select).
-   **Tailwind/CSS Classes:**
    ```css
    .InputGroup {
        @apply mb-4;
    }
    .InputGroup__label {
        @apply block text-sm font-medium font-inter text-surface-700 mb-2;
    }
    .InputStyle {
        @apply w-full p-3 border border-surface-200 rounded-lg bg-surface-50 text-surface-800;
        @apply focus:outline-none focus:ring-2 focus:ring-primary-500 focus:border-primary-500;
        @apply transition-all duration-200 ease-in-out;
    }
    .InputStyle::placeholder {
        @apply text-surface-500;
    }
    .InputStyle--error {
        @apply border-error focus:ring-error focus:border-error;
    }
    .InputStyle--success {
        @apply border-success focus:ring-success focus:border-success;
    }
    .InputStyle--warning {
        @apply border-warning focus:ring-warning focus:border-warning;
    }
    .InputGroup__help-text {
        @apply text-xs mt-1;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <div class="InputGroup">
      <label for="name" class="InputGroup__label">Full Name</label>
      <input type="text" id="name" name="name" placeholder="John Doe" class="InputStyle" />
      <!-- Optional help/error text -->
      <p class="InputGroup__help-text text-surface-600">Please enter your full name.</p>
    </div>
    ```
-   **Responsive Behavior:**
    -   Inputs are `w-full` by default, making them fluid and responsive.
-   **Animation/Interaction:**
    -   **Focus Ring:** `focus:ring-2 focus:ring-primary-500` provides clear feedback on focus.
    -   **Transitions:** `transition-all` on border and ring for a smooth effect.
-   **Variations:**

    1.  **Standard:** Label above the input field.
    2.  **With Placeholder:** Use `placeholder="Your Email Address"` as a hint.
    3.  **With Help Text:** A small `InputGroup__help-text` (`text-surface-600`) provides additional guidance below the input.

### Button Hierarchy

-   **Purpose:** Defines distinct visual styles for different levels of action priority.
-   **Tailwind/CSS Classes:**
    ```css
    .Button {
        @apply px-6 py-3 rounded-lg font-medium font-poppins text-lg text-center inline-flex items-center justify-center;
        @apply transition-transform duration-200 ease-in-out hover:scale-105; /* Consistent hover effect */
    }
    .Button--primary {
        @apply bg-accent-500 text-white shadow-md hover:bg-accent-600 focus:outline-none focus:ring-2 focus:ring-accent-500 focus:ring-offset-2;
    }
    .Button--secondary {
        @apply bg-primary-600 text-white shadow-md hover:bg-primary-700 focus:outline-none focus:ring-2 focus:ring-primary-500 focus:ring-offset-2;
    }
    .Button--outline {
        @apply border-2 border-primary-600 text-primary-600 bg-transparent hover:bg-primary-600 hover:text-white focus:outline-none focus:ring-2 focus:ring-primary-500 focus:ring-offset-2;
    }
    .Button--white-outline {
        @apply border-2 border-surface-50 text-surface-50 bg-transparent hover:bg-surface-50 hover:text-primary-600 focus:outline-none focus:ring-2 focus:ring-surface-50 focus:ring-offset-2;
    }
    .Button--ghost {
        @apply text-primary-600 bg-transparent hover:bg-primary-50 focus:outline-none focus:ring-2 focus:ring-primary-500 focus:ring-offset-2;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <button type="submit" class="Button Button--primary">Submit Form</button>
    <a href="/learn-more" class="Button Button--secondary">Learn More</a>
    ```
-   **Responsive Behavior:**
    -   Buttons are inline-flex by default. For full-width on mobile, add `w-full md:w-auto`.
-   **Animation/Interaction:**
    -   **Hover Effect:** `hover:scale-105` is applied to all buttons for a subtle, consistent lift.
    -   **Focus Ring:** `focus:ring-2` provides clear accessibility feedback.
-   **Variations:**

    1.  **Primary CTA:** `Button--primary` (Bold orange, highest emphasis).
    2.  **Secondary Action:** `Button--secondary` (Deep navy, strong but not primary emphasis).
    3.  **Outline/Ghost:** `Button--outline` (Navy border, transparent background, for less critical actions or as an alternative). `Button--white-outline` (for use on dark backgrounds).

### Form Layout

-   **Purpose:** Structures multiple input fields into a coherent and usable form.
-   **Tailwind/CSS Classes:**
    ```css
    .FormLayout {
        @apply p-8 bg-surface-50 rounded-xl shadow-lg; /* Form container styling */
    }
    .FormLayout--grid-cols-2 {
        @apply grid grid-cols-1 md:grid-cols-2 gap-x-8;
    }
    .FormLayout__actions {
        @apply mt-6 flex justify-end gap-4; /* For multiple buttons */
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <section class="SectionWrapper bg-surface-100">
      <div class="Container max-w-3xl mx-auto">
        <h2 class="text-4xl font-semibold font-poppins text-primary-600 text-center mb-10">Contact Us</h2>
        <form class="FormLayout">
          <div class="FormLayout--grid-cols-2">
            <div class="InputGroup">
              <label for="firstName" class="InputGroup__label">First Name</label>
              <input type="text" id="firstName" name="firstName" class="InputStyle" />
            </div>
            <div class="InputGroup">
              <label for="lastName" class="InputGroup__label">Last Name</label>
              <input type="text" id="lastName" name="lastName" class="InputStyle" />
            </div>
          </div>
          <div class="InputGroup">
            <label for="email" class="InputGroup__label">Email Address</label>
            <input type="email" id="email" name="email" class="InputStyle" />
          </div>
          <div class="InputGroup">
            <label for="message" class="InputGroup__label">Your Message</label>
            <textarea id="message" name="message" rows="5" class="InputStyle"></textarea>
          </div>
          <div class="FormLayout__actions">
            <button type="submit" class="Button Button--primary">Send Message</button>
          </div>
        </form>
      </div>
    </section>
    ```
-   **Responsive Behavior:**
    -   `FormLayout--grid-cols-2` ensures a two-column layout on desktop and stacks to a single column on mobile.
-   **Animation/Interaction:** None on the form layout itself. Individual inputs and buttons follow their own animation rules.
-   **Variations:**

    1.  **Single Column:** All input groups stack vertically. (Remove `FormLayout--grid-cols-2`).
    2.  **Responsive Two-Column:** Uses `FormLayout--grid-cols-2` for a more organized look, particularly for name, email, etc.
    3.  **Card-Based:** The `FormLayout` itself has `p-8 bg-surface-50 rounded-xl shadow-lg` applied, essentially making it a distinct card.

### Validation States

-   **Purpose:** Provides clear visual feedback for input validation (error, success, warning).
-   **Tailwind/CSS Classes:**
    ```css
    .InputGroup__error-message {
        @apply InputGroup__help-text text-error;
    }
    .InputGroup__success-message {
        @apply InputGroup__help-text text-success;
    }
    .InputGroup__warning-message {
        @apply InputGroup__help-text text-warning;
    }
    /* InputStyle--error/success/warning classes already defined in Input Styling */
    ```
-   **HTML Structure Sketch:**
    ```html
    <div class="InputGroup">
      <label for="email" class="InputGroup__label">Email Address</label>
      <input type="email" id="email" name="email" class="InputStyle InputStyle--error" value="invalid@example" />
      <p class="InputGroup__error-message">Please enter a valid email address.</p>
    </div>

    <div class="InputGroup">
      <label for="username" class="InputGroup__label">Username</label>
      <input type="text" id="username" name="username" class="InputStyle InputStyle--success" value="johndoe123" />
      <p class="InputGroup__success-message">Username is available!</p>
    </div>
    ```
-   **Responsive Behavior:** No specific responsive behavior beyond inputs being `w-full`.
-   **Animation/Interaction:** No animation on state change. Visual cues are instant.
-   **Variations:**

    1.  **Error:** Red border (`InputStyle--error`) and red message (`InputGroup__error-message`).
    2.  **Success:** Green border (`InputStyle--success`) and green message (`InputGroup__success-message`).
    3.  **Warning:** Amber border (`InputStyle--warning`) and amber message (`InputGroup__warning-message`).

---

## Utility Patterns

These are reusable classes or small snippets to apply common design system directives across components.

### Page Transition Wrapper

-   **Purpose:** Provides a smooth visual transition when navigating between pages (useful with client-side routing or Astro's View Transitions API).
-   **Tailwind/CSS Classes:**
    ```css
    /* For simple CSS opacity transition on page load (requires JS to toggle classes) */
    .PageTransitionWrapper {
        @apply opacity-0 transition-opacity duration-500 ease-in-out;
    }
    .PageTransitionWrapper--active {
        @apply opacity-100;
    }

    /* Astro View Transitions API (recommended for Astro) */
    /* Add this to your base layout component's <html> tag: */
    /* <html class="scroll-smooth" data-astro-view-transitions> */
    /* Then define transitions in global CSS: */
    /*
    @keyframes fade-in-from-right {
        from { opacity: 0; transform: translateX(20px); }
        to { opacity: 1; transform: translateX(0); }
    }
    @keyframes fade-out-to-left {
        from { opacity: 1; transform: translateX(0); }
        to { opacity: 0; transform: translateX(-20px); }
    }
    html.astro-view-transitions::view-transition-old(root) {
        animation: 300ms cubic-bezier(0.4, 0, 0.2, 1) both fade-out-to-left;
    }
    html.astro-view-transitions::view-transition-new(root) {
        animation: 500ms cubic-bezier(0.4, 0, 0.2, 1) both fade-in-from-right;
    }
    */
    ```
-   **HTML Structure Sketch:**
    ```html
    <!-- For simple JS-driven fade -->
    <body class="PageTransitionWrapper PageTransitionWrapper--active">
        <!-- All page content here -->
    </body>

    <!-- For Astro View Transitions, no wrapper needed, just ensure data-astro-view-transitions is on <html> -->
    ```
-   **Responsive Behavior:** N/A.
-   **Animation/Interaction:**
    -   **Fade In/Out:** A simple opacity change (`opacity-0` to `opacity-100`).
    -   **Astro View Transitions:** Offers more sophisticated (and built-in) browser-level transitions, potentially including elements moving. The design system prefers a "simple, quick cross-fade" for pages, so `fade-in-from-right` and `fade-out-to-left` are good starting points.
-   **Variations:**

    1.  **Simple Fade:** `opacity` transition.
    2.  **Fade + Slight Slide (Astro VT):** Using `fade-in-from-right` and `fade-out-to-left` as defined above.
    3.  *(Other complex animations are not recommended per design system guidance)*

### Scroll-Reveal Animation Classes

-   **Purpose:** Applies subtle entrance animations to elements as they enter the viewport, adding polish and guiding attention. Requires a JavaScript Intersection Observer.
-   **Tailwind/CSS Classes:**
    ```css
    .reveal-on-scroll {
        @apply opacity-0 transform translate-y-4 transition-all duration-700 ease-out;
    }
    .reveal-on-scroll.is-visible {
        @apply opacity-100 translate-y-0;
    }
    .reveal-on-scroll--delay {
        @apply transition-delay-150; /* Delay of 150ms */
    }
    .reveal-on-scroll--delay-fast {
        @apply transition-delay-75; /* Delay of 75ms */
    }
    /* Add more delays if needed, e.g., transition-delay-300 */
    ```
-   **HTML Structure Sketch:**
    ```html
    <h2 class="text-4xl reveal-on-scroll">Our Vision</h2>
    <p class="text-lg reveal-on-scroll reveal-on-scroll--delay">A paragraph that appears slightly after the heading.</p>
    <div class="Card reveal-on-scroll reveal-on-scroll--delay-fast">...</div>
    ```
-   **Responsive Behavior:** N/A.
-   **Animation/Interaction:**
    -   JavaScript adds the `is-visible` class when the element enters the viewport, triggering the CSS transition.
-   **Variations:**

    1.  **Fade Up (Default):** `opacity-0 translate-y-4` to `opacity-100 translate-y-0`.
    2.  **Fade Right:** `opacity-0 translate-x-4` to `opacity-100 translate-x-0`.
    3.  **Fade Left:** `opacity-0 -translate-x-4` to `opacity-100 -translate-x-0`.
        -   **Usage:** Replace `translate-y-4` with desired `translate-x` or `-translate-x` in `.reveal-on-scroll` class (or create specific utility classes for each direction).

### Responsive Image/Video Container

-   **Purpose:** Ensures media (images, iframes for video) maintains its aspect ratio and scales correctly across different screen sizes.
-   **Tailwind/CSS Classes:**
    ```css
    .ResponsiveMediaContainer {
        @apply relative w-full overflow-hidden;
    }
    .ResponsiveMediaContainer--16x9 {
        padding-top: 56.25%; /* 9 / 16 * 100 */
    }
    .ResponsiveMediaContainer--4x3 {
        padding-top: 75%; /* 3 / 4 * 100 */
    }
    .ResponsiveMediaContainer--1x1 {
        padding-top: 100%; /* 1 / 1 * 100 */
    }
    .ResponsiveMediaContainer__content {
        @apply absolute top-0 left-0 w-full h-full object-cover;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <div class="ResponsiveMediaContainer ResponsiveMediaContainer--16x9">
      <img src="/your-image.jpg" alt="Description" class="ResponsiveMediaContainer__content" />
      <!-- Or for video: -->
      <iframe src="https://www.youtube.com/embed/..." frameborder="0" allowfullscreen class="ResponsiveMediaContainer__content"></iframe>
    </div>
    ```
-   **Responsive Behavior:** The `padding-top` trick makes the container maintain its aspect ratio, and the absolute-positioned content fills it.
-   **Animation/Interaction:** None directly on the container.
-   **Variations:**

    1.  **16:9 Aspect Ratio:** `ResponsiveMediaContainer--16x9` (common for videos).
    2.  **4:3 Aspect Ratio:** `ResponsiveMediaContainer--4x3` (traditional image format).
    3.  **1:1 Aspect Ratio (Square):** `ResponsiveMediaContainer--1x1` (for avatars, small graphics).

### Gradient Overlay Mixin

-   **Purpose:** Creates subtle, branded gradient overlays, especially useful over images or as abstract background elements.
-   **Tailwind/CSS Classes:**
    ```css
    .GradientOverlay--primary-dark {
        @apply bg-gradient-to-t from-primary-800 to-transparent opacity-70;
    }
    .GradientOverlay--primary-full {
        @apply bg-gradient-to-br from-primary-600 to-primary-900 opacity-60;
    }
    .GradientOverlay--accent-subtle {
        @apply bg-gradient-to-tr from-accent-500/20 via-transparent to-primary-600/20;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <div class="relative w-full h-64">
      <img src="/background-image.jpg" alt="Background" class="absolute inset-0 w-full h-full object-cover" />
      <div class="absolute inset-0 GradientOverlay--primary-dark"></div>
      <div class="relative z-10 p-8 text-surface-50">
        <!-- Content over the gradient -->
        <h2 class="text-3xl font-bold">Content Over Image</h2>
      </div>
    </div>
    ```
-   **Responsive Behavior:** N/A. `absolute inset-0` ensures it covers the parent.
-   **Animation/Interaction:** None.
-   **Variations:**

    1.  **Primary Dark Overlay:** `GradientOverlay--primary-dark` (from dark navy at bottom to transparent at top, common for text over images).
    2.  **Primary Full Overlay:** `GradientOverlay--primary-full` (a stronger, encompassing gradient for more abstract backdrops).
    3.  **Accent Subtle Diagonal:** `GradientOverlay--accent-subtle` (a very light, diagonal gradient using accent and primary colors, for decorative background elements).

### Badge/Tag/Chip Style

-   **Purpose:** Small, concise labels for categorization, status, or emphasis.
-   **Tailwind/CSS Classes:**
    ```css
    .Badge {
        @apply inline-flex items-center px-3 py-1 rounded-full text-xs font-medium font-inter;
    }
    .Badge--primary {
        @apply bg-primary-100 text-primary-800;
    }
    .Badge--accent {
        @apply bg-accent-100 text-accent-800;
    }
    .Badge--outline {
        @apply border border-primary-600 text-primary-600;
    }
    .Badge--success {
        @apply bg-success/10 text-success; /* Use Tailwind's opacity syntax */
    }
    .Badge--error {
        @apply bg-error/10 text-error;
    }
    ```
-   **HTML Structure Sketch:**
    ```html
    <span class="Badge Badge--primary">IT Services</span>
    <span class="Badge Badge--accent">New!</span>
    <span class="Badge Badge--success">Live</span>
    ```
-   **Responsive Behavior:** N/A.
-   **Animation/Interaction:** None.
-   **Variations:**

    1.  **Primary (Subtle):** `Badge--primary` (Light navy background, dark navy text).
    2.  **Accent (Subtle):** `Badge--accent` (Light orange background, dark orange text).
    3.  **Outline:** `Badge--outline` (Navy border, navy text, transparent background). Also `Badge--success`, `Badge--error` for semantic feedback.

---
```