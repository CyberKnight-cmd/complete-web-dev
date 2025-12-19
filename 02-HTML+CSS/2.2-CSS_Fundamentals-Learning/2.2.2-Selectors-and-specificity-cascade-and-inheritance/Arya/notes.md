# Selectors & Specificity; Cascade & Inheritance - Notes

## Core Concepts

### CSS Selectors

#### Basic Selectors
```css
/* Element selector */
p { color: blue; }

/* Class selector */
.highlight { background: yellow; }

/* ID selector */
#header { font-size: 24px; }

/* Universal selector */
* { margin: 0; padding: 0; }
```

#### Attribute Selectors
```css
/* Has attribute */
[title] { cursor: help; }

/* Exact value */
[type="text"] { border: 1px solid #ccc; }

/* Contains value */
[class*="btn"] { padding: 10px; }

/* Starts with */
[href^="https"] { color: green; }

/* Ends with */
[src$=".jpg"] { border: 2px solid red; }
```

#### Pseudo-classes
```css
/* State pseudo-classes */
a:hover { color: red; }
input:focus { outline: 2px solid blue; }
button:active { transform: scale(0.95); }

/* Structural pseudo-classes */
li:first-child { font-weight: bold; }
tr:nth-child(even) { background: #f0f0f0; }
p:last-of-type { margin-bottom: 0; }
```

#### Pseudo-elements
```css
/* Content pseudo-elements */
p::first-line { font-weight: bold; }
p::first-letter { font-size: 2em; }

/* Generated content */
.quote::before { content: """; }
.quote::after { content: """; }
```

#### Combinators
```css
/* Descendant combinator */
div p { color: blue; }

/* Child combinator */
ul > li { list-style: none; }

/* Adjacent sibling */
h1 + p { margin-top: 0; }

/* General sibling */
h1 ~ p { color: gray; }
```

## Specificity Calculation

### Specificity Values
- **Inline styles**: 1000 points
- **IDs**: 100 points each
- **Classes, attributes, pseudo-classes**: 10 points each
- **Elements, pseudo-elements**: 1 point each

### Calculation Examples
```css
/* Specificity: 0,0,0,1 (1 point) */
p { color: blue; }

/* Specificity: 0,0,1,0 (10 points) */
.highlight { color: red; }

/* Specificity: 0,1,0,0 (100 points) */
#header { color: green; }

/* Specificity: 0,1,1,1 (111 points) */
#header .nav a { color: purple; }

/* Specificity: 1,0,0,0 (1000 points) */
<p style="color: orange;">Inline</p>
```

### Specificity Rules
1. Higher specificity wins
2. Equal specificity: last rule wins
3. `!important` overrides specificity
4. Inline styles beat everything (except `!important`)

## The Cascade

### Cascade Order (lowest to highest priority)
1. **User agent styles** (browser defaults)
2. **User styles** (user's custom CSS)
3. **Author styles** (website's CSS)
4. **Author `!important`** declarations
5. **User `!important`** declarations
6. **User agent `!important`** declarations

### Source Order
```css
/* Later rules override earlier ones with same specificity */
p { color: blue; }
p { color: red; } /* This wins */

.text { color: green; }
.text { color: purple; } /* This wins */
```

## Inheritance

### Inherited Properties
```css
/* These properties inherit by default */
body {
    font-family: Arial, sans-serif; /* Inherits */
    color: #333; /* Inherits */
    line-height: 1.6; /* Inherits */
}

/* Child elements automatically inherit these values */
```

### Non-Inherited Properties
```css
/* These properties don't inherit by default */
div {
    border: 1px solid red; /* Doesn't inherit */
    margin: 20px; /* Doesn't inherit */
    padding: 10px; /* Doesn't inherit */
}
```

### Controlling Inheritance
```css
/* Force inheritance */
.child {
    border: inherit; /* Inherit parent's border */
}

/* Reset to initial value */
.reset {
    color: initial; /* Browser default */
}

/* Inherit from parent */
.inherit {
    font-size: inherit;
}

/* Use computed value */
.unset {
    margin: unset; /* Inherit if inheritable, initial if not */
}
```

## Mental Models

### Specificity as Weight
Think of specificity as weight on a scale:
- IDs are heavy (100kg)
- Classes are medium (10kg)  
- Elements are light (1kg)
- Inline styles are super heavy (1000kg)

### Cascade as Waterfall
Styles flow down from:
1. Browser defaults
2. User preferences  
3. Author stylesheets
4. Inline styles
5. `!important` declarations

## Common Pitfalls

### 1. Specificity Wars
```css
/* WRONG: Increasing specificity unnecessarily */
div.container div.content div.text p.paragraph { color: red; }

/* CORRECT: Use minimal specificity */
.paragraph { color: red; }
```

### 2. Overusing `!important`
```css
/* WRONG: !important everywhere */
.text { color: red !important; }
.text { font-size: 16px !important; }

/* CORRECT: Fix specificity instead */
.content .text { color: red; }
```

### 3. Inheritance Confusion
```css
/* WRONG: Expecting non-inherited properties to inherit */
.parent { border: 1px solid red; }
/* .child won't have border */

/* CORRECT: Apply to child or use inherit */
.child { border: inherit; }
```

### 4. Selector Performance
```css
/* WRONG: Overly complex selectors */
body div.container ul li a.link { color: blue; }

/* CORRECT: Simple, specific selectors */
.nav-link { color: blue; }
```

## Best Practices

### 1. Keep Specificity Low
```css
/* Good: Low specificity, easy to override */
.button { background: blue; }
.button-primary { background: green; }

/* Bad: High specificity, hard to override */
#sidebar .widget .button.primary { background: green; }
```

### 2. Use Classes Over IDs
```css
/* Preferred: Classes for styling */
.header { background: #333; }

/* Avoid: IDs for styling (too specific) */
#header { background: #333; }
```

### 3. Organize by Specificity
```css
/* 1. Base elements (lowest specificity) */
p { line-height: 1.6; }

/* 2. Classes */
.text { color: #333; }

/* 3. More specific combinations */
.sidebar .text { color: #666; }
```