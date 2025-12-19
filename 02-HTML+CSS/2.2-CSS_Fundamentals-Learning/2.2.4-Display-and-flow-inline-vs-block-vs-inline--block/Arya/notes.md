# Display & Flow; inline vs block vs inline-block - Notes

## Core Concepts

### Display Property Values

#### Block Elements
```css
div, p, h1-h6, section, article { display: block; }
```
- Take full width available
- Start on new line
- Can have width, height, margin, padding
- Stack vertically

#### Inline Elements
```css
span, a, em, strong, code { display: inline; }
```
- Only take space needed
- Flow with text
- Cannot have width/height
- Vertical margin/padding don't affect layout

#### Inline-Block Elements
```css
img, input, button { display: inline-block; }
```
- Flow with text like inline
- Can have width/height like block
- Respects all margin/padding

### Document Flow

Normal document flow is how elements are positioned by default:
1. Block elements stack vertically
2. Inline elements flow horizontally
3. Elements appear in source order

## Mental Models

### Block as Building Blocks
- Each block is a full-width building block
- Stacks on top of each other
- Can contain other blocks or inline content

### Inline as Text Flow
- Flows like words in a sentence
- Wraps at container edges
- Cannot be sized directly

### Inline-Block as Hybrid
- Behaves like inline for positioning
- Behaves like block for sizing

## Common Use Cases

### Block Elements
```css
.container { display: block; width: 100%; }
.section { display: block; margin: 20px 0; }
```

### Inline Elements
```css
.highlight { display: inline; background: yellow; }
.link { display: inline; color: blue; }
```

### Inline-Block Elements
```css
.button { display: inline-block; padding: 10px 20px; }
.nav-item { display: inline-block; width: 100px; }
```

## Common Pitfalls

### 1. Inline Element Sizing
```css
/* WRONG: Won't work */
span { width: 200px; height: 100px; }

/* CORRECT: Change display first */
span { display: inline-block; width: 200px; height: 100px; }
```

### 2. Inline-Block Spacing
```css
/* WRONG: Unexpected gaps between elements */
.nav-item { display: inline-block; }

/* CORRECT: Remove whitespace or use flexbox */
.nav { font-size: 0; }
.nav-item { font-size: 16px; }
```

### 3. Vertical Alignment
```css
/* Inline-block elements align to baseline by default */
.item { display: inline-block; vertical-align: top; }
```