# Sprout Seeds Design Language - Notes App Implementation Plan

**Project:** Notes App Redesign
**Design System:** Sprout Seeds
**Objective:** Apply complete Sprout Seeds design language to Notes App
**Status:** Planning Phase
**Date:** February 1, 2026

---

## EXECUTIVE SUMMARY

This document outlines the specific design language requirements for implementing Sprout Seeds across the Notes App. It provides a roadmap for:
- Design token implementation
- Component specifications for each page
- Color palette assignments
- Typography hierarchy
- Motion and interaction patterns
- Accessibility standards

---

## CURRENT STATE ASSESSMENT

### Existing Application
- **Pages:** 5 (Login, Signup, Dashboard, Create Note, Edit Note)
- **Current Design:** Basic HTML with minimal styling
- **Components:** Forms, buttons, cards (unstyled)
- **Framework:** Flask with Jinja2 templates
- **Database:** SQLite with User and Note models

### Gap Analysis
| Aspect | Current | Required | Gap |
|--------|---------|----------|-----|
| **Typography** | System fonts | Roboto Serif + Proxima Nova | Import fonts, apply hierarchy |
| **Color Palette** | 5-6 colors | 50+ Sprout colors | Define all token values |
| **Spacing** | Inconsistent margins | 8px grid system | Create 12 spacing tokens |
| **Components** | Basic HTML | 50+ styled components | Design & code components |
| **Elevation** | None | 4-level shadow system | Add shadow tokens |
| **Motion** | None | Animation tokens | Add transitions & animations |
| **Accessibility** | Basic | WCAG AA compliant | Add ARIA, focus states |
| **Responsive** | Basic | 3 breakpoints | Optimize for mobile/tablet/desktop |

---

## PHASE 1: FOUNDATION SETUP (Week 1)

### 1.1 File Structure Creation

```
static/
├── css/
│   ├── tokens.css                 (NEW - Design tokens)
│   ├── typography.css             (NEW - Font setup)
│   ├── global.css                 (NEW - Base styles)
│   ├── utilities.css              (NEW - Utility classes)
│   ├── components/
│   │   ├── buttons.css            (NEW)
│   │   ├── forms.css              (NEW)
│   │   ├── cards.css              (NEW)
│   │   ├── modal.css              (NEW)
│   │   ├── notifications.css      (NEW)
│   │   ├── navigation.css         (NEW)
│   │   └── empty-states.css       (NEW)
│   └── pages/
│       ├── auth.css               (NEW - Login/Signup specific)
│       ├── dashboard.css          (NEW)
│       └── note-form.css          (NEW - Create/Edit specific)
├── js/
│   ├── notifications.js           (NEW)
│   ├── modal.js                   (NEW)
│   ├── forms.js                   (NEW)
│   └── interactions.js            (NEW)
└── fonts/                          (Optional - if self-hosting)
    ├── roboto-serif.woff2
    └── proxima-nova.woff2
```

### 1.2 Design Tokens Definition

**File: `static/css/tokens.css`**

```
SPACING TOKENS (12 values)
- --space-0: 0px
- --space-100: 2px
- --space-200: 4px
- --space-300: 8px (base unit)
- --space-350: 12px
- --space-400: 16px (primary)
- --space-450: 24px
- --space-500: 32px
- --space-600: 40px (multiplier base)
- --space-700: 80px
- --space-800: 120px
- --space-900: 160px

COLOR TOKENS (50+ colors organized by family)
Blues (9 shades):
- --color-blue-50 through --color-blue-800

Grays (10 shades):
- --color-gray-50 through --color-gray-900

Greens (7 shades):
- --color-green-50 through --color-green-700

Reds (7 shades):
- --color-red-50 through --color-red-700

Yellows (7 shades):
- --color-yellow-50 through --color-yellow-700

Purples, Pinks, Cyans, Oranges (accent colors)

SEMANTIC TOKENS
- --text-primary: var(--color-gray-900)
- --text-secondary: var(--color-gray-600)
- --status-success: var(--color-green-500)
- --status-error: var(--color-red-500)
- --status-warning: var(--color-yellow-500)
- --status-info: var(--color-blue-500)
- --bg-primary: #FFFFFF
- --bg-secondary: var(--color-gray-50)

BORDER TOKENS
- --radius-inner: 6px
- --radius-outer: 8px
- --radius-pill: 9999em
- --border-default: var(--color-gray-200)

ELEVATION TOKENS
- --shadow-sm: 0px 2px 4px rgba(0,0,0,0.05)
- --shadow-md: 0px 8px 16px rgba(0,0,0,0.08)
- --shadow-lg: 0px 16px 32px rgba(0,0,0,0.1)

MOTION TOKENS
- --duration-fast: 150ms
- --duration-medium: 300ms
- --duration-slow: 600ms
- --easing-in: cubic-bezier(0.4, 0, 0.7, 0.2)
- --easing-out: cubic-bezier(0, 0, 0.2, 1)
- --easing-inout: cubic-bezier(0.4, 0, 0.2, 1)

Z-INDEX SCALE
- --z-base: 0
- --z-dropdown: 100
- --z-modal-backdrop: 400
- --z-modal: 500
- --z-notification: 700
```

### 1.3 Typography Setup

**File: `static/css/typography.css`**

