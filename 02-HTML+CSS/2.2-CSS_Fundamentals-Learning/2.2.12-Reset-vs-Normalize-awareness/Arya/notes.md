# Reset vs Normalize (awareness) - Notes

## CSS Reset vs Normalize

### CSS Reset Approach
Removes all default browser styling:
```css
/* Eric Meyer's CSS Reset */
* {
    margin: 0;
    padding: 0;
    border: 0;
    font-size: 100%;
    font: inherit;
    vertical-align: baseline;
}
```

### Normalize.css Approach
Preserves useful defaults, fixes inconsistencies:
```css
/* Normalize.css example */
h1 {
    font-size: 2em;
    margin: 0.67em 0;
}

button {
    font-family: inherit;
    font-size: 100%;
}
```

## When to Use Each

### Use CSS Reset When:
- Starting completely from scratch
- Have complete design control
- Want consistent baseline across browsers

### Use Normalize When:
- Want to preserve useful defaults
- Building on existing design systems
- Need accessibility-friendly defaults

## Modern Approach
```css
/* Modern minimal reset */
*, *::before, *::after {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: system-ui, sans-serif;
}

img, picture, video, canvas, svg {
    display: block;
    max-width: 100%;
}
```

## Best Practices

### Custom Reset
```css
/* Tailored to your needs */
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: -apple-system, BlinkMacSystemFont, sans-serif;
    line-height: 1.6;
}

h1, h2, h3, h4, h5, h6 {
    margin-top: 0;
}
```