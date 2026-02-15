```markdown
---
type: config
subtype: design-system
title: Design System
---

This design system translates the brand and design direction for Wimmer EDV into a set of rules and guidelines for the AI builder. It is structured in two parts:

1.  **Tokens:** Non-negotiable, exact values that ensure brand consistency. The builder **MUST** adhere to these.
2.  **Creative Direction:** Guiding principles that inspire creative choices while maintaining the core brand feel. The builder should use these to inform layouts and interactions.

---

# PART 1: TOKENS (The Builder MUST Use These)

## Colors

The color palette is designed to communicate **trust, stability, and intelligent precision**. The deep navy blue serves as the authoritative foundation, the off-white provides a clean, premium canvas, and the sharp orange is used intentionally to guide user action and highlight innovation.

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    colors: {
      primary: {
        50: '#E6EAF0',
        100: '#BFCADD',
        200: '#99ABCB',
        300: '#728DB8',
        400: '#4C6EA6',
        500: '#264F93',
        600: '#0A2A5B', // Base
        700: '#082249',
        800: '#061937',
        900: '#041125',
        950: '#020813',
      },
      accent: {
        50: '#FFF5EB',
        100: '#FEE6D0',
        200: '#FCCDA2',
        300: '#FBC48B',
        400: '#FAAC5E',
        500: '#FD7E14', // Base
        600: '#E47112',
        700: '#B1580E',
        800: '#89440B',
        900: '#603008',
        950: '#432205',
      },
      surface: {
        50: '#F8F9FA',   // Canvas Base (Off-white)
        100: '#F1F3F5',
        200: '#E9ECEF',  // Borders, Dividers (Light Grey)
        300: '#DEE2E6',
        400: '#CED4DA',
        500: '#ADB5BD',
        600: '#868E96',
        700: '#495057',
        800: '#343A40',  // Body Text Base (Charcoal)
        900: '#212529',
        950: '#131517',
      },
      // transparent, inherit, current, black, white are available by default
    },
  },
};
```

### Semantic Colors
Used for status indicators, alerts, and notifications.

-   **Success:** `#198754` (A confident, clear green)
-   **Warning:** `#FFC107` (A noticeable but not alarming amber)
-   **Error:** `#DC3545` (An unambiguous, serious red)

## Typography

The typographic system is built on a clear hierarchy to project confidence and ensure effortless readability.

-   **Heading Font:** **Poppins**
    -   **Reasoning:** Its geometric, stable letterforms provide an authoritative and modern voice for headlines. It feels structured and confident, perfectly matching the "precision" vibe.
-   **Body Font:** **Inter**
    -   **Reasoning:** A hyper-legible sans-serif designed specifically for UI and screen reading. It pairs beautifully with Poppins, ensuring that all content, from paragraphs to button labels, is clear and accessible.

### Font Scale & Line Heights

```css
/* Example CSS, to be implemented with Tailwind classes */
.text-xs   { font-size: 12px; line-height: 1.5; }
.text-sm   { font-size: 14px; line-height: 1.5; }
.text-base { font-size: 16px; line-height: 1.625; } /* Body */
.text-lg   { font-size: 18px; line-height: 1.625; }
.text-xl   { font-size: 20px; line-height: 1.5; }
.text-2xl  { font-size: 24px; line-height: 1.4; }
.text-3xl  { font-size: 32px; line-height: 1.3; } /* H3 */
.text-4xl  { font-size: 40px; line-height: 1.2; } /* H2 */
.text-5xl  { font-size: 48px; line-height: 1.1; } /* H1 */
.text-6xl  { font-size: 60px; line-height: 1.1; } /* Hero Headline */
```

### Font Weight Usage

-   **Regular (400):** Body copy (`<p>`, `<li>`), labels, and general UI text.
-   **Medium (500):** Sub-headings, navigation links, button text. Provides emphasis without the full weight of bold.
-   **SemiBold (600):** H2, H3, and key callouts. The primary weight for impactful headlines.
-   **Bold (700):** H1 / Hero headlines. Use sparingly for maximum impact.

## Spacing

Generous spacing is critical to the clean, structured, and premium feel.

-   **Section Vertical Padding:** Generous. Use `py-24` (96px) to `py-32` (128px) between major content sections.
-   **Content Max-Width:** `1280px` (Tailwind `max-w-7xl`).
-   **Container Horizontal Padding:** `px-6` (24px) on mobile, `px-8` (32px) on larger screens.

## Shapes

Shapes should be clean, precise, and understated.

