# Semantic Layout Implementation Challenge

## Problem Statement

Build a production-ready semantic HTML layout using proper landmark elements that passes accessibility audits and screen reader navigation tests.

## Requirements

### Core Implementation
You must create a complete webpage that demonstrates:

1. **Semantic Structure**: Use all required HTML5 semantic elements
   - `<header>` - Site/page header with branding and primary navigation
   - `<nav>` - Navigation menu with proper list structure
   - `<main>` - Primary content area (only one per page)
   - `<aside>` - Sidebar content related to main content
   - `<section>` - Thematic content groupings with headings
   - `<article>` - Self-contained content pieces
   - `<footer>` - Site/page footer with secondary information

2. **Heading Hierarchy**: Implement proper heading structure
   - Exactly **one `<h1>`** per page representing the main topic
   - Logical heading progression (h1 → h2 → h3, no skipping levels)
   - Each `<section>` and `<article>` must have a heading
   - Minimum 3 levels of heading hierarchy demonstrated

3. **Content Requirements**: Include realistic content
   - Header: Logo/brand, primary navigation (5+ items)
   - Main: At least 2 articles with 3+ sections each
   - Aside: Related links, recent posts, or supplementary info
   - Footer: Copyright, secondary nav, contact info

### Technical Constraints

- **HTML5 Doctype**: Must use `<!DOCTYPE html>`
- **Valid HTML**: Pass W3C markup validation
- **No CSS Framework**: Pure HTML/CSS only (no Bootstrap, Tailwind, etc.)
- **Responsive**: Must work on mobile and desktop
- **Cross-browser**: Support Chrome, Firefox, Safari, Edge

### Accessibility Requirements

- **Landmark Navigation**: Screen readers can navigate by landmarks
- **Skip Links**: Provide "Skip to main content" functionality
- **Focus Management**: Visible focus indicators on all interactive elements
- **Screen Reader Test**: Must pass basic screen reader navigation
- **WCAG 2.1 AA**: Meet accessibility guidelines

## Input Specifications

Create these files:
- `index.html` - Main semantic layout
- `styles.css` - Styling (semantic-first approach)
- `README.md` - Setup and testing instructions

## Expected Output

### Visual Structure
```
┌─────────────────────────────────────┐
│ HEADER (logo + nav)                 │
├─────────────────────────────────────┤
│ MAIN CONTENT        │ ASIDE         │
│ ┌─────────────────┐ │ ┌───────────┐ │
│ │ ARTICLE 1       │ │ │ Related   │ │
│ │ ├─ Section A    │ │ │ Links     │ │
│ │ ├─ Section B    │ │ │           │ │
│ │ └─ Section C    │ │ └───────────┘ │
│ └─────────────────┘ │               │
│ ┌─────────────────┐ │ ┌───────────┐ │
│ │ ARTICLE 2       │ │ │ Recent    │ │
│ │ ├─ Section A    │ │ │ Posts     │ │
│ │ └─ Section B    │ │ │           │ │
│ └─────────────────┘ │ └───────────┘ │
├─────────────────────────────────────┤
│ FOOTER (copyright + secondary nav)  │
└─────────────────────────────────────┘
```

### Document Outline
```
1. Page Title (h1)
   1.1. Article 1 Title (h2)
        1.1.1. Section A (h3)
        1.1.2. Section B (h3)
        1.1.3. Section C (h3)
   1.2. Article 2 Title (h2)
        1.2.1. Section A (h3)
        1.2.2. Section B (h3)
```

## Test Cases

### Test Case 1: HTML Validation
```bash
# Input: index.html
# Expected: 0 errors, 0 warnings from W3C validator
```

### Test Case 2: Semantic Structure
```html
<!-- Must contain exactly these elements -->
<header>...</header>     <!-- 1 instance -->
<nav>...</nav>          <!-- 1+ instances -->
<main>...</main>        <!-- exactly 1 instance -->
<aside>...</aside>      <!-- 1+ instances -->
<section>...</section>  <!-- 2+ instances -->
<article>...</article>  <!-- 2+ instances -->
<footer>...</footer>    <!-- 1 instance -->
```

### Test Case 3: Heading Hierarchy
```html
<!-- Must follow this pattern -->
<h1>...</h1>           <!-- exactly 1 -->
<h2>...</h2>           <!-- 2+ instances -->
<h3>...</h3>           <!-- 3+ instances -->
<!-- No h4 without h3, no h3 without h2, etc. -->
```

### Test Case 4: Screen Reader Navigation
```
# Using NVDA/JAWS/VoiceOver:
# 1. Can navigate by landmarks (D key)
# 2. Can navigate by headings (H key)
# 3. Skip link works (Tab → Enter)
# 4. All content is reachable and logical
```

## Acceptance Criteria

### Functional Requirements ✅
- [ ] All semantic elements present and properly nested
- [ ] Exactly one h1 per page
- [ ] Logical heading hierarchy (no skipped levels)
- [ ] Skip link functionality works
- [ ] Responsive layout (mobile + desktop)

### Quality Requirements ✅
- [ ] Passes W3C HTML validation
- [ ] Passes WAVE accessibility checker
- [ ] Screen reader can navigate all content
- [ ] Visible focus indicators on interactive elements
- [ ] Semantic meaning clear without CSS

### Documentation Requirements ✅
- [ ] README with setup instructions
- [ ] Testing procedures documented
- [ ] Screenshots of layout and accessibility tools
- [ ] Screen reader testing results

## Bonus Challenges

1. **Advanced Semantics**: Add `<time>`, `<address>`, `<details>` elements
2. **Microdata**: Include structured data markup
3. **Print Styles**: Optimize layout for printing
4. **Performance**: Achieve 100% Lighthouse accessibility score

## Common Pitfalls to Avoid

- Using `<div>` instead of semantic elements
- Multiple `<main>` elements
- Skipping heading levels (h1 → h3)
- Missing headings in sections/articles
- Inaccessible navigation menus
- No skip links for keyboard users
- Poor focus management

## Submission Format

```
semantic-layout-challenge/
├── index.html          # Main implementation
├── styles.css          # Styling
├── README.md           # Documentation
├── screenshots/        # Visual proof
│   ├── desktop.png
│   ├── mobile.png
│   └── accessibility-audit.png
└── tests/             # Test results
    ├── w3c-validation.png
    └── screen-reader-test.md
```