```
FONT IMPORTS
@import url('https://fonts.googleapis.com/css2?family=Roboto+Serif:wght@400;700&family=Proxima+Nova:wght@400;600;700');

TYPEFACE ASSIGNMENT
Primary Headlines (h1, h2): Roboto Serif Regular (400)
Secondary Headlines (h3, h4, h5, h6): Proxima Nova Bold (700)
Body Text: Proxima Nova Regular (400)
Labels & Buttons: Proxima Nova Bold (600)
Input Text: Proxima Nova Regular (400)

TYPE SCALE
h1: 2.5rem (40px) - Page titles
h2: 2rem (32px) - Major sections
h3: 1.5rem (24px) - Sub-sections
h4: 1.25rem (20px) - Card titles
h5: 1.125rem (18px) - Secondary titles
h6: 1rem (16px) - Tertiary titles
body: 1rem (16px) - Default body text
small: 0.875rem (14px) - Secondary text
code: 0.75rem (12px) - Monospace

LINE HEIGHTS
Headlines: 1.2
Body: 1.5
Tight: 1.2
```

### 1.4 Global Base Styles

**File: `static/css/global.css`**

```
RESET & DEFAULTS
- Box-sizing: border-box
- Remove default margins/padding
- Set font-smoothing

BODY STYLES
- Font: Proxima Nova, 16px, 1.5 line-height
- Color: Gray 900
- Background: White

FOCUS STATES
- 2px solid Blue 500 outline
- 2px outline-offset

TRANSITIONS
- Default: 150ms ease-out
- Applied to: background-color, color, border-color

UTILITY CLASSES
- Spacing (m, p, mt, mb, px, py)
- Layout (flex, flex-col, gap, items-center)
- Display (block, inline, hidden)
- Colors (text-primary, bg-secondary)
- Typography (text-bold, text-center)
```

---

## PHASE 2: COMPONENT SPECIFICATION (Week 2)

### 2.1 Button Component

**Specification:**

```
VARIANTS (6 types)
1. Primary
   - Background: Blue 600 (#2563EB)
   - Text: White
   - Hover: Blue 700
   - Use: Main call-to-action

2. Secondary
   - Background: Gray 100
   - Text: Gray 900
   - Border: Gray 300 (1px)
   - Hover: Gray 200
   - Use: Secondary actions, Cancel

3. Destructive
   - Background: Red 600 (#DC2626)
   - Text: White
   - Hover: Red 700
   - Use: Delete, Remove

4. Ghost
   - Background: Transparent
   - Text: Blue 600
   - Hover: Gray 100
   - Use: Tertiary actions

5. Disabled
   - Background: Gray 300
   - Text: Gray 400 (50% opacity)
   - Cursor: not-allowed
   - Use: When action unavailable

6. Loading
   - Show spinner
   - Disable interaction
   - Use: During async operations

SIZES (3 options)
- Small (sm): 32px height, 12px text
- Medium (md): 40px height, 14px text
- Large (lg): 48px height, 16px text

STATES
- Default
- Hover (+10% darker/lighter)
- Active (+20% change)
- Focus (2px outline)
- Disabled (50% opacity)
- Loading (spinner + disabled)

SPACING
- Padding: var(--space-350) var(--space-400)
- Icon gap: var(--space-300)
- Full width: width: 100%
```

**Implementation Location:** `static/css/components/buttons.css`

### 2.2 Input Field Component

**Specification:**

```
TYPES SUPPORTED
- text
- email
- password
- number
- date
- search
- textarea

APPEARANCES
1. Primary (Default)
   - Border: Gray 200 (1px)
   - Background: White
   - Focus: Blue 500 outline
   - Hover: Gray 300 border, shadow-sm

2. Secondary (Borderless)
   - Border: None
   - Background: Gray 100
   - Focus: Gray 200
   - Use: Inline editing

STATES
- Default: Normal appearance
- Hover: Border Gray 300, shadow-sm
- Focus: Blue 500 outline (2px)
- Invalid: Red 500 border, red background tint
- Valid: Green 500 border
- Disabled: Gray 300 border, 50% opacity
- Readonly: Normal appearance, no cursor change

SIZES
- Small: 32px height
- Default: 40px height
- Large: 48px height

FEATURES
- Label association (required)
- Placeholder support
- Helper text below
- Error message display
- Character counter
- Icon before/after
- Clear button (search type)

SPACING
- Padding: var(--space-400)
- Margin-bottom: var(--space-400)
- Label margin-bottom: var(--space-200)
```

**Implementation Location:** `static/css/components/forms.css`

### 2.3 Card Component

**Specification:**

```
CARD TYPES
1. Standard Card
   - Border: Gray 200 (1px)
   - Background: White
   - Radius: 8px (outer)
   - Padding: var(--space-500)
   - Shadow: None

2. Interactive Card
   - Same as standard, but:
   - Cursor: pointer
   - Hover: Background Gray 50, shadow-md
   - Focus: Blue 500 outline

3. Elevated Card
   - Shadow: var(--shadow-md)
   - Hover shadow: var(--shadow-lg)
   - No border

CONTENT AREAS
- Header: Title + optional actions
- Body: Primary content
- Footer: Action buttons

SPACING
- Padding: var(--space-500)
- Header border: 1px Gray 200
- Content gaps: var(--space-300)

GRID LAYOUT
- Desktop: 3 columns (minmax 300px)
- Tablet: 2 columns (minmax 250px)
- Mobile: 1 column
- Gap: var(--space-500)

STATES
- Default: Border + white background
- Hover: Shadow + color change
- Selected: Blue 500 border/highlight
- Disabled: Gray opacity
```

**Implementation Location:** `static/css/components/cards.css`

### 2.4 Modal Component

**Specification:**

