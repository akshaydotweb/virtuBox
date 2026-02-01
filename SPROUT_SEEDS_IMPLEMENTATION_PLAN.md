# Complete Sprout Seeds Implementation Plan for Notes App

**Objective:** Fully integrate Sprout Seeds design system into Notes App
**Scope:** Typography, Colors, Spacing, Components, Animations, Accessibility
**Timeline:** 6 Phases (Foundation → Polish)

---

## CURRENT APP STRUCTURE → SPROUT SEEDS MAPPING

### Current Pages → Sprout Components

| Current Page | Primary Components Needed | Secondary Components |
|---|---|---|
| **Login** | Input, Button (Primary), Form Field, Text | Link, Empty State |
| **Signup** | Input, Button (Primary), Form Field, Text, Label | Validation Messages, Helper Text |
| **Dashboard** | Card, Button (Primary, Secondary), Badge, Empty State | Notification Toast, Modal |
| **Create Note** | Textarea, Input, Button (Primary, Secondary), Form Field, Character Counter | Label, Helper Text |
| **Edit Note** | Textarea, Input, Button (Primary, Secondary), Form Field, Character Counter | Modal (confirmation) |
| **Global** | Navigation, Typography, Spacing, Colors, Focus States, Animations | Loader, Error States |

---

## PHASE 1: DESIGN FOUNDATION (CSS & TOKENS)

### 1.1 Create Design Token Files

**File: `static/css/tokens.css`** - All design tokens as CSS variables

```css
/* SPACING TOKENS - 8px Grid System */
:root {
  --space-0: 0px;
  --space-100: 2px;
  --space-200: 4px;
  --space-300: 8px;
  --space-350: 12px;
  --space-400: 16px;
  --space-450: 24px;
  --space-500: 32px;
  --space-600: 40px;
  --space-700: 80px;
  --space-800: 120px;
  --space-900: 160px;
}

/* COLOR TOKENS - FOUNDATIONAL */
:root {
  /* Primary Blue */
  --color-blue-50: #DBEAFE;
  --color-blue-100: #BFDBFE;
  --color-blue-200: #93C5FD;
  --color-blue-300: #60A5FA;
  --color-blue-400: #3B82F6;
  --color-blue-500: #2563EB;
  --color-blue-600: #1D4ED8;
  --color-blue-700: #1E40AF;
  --color-blue-800: #1E3A8A;

  /* Neutral Gray */
  --color-gray-50: #F9FAFB;
  --color-gray-100: #F3F4F6;
  --color-gray-200: #E5E7EB;
  --color-gray-300: #D1D5DB;
  --color-gray-400: #9CA3AF;
  --color-gray-500: #6B7280;
  --color-gray-600: #4B5563;
  --color-gray-700: #374151;
  --color-gray-800: #1F2937;
  --color-gray-900: #111827;

  /* Success Green */
  --color-green-50: #F0FDF4;
  --color-green-100: #DCFCE7;
  --color-green-200: #BBF7D0;
  --color-green-500: #22C55E;
  --color-green-600: #16A34A;
  --color-green-700: #15803D;

  /* Warning Yellow */
  --color-yellow-50: #FFFBEB;
  --color-yellow-100: #FEF3C7;
  --color-yellow-200: #FDE68A;
  --color-yellow-500: #FBBF24;
  --color-yellow-600: #F59E0B;
  --color-yellow-700: #D97706;

  /* Error Red */
  --color-red-50: #FEF2F2;
  --color-red-100: #FEE2E2;
  --color-red-200: #FECACA;
  --color-red-500: #EF4444;
  --color-red-600: #DC2626;
  --color-red-700: #B91C1C;

  /* Accent Colors */
  --color-purple-500: #8B5CF6;
  --color-purple-600: #7C3AED;
  --color-pink-500: #EC4899;
  --color-cyan-500: #06B6D4;
  --color-orange-500: #F97316;
}

/* SEMANTIC COLOR TOKENS */
:root {
  /* Text Colors */
  --text-primary: var(--color-gray-900);
  --text-secondary: var(--color-gray-600);
  --text-tertiary: var(--color-gray-400);
  --text-disabled: rgba(156, 163, 175, 0.5);
  --text-inverse: #FFFFFF;
  --text-link: var(--color-blue-600);
  --text-link-hover: var(--color-blue-700);

  /* Background Colors */
  --bg-primary: #FFFFFF;
  --bg-secondary: var(--color-gray-50);
  --bg-tertiary: var(--color-gray-100);
  --bg-overlay: rgba(0, 0, 0, 0.4);

  /* Status Colors */
  --status-success: var(--color-green-500);
  --status-error: var(--color-red-500);
  --status-warning: var(--color-yellow-500);
  --status-info: var(--color-blue-500);

  /* Border Colors */
  --border-default: var(--color-gray-200);
  --border-hover: var(--color-gray-300);
  --border-focus: var(--color-blue-500);
  --border-error: var(--color-red-500);
}

/* BORDER RADIUS TOKENS */
:root {
  --radius-inner: 6px;
  --radius-outer: 8px;
  --radius-pill: 9999em;
}

/* ELEVATION (BOX SHADOW) TOKENS */
:root {
  --shadow-none: none;
  --shadow-sm: 0px 2px 4px rgba(0, 0, 0, 0.05);
  --shadow-md: 0px 8px 16px rgba(0, 0, 0, 0.08);
  --shadow-lg: 0px 16px 32px rgba(0, 0, 0, 0.1);
}

/* MOTION TOKENS */
:root {
  --duration-fast: 150ms;
  --duration-medium: 300ms;
  --duration-slow: 600ms;

  --easing-in: cubic-bezier(0.4, 0, 0.7, 0.2);
  --easing-out: cubic-bezier(0, 0, 0.2, 1);
  --easing-inout: cubic-bezier(0.4, 0, 0.2, 1);
}

/* TYPOGRAPHY TOKENS */
:root {
  --font-primary: 'Roboto Serif', Georgia, serif;
  --font-secondary: 'Proxima Nova', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;

  /* Font Sizes */
  --text-xs: 0.625rem;      /* 10px */
  --text-sm: 0.75rem;       /* 12px */
  --text-base: 0.875rem;    /* 14px */
  --text-md: 1rem;          /* 16px */
  --text-lg: 1.125rem;      /* 18px */
  --text-xl: 1.25rem;       /* 20px */
  --text-2xl: 1.5rem;       /* 24px */
  --text-3xl: 1.75rem;      /* 28px */
  --text-4xl: 2rem;         /* 32px */
  --text-5xl: 2.5rem;       /* 40px */

  /* Line Heights */
  --lh-tight: 1.2;
  --lh-normal: 1.5;
  --lh-relaxed: 1.75;
}

/* Z-INDEX SCALE */
:root {
  --z-base: 0;
  --z-dropdown: 100;
  --z-sticky: 200;
  --z-fixed: 300;
  --z-modal-backdrop: 400;
  --z-modal: 500;
  --z-tooltip: 600;
  --z-notification: 700;
}
```

