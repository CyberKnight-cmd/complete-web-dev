# Transitions & Timing Functions - Notes

## Transition Properties

### Basic Syntax
```css
transition: property duration timing-function delay;
transition: all 0.3s ease-in-out 0.1s;
```

### Individual Properties
```css
transition-property: opacity, transform;
transition-duration: 0.3s, 0.5s;
transition-timing-function: ease, ease-out;
transition-delay: 0s, 0.1s;
```

## Timing Functions

### Built-in Functions
```css
transition-timing-function: ease; /* Default */
transition-timing-function: linear;
transition-timing-function: ease-in;
transition-timing-function: ease-out;
transition-timing-function: ease-in-out;
```

### Custom Cubic Bezier
```css
transition-timing-function: cubic-bezier(0.25, 0.1, 0.25, 1);
```

### Steps Function
```css
transition-timing-function: steps(4, end);
```

## Best Practices

### Performance
```css
/* Animate transform and opacity for best performance */
.element {
    transition: transform 0.3s ease, opacity 0.3s ease;
}

.element:hover {
    transform: translateY(-5px);
    opacity: 0.8;
}
```

### Smooth Interactions
```css
button {
    transition: all 0.2s ease;
}

button:hover {
    background-color: #007bff;
    transform: scale(1.05);
}
```