```
STRUCTURE
- Backdrop (dark overlay, 40% opacity)
- Dialog box (white background, shadow-lg)
- Header (title + close button)
- Body (scrollable content)
- Footer (action buttons)

SIZES
- Small: 400px max-width
- Standard: 600px max-width
- Large: 800px max-width

STYLING
- Background: White
- Border-radius: 8px (outer)
- Shadow: var(--shadow-lg)
- Header border-bottom: Gray 200 (1px)
- Footer border-top: Gray 200 (1px)

ANIMATIONS
- Entry: slideUp 300ms ease-out
- Exit: fadeOut 150ms ease-in
- Backdrop: fadeIn 150ms ease-out

INTERACTIONS
- Close on backdrop click
- Close on ESC key
- Focus trap inside modal
- Focus return on close
- Scrollable body

ACCESSIBILITY
- role="dialog"
- aria-modal="true"
- aria-labelledby (header)
- aria-describedby (body)
- Focus management
```

**Implementation Location:** `static/css/components/modal.css`

### 2.5 Notification/Toast Component

**Specification:**

```
TOAST TYPES (4 variants)
1. Success
   - Background: Green 600
   - Icon: ✓ Checkmark
   - Use: Operation succeeded

2. Error
   - Background: Red 600
   - Icon: ✕ X mark
   - Use: Operation failed

3. Warning
   - Background: Yellow 600
   - Icon: ⚠ Warning
   - Use: User should be cautious

4. Info
   - Background: Blue 600
   - Icon: ℹ Info
   - Use: Informational message

APPEARANCE
- Text: White
- Padding: var(--space-400)
- Border-radius: var(--radius-outer)
- Shadow: var(--shadow-lg)
- Max-width: 400px

POSITIONING
- Desktop: Top-right, 16px from edges
- Mobile: Bottom, full width minus 16px
- Stack vertically if multiple

ANIMATION
- Entry: slideIn 150ms ease-out (from right)
- Progress bar: 4000ms linear (shrinks)
- Exit: fadeOut 150ms ease-in

FEATURES
- Auto-dismiss (4000ms default)
- Manual close button
- Progress bar indicator
- Icon display
- Title + message support
- Keyboard accessible
```

**Implementation Location:** `static/css/components/notifications.css`

### 2.6 Form Field Component (Label + Input + Validation)

**Specification:**

```
STRUCTURE
- Label (with required indicator)
- Input field
- Helper text (optional)
- Character counter (optional)
- Error message (hidden by default)
- Success message (hidden by default)

LABEL
- Font-weight: 600
- Font-size: 14px
- Color: Gray 900
- Margin-bottom: 8px
- Required indicator: Red asterisk (*)

HELPER TEXT
- Font-size: 12px
- Color: Gray 600
- Margin-top: 8px
- Display: block

VALIDATION MESSAGES
- Font-size: 12px
- Font-weight: 600
- Margin-top: 8px
- Display: none (hidden)

ERROR STATE
- Border: Red 500 (1px)
- Background: Red 50 (light tint)
- Message: display block, color Red 500
- Error icon: optional

SUCCESS STATE
- Border: Green 500 (1px)
- Background: Green 50 (light tint)
- Message: display block, color Green 500
- Success icon: optional

CHARACTER COUNTER
- Font-size: 12px
- Color: Gray 600
- Position: Below input
- Format: "X / Max"
- Warning state: Yellow 600 (80%+)
- Error state: Red 600 (100%)
```

**Implementation Location:** `static/css/components/forms.css`

---

## PHASE 3: PAGE-SPECIFIC DESIGN (Week 2)

### 3.1 Login Page

**Design Requirements:**

```
LAYOUT
- Full-height container (100vh)
- Centered card (450px max-width)
- Gradient background (Blue 50 to Gray 50)

HEADER
- App title (h1, 2rem, Roboto Serif)
- Subtitle (p, 16px, Gray 600)
- Margin-bottom: 40px

FORM STRUCTURE
- Form group spacing: var(--space-400)
- 2 input fields: Username, Password
- Submit button: Primary, Full width, Large
- Sign-up link below form

COLOR SCHEME
- Background: Linear gradient Blue 50 → Gray 50
- Card: White, shadow-lg
- Text: Gray 900
- Links: Blue 600
- Focus: Blue 500

SPACING
- Card padding: 40px
- Form groups: 16px between
- Submit button margin-top: 32px
- Link section margin-top: 32px

RESPONSIVE
- Mobile: Full width minus 32px, adjust padding to 24px
- Tablet: 450px max-width maintained
```

**Deliverables:** 
- `static/css/pages/auth.css` (Login + Signup styles)
- `templates/login.html` (Updated)

### 3.2 Signup Page

**Design Requirements:**

```
LAYOUT
- Same as login page (450px card, gradient bg)
- Slightly taller for additional fields

FORM STRUCTURE
- Username input + helper text
- Password input + requirements
- Confirm password input
- Submit button: Primary, Full width, Large
- Sign-in link below form

VALIDATION DISPLAY
- Helper text under username (gray)
- Password requirements list:
  * At least 8 characters
  * Contains uppercase letter
  * Contains special character
- Real-time validation feedback
- Green checkmarks for completed requirements

COLOR SCHEME
- Same as login page
- Additional: Green 500 for valid requirements

SPACING
- Consistent with login page
- Extra space for requirements list

RESPONSIVE
- Mobile optimized for longer form
- Stack elements vertically
```

**Deliverables:**
- `templates/signup.html` (Updated)
- Extends `auth.css`

### 3.3 Dashboard Page

**Design Requirements:**