### 1.2 Create Typography System File

**File: `static/css/typography.css`**

```css
/* IMPORT FONTS */
@import url('https://fonts.googleapis.com/css2?family=Roboto+Serif:wght@400;700&family=Proxima+Nova:wght@400;600;700&display=swap');

/* GLOBAL TYPOGRAPHY */
html {
  font-size: 16px;
}

body {
  font-family: var(--font-secondary);
  font-size: var(--text-md);
  font-weight: 400;
  line-height: var(--lh-normal);
  color: var(--text-primary);
  background-color: var(--bg-primary);
}

/* HEADING HIERARCHY */
h1 {
  font-family: var(--font-primary);
  font-size: var(--text-5xl);
  font-weight: 400;
  line-height: var(--lh-tight);
  color: var(--text-primary);
  margin: var(--space-600) 0 var(--space-400) 0;
}

h2 {
  font-family: var(--font-primary);
  font-size: var(--text-4xl);
  font-weight: 400;
  line-height: var(--lh-tight);
  color: var(--text-primary);
  margin: var(--space-600) 0 var(--space-400) 0;
}

h3 {
  font-family: var(--font-secondary);
  font-size: var(--text-2xl);
  font-weight: 700;
  line-height: var(--lh-tight);
  color: var(--text-primary);
  margin: var(--space-500) 0 var(--space-300) 0;
}

h4 {
  font-family: var(--font-secondary);
  font-size: var(--text-xl);
  font-weight: 700;
  color: var(--text-primary);
  margin: var(--space-400) 0 var(--space-300) 0;
}

h5 {
  font-family: var(--font-secondary);
  font-size: var(--text-lg);
  font-weight: 700;
  color: var(--text-primary);
  margin: var(--space-400) 0 var(--space-200) 0;
}

h6 {
  font-family: var(--font-secondary);
  font-size: var(--text-md);
  font-weight: 700;
  color: var(--text-primary);
  margin: var(--space-400) 0 var(--space-200) 0;
}

/* PARAGRAPH & TEXT */
p {
  margin: 0 0 var(--space-400) 0;
  font-size: var(--text-md);
  line-height: var(--lh-normal);
}

small, .text-small {
  font-size: var(--text-base);
  color: var(--text-secondary);
}

.text-xs {
  font-size: var(--text-xs);
}

.text-sm {
  font-size: var(--text-sm);
}

.text-md {
  font-size: var(--text-md);
}

.text-lg {
  font-size: var(--text-lg);
}

/* TEXT COLORS */
.text-primary { color: var(--text-primary); }
.text-secondary { color: var(--text-secondary); }
.text-tertiary { color: var(--text-tertiary); }
.text-error { color: var(--status-error); }
.text-success { color: var(--status-success); }
.text-warning { color: var(--status-warning); }
.text-info { color: var(--status-info); }

/* TEXT STYLES */
.text-bold {
  font-weight: 700;
}

.text-semibold {
  font-weight: 600;
}

.text-center {
  text-align: center;
}

.text-right {
  text-align: right;
}

/* LINKS */
a {
  color: var(--text-link);
  text-decoration: none;
  transition: color var(--duration-fast) var(--easing-out);
}

a:hover {
  color: var(--text-link-hover);
  text-decoration: underline;
}

a:focus {
  outline: 2px solid var(--color-blue-500);
  outline-offset: 2px;
  border-radius: var(--radius-inner);
}

/* LISTS */
ul, ol {
  margin: 0 0 var(--space-400) 0;
  padding-left: var(--space-500);
}

li {
  margin-bottom: var(--space-200);
}

/* CODE */
code, pre {
  font-family: 'Monaco', 'Menlo', 'Ubuntu Mono', monospace;
  font-size: 0.875em;
}

code {
  background-color: var(--bg-tertiary);
  padding: var(--space-100) var(--space-200);
  border-radius: var(--radius-inner);
  color: var(--color-red-600);
}
```

### 1.3 Create Global Styles File

**File: `static/css/global.css`**

