# Images & Media with Accessible Alt/Captions - Notes

## Core Concepts

### Image Accessibility Fundamentals

Every image must have appropriate alternative text to be accessible to screen reader users and when images fail to load.

#### The `alt` Attribute
```html
<!-- Informative image -->
<img src="chart.png" alt="Sales increased 45% in Q4 2024">

<!-- Decorative image -->
<img src="decoration.png" alt="">

<!-- Functional image (link/button) -->
<a href="/home">
    <img src="logo.png" alt="Company Name Home">
</a>
```

### Alt Text Guidelines

#### When to Use Alt Text
1. **Informative Images**: Convey information or concepts
2. **Functional Images**: Part of links or buttons
3. **Complex Images**: Charts, graphs, diagrams

#### When to Use Empty Alt
1. **Decorative Images**: Pure visual decoration
2. **Redundant Images**: Text already describes the image
3. **Spacer Images**: Layout purposes only

```html
<!-- Informative -->
<img src="warning.png" alt="Warning: System maintenance scheduled">

<!-- Decorative -->
<img src="border-decoration.png" alt="">

<!-- Functional -->
<button>
    <img src="search-icon.png" alt="Search">
</button>
```

### Writing Effective Alt Text

#### Best Practices
- Be concise (under 125 characters)
- Describe the content and function
- Don't start with "image of" or "picture of"
- Include text that appears in the image
- Describe the purpose, not just appearance

```html
<!-- GOOD -->
<img src="ceo-photo.jpg" alt="Jane Smith, CEO, speaking at conference">

<!-- BAD -->
<img src="ceo-photo.jpg" alt="Image of a woman">
<img src="ceo-photo.jpg" alt="A professional woman in business attire standing at a podium with a microphone in front of a blue background with company logos">
```

### Responsive Images

#### Using `srcset` for Different Resolutions
```html
<img src="image-800.jpg"
     srcset="image-400.jpg 400w,
             image-800.jpg 800w,
             image-1200.jpg 1200w"
     sizes="(max-width: 600px) 400px,
            (max-width: 1000px) 800px,
            1200px"
     alt="Product showcase">
```

#### Using `<picture>` for Art Direction
```html
<picture>
    <source media="(max-width: 600px)" srcset="mobile-image.jpg">
    <source media="(max-width: 1200px)" srcset="tablet-image.jpg">
    <img src="desktop-image.jpg" alt="Responsive product image">
</picture>
```

### Modern Image Formats

```html
<picture>
    <source srcset="image.avif" type="image/avif">
    <source srcset="image.webp" type="image/webp">
    <img src="image.jpg" alt="Fallback for older browsers">
</picture>
```

### Lazy Loading

```html
<!-- Native lazy loading -->
<img src="large-image.jpg" 
     alt="Product detail" 
     loading="lazy">

<!-- Eager loading for above-the-fold images -->
<img src="hero-image.jpg" 
     alt="Hero banner" 
     loading="eager">
```

### Figure and Figcaption

Use `<figure>` and `<figcaption>` for images with captions:

```html
<figure>
    <img src="chart.png" alt="Sales data visualization">
    <figcaption>
        Figure 1: Quarterly sales growth from 2020-2024
    </figcaption>
</figure>
```

### Video Elements

#### Basic Video Implementation
```html
<video controls width="640" height="360">
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    <p>Your browser doesn't support HTML5 video. 
       <a href="video.mp4">Download the video</a>.</p>
</video>
```

#### Video with Accessibility Features
```html
<video controls 
       poster="thumbnail.jpg"
       preload="metadata">
    <source src="video.mp4" type="video/mp4">
    <track kind="captions" 
           src="captions-en.vtt" 
           srclang="en" 
           label="English" 
           default>
    <track kind="subtitles" 
           src="subtitles-es.vtt" 
           srclang="es" 
           label="Español">
</video>
```

### Audio Elements

