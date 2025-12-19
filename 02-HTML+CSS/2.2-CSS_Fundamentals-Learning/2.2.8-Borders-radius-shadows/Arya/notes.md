# Borders, Radius, Shadows - Notes

## Border Properties

### Basic Borders
```css
border: 2px solid red;
border-width: 1px 2px 3px 4px; /* top right bottom left */
border-style: solid | dashed | dotted | double;
border-color: red blue green yellow;
```

### Border Radius
```css
border-radius: 10px; /* All corners */
border-radius: 10px 20px; /* top-left/bottom-right, top-right/bottom-left */
border-radius: 10px 20px 30px 40px; /* Each corner */
border-radius: 50%; /* Circle */
```

### Box Shadow
```css
box-shadow: 2px 4px 8px rgba(0,0,0,0.3);
box-shadow: inset 0 2px 4px rgba(0,0,0,0.1); /* Inner shadow */
box-shadow: 0 0 10px red, 0 0 20px blue; /* Multiple shadows */
```

## Best Practices

### Subtle Effects
```css
.card {
    border: 1px solid #e0e0e0;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.button {
    border: none;
    border-radius: 4px;
    box-shadow: 0 2px 4px rgba(0,0,0,0.2);
}
```

### Performance
```css
/* Use transform for animations instead of box-shadow */
.hover-effect:hover {
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(0,0,0,0.2);
}
```