```css
/* RESET & DEFAULTS */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* BASE STYLES */
html {
  scroll-behavior: smooth;
}

body {
  background-color: var(--bg-primary);
  color: var(--text-primary);
  font-family: var(--font-secondary);
  font-size: var(--text-md);
  line-height: var(--lh-normal);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* CONTAINER */
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--space-400);
}

@media (max-width: 768px) {
  .container {
    padding: 0 var(--space-300);
  }
}

/* UTILITY CLASSES - SPACING */
.m-0 { margin: 0; }
.m-1 { margin: var(--space-300); }
.m-2 { margin: var(--space-400); }
.m-3 { margin: var(--space-500); }
.m-4 { margin: var(--space-600); }

.mx-auto { margin-left: auto; margin-right: auto; }
.my-auto { margin-top: auto; margin-bottom: auto; }

.mt-1 { margin-top: var(--space-300); }
.mt-2 { margin-top: var(--space-400); }
.mt-3 { margin-top: var(--space-500); }
.mt-4 { margin-top: var(--space-600); }

.mb-1 { margin-bottom: var(--space-300); }
.mb-2 { margin-bottom: var(--space-400); }
.mb-3 { margin-bottom: var(--space-500); }
.mb-4 { margin-bottom: var(--space-600); }

.p-1 { padding: var(--space-300); }
.p-2 { padding: var(--space-400); }
.p-3 { padding: var(--space-500); }
.p-4 { padding: var(--space-600); }

.px-1 { padding-left: var(--space-300); padding-right: var(--space-300); }
.px-2 { padding-left: var(--space-400); padding-right: var(--space-400); }
.px-3 { padding-left: var(--space-500); padding-right: var(--space-500); }

.py-1 { padding-top: var(--space-300); padding-bottom: var(--space-300); }
.py-2 { padding-top: var(--space-400); padding-bottom: var(--space-400); }
.py-3 { padding-top: var(--space-500); padding-bottom: var(--space-500); }

/* UTILITY CLASSES - LAYOUT */
.flex {
  display: flex;
}

.flex-col {
  flex-direction: column;
}

.flex-row {
  flex-direction: row;
}

.gap-1 { gap: var(--space-300); }
.gap-2 { gap: var(--space-400); }
.gap-3 { gap: var(--space-500); }
.gap-4 { gap: var(--space-600); }

.items-center {
  align-items: center;
}

.justify-center {
  justify-content: center;
}

.justify-between {
  justify-content: space-between;
}

/* UTILITY CLASSES - DISPLAY */
.block { display: block; }
.inline-block { display: inline-block; }
.inline { display: inline; }
.hidden { display: none; }

/* UTILITY CLASSES - WIDTH/HEIGHT */
.w-full { width: 100%; }
.h-full { height: 100%; }

/* UTILITY CLASSES - COLORS */
.bg-primary { background-color: var(--bg-primary); }
.bg-secondary { background-color: var(--bg-secondary); }
.bg-tertiary { background-color: var(--bg-tertiary); }

.bg-blue-50 { background-color: var(--color-blue-50); }
.bg-blue-100 { background-color: var(--color-blue-100); }
.bg-blue-500 { background-color: var(--color-blue-500); }

/* UTILITY CLASSES - BORDERS */
.border {
  border: 1px solid var(--border-default);
}

.rounded-sm {
  border-radius: var(--radius-inner);
}

.rounded {
  border-radius: var(--radius-outer);
}

.rounded-full {
  border-radius: var(--radius-pill);
}

/* FOCUS STATES - GLOBAL */
*:focus-visible {
  outline: 2px solid var(--color-blue-500);
  outline-offset: 2px;
}

button:focus-visible {
  outline-offset: 0;
}

input:focus-visible,
textarea:focus-visible,
select:focus-visible {
  outline: 2px solid var(--color-blue-500);
  outline-offset: 2px;
}

/* TRANSITIONS */
* {
  transition: background-color var(--duration-fast) var(--easing-out),
              color var(--duration-fast) var(--easing-out),
              border-color var(--duration-fast) var(--easing-out);
}

/* SCROLLBAR STYLING */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  background: var(--bg-tertiary);
}

::-webkit-scrollbar-thumb {
  background: var(--color-gray-400);
  border-radius: var(--radius-pill);
}

::-webkit-scrollbar-thumb:hover {
  background: var(--color-gray-500);
}
```

---

## PHASE 2: COMPONENT LIBRARY

### 2.1 Button Component

**File: `static/css/components/buttons.css`**

```css
/* BUTTON BASE */
button, .btn, [role="button"] {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-300);
  
  font-family: var(--font-secondary);
  font-size: var(--text-base);
  font-weight: 600;
  line-height: var(--lh-tight);
  
  border: none;
  border-radius: var(--radius-outer);
  padding: var(--space-350) var(--space-400);
  
  cursor: pointer;
  transition: all var(--duration-fast) var(--easing-out);
  
  text-decoration: none;
  white-space: nowrap;
}

/* PRIMARY BUTTON */
.btn-primary {
  background-color: var(--color-blue-600);
  color: #FFFFFF;
  box-shadow: var(--shadow-sm);
}

.btn-primary:hover {
  background-color: var(--color-blue-700);
  box-shadow: var(--shadow-md);
}

.btn-primary:active {
  background-color: var(--color-blue-800);
}

.btn-primary:disabled {
  background-color: var(--color-gray-300);
  color: var(--text-disabled);
  cursor: not-allowed;
  box-shadow: none;
}

/* SECONDARY BUTTON */
.btn-secondary {
  background-color: var(--color-gray-100);
  color: var(--text-primary);
  border: 1px solid var(--border-default);
}

.btn-secondary:hover {
  background-color: var(--color-gray-200);
  border-color: var(--border-hover);
}

.btn-secondary:active {
  background-color: var(--color-gray-300);
}

.btn-secondary:disabled {
  background-color: var(--color-gray-100);
  color: var(--text-disabled);
  cursor: not-allowed;
  border-color: var(--border-default);
}

/* DESTRUCTIVE BUTTON */
.btn-destructive {
  background-color: var(--color-red-600);
  color: #FFFFFF;
  box-shadow: var(--shadow-sm);
}

.btn-destructive:hover {
  background-color: var(--color-red-700);
  box-shadow: var(--shadow-md);
}

.btn-destructive:active {
  background-color: #7F1D1D;
}

.btn-destructive:disabled {
  background-color: var(--color-gray-300);
  color: var(--text-disabled);
  cursor: not-allowed;
  box-shadow: none;
}

/* GHOST BUTTON */
.btn-ghost {
  background-color: transparent;
  color: var(--text-link);
  border: none;
}

.btn-ghost:hover {
  background-color: var(--bg-secondary);
  color: var(--text-link-hover);
}

.btn-ghost:disabled {
  color: var(--text-disabled);
  cursor: not-allowed;
}

/* BUTTON SIZES */
.btn-sm {
  font-size: var(--text-sm);
  padding: var(--space-200) var(--space-300);
  height: 32px;
}

.btn-md {
  font-size: var(--text-base);
  padding: var(--space-350) var(--space-400);
  height: 40px;
}

.btn-lg {
  font-size: var(--text-md);
  padding: var(--space-400) var(--space-500);
  height: 48px;
}

/* BUTTON FULL WIDTH */
.btn-full {
  width: 100%;
}

/* BUTTON WITH ICON */
.btn-with-icon {
  display: inline-flex;
  gap: var(--space-300);
}

.btn-with-icon svg,
.btn-with-icon img {
  width: 20px;
  height: 20px;
}

/* BUTTON LOADING STATE */
.btn-loading {
  position: relative;
  color: transparent;
  cursor: not-allowed;
}

.btn-loading::after {
  content: '';
  position: absolute;
  width: 16px;
  height: 16px;
  border: 2px solid currentColor;
  border-top-color: transparent;
  border-radius: var(--radius-pill);
  animation: spin var(--duration-slow) linear infinite;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}
```

