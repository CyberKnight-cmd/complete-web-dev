# Performance: preconnect, preload (awareness) - Notes

## Core Concepts

### Resource Hints Overview
Resource hints help browsers optimize loading by providing advance information about resources the page will need.

### Preconnect
Establishes early connections to important third-party origins:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="preconnect" href="https://api.example.com">
```

### Preload
Loads critical resources early in the page lifecycle:
```html
<!-- Critical CSS -->
<link rel="preload" href="critical.css" as="style">

<!-- Hero image -->
<link rel="preload" href="hero.jpg" as="image">

<!-- Critical font -->
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>

<!-- Critical JavaScript -->
<link rel="preload" href="app.js" as="script">
```

### DNS Prefetch
Resolves DNS lookups for external domains:
```html
<link rel="dns-prefetch" href="//example.com">
<link rel="dns-prefetch" href="//cdn.example.com">
```

### Prefetch
Loads resources likely needed for future navigation:
```html
<link rel="prefetch" href="next-page.html">
<link rel="prefetch" href="likely-image.jpg">
```

## Use Cases

### Critical Resource Loading
```html
<!-- Above-the-fold CSS -->
<link rel="preload" href="above-fold.css" as="style" onload="this.onload=null;this.rel='stylesheet'">

<!-- Hero image -->
<link rel="preload" href="hero-image.jpg" as="image">

<!-- Critical JavaScript -->
<link rel="preload" href="critical.js" as="script">
```

### Third-Party Optimization
```html
<!-- Google Fonts optimization -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- Analytics -->
<link rel="dns-prefetch" href="//www.google-analytics.com">

<!-- CDN resources -->
<link rel="preconnect" href="https://cdn.jsdelivr.net">
```

### Font Loading Optimization
```html
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>
<style>
@font-face {
    font-family: 'CustomFont';
    src: url('font.woff2') format('woff2');
    font-display: swap;
}
</style>
```

## Mental Models

### Browser Loading Process
1. Parse HTML
2. Discover resource hints
3. Prioritize and fetch resources
4. Apply optimizations
5. Render page content

### Performance Impact
- **Preconnect**: Saves 100-500ms connection time
- **Preload**: Ensures critical resources load first
- **DNS Prefetch**: Reduces DNS lookup time
- **Prefetch**: Improves subsequent page loads

## Best Practices

### Preload Guidelines
- Only preload truly critical resources
- Limit to 3-5 preload hints per page
- Use appropriate `as` attribute
- Include `crossorigin` for fonts

### Preconnect Guidelines
- Limit to 4-6 connections
- Focus on critical third-party domains
- Include `crossorigin` when needed

## Common Pitfalls

### Overusing Preload
```html
<!-- WRONG: Too many preloads -->
<link rel="preload" href="image1.jpg" as="image">
<link rel="preload" href="image2.jpg" as="image">
<link rel="preload" href="image3.jpg" as="image">
<!-- ... 20 more preloads -->

<!-- CORRECT: Only critical resources -->
<link rel="preload" href="hero-image.jpg" as="image">
<link rel="preload" href="critical.css" as="style">
```

### Missing Crossorigin
```html
<!-- WRONG: Missing crossorigin for fonts -->
<link rel="preload" href="font.woff2" as="font" type="font/woff2">

<!-- CORRECT: Include crossorigin -->
<link rel="preload" href="font.woff2" as="font" type="font/woff2" crossorigin>
```

### Incorrect As Attribute
```html
<!-- WRONG: Incorrect as value -->
<link rel="preload" href="style.css" as="stylesheet">

<!-- CORRECT: Use 'style' for CSS -->
<link rel="preload" href="style.css" as="style">
```