# Mission Control: Design System Specification

## 1. Overview & Creative North Star

### Creative North Star: "The Silent Sentinel"
This design system is engineered for the high-stakes environment of robot mission control. Unlike consumer apps that compete for attention, this system embodies **The Silent Sentinel**: an invisible, authoritative partner that recedes when operations are normal and commands absolute focus when anomalies occur.

We move beyond the "Generic SaaS Dashboard" by adopting a **High-Density HMI (Human-Machine Interface)** aesthetic. The design breaks the traditional grid through **intentional asymmetry**—placing critical telemetry in high-contrast "Data Monoliths" while secondary controls live in muted, nested layers. We replace decorative elements with functional precision, ensuring that every pixel serves the operator's situational awareness.

---

## 2. Colors & Tonal Architecture

Our palette is rooted in a deep-space slate (`surface: #0b1326`) to reduce eye strain during long shifts. 

### The "No-Line" Rule
**Borders are a failure of contrast.** Designers are prohibited from using 1px solid borders to define primary sections. Instead, use background color shifts:
- A `surface-container-low` (#131b2e) sidebar sitting against a `surface` (#0b1326) background.
- Use the `spacing-scale.px` only for internal component logic, never for layout containment.

### Surface Hierarchy & Nesting
Treat the UI as a physical stack of technical glass. 
1.  **Base Layer**: `surface` (#0b1326) – The mission floor.
2.  **Section Layer**: `surface-container-low` (#131b2e) – Logical groupings.
3.  **Component Layer**: `surface-container` (#171f33) – Individual cards/modules.
4.  **Interaction Layer**: `surface-bright` (#31394d) – Active states and hover-focus.

### Signature Textures: The LED Glow
While we avoid decorative gradients, we use **Functional Chromatics**. For status indicators, use a subtle radial gradient on `secondary` (#4edea3) or `error` (#ffb4ab) to mimic a physical LED diode, providing a "real-product" feel that feels tactile and urgent.

---

## 3. Typography

The typography system prioritizes **Numerical Readability** and **Information Density**. We use **Inter** as our primary typeface for its neutral, technical clarity.

| Level | Token | Size | Weight | Use Case |
| :--- | :--- | :--- | :--- | :--- |
| **Display** | `display-md` | 2.75rem | 600 | Critical Telemetry (e.g., Robot Battery %) |
| **Headline** | `headline-sm` | 1.5rem | 500 | Main Section Headers (设备概览) |
| **Title** | `title-sm` | 1rem | 600 | Card Titles / Group Labels |
| **Body** | `body-md` | 0.875rem | 400 | Standard Labels & Metadata |
| **Label** | `label-sm` | 0.6875rem | 700 | Status Badges / Monospaced Data |

**Editorial Note**: In Chinese (Simplified) typesetting, increase `line-height` by 15% compared to English defaults to ensure legibility of complex glyphs within dense data tables.

---

## 4. Elevation & Depth

We eschew traditional drop shadows for **Tonal Layering**.

*   **The Layering Principle**: Depth is achieved by "stacking" the `surface-container` tiers. A `surface-container-highest` (#2d3449) element placed on a `surface-container-low` (#131b2e) background creates a natural lift.
*   **Ambient Shadows**: Floating modals must use a tinted shadow: `shadow-color: rgba(218, 226, 253, 0.06)` with a 40px blur. This mimics ambient light bouncing off the UI rather than a "pasted" black shadow.
*   **The "Ghost Border"**: For high-density tables where separation is critical, use `outline-variant` (#424656) at **20% opacity**. It should be felt, not seen.
*   **Glassmorphism**: Use `surface-container/80` with a `backdrop-blur: 12px` for persistent floating controls (e.g., Map Zoom Tools) to maintain a sense of environmental context.

---

## 5. Components

### 5.1 Buttons
*   **Primary**: `primary-container` (#0066ff) background with `on-primary-container` (#f8f7ff) text. No border. Radius: `md` (0.375rem).
*   **Secondary/Ghost**: Background: `transparent`. Border: `Ghost Border` (outline-variant @ 20%). 
*   **Tertiary**: Text only in `primary` (#b3c5ff). Use for low-priority actions like "View Logs" (查看日志).

### 5.2 Status Indicators (The "LED")
Status chips must include a 6px circular "LED" icon.
*   **Active**: `secondary` (#4edea3) with a 4px outer glow of the same color.
*   **Error**: `error` (#ffb4ab) with a steady pulse animation.

### 5.3 Data-Dense Tables
*   **Constraint**: Forbid divider lines. 
*   **Separation**: Use `spacing-scale.2.5` (0.5rem) vertical padding and zebra-striping using `surface-container-low` on even rows.
*   **Typography**: Numerical data must use tabular lining (tnum) to ensure columns align perfectly for rapid scanning.

### 5.4 Mission Control Specifics
*   **Robot Telemetry Card**: Use a `surface-container-highest` background for the header to anchor the robot ID, and `surface-container` for the body.
*   **Command Input**: Text inputs must use `surface-container-lowest` (#060e20) for the field to create an "etched" look, signifying a place where data is "poured" in.

---

## 6. Do’s and Don'ts

### Do
*   **Do** use `spacing-scale.1` (0.2rem) for tight technical groupings (e.g., coordinates).
*   **Do** use `tertiary` (#ffb95f) for maintenance/warning states—it is the only "warm" color in this cold system.
*   **Do** treat white space as a structural element. A gap of `spacing-scale.16` (3.5rem) is more effective than a line.

### Don't
*   **Don't** use pure black (#000000). Our darkest color is `surface-container-lowest` (#060e20).
*   **Don't** use 100% opaque `outline` colors for borders; it breaks the HMI "glass" illusion.
*   **Don't** use rounded corners larger than `xl` (0.75rem). This is a professional tool, not a consumer social app. Keep it architectural.