```
LAYOUT
- Container-based (max-width: 1200px, centered)
- Header section (title + CTA button)
- Content area (card grid or empty state)

HEADER
- Title: "My Notes" (h1, 2.5rem, Roboto Serif)
- Subtitle: "Manage your notes here" (Gray 600, 16px)
- CTA Button: "+ New Note" (Primary, Large)
- Header layout: Space-between, align-center

NOTES GRID
- Desktop: 3 columns (minmax 300px)
- Tablet: 2 columns (minmax 250px)
- Mobile: 1 column
- Gap: var(--space-500)

CARD STRUCTURE (per note)
- Header: Note title (h4)
- Body: Note preview (3-line ellipsis)
- Footer: Edit + Delete buttons (Secondary + Destructive)

EMPTY STATE
- Large centered container (600px max)
- Icon/illustration area
- Headline: "No notes yet" (Gray 600, 24px)
- Message: "Create your first note..." (Gray 500)
- CTA: "Create Note" button (Primary)

FOOTER
- Sign Out button (Ghost, centered)
- Margin-top: var(--space-700)

COLOR SCHEME
- Background: White
- Cards: White with borders
- Card hover: Gray 50 + shadow-md
- Text: Gray 900 (title), Gray 600 (preview)

SPACING
- Container padding: var(--space-400) horizontal
- Header margin-bottom: var(--space-600)
- Card grid gap: var(--space-500)
- Footer margin-top: var(--space-700)

RESPONSIVE
- Mobile: Reduce heading to 28px, padding to 16px
- Tablet: Adjust card grid to 2 columns
```

**Deliverables:**
- `static/css/pages/dashboard.css`
- `templates/dashboard.html` (Updated)

### 3.4 Create/Edit Note Page

**Design Requirements:**

```
LAYOUT
- Full-height white background
- Container (max-width: 800px, centered)
- Form card with shadow

HEADER
- Title: "Create New Note" (h1)
- Subtitle: "Write and save your thoughts" (Gray 600)
- Margin-bottom: var(--space-600)

FORM STRUCTURE
- Form card: White, padding var(--space-600), shadow-md
- 2 form groups: Title + Content
- Character counter for each field
- Button group (Cancel + Create/Save)

TITLE FIELD
- Label: "Note Title" (required)
- Input: text type, placeholder "Enter note title"
- Maxlength: 200 characters
- Character counter: "0 / 200"

CONTENT FIELD
- Label: "Note Content" (required)
- Textarea: placeholder "Write your note here..."
- Minheight: 200px, resizable vertical only
- Maxlength: 5000 characters
- Character counter: "0 / 5000"

CHARACTER COUNTER
- Font-size: 12px
- Color: Gray 600
- Position: Below input
- Format: "X / Max"
- Update real-time on input
- Color change at 80% (Yellow 600) and 100% (Red 600)

BUTTON GROUP
- Layout: flex, justify-end
- Gap: var(--space-400)
- Cancel: Secondary button, Large
- Create/Save: Primary button, Large
- Margin-top: var(--space-600)

PAGE BACKGROUND
- Gray 50 (light background)

COLOR SCHEME
- Page background: Gray 50
- Form card: White
- Text: Gray 900
- Accents: Blue for primary action

SPACING
- Container padding: var(--space-600)
- Form padding: var(--space-600)
- Form groups: var(--space-400) between
- Buttons margin-top: var(--space-600)

RESPONSIVE
- Mobile: Form padding reduces to 24px
- Form width: 100%
- Button group: Stack vertically (100% width each)
```

**Deliverables:**
- `static/css/pages/note-form.css`
- `templates/create_note.html` (Updated)
- `templates/edit_note.html` (Updated)

---

## PHASE 4: INTERACTION & ANIMATION DESIGN (Week 3)

### 4.1 Button Interactions

```
ANIMATION SPECIFICATION
- Hover: Box-shadow increase (sm → md), background color change
- Active: Background color darker, no shadow change
- Focus: 2px outline, 2px offset
- Disabled: Opacity 50%, cursor not-allowed
- Loading: Spinner appears, button disabled

TIMING
- Transition duration: 150ms (fast)
- Easing: ease-out (cubic-bezier(0, 0, 0.2, 1))
- Properties: background-color, box-shadow, color

CSS
```css
button {
    transition: all 150ms cubic-bezier(0, 0, 0.2, 1);
}

button:hover {
    box-shadow: var(--shadow-md);
    transform: translateY(-1px);
}

button:active {
    transform: translateY(0);
}

button:focus-visible {
    outline: 2px solid var(--color-blue-500);
    outline-offset: 2px;
}
```

### 4.2 Form Field Interactions

```
FOCUS STATE
- 2px Blue 500 outline
- 2px outline-offset
- Border color change to Blue 500
- Subtle box-shadow on hover

VALIDATION FEEDBACK
- Real-time on blur
- Icon display (✓ or ✕)
- Message display with animation
- Color coded: Green (valid), Red (invalid)

HOVER STATE
- Border color: Gray 300
- Box-shadow: var(--shadow-sm)

CHARACTER COUNTER UPDATE
- Real-time on input
- Color changes at thresholds:
  * Normal: Gray 600 (0-79%)
  * Warning: Yellow 600 (80-99%)
  * Error: Red 600 (100%)

TIMING
- All transitions: 150ms ease-out
- Character counter update: Instant (no delay)
```

### 4.3 Card Interactions

```
HOVER EFFECT
- Shadow: None → var(--shadow-md)
- Border: Gray 200 → Gray 300
- Background: White → Gray 50 (interactive cards only)
- Duration: 300ms ease-out

ACTIVE STATE
- Border: Gray 200 → Blue 500
- Background: Gray 50 (click confirms selection)