-   **Border Radius:** Use minimal rounding to maintain a crisp, professional look.
    -   `rounded-lg` (8px): Default for primary buttons and content cards.
    -   `rounded-xl` (12px): For larger containers or image frames.
    -   `rounded-full`: Only for avatars or circular icons.
    -   `rounded-none`: For full-bleed hero sections or sharp-edged elements.
-   **Shadow Style:** Subtle and diffuse. Use shadows to add depth and lift interactive elements, not for decoration.
    -   **Default:** `shadow-md`.
    -   **On Hover:** `shadow-lg` or `shadow-xl`.

---

# PART 2: CREATIVE DIRECTION (Inspire the Builder)

## Visual Personality

**Precise, Authoritative, and Trustworthy.**

Every element should feel intentional and well-crafted. The design is confident but not arrogant; it's the digital equivalent of a bespoke suit or a high-end mechanical watch. It communicates serious, enterprise-grade expertise that customers can rely on.

## Animation & Motion Language

Motion should be **subtle, smooth, and purposeful**. It serves to guide the user and add a layer of polish, never to distract.

-   **Personality:** Calm, confident, and fluid.
-   **Page Transitions:** A simple, quick cross-fade (`opacity`).
-   **Scroll Animations:** A gentle fade-up and slight upward translation for sections and cards as they enter the viewport.
-   **Hover Effects:**
    -   **Cards:** A subtle lift (`transform: translateY(-4px)`) combined with a transition to a larger shadow (`shadow-xl`).
    -   **Buttons:** A slight scale-up (`transform: scale(1.03)`) or a subtle glow/brighter background.
    -   **Links:** A simple color shift to `accent-500` or an animated underline.
-   **Speed:** Smooth and deliberate, around **300-400ms**.
-   **Easing:** `ease-in-out` for an elegant, polished feel.

### Reusable Examples:

-   **Card Hover:** `transition-all duration-300 ease-in-out hover:shadow-xl hover:-translate-y-1`
-   **Button Hover:** `transition-transform duration-200 ease-in-out hover:scale-105`
-   **Link Underline:** Use background gradients for a `[text-decoration-skip-ink:none]` style animated underline effect on hover.

## Layout Philosophy

The layout is the backbone of our visual identity: ordered, logical, and breathable.

-   **Whitespace:** Generous and non-negotiable. It is an active element that creates focus and a premium feel.
-   **Grid Rhythm:** A strict 12-column grid should be the foundation for all primary page layouts to ensure structure and alignment.
-   **Image Treatment:**
    -   **Abstract Visuals:** Often used as full-width, low-opacity backgrounds with subtle animations. Can also be contained within grid elements.
    -   **Portraits:** Cleanly framed within cards or grid columns, never full-bleed.
-   **Section Rhythm:** Alternate section backgrounds between `surface-50` (off-white) and `surface-100` (very light grey) to create subtle visual separation without heavy dividers. Use a thin `surface-200` border where necessary.

## Photography & Image Style

The style is defined by conceptual abstraction and professional polish. **Generic stock photography is forbidden.**

-   **Primary Visuals:** **Abstract graphics and data visualizations.** These should be clean, sophisticated representations of networks, data flows, or architectural structures using brand colors. Think thin lines, nodes, and subtle gradients.
-   **People:** When team members are shown, use high-quality, professional portraits against a neutral (`surface-100` or `surface-200`) background. The tone should be confident, professional, and approachable.
-   **Color Treatment:** Imagery should feel integrated. Use duotone overlays with `primary-600` or muted color palettes that don't clash with the UI.

## Inspiration References

-   **Stripe (stripe.com):** Emulate their masterful use of clean typography, structured layouts, and subtle, meaningful animations. Their component design is a benchmark for clarity and polish.
-   **Bain & Company (bain.com):** Reference their use of a strong grid, authoritative typography, and generous whitespace to convey expertise and confidence.
-   **Linear (linear.app):** Observe their impeccable execution of a dark theme (using our `primary` shades as a base), precise component design, and subtle gradient accents.

## Do's and Don'ts

### DO...
-   **DO** adhere strictly to the grid to maintain order and structure.
-   **DO** prioritize typographic hierarchy and readability above all else.
-   **DO** use the `accent-500` orange with clear intent for primary calls-to-action.
-   **DO** use generous whitespace to let content breathe and guide the user's eye.
-   **DO** use abstract graphics to visually communicate complex IT concepts.

### DON'T...
-   **DON'T** use cheesy, generic stock photos of people at computers.
-   **DON'T** use flashy or distracting animations. Motion must have a purpose.
-   **DON'T** use gradients other than very subtle, abstract background elements.
-   **DON'T** introduce new colors or fonts. Adhere to the tokens.
-   **DON'T** create cluttered layouts. When in doubt, add more space.
```