# Adding CSS: inline, embedded, external (best practice) - Notes

## Core Concepts

### Three Methods of Adding CSS

CSS can be added to HTML documents in three ways, each with different use cases and implications.

#### 1. Inline CSS
Applied directly to HTML elements using the `style` attribute:
```html
<p style="color: blue; font-size: 16px;">This text is styled inline.</p>
<div style="background-color: #f0f0f0; padding: 20px;">Inline styled div</div>
```

#### 2. Embedded CSS
Placed within `<style>` tags in the document's `<head>`:
```html
<head>
    <style>
        p { color: blue; font-size: 16px; }
        .highlight { background-color: yellow; }
        #header { font-weight: bold; }
    </style>
</head>
```

#### 3. External CSS
Linked from separate `.css` files:
```html
<head>
    <link rel="stylesheet" href="styles.css">
    <link rel="stylesheet" href="theme.css">
</head>
```

## Method Comparison

### Inline CSS
**Pros:**
- Highest specificity (overrides other styles)
- Quick testing and debugging
- No additional HTTP requests

**Cons:**
- Not reusable
- Difficult to maintain
- Mixes content with presentation
- No caching benefits

### Embedded CSS
**Pros:**
- Styles specific to one page
- No additional HTTP requests
- Can use selectors and media queries

**Cons:**
- Not reusable across pages
- Increases HTML file size
- No caching benefits

### External CSS
**Pros:**
- Reusable across multiple pages
- Cacheable by browsers
- Separates content from presentation
- Easier maintenance and updates
- Smaller HTML files

**Cons:**
- Additional HTTP request
- Render-blocking resource

## Best Practices

### 1. Use External CSS (Recommended)
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Best Practice Example</title>
    <link rel="stylesheet" href="css/main.css">
</head>
<body>
    <h1 class="page-title">Welcome</h1>
    <p class="intro">This uses external CSS.</p>
</body>
</html>
```

### 2. Loading Order Matters
```html
<head>
    <!-- Load base styles first -->
    <link rel="stylesheet" href="css/reset.css">
    <link rel="stylesheet" href="css/base.css">
    
    <!-- Then component styles -->
    <link rel="stylesheet" href="css/components.css">
    
    <!-- Finally, page-specific styles -->
    <link rel="stylesheet" href="css/page.css">
</head>
```

### 3. Performance Optimization
```html
<head>
    <!-- Preload critical CSS -->
    <link rel="preload" href="css/critical.css" as="style">
    <link rel="stylesheet" href="css/critical.css">
    
    <!-- Load non-critical CSS asynchronously -->
    <link rel="preload" href="css/non-critical.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
    <noscript><link rel="stylesheet" href="css/non-critical.css"></noscript>
</head>
```

## Mental Models

### CSS Loading Process
1. Browser parses HTML
2. Discovers CSS links in `<head>`
3. Downloads CSS files (render-blocking)
4. Parses CSS and builds CSSOM
5. Combines DOM + CSSOM = Render Tree
6. Renders page

### Specificity Hierarchy
1. **Inline styles** (highest specificity)
2. **Embedded styles** (medium specificity)
3. **External styles** (lowest specificity)

Note: Specificity is actually calculated by selector type, not CSS location, but inline styles always win.

## Common Pitfalls

### 1. Overusing Inline Styles
```html
<!-- WRONG: Hard to maintain -->
<div style="color: red; font-size: 18px; margin: 10px; padding: 15px; background: #f0f0f0;">
    Content
</div>

<!-- CORRECT: Use classes -->
<div class="content-box">Content</div>
```

### 2. Missing CSS Files
```html
<!-- WRONG: Broken link -->
<link rel="stylesheet" href="styes.css"> <!-- Typo in filename -->

<!-- CORRECT: Verify file paths -->
<link rel="stylesheet" href="styles.css">
```

### 3. Incorrect MIME Type
```html
<!-- Server must serve CSS with correct MIME type -->
<!-- Content-Type: text/css -->
```

### 4. CSS in Body
```html
<!-- WRONG: CSS in body causes reflow -->
<body>
    <style>
        .late-style { color: red; }
    </style>
</body>

<!-- CORRECT: CSS in head -->
<head>
    <style>
        .early-style { color: red; }
    </style>
</head>
```

## Performance Considerations

### Critical CSS Inlining
```html
<head>
    <style>
        /* Critical above-the-fold styles */
        body { font-family: Arial, sans-serif; }
        .header { background: #333; color: white; }
    </style>
    
    <!-- Non-critical CSS loaded asynchronously -->
    <link rel="preload" href="full-styles.css" as="style" onload="this.rel='stylesheet'">
</head>
```

### CSS File Organization
```
css/
├── reset.css          # Browser reset
├── base.css           # Base typography and elements
├── layout.css         # Layout and grid systems
├── components.css     # Reusable components
├── utilities.css      # Utility classes
└── theme.css         # Colors and theming
```

## Debugging CSS Loading

### Check Network Tab
1. Open DevTools (F12)
2. Go to Network tab
3. Reload page
4. Look for CSS files in requests
5. Check for 404 errors or slow loading

### Inspect Applied Styles
1. Right-click element → Inspect
2. Check Styles panel
3. Look for crossed-out styles (overridden)
4. Verify CSS file sources

### Common Issues
- **404 errors**: Incorrect file paths
- **MIME type errors**: Server configuration
- **Caching issues**: Hard refresh (Ctrl+F5)
- **Specificity conflicts**: Inline overriding external