FOCUS STATE
- Outline: 2px Blue 500
- Outline-offset: 0
```

### 4.4 Modal Animations

```
ENTRY ANIMATION
- Name: slideUp
- Duration: 300ms
- Easing: ease-out
- From: opacity 0, translateY(20px)
- To: opacity 1, translateY(0)

BACKDROP ANIMATION
- Name: fadeIn
- Duration: 150ms
- Easing: ease-out
- From: opacity 0
- To: opacity 0.4

EXIT ANIMATION
- Name: fadeOut
- Duration: 150ms
- Easing: ease-in
- From: opacity 1
- To: opacity 0
```

### 4.5 Toast/Notification Animations

```
ENTRY ANIMATION
- Name: slideIn
- Duration: 150ms (fast)
- Easing: ease-out
- From: opacity 0, translateX(100px)
- To: opacity 1, translateX(0)
- Direction: From right

PROGRESS BAR ANIMATION
- Name: progress
- Duration: 4000ms
- Linear easing
- From: width 100%
- To: width 0%

AUTO-DISMISS
- Duration: 4000ms
- Exit: fadeOut 150ms ease-in

STACKING
- Multiple toasts stack vertically
- Gap: var(--space-300)
- Each can be dismissed independently
```

---

## PHASE 5: RESPONSIVE DESIGN STRATEGY (Week 3)

### 5.1 Breakpoints

```
MOBILE (< 768px)
- 1 column layouts
- Full-width components
- Reduced padding: var(--space-300)
- Reduced font sizes (-1 level)
- Stacked buttons (100% width)
- Bottom sheet modals
- Full-width toast notifications

TABLET (768px - 1024px)
- 2 column grids
- Moderate padding: var(--space-400)
- Standard font sizes
- 2-column buttons where appropriate
- Standard modals
- Toast positioning: top-right

DESKTOP (> 1024px)
- 3+ column grids
- Full padding: var(--space-500/600)
- All font sizes at full scale
- Side-by-side buttons
- Standard modals
- Toast positioning: top-right
```

### 5.2 Mobile-Specific Adjustments

```
TYPOGRAPHY
- h1: 28px (from 40px)
- h2: 24px (from 32px)
- h3: 20px (from 24px)
- Body: 16px (unchanged)

SPACING
- Margins: Reduce by 25%
- Padding: var(--space-300) primary (from var(--space-400))
- Container padding: 12px sides
- Gap between elements: var(--space-300)

COMPONENTS
- Button: Full width (100%)
- Card: Single column grid
- Form: Single column, stack inputs vertically
- Modal: Bottom sheet (full width, no max-width)
- Toast: Bottom position, full width minus 16px

INTERACTIONS
- Touch targets: Minimum 44x44px (WCAG)
- Increase hover areas
- Reduce shadow emphasis (less z-depth perception needed)
```

### 5.3 Tablet-Specific Adjustments

```
GRIDS
- 2-column layouts (card grid, form layouts)
- 50% width components where appropriate

SPACING
- Moderate padding: var(--space-400) to var(--space-500)
- Gap: var(--space-400)

COMPONENTS
- Button: 2 buttons per row (side-by-side)
- Modal: 600px max-width
```

---

## PHASE 6: ACCESSIBILITY STANDARDS (Week 4)

### 6.1 WCAG 2.1 AA Compliance

```
COLOR CONTRAST
- Text on background: Minimum 4.5:1
- Large text (18pt+): Minimum 3:1
- UI components & borders: Minimum 3:1
- Tested with: WebAIM Contrast Checker

FOCUS MANAGEMENT
- Visible focus indicators: 2px solid Blue 500
- Focus order: Logical (top-to-bottom, left-to-right)
- Focus trap: Modal dialogs contain focus
- Focus restoration: Return to trigger element on close

KEYBOARD NAVIGATION
- All interactive elements accessible via Tab
- Buttons: Activate with Enter/Space
- Links: Activate with Enter
- Modals: ESC key closes
- Forms: Tab through inputs in order
- Escape key handling on all overlays

TOUCH TARGETS
- Minimum size: 44x44px
- Minimum spacing: 8px between targets
- Applied to: buttons, links, form controls

SEMANTIC HTML
- Proper heading hierarchy (h1 > h2 > h3)
- Form labels linked to inputs (for + id)
- ARIA labels for icon-only buttons
- ARIA roles for custom components
- ARIA live regions for dynamic content

ARIA ATTRIBUTES
- aria-label: Icon buttons, close buttons
- aria-labelledby: Modal headers
- aria-describedby: Form help text, errors
- aria-invalid: Form validation state
- aria-required: Required form fields
- aria-live="polite": Notification container
- aria-modal="true": Modal dialogs
- role="alert": Error messages, alerts

FORM VALIDATION
- Error messages in aria-live region
- aria-invalid="true" on invalid fields
- aria-describedby linking to error text
- Inline validation feedback
- Disabled attribute on buttons during validation

SKIP LINKS
- "Skip to main content" link
- Position: Fixed, top-left
- Initially off-screen: top: -40px
- Show on focus: focus → top: 0

MOBILE ACCESSIBILITY
- Touch-friendly spacing: 8px minimum between targets
- Large touch targets: 44x44px minimum
- Readable font sizes: 16px minimum
- Sufficient color contrast
```

### 6.2 Screen Reader Support

```
IMAGES & ICONS
- Icons in buttons: aria-label required
- Decorative icons: aria-hidden="true"
- Images: alt text or aria-label

FORM FIELDS
- All inputs have associated <label>
- Label text descriptive (not "Field 1")
- Help text: aria-describedby
- Error messages: aria-describedby + role="alert"

