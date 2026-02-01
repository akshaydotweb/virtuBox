# Sprout Seeds Form Spacing Guide

**Source:** Official Sprout Social Seeds Design System  
**Last Updated:** February 1, 2026

---

## KEY FINDING: Form Field Spacing

### Stack Component (Default)
According to Sprout Seeds **Stack Component** documentation:
```
"By default, the Stack component will distribute items vertically using 
space token 300 (8px) between the items."
```

**This is the standard spacing between form fields in Sprout Seeds.**

---

## Complete Form Spacing Breakdown

### Within a Single Form Field
```
┌─────────────────────────────────┐
│     Label                       │  ← Text: 14px, Weight: 600 (SemiBold)
│     (margin-bottom: 8px)        │  ← Size 300
├─────────────────────────────────┤
│     Input Field                 │  ← Height: 40px
│     (padding: 12px 16px)        │  ← Internal spacing
├─────────────────────────────────┤
│     Helper Text (optional)      │  ← Text: 12px, margin-top: 4px (Size 200)
└─────────────────────────────────┘
```

### Between Form Fields (CRITICAL)
**Sprout Seeds Default: 8px (Size 300)**

```
┌─────────────────────────────────┐
│     Label 1                     │
│                                 │
│     Input 1                     │
│                                 │
│     Helper Text 1               │
└─────────────────────────────────┘
         ↓ 8px gap (Size 300) ↓     ← STANDARD between form groups
┌─────────────────────────────────┐
│     Label 2                     │
│                                 │
│     Input 2                     │
│                                 │
│     Helper Text 2               │
└─────────────────────────────────┘
```

### Form Container Spacing
- **Top/Bottom padding:** 32px (Size 500) or 40px (Size 600)
- **Left/Right padding:** 32px (Size 500) or 40px (Size 600)
- **Gap between form groups:** 8px (Size 300) ← **PRIMARY**
- **Gap between sections:** 32px (Size 500) or 40px (Size 600)

---

## When to Use Different Spacing

| Spacing Level | Token | Pixels | Use Case |
|---|---|---|---|
| **Micro** | Size 200 | 4px | Helper text margin-top, internal icon gaps |
| **Compact** | Size 300 | **8px** | **Between form fields (default)** |
| **Standard** | Size 400 | 16px | Padding within components, label margins |
| **Comfortable** | Size 500 | 32px | Card padding, section dividers |
| **Large** | Size 600 | 40px | Page padding, major section gaps |
| **XL** | Size 700 | 80px | Header margin, major layout gaps |

---

## Form Examples from Sprout Seeds

### Example 1: Basic Form Field Group
```html
<Box display="flex" flexDirection="column" gap={300}>
  <!-- Form Field 1 -->
  <FormField label="First Name">
    {props => <Input {...props} />}
  </FormField>
  
  <!-- Form Field 2 (8px gap from above) -->
  <FormField label="Email">
    {props => <Input {...props} />}
  </FormField>
  
  <!-- Form Field 3 (8px gap from above) -->
  <FormField label="Password">
    {props => <Input {...props} />}
  </FormField>
</Box>
```

### Example 2: Using Stack Component (Recommended)
```html
<Stack space={300}>  <!-- 8px between items -->
  <FormField label="First Name">
    {props => <Input {...props} />}
  </FormField>
  
  <FormField label="Email">
    {props => <Input {...props} />}
  </FormField>
  
  <FormField label="Password">
    {props => <Input {...props} />}
  </FormField>
</Stack>
```

### Example 3: Multi-section Form
```html
<Box display="flex" flexDirection="column" gap={500}>
  <!-- Section 1 with 8px between fields -->
  <Box display="flex" flexDirection="column" gap={300}>
    <FormField label="First Name">
      {props => <Input {...props} />}
    </FormField>
    <FormField label="Last Name">
      {props => <Input {...props} />}
    </FormField>
  </Box>
  
  <!-- Section 2 (32px gap from section 1) -->
  <Box display="flex" flexDirection="column" gap={300}>
    <FormField label="Email">
      {props => <Input {...props} />}
    </FormField>
    <FormField label="Confirm Email">
      {props => <Input {...props} />}
    </FormField>
  </Box>
</Box>
```

---

## Label Spacing Details

### Label to Input
**8px (Size 300) margin-bottom on label**

Code example:
```css
label {
  margin-bottom: var(--space-300);  /* 8px */
}
```

**OR using mb prop:**
```jsx
<Label htmlFor="email" mb={300}>
  Email Address
</Label>
```

---

## Helper Text Spacing Details

### Helper Text to Input
**4px (Size 200) margin-top on helper text**

Code example:
```css
.helper-text {
  margin-top: var(--space-200);  /* 4px */
}
```

**OR using mt prop:**
```jsx
<Text as="p" mt={200} color="text.secondary">
  We'll never share your email
</Text>
```

---

## ERROR MESSAGES & VALIDATION

### Error Message Spacing
- **Margin above error:** 4px (Size 200)
- **Font size:** 12px
- **Color:** Red 700 or status.error
- **Placement:** Below input field, before helper text

---

## FORM BUTTON SPACING