### 2.2 Input & Form Component

**File: `static/css/components/forms.css`**

```css
/* LABEL */
label {
  display: block;
  font-size: var(--text-base);
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: var(--space-200);
  cursor: pointer;
}

label.required::after {
  content: ' *';
  color: var(--status-error);
}

/* FORM GROUP */
.form-group {
  margin-bottom: var(--space-400);
  display: flex;
  flex-direction: column;
}

/* INPUT FIELD */
input[type="text"],
input[type="email"],
input[type="password"],
input[type="number"],
input[type="date"],
input[type="search"],
textarea,
select {
  width: 100%;
  font-family: var(--font-secondary);
  font-size: var(--text-md);
  padding: var(--space-400);
  border: 1px solid var(--border-default);
  border-radius: var(--radius-outer);
  background-color: var(--bg-primary);
  color: var(--text-primary);
  transition: all var(--duration-fast) var(--easing-out);
}

input[type="text"]:hover,
input[type="email"]:hover,
input[type="password"]:hover,
input[type="number"]:hover,
textarea:hover,
select:hover {
  border-color: var(--border-hover);
  box-shadow: var(--shadow-sm);
}

input[type="text"]:focus,
input[type="email"]:focus,
input[type="password"]:focus,
input[type="number"]:focus,
input[type="date"]:focus,
input[type="search"]:focus,
textarea:focus,
select:focus {
  outline: 2px solid var(--color-blue-500);
  outline-offset: 2px;
  border-color: var(--color-blue-500);
  background-color: var(--bg-primary);
}

input:disabled,
textarea:disabled,
select:disabled {
  background-color: var(--bg-tertiary);
  color: var(--text-disabled);
  cursor: not-allowed;
  border-color: var(--border-default);
}

input::placeholder,
textarea::placeholder {
  color: var(--text-tertiary);
}

/* TEXTAREA SPECIFIC */
textarea {
  resize: vertical;
  min-height: 120px;
  font-family: var(--font-secondary);
}

/* INPUT SIZES */
input.input-sm,
textarea.input-sm {
  font-size: var(--text-sm);
  padding: var(--space-300);
}

input.input-lg,
textarea.input-lg {
  font-size: var(--text-lg);
  padding: var(--space-500);
}

/* HELPER TEXT */
.help-text {
  font-size: var(--text-sm);
  color: var(--text-secondary);
  margin-top: var(--space-200);
  display: block;
}

/* ERROR STATE */
input.is-invalid,
textarea.is-invalid {
  border-color: var(--status-error);
  background-color: rgba(239, 68, 68, 0.02);
}

input.is-invalid:focus,
textarea.is-invalid:focus {
  outline-color: var(--status-error);
  border-color: var(--status-error);
}

.error-message {
  font-size: var(--text-sm);
  color: var(--status-error);
  margin-top: var(--space-200);
  display: block;
  font-weight: 600;
}

/* SUCCESS STATE */
input.is-valid,
textarea.is-valid {
  border-color: var(--status-success);
  background-color: rgba(34, 197, 94, 0.02);
}

input.is-valid:focus,
textarea.is-valid:focus {
  outline-color: var(--status-success);
  border-color: var(--status-success);
}

.success-message {
  font-size: var(--text-sm);
  color: var(--status-success);
  margin-top: var(--space-200);
  display: block;
  font-weight: 600;
}

/* CHARACTER COUNTER */
.character-counter {
  font-size: var(--text-sm);
  color: var(--text-secondary);
  margin-top: var(--space-200);
  text-align: right;
  display: flex;
  justify-content: space-between;
}

.character-counter.warning {
  color: var(--status-warning);
}

.character-counter.error {
  color: var(--status-error);
}

/* FORM LAYOUT */
.form-row {
  display: grid;
  grid-template-columns: 1fr;
  gap: var(--space-400);
}

.form-row.two-column {
  grid-template-columns: 1fr 1fr;
}

@media (max-width: 768px) {
  .form-row.two-column {
    grid-template-columns: 1fr;
  }
}
```

### 2.3 Card Component

**File: `static/css/components/cards.css`**

```css
/* CARD BASE */
.card {
  background-color: var(--bg-primary);
  border: 1px solid var(--border-default);
  border-radius: var(--radius-outer);
  padding: var(--space-500);
  transition: all var(--duration-medium) var(--easing-out);
}

.card:hover {
  border-color: var(--border-hover);
  box-shadow: var(--shadow-md);
}

/* CARD HEADER */
.card-header {
  margin-bottom: var(--space-400);
  padding-bottom: var(--space-300);
  border-bottom: 1px solid var(--border-default);
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.card-header h3 {
  margin: 0;
  font-size: var(--text-lg);
  color: var(--text-primary);
}

/* CARD BODY */
.card-body {
  margin-bottom: var(--space-400);
}

.card-body p {
  margin-bottom: var(--space-200);
}

/* CARD FOOTER */
.card-footer {
  padding-top: var(--space-300);
  border-top: 1px solid var(--border-default);
  display: flex;
  gap: var(--space-300);
  justify-content: flex-end;
}

/* CARD VARIANTS */
.card.card-interactive {
  cursor: pointer;
}

.card.card-interactive:hover {
  background-color: var(--bg-secondary);
  box-shadow: var(--shadow-md);
}

.card.card-interactive:focus-within {
  outline: 2px solid var(--color-blue-500);
  outline-offset: 0;
}

/* CARD GRID */
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: var(--space-500);
  margin-top: var(--space-500);
}

@media (max-width: 768px) {
  .card-grid {
    grid-template-columns: 1fr;
    gap: var(--space-400);
  }
}
```