NOTIFICATIONS
- Container: role="region" aria-live="polite"
- Toast: Announce to screen readers
- Auto-dismiss: No abrupt removal

MODALS
- aria-modal="true"
- aria-labelledby (header ID)
- aria-describedby (body ID)
- Focus trap (focus stays inside)
- Keyboard handling (ESC to close)

NAVIGATION
- Skip link at page start
- Main landmarks: <main>, <nav>
- Proper heading hierarchy
- ARIA navigation region: role="navigation"
```

---

## PHASE 7: RESPONSIVE COLOR PALETTE MAPPING (Week 4)

### 7.1 Semantic Color Usage in Notes App

```
PRIMARY ACTION (Blue)
- Create note button: Blue 600 hover → Blue 700
- Login/Signup submit: Blue 600
- Form focus states: Blue 500 outline
- Links: Blue 600 → Blue 700 on hover
- Selected items: Blue 500 background or border

SECONDARY ACTION (Gray)
- Cancel buttons: Gray 100 bg, Gray 900 text
- Edit buttons: Gray 100 bg
- Outline buttons: Gray 100 with Gray 300 border
- Disabled state: Gray 300 bg, Gray 400 text
- Secondary text: Gray 600 color

DESTRUCTIVE ACTION (Red)
- Delete button: Red 600 → Red 700 hover
- Error states: Red 500 border, Red 50 background
- Error text: Red 600
- Validation errors: Red 500 outline
- Error toast: Red 600 background

SUCCESS STATE (Green)
- Success toast: Green 600 background
- Valid form field: Green 500 border
- Success messages: Green 600 text
- Success icon: Green 500

WARNING STATE (Yellow)
- Warning toast: Yellow 600 background
- Character counter 80%+: Yellow 600
- Warning border: Yellow 500
- Caution text: Yellow 600

INFO STATE (Blue - different from primary)
- Info toast: Blue 600 background
- Info icon: Blue 500
- Informational text: Blue 600

BACKGROUNDS
- Page background: White
- Secondary background: Gray 50
- Tertiary background: Gray 100
- Hover background: Gray 50
- Focus background: Blue 50 (light tint)
- Error background: Red 50
- Success background: Green 50

BORDERS & DIVIDERS
- Default border: Gray 200
- Hover border: Gray 300
- Focus border: Blue 500
- Error border: Red 500
- Disabled border: Gray 300

TEXT HIERARCHY
- Primary text: Gray 900 (headings, primary content)
- Secondary text: Gray 600 (subtitles, secondary info)
- Tertiary text: Gray 400 (placeholder, disabled)
- Inverse text: White (on dark backgrounds)
```

### 7.2 Color Application by Component

```
LOGIN PAGE
- Background: Linear gradient (Blue 50 → Gray 50)
- Card: White bg, Gray 200 border
- Input border: Gray 200 (Gray 300 hover, Blue 500 focus)
- Button: Blue 600 (Blue 700 hover)
- Link: Blue 600 (underline on hover)
- Error text: Red 600

DASHBOARD PAGE
- Background: White
- Card: White bg, Gray 200 border
- Card hover: Gray 50 bg, Gray 300 border, shadow-md
- Text: Gray 900 (title), Gray 600 (preview)
- Button: Blue 600 primary, Gray 100 secondary, Red 600 destructive
- Empty state: Gray 50 bg, Gray 600 text

NOTE FORM PAGE
- Page background: Gray 50
- Form card: White bg
- Input: Gray 200 border (Gray 300 hover, Blue 500 focus)
- Valid input: Green 500 border
- Invalid input: Red 500 border, Red 50 bg
- Counter normal: Gray 600
- Counter warning: Yellow 600
- Counter error: Red 600
- Button: Blue 600 primary, Gray 100 secondary

TOAST NOTIFICATIONS
- Success: Green 600 bg, White text
- Error: Red 600 bg, White text
- Warning: Yellow 600 bg, White text
- Info: Blue 600 bg, White text
- Icon: White color
- Close: White color, opacity 70% hover

FORM VALIDATION
- Valid state: Green 500 border, Green 600 text
- Invalid state: Red 500 border, Red 600 text, Red 50 bg
- Help text: Gray 600 color
- Required indicator: Red 600 asterisk (*)
```

---

## PHASE 8: FILE MANIFEST & CHECKLIST (Week 4)

### 8.1 CSS Files to Create

```
✓ static/css/tokens.css
  - All 50+ color definitions
  - 12 spacing tokens
  - Border radius values
  - Shadow tokens
  - Motion tokens
  - Z-index scale
  - Typography tokens

✓ static/css/typography.css
  - Font imports (Google Fonts)
  - Font family assignments
  - Heading hierarchy (h1-h6)
  - Body text defaults
  - Type scale definitions
  - Line height settings
  - Text color classes

✓ static/css/global.css
  - Reset & defaults
  - Body styles
  - Link styles
  - Focus states
  - Transition defaults
  - Scrollbar styling
  - Utility classes (spacing, layout, display, colors)

✓ static/css/utilities.css
  - Spacing utilities (margin, padding)
  - Layout utilities (flex, grid, gap)
  - Display utilities
  - Color utilities
  - Typography utilities
  - Border utilities

✓ static/css/components/buttons.css
  - Button base styles
  - 6 appearance variants
  - 3 size variants
  - State styles (hover, active, focus, disabled, loading)
  - Animation

✓ static/css/components/forms.css
  - Label styles
  - Input field styles
  - Textarea styles
  - Form group layout
  - Helper text
  - Error/success messages
  - Character counter
  - Validation states
  - Input sizes

