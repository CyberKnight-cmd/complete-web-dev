# Text Semantics & Hierarchy (h1–h6, p, small, code) - Notes

## Core Concepts

### HTML Heading Hierarchy

HTML provides six levels of headings (h1-h6) that create a logical document structure. This hierarchy is crucial for accessibility, SEO, and document organization.

#### Heading Level Rules
1. **h1**: Main page title (only one per page recommended)
2. **h2**: Major section headings
3. **h3**: Subsection headings under h2
4. **h4-h6**: Further subdivisions as needed

```html
<h1>Main Article Title</h1>
  <h2>Introduction</h2>
    <h3>Background Information</h3>
    <h3>Problem Statement</h3>
  <h2>Methodology</h2>
    <h3>Data Collection</h3>
      <h4>Survey Design</h4>
      <h4>Sample Selection</h4>
    <h3>Analysis Approach</h3>
  <h2>Results</h2>
  <h2>Conclusion</h2>
```

### Document Outline Algorithm

Browsers and assistive technologies create a document outline based on heading hierarchy:

#### Correct Hierarchy
```html
<h1>Website Title</h1>
<h2>Section 1</h2>
<h3>Subsection 1.1</h3>
<h3>Subsection 1.2</h3>
<h2>Section 2</h2>
<h3>Subsection 2.1</h3>
```

#### Incorrect Hierarchy (Skipping Levels)
```html
<!-- WRONG: Skipping from h1 to h3 -->
<h1>Website Title</h1>
<h3>Section 1</h3> <!-- Should be h2 -->
<h5>Subsection</h5> <!-- Should be h3 -->
```

### Text Semantic Elements

#### Paragraph Structure
The `<p>` element represents a paragraph of text and is a block-level element.

```html
<p>This is a standard paragraph containing regular text content. 
   Paragraphs automatically add spacing above and below.</p>

<p>Each paragraph should contain a single idea or concept. 
   Break content into multiple paragraphs for better readability.</p>
```

#### Emphasis vs Importance

**Emphasis (`<em>`)**: Stress emphasis, changes meaning
```html
<p>I <em>love</em> chocolate cake.</p>
<p>I love <em>chocolate</em> cake.</p>
<!-- Different emphasis changes the meaning -->
```

**Strong Importance (`<strong>`)**: Strong importance, urgency
```html
<p><strong>Warning:</strong> This action cannot be undone.</p>
<p>The deadline is <strong>tomorrow</strong> at 5 PM.</p>
```

#### Small Text Element
The `<small>` element represents side comments, legal text, or fine print.

```html
<p>Our premium service costs $99/month.</p>
<p><small>*Price subject to change. Terms and conditions apply.</small></p>

<footer>
    <p><small>&copy; 2024 Company Name. All rights reserved.</small></p>
</footer>
```

### Code Representation

#### Inline Code
Use `<code>` for short code snippets within text:

```html
<p>Use the <code>console.log()</code> function to debug JavaScript.</p>
<p>The <code>&lt;div&gt;</code> element is a generic container.</p>
```

#### Code Blocks
For multi-line code, combine `<pre>` and `<code>`:

```html
<pre><code>function greetUser(name) {
    console.log("Hello, " + name + "!");
}

greetUser("World");</code></pre>
```

#### Keyboard Input
Use `<kbd>` for keyboard shortcuts:

```html
<p>Press <kbd>Ctrl</kbd> + <kbd>C</kbd> to copy text.</p>
<p>Use <kbd>F12</kbd> to open developer tools.</p>
```

#### Sample Output
Use `<samp>` for sample program output:

```html
<p>The program will display:</p>
<samp>Hello, World!
Process completed successfully.</samp>
```

### Additional Text Semantics

#### Quotations
```html
<!-- Inline quotations -->
<p>Einstein said, <q>Imagination is more important than knowledge.</q></p>

<!-- Block quotations -->
<blockquote cite="https://example.com/source">
    <p>The best way to predict the future is to invent it.</p>
    <footer>— <cite>Alan Kay</cite></footer>
</blockquote>
```

#### Abbreviations and Acronyms
```html
<p>The <abbr title="World Wide Web">WWW</abbr> was invented by Tim Berners-Lee.</p>
<p>We use <abbr title="HyperText Markup Language">HTML</abbr> for web structure.</p>
```

#### Definitions
```html
<p><dfn>Semantic HTML</dfn> is the use of HTML markup to reinforce 
   the semantics, or meaning, of the information in web pages.</p>
```

## Mental Models

### Screen Reader Navigation
Screen readers use heading hierarchy to:
1. Generate page outlines
2. Allow users to jump between sections
3. Understand content structure
4. Navigate efficiently through content

### SEO Impact
Search engines use heading hierarchy to:
1. Understand content structure
2. Determine topic relevance
3. Create featured snippets
4. Rank content appropriately

### Visual Hierarchy
Proper semantic markup enables:
1. Consistent styling with CSS
2. Responsive design adaptation
3. Theme customization
4. Print stylesheet optimization

## Common Pitfalls

### 1. Heading Level Skipping
```html
<!-- WRONG -->
<h1>Main Title</h1>
<h3>Section</h3> <!-- Skipped h2 -->

<!-- CORRECT -->
<h1>Main Title</h1>
<h2>Section</h2>
```

### 2. Using Headings for Styling
```html
<!-- WRONG: Using h4 just for smaller text -->
<h1>Main Title</h1>
<h4>Subtitle</h4> <!-- Should be styled p or h2 -->

<!-- CORRECT -->
<h1>Main Title</h1>
<p class="subtitle">Subtitle</p>
```

### 3. Misusing Small Element
```html
<!-- WRONG: Using small for general text sizing -->
<p><small>This is just smaller text</small></p>

<!-- CORRECT: Using small for fine print -->
<p>Product price: $99</p>
<p><small>*Shipping not included</small></p>
```

### 4. Improper Code Escaping
```html
<!-- WRONG: Not escaping HTML in code examples -->
<code><div>Hello</div></code>

<!-- CORRECT: Properly escaped HTML -->
<code>&lt;div&gt;Hello&lt;/div&gt;</code>
```

### 5. Div Soup
```html
<!-- WRONG: Using divs instead of semantic elements -->
<div class="heading">Section Title</div>
<div class="paragraph">Content goes here.</div>

<!-- CORRECT: Using semantic elements -->
<h2>Section Title</h2>
<p>Content goes here.</p>
```

## Debugging Techniques

### 1. Document Outline Tools
- HTML5 Outliner browser extension
- WAVE Web Accessibility Evaluator
- Browser developer tools accessibility tree

### 2. Screen Reader Testing
- NVDA (Windows, free)
- JAWS (Windows, commercial)
- VoiceOver (macOS, built-in)
- TalkBack (Android, built-in)

### 3. Validation Tools
- W3C Markup Validator
- HTML5 validator
- Accessibility checkers (axe, WAVE)

### 4. Browser DevTools
- Elements panel for DOM inspection
- Accessibility tree view
- Computed styles panel
- Console for JavaScript testing

## Best Practices

1. **Use only one h1 per page** for the main title
2. **Don't skip heading levels** - maintain logical hierarchy
3. **Use headings for structure, not styling** - style with CSS
4. **Write descriptive headings** that summarize section content
5. **Use semantic text elements** appropriately (em, strong, code)
6. **Escape HTML entities** in code examples
7. **Test with screen readers** to ensure proper navigation
8. **Validate markup** regularly with W3C validator