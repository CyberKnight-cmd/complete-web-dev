# Print Styles (intro) - Notes

## Print Media Queries

### Basic Print Styles
```css
@media print {
    body { font-size: 12pt; color: black; }
    .no-print { display: none; }
    a { text-decoration: underline; }
}
```

### Page Control
```css
@page {
    margin: 1in;
    size: A4;
}

.page-break {
    page-break-before: always;
}

.keep-together {
    page-break-inside: avoid;
}
```

## Print Optimization

### Typography
```css
@media print {
    body { font-family: serif; }
    h1, h2, h3 { page-break-after: avoid; }
    p { orphans: 3; widows: 3; }
}
```

### Colors and Images
```css
@media print {
    * { color: black !important; }
    .background-image { background: none !important; }
    img { max-width: 100%; }
}
```

### Navigation and UI
```css
@media print {
    nav, .sidebar, .ads { display: none; }
    .main-content { width: 100%; }
}
```

## Best Practices

### Essential Content Only
```css
@media print {
    .print-only { display: block; }
    .screen-only { display: none; }
}
```

### Readable Typography
```css
@media print {
    body { font-size: 12pt; line-height: 1.4; }
    h1 { font-size: 18pt; }
    h2 { font-size: 16pt; }
}
```