```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    <p>Your browser doesn't support HTML5 audio. 
       <a href="audio.mp3">Download the audio</a>.</p>
</audio>
```

### Video/Audio Attributes

```html
<video controls          <!-- Show playback controls -->
       autoplay          <!-- Auto-start (use sparingly) -->
       muted             <!-- Start muted (required for autoplay) -->
       loop              <!-- Loop playback -->
       preload="auto"    <!-- Preload: none, metadata, auto -->
       poster="thumb.jpg" <!-- Thumbnail before play -->
       width="640"
       height="360">
    <source src="video.mp4" type="video/mp4">
</video>
```

### WebVTT Captions

Create a `.vtt` file for captions:

```vtt
WEBVTT

00:00:00.000 --> 00:00:03.000
Welcome to our tutorial video.

00:00:03.500 --> 00:00:07.000
Today we'll learn about HTML media elements.

00:00:07.500 --> 00:00:11.000
Let's start with images and accessibility.
```

## Mental Models

### Image Loading Process
1. Browser parses `<img>` tag
2. Checks `srcset` and `sizes` for best match
3. Downloads appropriate image
4. Displays image or alt text if loading fails
5. Screen readers announce alt text

### Responsive Image Selection
- Browser considers viewport width
- Evaluates device pixel ratio
- Matches against `srcset` descriptors
- Selects optimal image size
- Falls back to `src` if needed

## Common Pitfalls

### 1. Missing Alt Text
```html
<!-- WRONG -->
<img src="important-chart.png">

<!-- CORRECT -->
<img src="important-chart.png" alt="Q4 revenue increased 45%">
```

### 2. Redundant Alt Text
```html
<!-- WRONG -->
<img src="photo.jpg" alt="Image of a sunset">

<!-- CORRECT -->
<img src="photo.jpg" alt="Sunset over mountain range">
```

### 3. Alt Text for Decorative Images
```html
<!-- WRONG -->
<img src="decoration.png" alt="Decorative border">

<!-- CORRECT -->
<img src="decoration.png" alt="">
```

### 4. Missing Video Captions
```html
<!-- WRONG: No captions -->
<video controls src="video.mp4"></video>

<!-- CORRECT: With captions -->
<video controls>
    <source src="video.mp4" type="video/mp4">
    <track kind="captions" src="captions.vtt" srclang="en" default>
</video>
```

### 5. Incorrect Srcset Syntax
```html
<!-- WRONG -->
<img srcset="small.jpg, medium.jpg, large.jpg" src="default.jpg" alt="Product">

<!-- CORRECT -->
<img srcset="small.jpg 400w, medium.jpg 800w, large.jpg 1200w" 
     sizes="(max-width: 600px) 400px, 800px"
     src="default.jpg" 
     alt="Product">
```

## Best Practices

### Image Optimization
1. **Compress images** before uploading
2. **Use appropriate formats**: JPEG for photos, PNG for graphics, SVG for icons
3. **Implement lazy loading** for below-fold images
4. **Provide multiple resolutions** with srcset
5. **Set explicit dimensions** to prevent layout shift

### Accessibility Checklist
- [ ] All images have alt attributes
- [ ] Alt text is descriptive and concise
- [ ] Decorative images have empty alt
- [ ] Complex images have detailed descriptions
- [ ] Videos have captions/subtitles
- [ ] Audio has transcripts
- [ ] Media controls are keyboard accessible

### Performance Optimization
```html
<!-- Optimized image implementation -->
<picture>
    <source srcset="image.avif" type="image/avif">
    <source srcset="image.webp" type="image/webp">
    <img src="image.jpg" 
         alt="Product showcase"
         width="800" 
         height="600"
         loading="lazy"
         decoding="async">
</picture>
```

### SEO Considerations
- Use descriptive filenames: `red-running-shoes.jpg` not `img001.jpg`
- Include relevant keywords in alt text naturally
- Optimize image file sizes for faster loading
- Use structured data for images when appropriate