# Typography: stacks, line-height, letter-spacing - Notes

## Core Concepts

### Font Stacks
```css
/* System font stack */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;

/* Web font with fallbacks */
font-family: 'Open Sans', Arial, sans-serif;

/* Generic families */
font-family: serif;      /* Times, Georgia */
font-family: sans-serif; /* Arial, Helvetica */
font-family: monospace;  /* Courier, Monaco */
```

### Line Height
```css
/* Unitless (recommended) */
line-height: 1.5; /* 1.5x font-size */

/* Fixed units */
line-height: 24px; /* Fixed 24px */
line-height: 1.5rem; /* 1.5x root font-size */

/* Percentage */
line-height: 150%; /* 1.5x font-size */
```

### Letter Spacing
```css
/* Tracking adjustment */
letter-spacing: 0.05em; /* Slightly spaced */
letter-spacing: -0.02em; /* Tighter */
letter-spacing: normal; /* Default */

/* Word spacing */
word-spacing: 0.2em;
```

## Best Practices

### Readable Typography
```css
body {
    font-family: -apple-system, BlinkMacSystemFont, sans-serif;
    font-size: 16px;
    line-height: 1.6;
    letter-spacing: 0.01em;
}

h1 { font-size: 2rem; line-height: 1.2; }
h2 { font-size: 1.5rem; line-height: 1.3; }
p { font-size: 1rem; line-height: 1.6; }
```

### Font Loading
```css
@font-face {
    font-family: 'CustomFont';
    src: url('font.woff2') format('woff2');
    font-display: swap; /* Improve loading performance */
}
```

## Common Pitfalls

### 1. Poor Font Stacks
```css
/* WRONG: No fallbacks */
font-family: 'CustomFont';

/* CORRECT: Proper fallbacks */
font-family: 'CustomFont', Arial, sans-serif;
```

### 2. Fixed Line Heights
```css
/* WRONG: Doesn't scale */
line-height: 20px;

/* CORRECT: Scales with font-size */
line-height: 1.5;
```