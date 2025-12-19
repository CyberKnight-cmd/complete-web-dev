# Accessible Images & Media Implementation Challenge

## Problem Statement

Implement a production-ready image and media gallery that demonstrates perfect accessibility compliance using semantic HTML elements `<figure>`, `<figcaption>`, and proper alt text strategies.

## Requirements

### Core Implementation
Build a multimedia content page that includes:

1. **Image Gallery**: Minimum 8 images demonstrating different alt text scenarios
   - **Informative images**: Convey important information (3+ examples)
   - **Decorative images**: Pure visual decoration (2+ examples)  
   - **Functional images**: Part of links/buttons (2+ examples)
   - **Complex images**: Charts, graphs, diagrams (1+ example)

2. **Figure/Figcaption Usage**: Proper semantic markup
   - All images with captions must use `<figure>` + `<figcaption>`
   - Captions must provide additional context beyond alt text
   - Figures must be properly associated with surrounding content

3. **Media Elements**: Include video and audio
   - **Video**: With captions/subtitles and transcript
   - **Audio**: With transcript and controls
   - **Responsive**: All media scales properly

4. **Alt Text Quality**: Follow accessibility best practices
   - Informative: Describe content and function
   - Decorative: Empty alt attribute (`alt=""`)
   - Functional: Describe the action/destination
   - Complex: Brief alt + detailed description

### Technical Constraints

- **No JavaScript**: Pure HTML/CSS implementation
- **Valid HTML5**: Pass W3C validation
- **Responsive Images**: Use `srcset` and `sizes` attributes
- **Modern Formats**: Support WebP with fallbacks
- **Performance**: Lazy loading where appropriate

### Accessibility Requirements

- **Screen Reader Compatible**: All images accessible via screen reader
- **Keyboard Navigation**: All interactive images keyboard accessible
- **High Contrast**: Images work in high contrast mode
- **WCAG 2.1 AA**: Meet all relevant success criteria
- **Alternative Formats**: Provide alternatives for complex content

## Input Specifications

Create these files:
- `index.html` - Main gallery page
- `styles.css` - Responsive styling
- `images/` - Image assets (provide sample images)
- `media/` - Video/audio files with captions
- `README.md` - Documentation and testing guide

## Expected Output

### Image Categories Implementation

#### 1. Informative Images
```html
<figure>
    <img src="sales-chart.jpg" 
         alt="Sales increased 45% from Q3 to Q4 2024, reaching $2.3M">
    <figcaption>
        Quarterly sales performance showing significant growth in Q4
    </figcaption>
</figure>
```

#### 2. Decorative Images
```html
<img src="decorative-border.png" alt="" role="presentation">
<!-- No figure needed for purely decorative images -->
```

#### 3. Functional Images
```html
<a href="/search">
    <img src="search-icon.svg" alt="Search products">
</a>

<button type="submit">
    <img src="submit-icon.svg" alt="Submit form">
    Submit
</button>
```

#### 4. Complex Images
```html
<figure>
    <img src="org-chart.png" 
         alt="Company organizational chart with CEO at top, 3 VPs below">
    <figcaption>
        Company organizational structure as of 2024
    </figcaption>
    <details>
        <summary>Detailed chart description</summary>
        <p>The chart shows CEO John Smith at the top level, with three 
           Vice Presidents reporting directly: Sarah Johnson (VP Engineering), 
           Mike Chen (VP Sales), and Lisa Rodriguez (VP Marketing)...</p>
    </details>
</figure>
```

### Responsive Images
```html
<figure>
    <picture>
        <source srcset="hero-mobile.webp" 
                media="(max-width: 768px)" 
                type="image/webp">
        <source srcset="hero-desktop.webp" 
                media="(min-width: 769px)" 
                type="image/webp">
        <img src="hero-desktop.jpg" 
             alt="Team collaboration in modern office space"
             loading="lazy">
    </picture>
    <figcaption>Our team working together on innovative solutions</figcaption>
</figure>
```

### Video with Accessibility
```html
<figure>
    <video controls poster="video-thumbnail.jpg">
        <source src="tutorial.mp4" type="video/mp4">
        <track kind="captions" src="tutorial-en.vtt" srclang="en" default>
        <track kind="subtitles" src="tutorial-es.vtt" srclang="es">
        <p>Your browser doesn't support HTML5 video. 
           <a href="tutorial.mp4">Download the video</a>.</p>
    </video>
    <figcaption>Product tutorial: Getting started with our platform</figcaption>
</figure>

<details>
    <summary>Video Transcript</summary>
    <p>Welcome to our platform tutorial. In this video, we'll cover...</p>
</details>
```

## Test Cases