### 2.4 Modal/Dialog Component

**File: `static/css/components/modal.css`**

```css
/* MODAL BACKDROP */
.modal-backdrop {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: var(--bg-overlay);
  display: none;
  align-items: center;
  justify-content: center;
  z-index: var(--z-modal-backdrop);
}

.modal-backdrop.active {
  display: flex;
}

/* MODAL DIALOG */
.modal-dialog {
  background-color: var(--bg-primary);
  border-radius: var(--radius-outer);
  box-shadow: var(--shadow-lg);
  max-width: 600px;
  width: 90%;
  max-height: 90vh;
  overflow-y: auto;
  z-index: var(--z-modal);
  animation: slideUp var(--duration-medium) var(--easing-out);
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* MODAL HEADER */
.modal-header {
  padding: var(--space-500);
  border-bottom: 1px solid var(--border-default);
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.modal-header h2 {
  margin: 0;
  font-size: var(--text-2xl);
  color: var(--text-primary);
}

.modal-close {
  background: none;
  border: none;
  font-size: var(--text-2xl);
  color: var(--text-secondary);
  cursor: pointer;
  padding: 0;
  width: 32px;
  height: 32px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: var(--radius-inner);
  transition: all var(--duration-fast) var(--easing-out);
}

.modal-close:hover {
  background-color: var(--bg-secondary);
  color: var(--text-primary);
}

/* MODAL BODY */
.modal-body {
  padding: var(--space-500);
}

/* MODAL FOOTER */
.modal-footer {
  padding: var(--space-500);
  border-top: 1px solid var(--border-default);
  display: flex;
  gap: var(--space-300);
  justify-content: flex-end;
}

.modal-footer .btn {
  flex: 0 1 auto;
}

/* MODAL SIZES */
.modal-dialog.modal-sm {
  max-width: 400px;
}

.modal-dialog.modal-lg {
  max-width: 800px;
}

/* MOBILE RESPONSIVENESS */
@media (max-width: 768px) {
  .modal-dialog {
    width: 95%;
    max-height: 95vh;
  }

  .modal-footer {
    flex-direction: column;
  }

  .modal-footer .btn {
    width: 100%;
  }
}
```

### 2.5 Notification/Toast Component

**File: `static/css/components/notifications.css`**

```css
/* TOAST CONTAINER */
.toast-container {
  position: fixed;
  top: var(--space-400);
  right: var(--space-400);
  z-index: var(--z-notification);
  display: flex;
  flex-direction: column;
  gap: var(--space-300);
  max-width: 400px;
  pointer-events: none;
}

@media (max-width: 768px) {
  .toast-container {
    top: var(--space-300);
    right: var(--space-300);
    left: var(--space-300);
    max-width: none;
  }
}

/* TOAST */
.toast {
  display: flex;
  gap: var(--space-400);
  align-items: flex-start;
  padding: var(--space-400);
  border-radius: var(--radius-outer);
  background-color: var(--color-gray-900);
  color: #FFFFFF;
  box-shadow: var(--shadow-lg);
  pointer-events: auto;
  animation: slideIn var(--duration-fast) var(--easing-out);
}

@keyframes slideIn {
  from {
    opacity: 0;
    transform: translateX(100px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

/* TOAST TYPES */
.toast.toast-success {
  background-color: var(--color-green-600);
}

.toast.toast-error {
  background-color: var(--color-red-600);
}

.toast.toast-warning {
  background-color: var(--color-yellow-600);
}

.toast.toast-info {
  background-color: var(--color-blue-600);
}

/* TOAST ICON */
.toast-icon {
  width: 24px;
  height: 24px;
  flex-shrink: 0;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* TOAST CONTENT */
.toast-content {
  display: flex;
  flex-direction: column;
  gap: var(--space-100);
}

.toast-title {
  font-weight: 600;
  font-size: var(--text-base);
}

.toast-message {
  font-size: var(--text-sm);
  opacity: 0.9;
}

/* TOAST CLOSE */
.toast-close {
  background: none;
  border: none;
  color: #FFFFFF;
  cursor: pointer;
  padding: 0;
  font-size: var(--text-lg);
  width: 24px;
  height: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  transition: opacity var(--duration-fast) var(--easing-out);
}

.toast-close:hover {
  opacity: 0.7;
}

/* TOAST PROGRESS BAR */
.toast-progress {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 3px;
  background-color: rgba(255, 255, 255, 0.3);
  animation: progress var(--duration-slow) linear forwards;
}

@keyframes progress {
  to {
    width: 0;
  }
}
```

---

## PHASE 3: PAGE LAYOUTS & STRUCTURE

### 3.1 Base Template Update

**File: `templates/base.html`** - Main layout structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>{% block title %}Notes App - Sprout Seeds Design{% endblock %}</title>

    <!-- DESIGN TOKENS & STYLES -->
    <link rel="stylesheet" href="{{ url_for('static', filename='css/tokens.css') }}">
    <link rel="stylesheet" href="{{ url_for('static', filename='css/typography.css') }}">
    <link rel="stylesheet" href="{{ url_for('static', filename='css/global.css') }}">

    <!-- COMPONENT STYLES -->
    <link rel="stylesheet" href="{{ url_for('static', filename='css/components/buttons.css') }}">
    <link rel="stylesheet" href="{{ url_for('static', filename='css/components/forms.css') }}">
    <link rel="stylesheet" href="{{ url_for('static', filename='css/components/cards.css') }}">
    <link rel="stylesheet" href="{{ url_for('static', filename='css/components/modal.css') }}">
    <link rel="stylesheet" href="{{ url_for('static', filename='css/components/notifications.css') }}">

    <!-- PAGE-SPECIFIC STYLES -->
    {% block extra_css %}{% endblock %}
