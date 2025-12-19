# Text Semantics & Hierarchy Demo

## Setup Instructions

1. Open `demo.html` in any modern web browser
2. Use browser DevTools to inspect the heading structure
3. Test with accessibility tools and screen readers

## Running the Demo

### Basic Viewing
- Open `demo.html` in your browser
- Observe the visual hierarchy created by proper heading structure
- Notice how different text semantic elements are rendered

### Testing Document Outline
1. **Browser DevTools Method:**
   - Press F12 to open DevTools
   - Go to Elements tab
   - Look for accessibility tree or outline view
   - Observe the hierarchical structure

2. **HTML5 Outliner:**
   - Install HTML5 Outliner browser extension
   - Run it on the demo page
   - View the generated document outline

3. **Screen Reader Testing:**
   - Use NVDA (Windows), VoiceOver (Mac), or browser screen reader
   - Navigate using heading shortcuts (H key in NVDA)
   - Listen to how content is announced

### Accessibility Testing
1. **WAVE Web Accessibility Evaluator:**
   - Install WAVE browser extension
   - Run evaluation on the demo page
   - Check heading structure and semantic elements

2. **axe DevTools:**
   - Install axe browser extension
   - Run accessibility audit
   - Review heading hierarchy results

## Key Features Demonstrated

### Proper Heading Hierarchy
- **h1**: Single main page title
- **h2**: Major section headings
- **h3**: Subsection headings
- **h4-h6**: Further subdivisions
- **No skipped levels**: Logical progression from h1 to h6

### Text Semantic Elements
- **`<em>`**: Stress emphasis that changes meaning
- **`<strong>`**: Strong importance or urgency
- **`<small>`**: Fine print, legal text, side comments
- **`<code>`**: Inline code snippets
- **`<pre><code>`**: Multi-line code blocks
- **`<kbd>`**: Keyboard input representation
- **`<samp>`**: Sample program output

### Additional Semantics
- **`<q>`**: Inline quotations
- **`<blockquote>`**: Block quotations with citations
- **`<abbr>`**: Abbreviations with full forms
- **`<dfn>`**: Definition of terms
- **`<cite>`**: Citations and references

## Testing Procedures

### 1. Visual Hierarchy Test
- Scan the page visually
- Verify heading sizes decrease logically
- Check that content flows naturally

### 2. Document Outline Test
```
Expected Outline Structure:
1. Text Semantics & Hierarchy Demonstration
   1.1. Heading Hierarchy Examples
        1.1.1. Correct Heading Structure
        1.1.2. Incorrect Heading Structure
   1.2. Text Semantic Elements
        1.2.1. Emphasis vs Strong Importance
        1.2.2. Small Text Usage
        1.2.3. Code Examples
   1.3. Additional Text Semantics
   1.4. Document Outline Structure
   1.5. Accessibility Benefits
```

### 3. Screen Reader Navigation Test
- Use heading navigation shortcuts
- Verify logical reading order
- Check that emphasis is properly announced
- Test code examples for clarity

### 4. HTML Validation
1. Copy page source
2. Paste into W3C Markup Validator
3. Verify no heading hierarchy errors
4. Check semantic element usage

## Expected Results

### Accessibility Benefits
- Clear document structure for screen readers
- Logical heading navigation
- Proper emphasis and importance indicators
- Accessible code examples

### SEO Benefits
- Well-structured content for search engines
- Clear topic hierarchy
- Semantic meaning preserved
- Improved content understanding

### User Experience
- Scannable content structure
- Logical information flow
- Clear visual hierarchy
- Consistent text semantics

## Common Issues to Avoid

1. **Skipping Heading Levels**: Don't jump from h1 to h3
2. **Multiple h1 Elements**: Use only one h1 per page
3. **Styling with Headings**: Don't use h4 just for smaller text
4. **Misusing Small**: Don't use `<small>` for general text sizing
5. **Unescaped Code**: Always escape HTML entities in code examples
6. **Div Soup**: Use semantic elements instead of styled divs

## Browser Compatibility

- All modern browsers support these semantic elements
- Older browsers may need CSS styling for consistent appearance
- Screen readers have excellent support for semantic HTML
- Mobile browsers handle semantic elements properly