### Button Container Below Form
- **Margin-top from last form field:** 32px (Size 500) or 40px (Size 600)
- **Gap between buttons:** 8px (Size 300) for horizontal stacking

Code example:
```html
<Box display="flex" flexDirection="column" gap={500}>
  <!-- Form fields with 8px gap -->
  <Stack space={300}>
    <FormField label="Username">...</FormField>
    <FormField label="Password">...</FormField>
  </Stack>
  
  <!-- Buttons (32px above) -->
  <Box display="flex" gap={300}>
    <Button>Cancel</Button>
    <Button appearance="primary">Submit</Button>
  </Box>
</Box>
```

---

## Form Layout CSS (Correct Approach)

```css
/* Form container */
.form {
  display: flex;
  flex-direction: column;
  gap: var(--space-300);  /* 8px between form groups */
}

/* Within form field */
.form-field {
  display: flex;
  flex-direction: column;
  gap: 0;  /* No gap, use margins instead */
}

.form-field label {
  margin-bottom: var(--space-300);  /* 8px label to input */
  font-size: var(--text-sm);
  font-weight: var(--font-weight-semibold);
}

.form-field input {
  /* input styles */
}

.form-field .helper-text {
  margin-top: var(--space-200);  /* 4px input to helper */
  font-size: var(--text-xs);
  color: var(--text-secondary);
}

/* Between form groups */
.form-field + .form-field {
  margin-top: var(--space-300);  /* 8px between complete fields */
}

/* Buttons below form */
.form-buttons {
  margin-top: var(--space-500);  /* 32px above buttons */
  display: flex;
  gap: var(--space-300);  /* 8px between buttons */
}
```

---

## MOBILE RESPONSIVE SPACING

### Mobile (≤ 576px)
- **Form field gap:** 8px (Size 300) - **SAME as desktop**
- **Form padding:** 16px (Size 400) - reduced from 32px
- **Button margin-top:** 24px (Size 450) - reduced from 32px
- **Label margin:** 8px (Size 300) - **SAME**
- **Helper margin:** 4px (Size 200) - **SAME**

### Tablet (576px - 768px)
- **Form field gap:** 8px (Size 300) - **SAME as desktop**
- **Form padding:** 24px (Size 450)
- **Other spacing:** Same as desktop

### Desktop (> 768px)
- **Form field gap:** 8px (Size 300) - **STANDARD**
- **Form padding:** 32px (Size 500) or 40px (Size 600)
- **Button margin-top:** 32px (Size 500)

---

## COMMON MISTAKES TO AVOID

❌ **Using 32px between form fields**
- Too much whitespace
- Breaks visual grouping
- Not aligned with Sprout Standards

✅ **Using 8px between form fields**
- Proper visual grouping
- Consistent with Stack default
- Follows Sprout design system

---

❌ **Forgetting margin-bottom on labels**
- Creates confusion between label and input
- Impacts accessibility

✅ **Adding 8px margin-bottom on labels**
- Clear visual separation
- Proper spacing hierarchy
- Better accessibility

---

❌ **Using flexbox gap for entire form**
- `gap: 32px` applies between ALL children
- Overrides proper spacing hierarchy

✅ **Nesting spacing appropriately**
- Form-level gap: 8px (Size 300)
- Section-level gap: 32px (Size 500)
- Page-level gap: 80px (Size 700)

---

## ACCESSIBILITY CONSIDERATIONS

✓ **Proper spacing helps with:**
- Reducing cognitive load
- Improving visual hierarchy
- Making form easier to scan
- Supporting users with motor impairments
- Better focus indication visibility

✓ **Label spacing (8px) ensures:**
- Label clearly associated with input
- Larger click target area
- Better touch accessibility

---

## IMPLEMENTATION CHECKLIST

- [ ] Form container: `gap: 8px` (Size 300) between fields
- [ ] Label: `margin-bottom: 8px` (Size 300)
- [ ] Helper text: `margin-top: 4px` (Size 200)
- [ ] Buttons: `margin-top: 32px` (Size 500) from last field
- [ ] Button gap: `gap: 8px` (Size 300) between buttons
- [ ] Mobile padding: Reduced to 16px (Size 400)
- [ ] Responsive: Same gaps on all breakpoints
- [ ] Focus states: Maintained and visible
- [ ] ARIA labels: Present and correct
- [ ] Test: Keyboard navigation, screen readers

---

## SPROUT SEEDS REFERENCE

**Stack Component:** Default space={300}  
**FormField Component:** Label mb={300}, with helperText support  
**Input Component:** Works within FormField for proper spacing  
**Space Tokens:** 200=4px, 300=8px, 400=16px, 500=32px, 600=40px  

**Source:** https://seeds.sproutsocial.com/components/stack/  
**Source:** https://seeds.sproutsocial.com/components/form-field/  
**Source:** https://seeds.sproutsocial.com/patterns/forms/

---

## CONCLUSION

**Form field spacing in Sprout Seeds is 8px (Size 300), NOT 32px.**

The 32px spacing (Size 500) is for:
- Card/container padding
- Section dividers
- Major layout gaps

The 8px spacing (Size 300) is for:
- **Between form fields (default Stack gap)**
- Between buttons
- Between list items
- Between chips/tags

Current implementation needs adjustment: **32px → 8px**