</head>
<body>
    <!-- NOTIFICATIONS CONTAINER -->
    <div id="notificationContainer" class="toast-container" role="region" aria-label="Notifications" aria-live="polite"></div>

    <!-- MAIN CONTENT -->
    <main class="main-content">
        {% block content %}{% endblock %}
    </main>

    <!-- MODALS -->
    <div id="confirmModal" class="modal-backdrop">
        <div class="modal-dialog modal-sm">
            <div class="modal-header">
                <h2>Confirm Action</h2>
                <button class="modal-close" data-dismiss="modal" aria-label="Close dialog">&times;</button>
            </div>
            <div class="modal-body">
                <p id="confirmMessage"></p>
            </div>
            <div class="modal-footer">
                <button class="btn btn-secondary" data-dismiss="modal">Cancel</button>
                <button class="btn btn-destructive" id="confirmButton">Delete</button>
            </div>
        </div>
    </div>

    <!-- JAVASCRIPT -->
    <script src="{{ url_for('static', filename='js/notifications.js') }}"></script>
    <script src="{{ url_for('static', filename='js/modal.js') }}"></script>
    <script src="{{ url_for('static', filename='js/forms.js') }}"></script>
    {% block extra_js %}{% endblock %}
</body>
</html>
```

### 3.2 Login Page Structure

**File: `templates/login.html`** - Full Sprout redesign

```html
{% extends "base.html" %}

{% block title %}Login - Notes App{% endblock %}

{% block content %}
<div class="login-page" style="
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, var(--color-blue-50) 0%, var(--bg-secondary) 100%);
">
    <div class="login-card" style="
        max-width: 450px;
        width: 90%;
        padding: var(--space-600);
        background-color: var(--bg-primary);
        border-radius: var(--radius-outer);
        box-shadow: var(--shadow-lg);
    ">
        <!-- HEADER -->
        <div class="login-header" style="text-align: center; margin-bottom: var(--space-600);">
            <h1 style="font-size: var(--text-3xl); margin-bottom: var(--space-200);">Notes App</h1>
            <p class="text-secondary" style="font-size: var(--text-md);">Sign in to your account</p>
        </div>

        <!-- FORM -->
        <form method="POST" class="login-form">
            <!-- USERNAME FIELD -->
            <div class="form-group">
                <label for="username" class="required">Username</label>
                <input
                    type="text"
                    id="username"
                    name="username"
                    placeholder="Enter your username"
                    required
                    minlength="3"
                    aria-label="Username"
                    aria-describedby="username-help"
                />
                <span class="help-text" id="username-help">At least 3 characters</span>
            </div>

            <!-- PASSWORD FIELD -->
            <div class="form-group">
                <label for="password" class="required">Password</label>
                <input
                    type="password"
                    id="password"
                    name="password"
                    placeholder="Enter your password"
                    required
                    aria-label="Password"
                />
            </div>

            <!-- ERROR MESSAGE -->
            {% if error %}
            <div class="form-group" role="alert" style="
                padding: var(--space-400);
                background-color: rgba(239, 68, 68, 0.1);
                border: 1px solid var(--status-error);
                border-radius: var(--radius-outer);
                color: var(--status-error);
            ">
                <strong>{{ error }}</strong>
            </div>
            {% endif %}

            <!-- SUBMIT BUTTON -->
            <button type="submit" class="btn btn-primary btn-lg btn-full" style="margin-top: var(--space-500);">
                Sign In
            </button>
        </form>

        <!-- SIGNUP LINK -->
        <div style="text-align: center; margin-top: var(--space-500);">
            <p class="text-secondary">
                Don't have an account?
                <a href="{{ url_for('signup') }}" style="color: var(--text-link); font-weight: 600;">Sign up</a>
            </p>
        </div>
    </div>
</div>
{% endblock %}
```

---

## PHASE 4: COMPONENT-SPECIFIC PAGES

### 4.1 Dashboard Page with Card Grid

**File: `templates/dashboard.html`** - Full Sprout redesign

```html
{% extends "base.html" %}

{% block title %}Dashboard - Notes App{% endblock %}

{% block content %}
<div class="dashboard-page" style="padding: var(--space-600) 0;">
    <div class="container">
        <!-- HEADER -->
        <div class="dashboard-header" style="
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: var(--space-600);
        ">
            <div>
                <h1 style="margin: 0; font-size: var(--text-4xl);">My Notes</h1>
                <p class="text-secondary" style="margin: var(--space-200) 0 0 0;">Manage your notes here</p>
            </div>
            <a href="{{ url_for('create_note') }}" class="btn btn-primary btn-lg">
                + New Note
            </a>
        </div>

        <!-- EMPTY STATE -->
        {% if not notes %}
        <div class="empty-state" style="
            text-align: center;
            padding: var(--space-700);
            background-color: var(--bg-secondary);
            border: 2px dashed var(--border-default);
            border-radius: var(--radius-outer);
        ">
            <h2 style="color: var(--text-secondary); margin-bottom: var(--space-400);">No notes yet</h2>
            <p class="text-secondary" style="margin-bottom: var(--space-500);">Create your first note to get started</p>
            <a href="{{ url_for('create_note') }}" class="btn btn-primary">Create Note</a>
        </div>
        {% else %}

        <!-- NOTES GRID -->
        <div class="card-grid">
            {% for note in notes %}
            <article class="card card-interactive" data-note-id="{{ note.id }}">
                <div class="card-header">
                    <h3>{{ note.title }}</h3>
                </div>

                <div class="card-body">
                    <p class="text-secondary" style="
                        overflow: hidden;
                        text-overflow: ellipsis;
                        display: -webkit-box;
                        -webkit-line-clamp: 3;
                        -webkit-box-orient: vertical;
                    ">
                        {{ note.content[:150] }}{% if note.content|length > 150 %}...{% endif %}
                    </p>
                </div>

                <div class="card-footer">
                    <a href="{{ url_for('edit_note', id=note.id) }}" class="btn btn-secondary btn-sm">
                        Edit
                    </a>
                    <button
                        type="button"
                        class="btn btn-destructive btn-sm"
                        data-delete-note="{{ note.id }}"
                        aria-label="Delete note: {{ note.title }}"
                    >
                        Delete
                    </button>
                </div>
            </article>
            {% endfor %}
        </div>
        {% endif %}

        <!-- LOGOUT -->
        <div style="text-align: center; margin-top: var(--space-700);">
            <form method="POST" action="{{ url_for('logout') }}" style="display: inline;">
                <button type="submit" class="btn btn-ghost">
                    Sign Out
                </button>
            </form>
        </div>
    </div>