✓ static/css/components/cards.css
  - Card base styles
  - Card variants (standard, interactive, elevated)
  - Card sections (header, body, footer)
  - Card grid layout
  - Hover/focus states
  - Responsive grid

✓ static/css/components/modal.css
  - Backdrop styles
  - Dialog styles
  - Header/body/footer
  - Close button
  - Modal sizes
  - Animation (slideUp, fadeIn)
  - Mobile bottom sheet
  - Focus trap styles

✓ static/css/components/notifications.css
  - Toast container
  - Toast base styles
  - 4 toast variants (success, error, warning, info)
  - Toast icon & content
  - Close button
  - Progress bar animation
  - Stack spacing
  - Mobile positioning

✓ static/css/components/navigation.css
  - Navigation bar styles (if needed)
  - Navigation list layout
  - Active/hover states

✓ static/css/components/empty-states.css
  - Empty state container
  - Icon/illustration area
  - Headline & message
  - CTA button styling

✓ static/css/pages/auth.css
  - Login/Signup page layout
  - Card container (450px)
  - Gradient background
  - Form spacing
  - Header styling
  - Link styling

✓ static/css/pages/dashboard.css
  - Dashboard header layout
  - Card grid with responsive columns
  - Empty state styling
  - Footer (logout button)

✓ static/css/pages/note-form.css
  - Note form page layout
  - Form card styling
  - Form group spacing
  - Character counter styling
  - Button group layout
  - Responsive adjustments
```

### 8.2 HTML Template Updates

```
✓ templates/base.html
  - Link all CSS files (tokens, typography, global, components)
  - Add notification container with role & aria-live
  - Add modal container
  - Import JS files (notifications, modal, forms)

✓ templates/login.html
  - Apply card styles
  - Apply form styles
  - Apply button styles
  - Add error message container
  - Add helper text

✓ templates/signup.html
  - Apply card styles
  - Apply form styles with password requirements
  - Apply input styles
  - Real-time validation feedback
  - Success indicators

✓ templates/dashboard.html
  - Apply header layout
  - Apply card grid layout
  - Apply empty state styles
  - Apply button styles
  - Add delete confirmation modal
  - Add logout form styling

✓ templates/create_note.html
  - Apply form card styles
  - Apply form group styles
  - Apply textarea styles
  - Apply character counter styles
  - Apply button group styles
  - Mobile responsive layout

✓ templates/edit_note.html
  - Same as create_note.html
  - Pre-populate fields with note data
  - Update button text to "Save Note"
```

### 8.3 JavaScript Files to Create

```
✓ static/js/notifications.js
  - NotificationManager class
  - show(message, type, duration)
  - success/error/warning/info methods
  - Auto-dismiss logic
  - Close button handler
  - Toast animation handler

✓ static/js/modal.js
  - Modal class
  - open() method
  - close() method
  - Close button handler
  - Backdrop click handler
  - ESC key handler
  - Focus trap implementation
  - Auto-initialize all modals

✓ static/js/forms.js
  - FormValidator class
  - validateField(field)
  - validateForm()
  - Real-time validation on blur/input
  - Error message display
  - Character counter updates
  - Success message display
  - Auto-initialize all forms

✓ static/js/interactions.js
  - Delete note handler
  - Modal confirmation logic
  - Toast notification on success/error
  - Form submission handlers
```

### 8.4 Complete Implementation Checklist

```
PHASE 1 - FOUNDATION (Week 1)
[ ] Create directory structure
[ ] Create tokens.css with all 50+ colors
[ ] Create typography.css with font setup
[ ] Create global.css with base styles
[ ] Create utilities.css with utility classes
[ ] Link all CSS in base.html
[ ] Verify font loading in browser
[ ] Test token values (inspect colors in DevTools)

PHASE 2 - COMPONENTS (Week 2)
[ ] Create buttons.css (6 variants + 3 sizes)
[ ] Create forms.css (inputs, validation, counter)
[ ] Create cards.css (standard, interactive, grid)
[ ] Create modal.css (structure, animations)
[ ] Create notifications.css (toasts, animations)
[ ] Create navigation.css (if needed)
[ ] Create empty-states.css
[ ] Test all component states (hover, focus, active, disabled)
[ ] Test component interactions

PHASE 3 - PAGES (Week 2)
[ ] Create auth.css (login/signup styles)
[ ] Create dashboard.css (page layout)
[ ] Create note-form.css (create/edit styles)
[ ] Update templates/base.html
[ ] Update templates/login.html
[ ] Update templates/signup.html
[ ] Update templates/dashboard.html
[ ] Update templates/create_note.html
[ ] Update templates/edit_note.html
[ ] Test all pages visually
[ ] Test responsive layouts (mobile, tablet, desktop)

PHASE 4 - INTERACTIONS (Week 3)
[ ] Create notifications.js
[ ] Create modal.js
[ ] Create forms.js
[ ] Link JS files in base.html
[ ] Test button interactions (hover, click, disable)
[ ] Test form validation and error display
[ ] Test modal open/close
[ ] Test notification toasts
[ ] Test character counters
[ ] Test delete confirmation flow

PHASE 5 - RESPONSIVE (Week 3)
[ ] Test mobile breakpoints (< 768px)
[ ] Test tablet breakpoints (768px-1024px)
[ ] Test desktop layout (> 1024px)
[ ] Verify touch targets (44x44px minimum)
[ ] Test button stacking on mobile
[ ] Test modal bottom sheet on mobile
[ ] Test form layout responsiveness
[ ] Test card grid responsiveness
[ ] Test navigation on mobile (if applicable)

