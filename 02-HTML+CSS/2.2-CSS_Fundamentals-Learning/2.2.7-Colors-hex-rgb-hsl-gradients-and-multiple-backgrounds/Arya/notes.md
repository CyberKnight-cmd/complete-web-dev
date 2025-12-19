# Colors: hex/rgb/hsl; gradients & multiple backgrounds - Notes

## Color Formats

### Hex Colors
```css
color: #ff0000; /* Red */
color: #00ff00; /* Green */
color: #0000ff; /* Blue */
color: #fff; /* White (shorthand) */
color: #000; /* Black (shorthand) */
```

### RGB/RGBA
```css
color: rgb(255, 0, 0); /* Red */
color: rgba(255, 0, 0, 0.5); /* Semi-transparent red */
background: rgb(0 255 0 / 0.8); /* Modern syntax */
```

### HSL/HSLA
```css
color: hsl(0, 100%, 50%); /* Red */
color: hsl(120, 100%, 50%); /* Green */
color: hsla(240, 100%, 50%, 0.5); /* Semi-transparent blue */
```

## Gradients

### Linear Gradients
```css
background: linear-gradient(to right, red, blue);
background: linear-gradient(45deg, #ff0000, #0000ff);
background: linear-gradient(to bottom, red 0%, yellow 50%, blue 100%);
```

### Radial Gradients
```css
background: radial-gradient(circle, red, blue);
background: radial-gradient(ellipse at center, red 0%, blue 100%);
```

## Multiple Backgrounds
```css
background: 
    linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)),
    url('image.jpg');
background-size: cover, cover;
background-position: center, center;
```

## Best Practices

### Accessible Colors
```css
/* Ensure sufficient contrast */
color: #333; /* Dark text */
background: #fff; /* Light background */

/* Use CSS custom properties */
:root {
    --primary-color: #007bff;
    --text-color: #333;
}
```