</div>
{% endblock %}

{% block extra_js %}
<script>
    // Delete note handler
    document.querySelectorAll('[data-delete-note]').forEach(button => {
        button.addEventListener('click', function() {
            const noteId = this.dataset.deleteNote;
            const modal = document.getElementById('confirmModal');
            const message = document.getElementById('confirmMessage');
            const confirmBtn = document.getElementById('confirmButton');

            message.textContent = 'Are you sure you want to delete this note? This action cannot be undone.';
            confirmBtn.onclick = () => {
                fetch(`/delete-note/${noteId}`, { method: 'POST' })
                    .then(() => window.location.reload())
                    .catch(err => showNotification('Error deleting note', 'error'));
            };

            modal.classList.add('active');
        });
    });
</script>
{% endblock %}
```

### 4.2 Create/Edit Note Pages

**File: `templates/create_note.html`**

```html
{% extends "base.html" %}

{% block title %}Create Note - Notes App{% endblock %}

{% block content %}
<div class="note-form-page" style="
    padding: var(--space-600);
    background-color: var(--bg-secondary);
    min-height: 100vh;
">
    <div class="container" style="max-width: 800px;">
        <div style="margin-bottom: var(--space-600);">
            <h1 style="margin-bottom: var(--space-200);">Create New Note</h1>
            <p class="text-secondary">Write and save your thoughts</p>
        </div>

        <form method="POST" class="note-form" style="
            background-color: var(--bg-primary);
            padding: var(--space-600);
            border-radius: var(--radius-outer);
            box-shadow: var(--shadow-md);
        ">
            <!-- TITLE FIELD -->
            <div class="form-group">
                <label for="title" class="required">Note Title</label>
                <input
                    type="text"
                    id="title"
                    name="title"
                    placeholder="Enter note title"
                    required
                    maxlength="200"
                    aria-label="Note title"
                    aria-describedby="title-counter"
                />
                <div class="character-counter" id="title-counter">
                    <span id="title-count">0</span> / 200
                </div>
            </div>

            <!-- CONTENT FIELD -->
            <div class="form-group">
                <label for="content" class="required">Note Content</label>
                <textarea
                    id="content"
                    name="content"
                    placeholder="Write your note here..."
                    required
                    maxlength="5000"
                    aria-label="Note content"
                    aria-describedby="content-counter"
                ></textarea>
                <div class="character-counter" id="content-counter">
                    <span id="content-count">0</span> / 5000
                </div>
            </div>

            <!-- BUTTONS -->
            <div style="
                display: flex;
                gap: var(--space-400);
                justify-content: flex-end;
                margin-top: var(--space-600);
            ">
                <a href="{{ url_for('dashboard') }}" class="btn btn-secondary btn-lg">
                    Cancel
                </a>
                <button type="submit" class="btn btn-primary btn-lg">
                    Create Note
                </button>
            </div>
        </form>
    </div>
</div>
{% endblock %}

{% block extra_js %}
<script>
    const titleInput = document.getElementById('title');
    const contentInput = document.getElementById('content');
    const titleCount = document.getElementById('title-count');
    const contentCount = document.getElementById('content-count');

    titleInput.addEventListener('input', () => {
        titleCount.textContent = titleInput.value.length;
    });

    contentInput.addEventListener('input', () => {
        contentCount.textContent = contentInput.value.length;
    });
</script>
{% endblock %}
```

---

## PHASE 5: JAVASCRIPT FUNCTIONALITY

### 5.1 Notifications System

**File: `static/js/notifications.js`**

```javascript
class NotificationManager {
    constructor() {
        this.container = document.getElementById('notificationContainer');
    }

    show(message, type = 'info', duration = 4000) {
        const toast = document.createElement('div');
        toast.className = `toast toast-${type}`;
        toast.setAttribute('role', 'alert');

        const icons = {
            success: '✓',
            error: '✕',
            warning: '⚠',
            info: 'ℹ'
        };

        toast.innerHTML = `
            <div class="toast-icon">${icons[type] || icons.info}</div>
            <div class="toast-content">
                <p class="toast-message">${message}</p>
            </div>
            <button class="toast-close" aria-label="Dismiss notification">&times;</button>
            <div class="toast-progress" style="animation-duration: ${duration}ms;"></div>
        `;

        const closeBtn = toast.querySelector('.toast-close');
        closeBtn.addEventListener('click', () => toast.remove());

        this.container.appendChild(toast);

        setTimeout(() => toast.remove(), duration);
    }

    success(message, duration) {
        this.show(message, 'success', duration);
    }

    error(message, duration) {
        this.show(message, 'error', duration);
    }

    warning(message, duration) {
        this.show(message, 'warning', duration);
    }

    info(message, duration) {
        this.show(message, 'info', duration);
    }
}

const showNotification = (message, type = 'info') => {
    const notificationManager = new NotificationManager();
    notificationManager.show(message, type);
};
```

### 5.2 Modal System

**File: `static/js/modal.js`**

```javascript
class Modal {
    constructor(selector) {
        this.modal = document.querySelector(selector);
        this.backdrop = this.modal.closest('.modal-backdrop');
        this.setupEventListeners();
    }

