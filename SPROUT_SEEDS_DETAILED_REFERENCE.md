# Sprout Seeds Design System - Complete Visual & Component Reference

**Design System:** https://seeds.sproutsocial.com/
**Last Updated:** February 1, 2026
**Document Purpose:** Complete specification of visual elements, typography, color palette, and design tokens

---

## TABLE OF CONTENTS

1. [Typography System](#typography-system)
2. [Color Palette](#color-palette)
3. [Spacing & Layout System](#spacing--layout-system)
4. [Border & Radius System](#border--radius-system)
5. [Elevation & Shadows](#elevation--shadows)
6. [Motion & Animation](#motion--animation)
7. [Components Overview](#components-overview)
8. [Visual Elements](#visual-elements)
9. [Design Tokens](#design-tokens)
10. [Implementation Checklist](#implementation-checklist)

---

## TYPOGRAPHY SYSTEM

### Brand Typefaces

#### Primary: Roboto Serif
- **Usage:** Headlines, premium brand experiences, display text
- **Characteristics:**
  - Modern serif with minimal design
  - Comfortable paired with sans-serif
  - Reduced reader fatigue
  - Distinctive curves and terminals
  - Cross between traditional serif and slab serif
- **Font Weights Available:** Regular, Bold
- **Design Philosophy:** Conveying modern sophistication and trustworthiness

#### Secondary: Proxima Nova
- **Usage:** Body copy, UI labels, buttons, supporting content
- **Characteristics:**
  - Geometric sans-serif
  - Excellent screen readability
  - Clean and professional
  - Strong international support
- **Font Weights Available:** Regular, Bold, SemiBold
- **Fallback Stack:** -apple-system, BlinkMacSystemFont, Segoe UI

### Type Hierarchy & Scales

#### Text Hierarchy Standards

| Element Type | Font | Size | Weight | Case | Usage |
|---|---|---|---|---|---|
| H1 Headlines | Roboto Serif | Large (2.5rem+) | Regular | Sentence case | Page/section headlines |
| H2 Subheadings | Roboto Serif | 1.875rem | Regular | Sentence case | Major section breaks |
| H3 Sections | Proxima Nova | 1.5rem | Bold | Sentence case | Sub-sections |
| Body Text | Proxima Nova | 1rem (16px) | Regular | Sentence case | Primary content |
| Small Text | Proxima Nova | 0.875rem (14px) | Regular | Sentence case | Secondary content, labels |
| Micro Text | Proxima Nova | 0.75rem (12px) | Regular | Sentence case | Captions, helper text |
| Labels | Proxima Nova | 0.875rem-1rem | Bold | Title Case | Form labels, buttons, UI |
| Numbers/Data | Proxima Nova | 1.125rem-1.5rem | Bold | Numeric | Stats, metrics, counters |

#### Type Setting Rules

**Global Standards:**
- **Case Conventions:** Sentence case for headlines/body, Title Case for labels/buttons
- **Punctuation:** No periods at end of single headlines
- **International Support:** Proxima Nova for technical consistency across locales
- **Line Height:** 1.5x for body (24px on 16px base), 1.2x for headlines
- **Letter Spacing:** Default browser, no custom adjustments for Roboto Serif

**Context-Specific Rules:**
- **Headlines:** One per section, sentence case, no period
- **Titles:** Title case, project/cover names
- **Labels:** Title case, bold weight, scannable
- **Buttons & Links:** Sentence case, consistent international standard
- **Form Helper Text:** Small, gray, clear description of field requirements

### Product Typography

#### Product Type Scale (Digital Interfaces)

**Desktop/Web:**
- Display Large: 2.5rem (40px) - Page titles
- Display: 2rem (32px) - Major headings
- Headline Large: 1.75rem (28px) - Section headers
- Headline: 1.5rem (24px) - Sub-sections
- Title Large: 1.25rem (20px) - Card/panel titles
- Title: 1.125rem (18px) - Secondary titles
- Body Large: 1rem (16px) - Primary body text
- Body: 0.9375rem (15px) - Default content
- Label Large: 0.875rem (14px) - UI labels, buttons
- Label: 0.8125rem (13px) - Secondary labels
- Small: 0.75rem (12px) - Captions, helper text
- Tiny: 0.625rem (10px) - Minimal labels

**Mobile Scaling:**
- Reduce headline sizes by 20-30% for viewport < 768px
- Maintain minimum 14px for readability
- Preserve line height ratios

---

## COLOR PALETTE

### Color System Structure

**5-Tier Hierarchy:**
1. **Foundational Colors** (5 colors) - Core semantic meanings
2. **Core Colors** (10 colors) - Primary UI colors
3. **Secondary Colors** (15+ colors) - Extended palette
4. **Color Gradients** - Smooth transitions
5. **Human Tones** - Skin tone diversity

### Foundational Colors

**Critical semantic colors used throughout the system:**

| Name | Purpose | Hex | RGB | Usage |
|------|---------|-----|-----|-------|
| **Blue** | Primary action, information | #0052CC | rgb(0, 82, 204) | Buttons, links, primary CTAs |
| **Green** | Success, positive states | #22C55E | rgb(34, 197, 94) | Success messages, confirmations |
| **Yellow** | Warning, caution | #FBBF24 | rgb(251, 191, 36) | Warning alerts, cautionary states |
| **Red** | Error, destructive | #EF4444 | rgb(239, 68, 68) | Errors, deletions, destructive actions |
| **Gray** | Neutral, disabled | #6B7280 | rgb(107, 114, 128) | Borders, text, disabled states |

### Core Colors (Extended)

**Primary Color Family - Blue:**
- Blue 100: #DBEAFE (very light, backgrounds)
- Blue 200: #BFDBFE (light, hover states)
- Blue 300: #93C5FD (medium-light)
- Blue 400: #60A5FA (medium)
- Blue 500: #3B82F6 (standard)
- Blue 600: #2563EB (darker)
- Blue 700: #1D4ED8 (dark)
- Blue 800: #1E40AF (very dark)
- Blue 900: #1E3A8A (darkest, text)

**Neutral Color Family - Gray:**
- Gray 50: #F9FAFB (nearly white, light backgrounds)
- Gray 100: #F3F4F6 (light background, hover)
- Gray 200: #E5E7EB (light border)
- Gray 300: #D1D5DB (border)
- Gray 400: #9CA3AF (secondary text)
- Gray 500: #6B7280 (primary neutral)
- Gray 600: #4B5563 (dark text)
- Gray 700: #374151 (darker text)
- Gray 800: #1F2937 (very dark text)
- Gray 900: #111827 (darkest, body text)

**Success Color Family - Green:**
- Green 50: #F0FDF4
- Green 100: #DCFCE7
- Green 200: #BBF7D0
- Green 500: #22C55E (standard)
- Green 600: #16A34A (darker)
- Green 700: #15803D (darkest)

**Warning Color Family - Yellow:**
- Yellow 50: #FFFBEB
- Yellow 100: #FEF3C7
- Yellow 200: #FDE68A
- Yellow 500: #FBBF24 (standard)
- Yellow 600: #F59E0B (darker)
- Yellow 700: #D97706 (darkest)

**Error Color Family - Red:**
- Red 50: #FEF2F2
- Red 100: #FEE2E2
- Red 200: #FECACA
- Red 500: #EF4444 (standard)
- Red 600: #DC2626 (darker)
- Red 700: #B91C1C (darkest)

### Secondary Colors (Accent Palette)

**Purple/Violet Family:**
- Purple 400: #A78BFA
- Purple 500: #8B5CF6
- Purple 600: #7C3AED

**Pink/Rose Family:**
- Pink 400: #F472B6
- Pink 500: #EC4899
- Pink 600: #DB2777

**Cyan/Teal Family:**
- Cyan 400: #22D3EE
- Cyan 500: #06B6D4
- Teal 500: #14B8A6

**Orange Family:**
- Orange 400: #FB923C
- Orange 500: #F97316
- Orange 600: #EA580C

### Human Tones (Skin Tone Diversity)

**6-Tone Diversity Palette (Fitzpatrick Scale):**
- Tone 1: #FDBCB4 (Lightest)
- Tone 2: #F7B8A5
- Tone 3: #E8A591
- Tone 4: #D5956E
- Tone 5: #A67C52
- Tone 6: #6A4A3A (Darkest)

**Use Case:** Avatar backgrounds, identity visuals, inclusive representation

### Color Semantics in UI

**Text Colors:**
- Primary Text: Gray 900 (#111827)
- Secondary Text: Gray 600 (#4B5563)
- Tertiary Text: Gray 400 (#9CA3AF)
- Disabled Text: Gray 400 (#9CA3AF) with reduced opacity
- Link Text: Blue 600 (#2563EB)
- Link Hover: Blue 700 (#1D4ED8)

**Background Colors:**
- Primary Background: White (#FFFFFF)
- Secondary Background: Gray 50 (#F9FAFB)
- Tertiary Background: Gray 100 (#F3F4F6)
- Input Background: White (#FFFFFF) with Gray 200 border
- Button Background (Primary): Blue 600 (#2563EB)
- Button Background (Secondary): Gray 100 (#F3F4F6)

**State Colors:**
- Hover: 10% darker or lighter depending on base
- Active: 20% darker or lighter
- Disabled: 50% opacity reduction
- Focus: Full saturation with high contrast outline

**Accessibility Contrast Ratios:**
- Text on Background: Minimum 4.5:1 (WCAG AA)
- Large Text: Minimum 3:1 (WCAG AA)
- UI Components: Minimum 3:1 (WCAG AA)

---

## SPACING & LAYOUT SYSTEM

### Spacing Scale

**8px Grid System (+ Half-Sizes):**

| Token | Size | Usage | Example |
|-------|------|-------|---------|
| Size 0 | 0px | None | Negative space |
| Size 100 | 2px | Micro spacing | Icon padding |
| Size 200 | 4px | Very small | Inner icon spacing |
| Size 300 | 8px | **Standard base unit** | Default padding, gap |
| Size 350 | 12px | Between small & base | Button text-to-icon |
| Size 400 | 16px | **Primary spacing** | Component padding, margins |
| Size 450 | 24px | Large spacing | Card gaps, section breaks |
| Size 500 | 32px | Extra large | Container padding |
| Size 600 | 40px | **Base multiplier** | Component gaps |
| Size 700+ | 40px × n | Scaled spacing | 80px (×2), 120px (×3), etc. |

### Spacing Usage Guidelines

**Component-Level Spacing:**
- Input/Button padding: Size 400 (16px)
- Card padding: Size 500 (32px)
- List item gaps: Size 400 (16px)
- Grid gaps: Size 450 (24px)

**Page-Level Spacing:**
- Section margins: Size 600 (40px) to Size 700 (80px)
- Container gutters: Size 500 (32px) to Size 600 (40px)
- Vertical rhythm: Maintain consistent gaps for reading flow

**Responsive Adjustments:**
- Desktop: Full spacing scale applied
- Tablet: Reduce Size 600+ to Size 500 (32px)
- Mobile: Reduce to Size 400 (16px) minimum

### Flexbox & Grid

**Default Gap Values:**
- Flex gap: Size 300 (8px) to Size 400 (16px)
- Grid gap: Size 400 (16px) to Size 500 (32px)
- Flex direction row: Use Size 300/400
- Flex direction column: Use Size 400/500

**Grid System:**
- 12-column layout for desktop
- 6-column layout for tablet
- 1-column layout for mobile
- All columns equal width with consistent gutters (Size 500)

---

## BORDER & RADIUS SYSTEM

### Border Radius Values

**Three Primary Values (Semantic Intent):**

| Name | Value | Token | Usage | When |
|------|-------|-------|-------|------|
| **Outer** | 8px | `BORDER_RADIUS_600` | Container corners | Element is outermost |
| **Inner** | 6px | `BORDER_RADIUS_500` | Nested element corners | Element is contained within outer |
| **Pill** | 9999em | `BORDER_RADIUS_1000` | Fully rounded shape | Buttons, badges, avatars |

### Border Radius Philosophy

**Optical Compensation:**
- Outer containers use 8px
- Inner (nested) elements use 6px to prevent "bulging" visual illusion
- This maintains visual alignment when stacked

**Special Cases:**
- Checkbox: 4px exception (small component, needs square appearance)
- Avatar: Pill (9999em) for circular appearance
- Badge: Pill (9999em) for rounded pill style
- Button: Outer (8px) for consistency

### Border Width

**Standard Border Weight:**
- **1px solid** - Default border thickness (`BORDER_WIDTH_500`)
- Use: Input fields, cards, dividers, container outlines
- Color: Gray 200 (#E5E7EB) to Gray 300 (#D1D5DB)

**Semantic Border Colors:**
- **Default:** Gray 200 (#E5E7EB)
- **Focus:** Blue 500 (#3B82F6) - 2px
- **Error:** Red 500 (#EF4444)
- **Success:** Green 500 (#22C55E)
- **Hover:** Gray 300 (#D1D5DB)

---

## ELEVATION & SHADOWS

### Shadow System (Z-Axis Depth)

**4-Level Elevation Hierarchy:**

| Level | Y Offset | Blur | Token | Usage | Components |
|-------|----------|------|-------|-------|------------|
| **Reserved** | — | — | `ELEVATION_RESERVED` | Navigation layers | Left nav, top nav |
| **Level 400** | 16px | 32px | `ELEVATION_LEVEL_400` | High emphasis modals | Modal, Drawer, Tooltip |
| **Level 300** | 8px | 16px | `ELEVATION_LEVEL_300` | Medium interactive | Card (hover), Popout |
| **Level 100** | 2px | 4px | `ELEVATION_LEVEL_100` | Subtle hover states | Button hover, input focus |
| **Base** | 0px | 0px | — | Container surfaces | Cards, panels at rest |

### Shadow CSS Values

```css
/* Reserved Level - Global Navigation */
box-shadow: none; (on independent plane)

/* Elevation 400 - High Priority Overlays */
box-shadow: 0px 16px 32px rgba(0, 0, 0, 0.1);

/* Elevation 300 - Medium Interactive */
box-shadow: 0px 8px 16px rgba(0, 0, 0, 0.08);

/* Elevation 100 - Subtle Interaction */
box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.05);

/* Base - No Shadow */
box-shadow: none;
```

### Elevation Application Rules

**Reserved Level:**
- Main navigation (left sidebar)
- Top app bar
- Persistent UI chrome
- Should rarely be obstructed

**Level 400:**
- Primary modal overlays
- Drawer panels
- Floating tours
- Important temporary interruptions

**Level 300:**
- Card hover states (expressive style)
- Dropdown/popout menus
- Medium-sized interactive elements
- Tooltip containers

**Level 100:**
- Button hover states
- Input focus elevation
- Subtle interactive feedback
- Functional interactions

**Base:**
- Cards at rest
- Input fields (unfocused)
- Button default state
- Container elements

---

## MOTION & ANIMATION

### Animation Principles

**4 Core Principles:**

1. **Integrity**
   - Each frame must be as strong as the last
   - Maintain visual weight throughout transformation
   - Build anticipation, not just visual change

2. **Intentionality**
   - Objects must have motivation for movement
   - Never animate just for aesthetics
   - Every motion serves a purpose

3. **Consistency**
   - Elements operate within consistent physics
   - Physics don't need to be real-world
   - Establish and maintain animation rules

4. **Emotional Appeal**
   - Evoke emotional response through motion
   - Create surprise and delight
   - Use anthropomorphization when appropriate

### Easing Functions

**CSS Timing Functions:**

| Easing | Curve | CSS Value | Usage |
|--------|-------|-----------|-------|
| **Ease In** | Slow start, fast end | `cubic-bezier(.4, 0, .7, .2)` | Removing objects from screen |
| **Ease Out** | Fast start, slow end | `cubic-bezier(0, 0, .2, 1)` | Introducing objects to screen |
| **Ease In-Out** | Slow start & end, fast middle | `cubic-bezier(.4, 0, .2, 1)` | Moving objects within screen |

### Duration Tokens

**3-Level Duration System:**

| Duration | Time | Token | Usage |
|----------|------|-------|-------|
| **Fast** | 150ms (0.15s) | `MOTION_DURATION_FAST` | Small elements, short distances |
| **Medium** | 300ms (0.3s) | `MOTION_DURATION_MEDIUM` | Medium elements, medium distances |
| **Slow** | 600ms (0.6s) | `MOTION_DURATION_SLOW` | Large elements, long distances |

### Distance-Based Animation

**Distance Categories:**

| Distance | Viewport Coverage | Duration | Easing | Example |
|----------|------------------|----------|--------|---------|
| **Short** | ≤ 25% viewport width | Fast (150ms) | Ease In or Out | Alert slide-in, menu popup |
| **Medium** | 26-50% viewport width | Medium (300ms) | Ease In-Out | Card expansion, modal fade |
| **Long** | 51-100% viewport width | Slow (600ms) | Ease In-Out | Panel transition, page change |

### Fade Animations

**Fade Types:**

| Type | Duration | Easing | Usage |
|------|----------|--------|-------|
| **Fast Fade** | 150ms | Ease Out | Button hover, list item highlight |
| **Medium Fade** | 300ms | Ease In-Out | Card opacity change, modal appearance |
| **Slow Fade** | 600ms | Ease Out | Empty state appearance, page load |

### Animation Combinations (Combos)

**Recommended Combinations:**

1. **Fast Fade + Short Distance** (150ms)
   - Example: Alert message, small notifications
   - Motion: Slide in while fading
   - Best for: Quick feedback

2. **Medium Fade + Medium Distance** (300ms)
   - Example: Modal appearance, card expansion
   - Motion: Moderate slide with fade
   - Best for: Standard interactions

3. **Slow Fade + Long Distance** (600ms)
   - Example: Large panel transitions, page changes
   - Motion: Smooth sweep with fade
   - Best for: Major navigation

### Performance Considerations

**GPU-Accelerated Properties:**
- `transform` (translate, scale, rotate)
- `opacity`
- `filter`

**Avoid Animating:**
- `width`, `height`, `margin`, `padding` (use transform instead)
- `top`, `left`, `bottom`, `right` (use transform instead)
- `box-shadow` (expensive)
- `blur` filters (performance impact)

---

## COMPONENTS OVERVIEW

### Core Components (50+)

**Navigation:**
- Breadcrumb
- Tabs
- Menu (Single Select, Multi Select)
- Action Menu
- Nested Menu

**Forms & Input:**
- Input (text, email, password, etc.)
- Textarea
- Checkbox
- Radio
- Toggle/Switch
- Select
- Multi Select Menu
- Date Picker
- Token Input

**Buttons & Actions:**
- Button (6 appearance variants)
- Loader Button
- Segmented Control
- Icon Button

**Display:**
- Card
- Badge
- Banner
- Avatar
- Image
- Skeleton
- Spot Illustration

**Overlay & Dialog:**
- Modal V2 (with header, body, footer)
- Drawer
- Popout
- Tooltip

**Feedback:**
- Notification
- Toast
- Message
- Loader
- Empty State
- Indicator

**Data Display:**
- Table
- List
- DataList
- Chart Legend

**Layout:**
- Box (layout primitive)
- Container
- Stack
- Content Block

**Typography:**
- Text
- Label
- Keyboard Key
- Duration (time display)
- Numeral (number formatting)
- Visually Hidden

**Advanced:**
- Collapsible
- Accordion
- Rating
- Token (tag display)
- Character Counter

---

## VISUAL ELEMENTS

### Button Component Detailed Specification

**6 Appearance Variants:**

1. **Primary** 
   - Background: Blue 600 (#2563EB)
   - Text: White (#FFFFFF)
   - Border: None
   - Hover: Blue 700 (#1D4ED8)
   - Active: Blue 800 (#1E40AF)
   - Disabled: Gray 400 (#9CA3AF) with 50% opacity
   - Use: Primary call-to-action, form submission

2. **Secondary**
   - Background: Gray 100 (#F3F4F6)
   - Text: Gray 900 (#111827)
   - Border: Gray 300 (#D1D5DB)
   - Hover: Gray 200 (#E5E7EB)
   - Active: Gray 300 (#D1D5DB)
   - Use: Secondary actions, cancel buttons

3. **Destructive**
   - Background: Red 600 (#DC2626)
   - Text: White (#FFFFFF)
   - Border: None
   - Hover: Red 700 (#B91C1C)
   - Active: Red 800 (#7F1D1D)
   - Use: Delete, remove, dangerous actions

4. **Pill**
   - Background: Blue 600 (#2563EB)
   - Border Radius: 9999em (fully rounded)
   - Text: White (#FFFFFF)
   - Use: Chips, tags, specialized buttons

5. **Placeholder**
   - Background: Transparent
   - Text: Gray 600 (#4B5563)
   - Border: Gray 300 dashed (#D1D5DB)
   - Icon: Plus outline
   - Hover: Gray 100 (#F3F4F6)
   - Use: Add new item, create action

6. **Unstyled**
   - Background: None
   - Border: None
   - Text: Gray 900 (#111827)
   - Hover: Underline Gray 400 (#9CA3AF)
   - Use: Text-only actions, minimal UI

**Button Sizes:**
- **Small:** 32px height, 14px text
- **Default:** 40px height, 15px text
- **Large:** 48px height, 16px text

**Button States:**
- **Default:** Base appearance
- **Hover:** 10% darker/lighter
- **Active:** 20% change
- **Disabled:** 50% opacity, cursor: not-allowed
- **Focus:** 2px outline (Blue 500 for primary)
- **Loading:** Spinner icon, disabled state

**Button Content:**
- **Text Only:** Minimum 32px width
- **Icon + Text:** Icon (20px) + 8px gap + text
- **Icon Only:** 40x40px, requires aria-label
- **Full Width:** 100% of container

### Input Component Detailed Specification

**Input Appearances:**
1. **Primary** - Standard bordered input
   - Border: Gray 300 (#D1D5DB)
   - Background: White (#FFFFFF)
   - Focus: Blue 500 (#3B82F6) outline (2px)
   - Error: Red 500 (#EF4444) border

2. **Secondary** - Borderless input
   - Border: None
   - Background: Gray 100 (#F3F4F6)
   - Focus: Gray 200 (#E5E7EB) background
   - Requires placeholder for accessibility

**Input Types:**
- text (default)
- email
- password
- number
- date
- url
- search (includes clear button)
- tel

**Input States:**
- **Default:** Normal appearance
- **Hover:** Border Gray 400 (#9CA3AF)
- **Focus:** 2px Blue 500 outline, background white
- **Invalid:** Red 500 border, error message below
- **Warning:** Yellow 500 border, warning text below
- **Disabled:** Gray 300 border, 50% opacity, no interaction
- **Read-only:** Normal appearance, no cursor change

**Input Features:**
- Optional clear button (elemAfter)
- Optional icon/element before/after (16x16px)
- Character counter display
- Helper text (aria-describedby)
- Label association (required)
- Placeholder text (optional, but recommended for secondary)
- Maxlength enforcement

**Input Sizes:**
- **Small:** 32px height
- **Default:** 40px height
- **Large:** 48px height

### Card Component

**Card Types:**
1. **Standard Card**
   - Border: Gray 200 (#E5E7EB)
   - Background: White (#FFFFFF)
   - Radius: 8px (outer)
   - Padding: Size 500 (32px)

2. **Expressive Card**
   - Shadow: Elevation 300 (0px 8px 16px)
   - Hover shadow: Elevation 300
   - Background: White (#FFFFFF)
   - Radius: 8px (outer)

3. **Interactive Card**
   - Cursor: pointer
   - Hover: Background Gray 50 (#F9FAFB)
   - Hover shadow: Elevation 300
   - Focus: Blue 500 outline (2px)

**Card Content Areas:**
- Header (optional) - Top section with title/actions
- Media (optional) - Image or illustration area
- Body - Primary content area
- Footer (optional) - Actions or metadata

### Modal Component (V2)

**Structure:**
- Modal (root, manages state)
  - ModalHeader (title + subtitle)
  - ModalBody (scrollable content)
  - ModalFooter (action buttons)

**Modal Features:**
- Backdrop overlay (Dark gray, 40% opacity)
- Focus trap (keyboard navigation contained)
- Close button (floating rail)
- Draggable header (optional)
- Custom actions rail (optional)
- Responsive bottom sheet on mobile

**Modal Sizes:**
- Max width: 600px (standard)
- Max width: 800px (large content)
- Mobile: Full width - 16px margins (Size 400)

**Modal States:**
- **Uncontrolled:** modalTrigger manages open/close
- **Controlled:** open + onOpenChange props
- **Loading:** Loader inside footer, disabled buttons
- **Dragging:** Header changes cursor to grab

### Notification/Toast Component

**Toast Appearance:**
- Background: Gray 900 (#111827) or semantic color
- Text: White (#FFFFFF)
- Icon: Color-coded (Green for success, Red for error, etc.)
- Dismiss: Auto-close (4s default) + X button
- Animation: Slide in from right/top (fast)

**Toast Types:**
1. **Success** - Green 500 background
2. **Error** - Red 500 background
3. **Warning** - Yellow 500 background
4. **Info** - Blue 500 background

**Toast Placement:**
- Top-right (default)
- Top-center (optional)
- Bottom-right (optional)
- Stack upward when multiple

---

## DESIGN TOKENS

### Complete Token Reference

**Spacing Tokens (Sass/CSS):**
```
$Space-size--0: 0px;
$Space-size--100: 2px;
$Space-size--200: 4px;
$Space-size--300: 8px;
$Space-size--350: 12px;
$Space-size--400: 16px;
$Space-size--450: 24px;
$Space-size--500: 32px;
$Space-size--600: 40px;
```

**Border Tokens:**
```
$Border-radius--500: 6px (inner);
$Border-radius--600: 8px (outer);
$Border-radius--1000: 9999em (pill);
$Border-width--500: 1px;
```

**Elevation Tokens:**
```
$Elevation-level--100: 0px 2px 4px;
$Elevation-level--300: 0px 8px 16px;
$Elevation-level--400: 0px 16px 32px;
$Elevation-reserved: Independent plane;
```

**Motion Tokens:**
```
$Motion-duration--fast: 0.15s;
$Motion-duration--medium: 0.3s;
$Motion-duration--slow: 0.6s;

$Motion-ease--in: cubic-bezier(0.4, 0, 0.7, 0.2);
$Motion-ease--out: cubic-bezier(0, 0, 0.2, 1);
$Motion-ease--inout: cubic-bezier(0.4, 0, 0.2, 1);
```

**Color Tokens (Sample):**
```
$Color-blue--600: #2563EB;
$Color-red--500: #EF4444;
$Color-green--500: #22C55E;
$Color-gray--900: #111827;
$Color-neutral--100: #F3F4F6;
```

---

## IMPLEMENTATION CHECKLIST

### Phase 1: Foundation (Typography + Spacing)
- [ ] Import Roboto Serif + Proxima Nova fonts
- [ ] Set up CSS custom properties for all spacing tokens
- [ ] Apply global font stacks
- [ ] Define heading hierarchy (h1-h6)
- [ ] Create body text base styles

### Phase 2: Colors & States
- [ ] Define CSS variables for all 50+ colors
- [ ] Create semantic color maps (primary, success, error, etc.)
- [ ] Set up hover/active/disabled state colors
- [ ] Implement focus outline styles
- [ ] Test contrast ratios (minimum 4.5:1 for text)

### Phase 3: Components
- [ ] Build button component with 6 appearances
- [ ] Create input field with validation states
- [ ] Implement card component with variants
- [ ] Build modal with header/body/footer structure
- [ ] Create notification/toast system

### Phase 4: Advanced Features
- [ ] Implement animation tokens (durations, easing)
- [ ] Add elevation shadows to components
- [ ] Set up responsive spacing adjustments
- [ ] Create focus management for modals/dialogs
- [ ] Build accessible form patterns

### Phase 5: Refinement
- [ ] Test with real content at multiple viewport sizes
- [ ] Verify accessibility (keyboard nav, screen readers)
- [ ] Performance testing (animations, rendering)
- [ ] Cross-browser testing
- [ ] Document component usage patterns

### Phase 6: Documentation
- [ ] Create component library documentation
- [ ] Build design tokens reference guide
- [ ] Document brand guidelines
- [ ] Create code examples and recipes
- [ ] Establish maintenance processes

---

## NOTES FOR NOTES APP IMPLEMENTATION

### Priority Components for Notes App

**Must Have:**
1. Button (primary, secondary, destructive)
2. Input field (text input for title)
3. Textarea (note content)
4. Card (note list items)
5. Modal (confirmations)
6. Notification/Toast (success/error feedback)
7. Form Field (label + input + validation)

**Should Have:**
1. Badge (status tags)
2. Empty State (no notes message)
3. Loader (async operations)
4. Tabs (optional: organize notes)
5. Character Counter (for content limits)

**Nice to Have:**
1. Tooltip (help text)
2. Skeleton (loading states)
3. Collapsible (note categories)
4. Date Picker (created/updated dates)

### Responsive Considerations

**Mobile (< 768px):**
- Reduce heading sizes 20-30%
- Use Size 400 (16px) spacing throughout
- Stack cards in single column
- Use 100% width buttons/inputs
- Toast notifications: bottom of screen

**Tablet (768px - 1024px):**
- Use Size 450-500 spacing
- 2-column card grid
- Standard component sizes

**Desktop (> 1024px):**
- Full spacing scale (Size 600+)
- 3+ column card grid
- Standard/large component sizes
- Expressive card shadows

### Accessibility Requirements

**All Components Must:**
- Have proper ARIA labels
- Support keyboard navigation
- Include focus indicators (2px outline)
- Maintain color contrast (4.5:1 minimum)
- Provide error messages as aria-live

**Forms Must:**
- Use `<label>` elements
- Associate inputs with labels
- Display validation errors
- Indicate required fields
- Provide helper text when needed

**Buttons Must:**
- Have descriptive text or aria-label
- Indicate loading state
- Show disabled state clearly
- Provide visual feedback on interaction

---

## RESOURCES

- **Official Documentation:** https://seeds.sproutsocial.com/
- **Component Library:** @sproutsocial/racine (npm)
- **Token Documentation:** https://seeds.sproutsocial.com/resources/tokens
- **Design Tokens:** JSON token file with all values
- **Contribution Guide:** https://seeds.sproutsocial.com/contribute/

---

**Document Version:** 2.0
**Last Updated:** February 1, 2026
**Maintainer:** Design Team
