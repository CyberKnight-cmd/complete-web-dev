# Debugging CSS with DevTools - Notes

## DevTools Features

### Elements Panel
- Inspect HTML structure
- View applied CSS styles
- Edit styles in real-time
- See computed values

### Styles Pane
- View all applied styles
- See specificity conflicts
- Toggle properties on/off
- Add new properties

### Computed Tab
- See final calculated values
- Filter by property name
- View inheritance chain

### Box Model Viewer
- Visual representation of box model
- Color-coded areas (content, padding, border, margin)
- Edit values directly

## Debugging Workflow

### 1. Identify the Problem
```css
/* Element not appearing as expected */
/* Check: display, visibility, opacity, z-index */
```

### 2. Inspect Element
- Right-click → Inspect Element
- Find element in DOM tree
- Check applied styles

### 3. Check Specificity
- Look for crossed-out styles
- Identify winning selectors
- Resolve conflicts

### 4. Test Changes
- Edit styles in DevTools
- Copy working CSS back to files
- Verify across browsers

## Common Issues

### Layout Problems
```css
/* Check these properties */
display: block | inline | flex | grid;
position: static | relative | absolute | fixed;
float: left | right | none;
clear: both | left | right | none;
```

### Sizing Issues
```css
/* Verify box model */
box-sizing: content-box | border-box;
width, height, padding, border, margin
```

### Positioning Problems
```css
/* Check positioning context */
position: relative; /* Creates positioning context */
top, right, bottom, left
z-index: 1;
```