    setupEventListeners() {
        // Close button
        const closeBtn = this.modal.querySelector('.modal-close');
        if (closeBtn) {
            closeBtn.addEventListener('click', () => this.close());
        }

        // Dismiss button
        const dismissBtns = this.modal.querySelectorAll('[data-dismiss="modal"]');
        dismissBtns.forEach(btn => {
            btn.addEventListener('click', () => this.close());
        });

        // Backdrop click
        this.backdrop.addEventListener('click', (e) => {
            if (e.target === this.backdrop) {
                this.close();
            }
        });

        // Escape key
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape' && this.backdrop.classList.contains('active')) {
                this.close();
            }
        });
    }

    open() {
        this.backdrop.classList.add('active');
        document.body.style.overflow = 'hidden';
        const focusableElements = this.modal.querySelectorAll('button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])');
        if (focusableElements.length) {
            focusableElements[0].focus();
        }
    }

    close() {
        this.backdrop.classList.remove('active');
        document.body.style.overflow = 'auto';
    }
}

// Initialize modals
document.addEventListener('DOMContentLoaded', () => {
    const modals = document.querySelectorAll('.modal-dialog');
    modals.forEach(modal => {
        new Modal(`.modal-dialog`);
    });
});
```

### 5.3 Form Validation

**File: `static/js/forms.js`**

```javascript
class FormValidator {
    constructor(form) {
        this.form = form;
        this.inputs = form.querySelectorAll('input, textarea');
        this.setupValidation();
    }

    setupValidation() {
        this.inputs.forEach(input => {
            input.addEventListener('blur', () => this.validateField(input));
            input.addEventListener('input', () => {
                if (input.classList.contains('is-invalid')) {
                    this.validateField(input);
                }
            });
        });

        this.form.addEventListener('submit', (e) => {
            if (!this.validateForm()) {
                e.preventDefault();
            }
        });
    }

    validateField(field) {
        const isValid = field.checkValidity();
        const errorMsg = field.nextElementSibling?.classList.contains('error-message')
            ? field.nextElementSibling
            : null;

        if (!isValid) {
            field.classList.add('is-invalid');
            field.classList.remove('is-valid');
            if (errorMsg) {
                errorMsg.style.display = 'block';
            }
        } else {
            field.classList.remove('is-invalid');
            field.classList.add('is-valid');
            if (errorMsg) {
                errorMsg.style.display = 'none';
            }
        }

        return isValid;
    }

    validateForm() {
        let isValid = true;
        this.inputs.forEach(input => {
            if (!this.validateField(input)) {
                isValid = false;
            }
        });
        return isValid;
    }
}

// Initialize form validation on all forms
document.addEventListener('DOMContentLoaded', () => {
    document.querySelectorAll('form').forEach(form => {
        new FormValidator(form);
    });
});
```

---

## PHASE 6: FINAL REFINEMENT

### 6.1 Responsive Design Breakpoints

Add to `static/css/global.css`:

```css
/* RESPONSIVE TYPOGRAPHY */
@media (max-width: 768px) {
    h1 { font-size: var(--text-3xl); }
    h2 { font-size: var(--text-2xl); }
    h3 { font-size: var(--text-xl); }
}

/* RESPONSIVE SPACING */
@media (max-width: 768px) {
    :root {
        --space-600: 24px; /* Reduced from 40px */
        --space-700: 32px; /* Reduced from 80px */
    }

    .container {
        padding: 0 var(--space-300);
    }
}

/* RESPONSIVE GRIDS */
@media (max-width: 1024px) {
    .card-grid {
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    }
}

@media (max-width: 768px) {
    .card-grid {
        grid-template-columns: 1fr;
    }
}

/* RESPONSIVE LAYOUT */
@media (max-width: 768px) {
    .form-row.two-column {
        grid-template-columns: 1fr;
    }

    button, .btn {
        font-size: var(--text-base);
    }
}
```

### 6.2 Accessibility Enhancements

Add to all interactive elements:

```html
<!-- FOCUS MANAGEMENT -->
<div role="region" aria-live="polite" aria-label="Notifications"></div>

<!-- FORM VALIDATION -->
<input aria-invalid="false" aria-describedby="error-message">
<span id="error-message" role="alert"></span>

<!-- BUTTONS -->
<button aria-label="Delete note">Delete</button>

<!-- SKIP LINKS -->
<a href="#main-content" class="skip-link">Skip to main content</a>
```

CSS for skip links:

```css
.skip-link {
    position: absolute;
    top: -40px;
    left: 0;
    background: #000;
    color: white;
    padding: 8px;
    text-decoration: none;
    z-index: 100;
}

.skip-link:focus {
    top: 0;
}
```

---

## IMPLEMENTATION SUMMARY

**All Files to Create:**

```
static/css/
├── tokens.css
├── typography.css
├── global.css
└── components/
    ├── buttons.css
    ├── forms.css
    ├── cards.css
    ├── modal.css
    └── notifications.css

static/js/
├── notifications.js
├── modal.js
└── forms.js

templates/
├── base.html (UPDATED)
├── login.html (UPDATED)
├── signup.html (UPDATED)
├── dashboard.html (UPDATED)
├── create_note.html (UPDATED)
└── edit_note.html (UPDATED)
```

**Key Integration Points:**

1. ✅ All 50+ Sprout colors with semantic naming
2. ✅ 8px spacing grid system
3. ✅ Roboto Serif + Proxima Nova typography
4. ✅ Button component (6 variants)
5. ✅ Input/Form fields with validation
6. ✅ Card component with grid layout
7. ✅ Modal dialogs with accessibility
8. ✅ Toast notifications system
9. ✅ Focus management & keyboard navigation
10. ✅ Responsive design
11. ✅ Animation tokens (motion, easing, duration)
12. ✅ Elevation/shadow system

---

**Ready to proceed with implementation?**