### Test Case 1: Alt Text Quality
```javascript
// Automated test criteria
const images = document.querySelectorAll('img');
images.forEach(img => {
    // Informative images: alt text 5-125 characters
    // Decorative images: alt="" exactly
    // Functional images: describes action, not appearance
    // No "image of", "picture of", "graphic of"
});
```

### Test Case 2: Figure/Figcaption Association
```html
<!-- Each figure must have exactly one figcaption -->
<figure>
    <img src="..." alt="...">
    <figcaption>...</figcaption> <!-- Required -->
</figure>

<!-- Figcaption must add value beyond alt text -->
<!-- Alt: "Bar chart showing 2024 sales data" -->
<!-- Caption: "Sales performance exceeded targets by 15%" -->
```

### Test Case 3: Screen Reader Navigation
```
# Using NVDA/JAWS:
# 1. Navigate by graphics (G key)
# 2. All images announced with proper alt text
# 3. Decorative images skipped
# 4. Figure captions read after alt text
# 5. Complex image descriptions accessible
```

### Test Case 4: Keyboard Accessibility
```
# Tab navigation test:
# 1. All functional images reachable via Tab
# 2. Enter/Space activates image links/buttons
# 3. Focus indicators visible
# 4. Logical tab order maintained
```

## Acceptance Criteria

### Content Requirements ✅
- [ ] 8+ images covering all 4 categories
- [ ] Proper figure/figcaption usage for captioned images
- [ ] Video with captions and transcript
- [ ] Audio with transcript
- [ ] Responsive image implementation

### Accessibility Requirements ✅
- [ ] All images have appropriate alt text
- [ ] Decorative images have empty alt or role="presentation"
- [ ] Complex images have detailed descriptions
- [ ] Screen reader can access all content
- [ ] Keyboard navigation works for interactive images

### Technical Requirements ✅
- [ ] Valid HTML5 markup
- [ ] Responsive design (mobile + desktop)
- [ ] Modern image formats with fallbacks
- [ ] Lazy loading implemented
- [ ] Performance optimized

### Quality Assurance ✅
- [ ] Passes WAVE accessibility checker
- [ ] 100% Lighthouse accessibility score
- [ ] Screen reader testing documented
- [ ] Cross-browser compatibility verified

## Detailed Test Scenarios

### Scenario 1: Screen Reader User
```
User Story: As a blind user using NVDA, I want to understand 
all visual content on the page.

Test Steps:
1. Navigate page with screen reader
2. Use graphics navigation (G key)
3. Verify all meaningful images described
4. Check decorative images are skipped
5. Confirm captions provide additional context
```

### Scenario 2: Low Vision User
```
User Story: As a user with low vision, I need images to work 
in high contrast mode and when zoomed to 200%.

Test Steps:
1. Enable Windows High Contrast mode
2. Zoom browser to 200%
3. Verify all images remain functional
4. Check text alternatives are readable
5. Confirm layout doesn't break
```

### Scenario 3: Keyboard-Only User
```
User Story: As a user who cannot use a mouse, I need to 
access all interactive images via keyboard.

Test Steps:
1. Navigate using only Tab/Shift+Tab
2. Activate image links with Enter
3. Activate image buttons with Space
4. Verify focus indicators visible
5. Check logical tab order
```

## Performance Requirements

- **Image Optimization**: All images under 500KB
- **Lazy Loading**: Below-fold images load on demand
- **Format Support**: WebP with JPEG/PNG fallbacks
- **Responsive**: Appropriate image sizes served
- **Caching**: Proper cache headers for images

## Bonus Challenges

1. **Art Direction**: Use `<picture>` for different crops
2. **Dark Mode**: Images adapt to dark/light themes
3. **Print Styles**: Optimize images for printing
4. **Progressive Enhancement**: Enhance with JavaScript
5. **Image Maps**: Accessible image map implementation

## Common Mistakes to Avoid

- Generic alt text ("image", "photo", "graphic")
- Missing alt attributes
- Redundant captions that repeat alt text
- Using figures for decorative images
- Missing video captions/transcripts
- Poor image compression
- Broken responsive images
- Inaccessible image carousels

## Submission Format

```
accessible-images-challenge/
├── index.html              # Main gallery
├── styles.css              # Responsive styles
├── images/                 # Image assets
│   ├── informative/
│   ├── decorative/
│   ├── functional/
│   └── complex/
├── media/                  # Video/audio files
│   ├── videos/
│   ├── audio/
│   └── captions/
├── README.md               # Documentation
├── accessibility-report.md # Test results
└── screenshots/           # Visual proof
    ├── desktop-view.png
    ├── mobile-view.png
    ├── high-contrast.png
    └── lighthouse-score.png
```