PHASE 6 - ACCESSIBILITY (Week 4)
[ ] Test color contrast (minimum 4.5:1)
[ ] Test keyboard navigation (Tab, Enter, Escape)
[ ] Test focus indicators (visible on all interactive elements)
[ ] Test screen reader (NVDA/JAWS)
[ ] Add aria-labels to icon buttons
[ ] Add aria-describedby to form help text
[ ] Add aria-invalid to invalid fields
[ ] Add aria-live to notification container
[ ] Test form validation with screen reader
[ ] Add skip-to-content link
[ ] Test focus trap in modals
[ ] Verify semantic HTML structure

PHASE 7 - TESTING & QA (Week 4)
[ ] Cross-browser testing (Chrome, Firefox, Safari, Edge)
[ ] Mobile device testing (iOS Safari, Android Chrome)
[ ] Accessibility audit (WAVE, axe DevTools)
[ ] Performance testing (animation frame rate)
[ ] Responsive design testing (all breakpoints)
[ ] Form validation testing (all error cases)
[ ] Modal testing (open, close, confirm, cancel)
[ ] Notification testing (toast messages, stacking)
[ ] Component states testing (all variants)
[ ] Edge case testing (long text, empty states, slow network)

PHASE 8 - DOCUMENTATION (Week 4)
[ ] Create component usage guide
[ ] Document color palette usage
[ ] Document typography hierarchy
[ ] Create design token reference
[ ] Document accessibility features
[ ] Create responsive design guide
[ ] Document animation behaviors
[ ] Add code comments to CSS
[ ] Create migration guide (old styles → new styles)
```

---

## VISUAL DESIGN SUMMARY

### Design Tokens Summary

```
COLORS: 50+ organized by family (Blue, Gray, Green, Red, Yellow, Purple, Pink, Cyan, Orange)
SPACING: 8px grid with 12 tokens (0px to 160px)
TYPOGRAPHY: Roboto Serif (headlines) + Proxima Nova (body)
BORDERS: 3 semantic radius values (6px, 8px, 9999em)
SHADOWS: 4-level elevation system
MOTION: 3 durations + 3 easing functions
Z-INDEX: 7-level scale for layering

BUTTON APPEARANCE: 6 variants × 3 sizes = 18 combinations
INPUT STATES: 7 states × 2 appearances = 14 variations
CARD VARIANTS: 3 types with hover/focus states
TOAST TYPES: 4 variants with auto-dismiss + progress bar
MODAL SIZES: 3 sizes with bottom sheet on mobile
```

### Component Interaction Matrix

```
BUTTONS
- Hover: Shadow, color change
- Active: Darker color
- Focus: 2px outline
- Disabled: Opacity, no interaction
- Loading: Spinner, disabled

FORM FIELDS
- Hover: Border, shadow
- Focus: Blue outline, border color
- Valid: Green border
- Invalid: Red border, background tint
- Disabled: Gray background, no interaction

CARDS
- Hover: Shadow, background change (interactive only)
- Focus: Blue outline
- Active: Blue border
- Disabled: Gray opacity

MODALS
- Entry: Slide up + fade in (300ms)
- Exit: Fade out (150ms)
- Backdrop: Fade in/out (150ms)
- Focus: Trapped inside

TOASTS
- Entry: Slide in from right (150ms)
- Progress bar: Shrink over 4000ms
- Exit: Fade out (150ms)
- Manual close: Instant remove
```

---

## SUCCESS CRITERIA

### Visual Consistency
- ✓ All colors from Sprout palette
- ✓ Typography follows hierarchy
- ✓ Spacing uses 8px grid
- ✓ Components consistent across pages
- ✓ Focus states visible on all interactive elements

### Functionality
- ✓ All buttons clickable with feedback
- ✓ Forms validate with clear error messages
- ✓ Modals open/close smoothly
- ✓ Toasts appear and dismiss automatically
- ✓ Responsive layouts on all devices

### Accessibility
- ✓ WCAG 2.1 AA compliant
- ✓ Color contrast minimum 4.5:1
- ✓ Keyboard navigation complete
- ✓ Focus indicators visible
- ✓ Screen reader compatible
- ✓ Touch targets 44x44px minimum

### Performance
- ✓ CSS loads without Flash of Unstyled Content (FOUC)
- ✓ Animations run smoothly (60fps)
- ✓ JS executes efficiently
- ✓ Page load time < 3 seconds
- ✓ Mobile optimization for slower networks

### Browser Support
- ✓ Chrome/Edge (latest 2 versions)
- ✓ Firefox (latest 2 versions)
- ✓ Safari (latest 2 versions)
- ✓ iOS Safari 12+
- ✓ Android Chrome 90+

---

## TIMELINE OVERVIEW

```
WEEK 1: Foundation Setup (Phase 1)
- Create CSS file structure
- Implement all design tokens
- Setup typography system
- Create global base styles

WEEK 2: Components & Pages (Phases 2-3)
- Build all component CSS files
- Update HTML templates
- Implement page-specific styles
- Create form validation styles

WEEK 3: Interactions & Responsive (Phases 4-5)
- Create JavaScript files
- Implement animations
- Test responsive breakpoints
- Optimize mobile experience

WEEK 4: Accessibility & Polish (Phases 6-8)
- Add accessibility features
- Perform QA testing
- Cross-browser testing
- Create documentation

LAUNCH: Production-ready Sprout Seeds Notes App
```

---

**Document Version:** 1.0
**Status:** Ready for Implementation
**Next Step:** Begin Phase 1 - Create CSS file structure and design tokens
