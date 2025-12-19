# CSS Units: px, %, em, rem, vw, vh; min/max/fit-content - Notes

## Core Concepts

### Absolute Units
- **px (pixels)**: Fixed size, device-dependent
- **pt (points)**: 1pt = 1/72 inch
- **in, cm, mm**: Physical measurements

### Relative Units
- **% (percentage)**: Relative to parent element
- **em**: Relative to current element's font-size
- **rem**: Relative to root element's font-size
- **vw**: 1% of viewport width
- **vh**: 1% of viewport height
- **vmin**: 1% of smaller viewport dimension
- **vmax**: 1% of larger viewport dimension

### Sizing Functions
- **min-content**: Minimum size needed
- **max-content**: Maximum size wanted
- **fit-content**: Between min and max
- **min()**: Smallest of given values
- **max()**: Largest of given values
- **clamp()**: Value between min and max

## Unit Comparison

### Pixels (px)
```css
.fixed { width: 300px; font-size: 16px; }
```
- Precise control
- Not responsive
- Good for borders, small details

### Percentages (%)
```css
.responsive { width: 50%; margin: 10%; }
```
- Relative to parent
- Responsive by nature
- Good for layouts

### Em Units
```css
.em-example { font-size: 1.2em; padding: 0.5em; }
```
- Relative to current font-size
- Compounds with nesting
- Good for typography scaling

### Rem Units
```css
.rem-example { font-size: 1.2rem; margin: 2rem; }
```
- Relative to root font-size
- No compounding
- Predictable scaling

### Viewport Units
```css
.hero { height: 100vh; width: 100vw; }
.sidebar { width: 25vw; }
```
- Relative to viewport
- Great for full-screen layouts
- Responsive without media queries

## Best Practices

### Typography
```css
html { font-size: 16px; } /* Base size */
h1 { font-size: 2rem; } /* 32px */
p { font-size: 1rem; line-height: 1.5; } /* 16px */
small { font-size: 0.875rem; } /* 14px */
```

### Layout
```css
.container { max-width: 1200px; width: 90%; }
.column { width: calc(50% - 1rem); }
.spacing { margin: 1rem 0; padding: 0 2rem; }
```

### Responsive Design
```css
.responsive-text {
    font-size: clamp(1rem, 4vw, 2rem);
}

.flexible-width {
    width: min(90%, 800px);
}
```

## Common Pitfalls

### 1. Em Compounding
```css
/* WRONG: Compounds with nesting */
.parent { font-size: 1.2em; }
.child { font-size: 1.2em; } /* 1.44x base size */

/* CORRECT: Use rem for consistency */
.parent { font-size: 1.2rem; }
.child { font-size: 1.2rem; }
```

### 2. Viewport Unit Issues
```css
/* WRONG: Can cause horizontal scrolling */
.full-width { width: 100vw; }

/* CORRECT: Use percentage instead */
.full-width { width: 100%; }
```

### 3. Percentage Height Issues
```css
/* WRONG: Parent has no defined height */
.parent { height: auto; }
.child { height: 50%; } /* Won't work */

/* CORRECT: Define parent height */
.parent { height: 400px; }
.child { height: 50%; } /* 200px */
```