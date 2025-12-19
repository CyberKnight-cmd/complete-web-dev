# HTML Document Structure & Semantics - Notes

## Core Concepts

### Document Structure Fundamentals

HTML documents follow a hierarchical tree structure that browsers parse to create the DOM (Document Object Model). Every HTML document must have:

1. **DOCTYPE Declaration**: Tells the browser which HTML version to use
2. **HTML Root Element**: Contains all other elements
3. **Head Section**: Metadata not displayed to users
4. **Body Section**: Visible content

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document Structure Example</title>
</head>
<body>
    <!-- Visible content goes here -->
</body>
</html>
```

### Semantic HTML Elements

Semantic elements provide meaning to content, not just presentation:

#### Sectioning Elements
- `<header>`: Introductory content or navigation
- `<nav>`: Navigation links
- `<main>`: Primary content of document
- `<section>`: Thematic grouping of content
- `<article>`: Self-contained content
- `<aside>`: Sidebar content
- `<footer>`: Footer information

#### Text-Level Semantics
- `<em>`: Emphasized text (stress emphasis)
- `<strong>`: Important text (strong importance)
- `<mark>`: Highlighted text
- `<time>`: Date/time information

```html
<article>
    <header>
        <h1>Article Title</h1>
        <time datetime="2024-01-15">January 15, 2024</time>
    </header>
    
    <section>
        <h2>Introduction</h2>
        <p>This is <em>emphasized</em> and this is <strong>important</strong>.</p>
    </section>
    
    <aside>
        <p>Related information goes here.</p>
    </aside>
    
    <footer>
        <p>Article footer content.</p>
    </footer>
</article>
```

## Mental Models

### Document Outline Algorithm
Browsers create an outline based on heading levels and sectioning elements:
- Each sectioning element creates a new section
- Headings create subsections within their containing section
- Screen readers use this outline for navigation

### Accessibility Implications
- Screen readers navigate by landmarks (header, nav, main, etc.)
- Proper semantic structure enables "skip to content" functionality
- ARIA roles complement but don't replace semantic HTML

## Common Pitfalls

1. **Div Soup**: Using `<div>` instead of semantic elements
2. **Improper Nesting**: Block elements inside inline elements
3. **Missing Landmarks**: No main, header, or nav elements
4. **Incorrect Sectioning**: Misusing article vs section

## Debugging Techniques

1. Use browser DevTools to inspect DOM structure
2. Validate with W3C Markup Validator
3. Test with screen readers (NVDA, JAWS, VoiceOver)
4. Use accessibility testing tools (axe, WAVE)