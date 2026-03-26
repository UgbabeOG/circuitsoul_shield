# Design System Specification: The Guardian’s Lens

## 1. Overview & Creative North Star
This design system is built to transform complex security data into a calm, authoritative experience. We are moving away from the "cluttered dashboard" trope of the early 2010s and toward a **Creative North Star: The Digital Curator.**

The Digital Curator approach treats every piece of data as a high-end editorial insight. We reject the rigid, "boxed-in" feeling of traditional SaaS. Instead, we use **intentional asymmetry**—offsetting headers from their data columns—and **tonal depth** to guide the eye. By breaking the grid with overlapping status indicators and high-contrast typography scales, we create a UI that feels less like a spreadsheet and more like a premium security command center. It is secure, reliable, and sophisticated.

---

## 2. Colors: Tonal Architecture
Color in this system is not just decorative; it is functional infrastructure. We use a palette of deep, trustworthy blues (`primary`) balanced by high-signal security greens (`secondary`) and urgent alerts (`tertiary`/`error`).

### The "No-Line" Rule
Standard 1px borders are strictly prohibited for sectioning. They create visual noise and "trap" data. Boundaries must be defined through **Background Color Shifts**. For example, a `surface-container-low` section should sit directly on a `surface` background to define its territory.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack of materials. Use the `surface-container` tiers to create "nested" depth:
- **Base Layer:** `surface` (#f4faff)
- **Primary Layout Sections:** `surface-container-low` (#e9f6fd)
- **Interactive Widgets/Cards:** `surface-container-lowest` (#ffffff)
- **Active/Hover States:** `surface-container-high` (#ddeaf2)

### The "Glass & Gradient" Rule
To elevate the experience, use **Glassmorphism** for floating elements (like dropdowns or hovering status modals). Apply `surface-variant` at 60% opacity with a `20px` backdrop-blur. 
For primary CTAs and high-level status hero cards, use a subtle linear gradient:
*Direction: 135deg | From: `primary` (#003178) | To: `primary_container` (#0d47a1).*

---

## 3. Typography: The Editorial Edge
We utilize a dual-font strategy to balance character with extreme readability.

*   **Display & Headlines (Manrope):** This is our "Authority" typeface. Its geometric yet approachable curves provide a modern, premium feel. Use `display-lg` for high-level security scores to make them feel like a statement, not just a number.
*   **Body & Labels (Inter):** Our "Utility" typeface. Inter is used for all data-heavy views. Its tall x-height ensures that even `label-sm` (#0.6875rem) remains legible during high-stress security audits.

**Hierarchy Tip:** Always pair a `headline-sm` in `on_surface` with a `label-md` in `outline` to create a clear "Title / Metadata" relationship that feels intentional and curated.

---

## 4. Elevation & Depth: Tonal Layering
Traditional drop shadows are often too "heavy" for a professional security platform. We use **Tonal Layering** to convey hierarchy.

*   **The Layering Principle:** Place a `surface-container-lowest` card on a `surface-container-low` background. The contrast between white and the soft blue-tinted grey creates a natural "lift" without a single shadow.
*   **Ambient Shadows:** If a card must float (e.g., a dragged widget), use a "Security Aura":
    *   `box-shadow: 0 12px 32px -4px rgba(17, 29, 35, 0.06);` (Using a 6% tint of `on_surface`).
*   **The Ghost Border:** If a boundary is required for accessibility (e.g., input fields), use a "Ghost Border": `outline_variant` at **15% opacity**. Never use 100% opaque borders.

---

## 5. Components: Precision Primitives

### Buttons
*   **Primary:** Solid `primary` background with `on_primary` text. Use `rounded-md` (0.375rem). Use the Gradient Rule for a subtle 5% top-to-bottom shift.
*   **Secondary:** `surface-container-highest` background with `on_surface` text. No border.
*   **Tertiary/Ghost:** `on_surface` text with no background. On hover, apply a 4% `surface-tint`.

### Status Indicators (Chips)
*   **Safe State:** `secondary_fixed` background with `on_secondary_container` text.
*   **Warning State:** `tertiary_fixed` background with `on_tertiary_fixed_variant` text.
*   **Critical State:** `error_container` background with `on_error_container` text.
*   *Note: Chips must use `rounded-full` to contrast against the `rounded-md` cards.*

### Cards & Lists
*   **Forbid Divider Lines.** To separate list items, use vertical whitespace (Spacing `4` or `5`) or a alternating `surface-container-low` background on every second item.
*   **Interactive State:** On hover, a card should shift from `surface-container-lowest` to `surface-bright` and gain an Ambient Shadow.

### Dashboard Widgets (The "Curated Widget")
Widgets should utilize **Asymmetric Padding**. Give the top-left title more breathing room (Spacing `8`) than the data within the widget (Spacing `4`). This creates a sophisticated, unbalanced look that feels "designed" rather than "generated."

---

## 6. Do’s and Don’ts

### Do
*   **DO** use whitespace as a separator. If you think you need a line, try adding `1.1rem` (Spacing `5`) of empty space instead.
*   **DO** use `secondary` (Green) sparingly. It should represent a "clean bill of health," not just an accent color.
*   **DO** utilize `surface-container-highest` for "empty states" to make the interface feel full even when data is missing.

### Don’t
*   **DON'T** use pure black (#000000). Always use `on_surface` (#111d23) to maintain the deep blue tonal harmony.
*   **DON'T** use `rounded-none`. Security should feel approachable; sharp corners feel hostile. Stick to the `md` (0.375rem) or `lg` (0.5rem) scale.
*   **DON'T** clutter the navigation. Use the `0.1rem` (Spacing `0.5`) "Ghost Border" to subtly separate nav items if necessary, but prefer tonal shifts.

---

## 7. Spacing Logic
The spacing scale is built on a tight `0.2rem` base to allow for high-density data views without sacrificing the "Editorial" feel.
*   **Section Gaps:** Use `16` (3.5rem) or `20` (4.5rem).
*   **Component Padding:** Use `4` (0.9rem) for standard containers.
*   **Label-to-Value Gap:** Use `1.5` (0.3rem) to keep data clusters tight and readable.