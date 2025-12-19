# Coffee Shop Homepage Implementation Challenge

## Problem Statement

Build a production-ready coffee shop homepage that demonstrates modern web development best practices, semantic HTML structure, responsive design, and perfect accessibility compliance. The site must convert visitors into customers through compelling design and flawless user experience.

## Requirements

### Core Features
Implement a complete coffee shop homepage with:

1. **Hero Section**
   - Eye-catching hero image with overlay text
   - Compelling headline and call-to-action button
   - Responsive design (mobile-first approach)
   - Accessible contrast ratios (WCAG AA compliant)

2. **Navigation System**
   - Sticky/fixed navigation bar
   - Mobile hamburger menu with smooth animations
   - Keyboard accessible navigation
   - Clear visual hierarchy and focus indicators

3. **Content Sections**
   - **About Us**: Brief story with engaging imagery
   - **Featured Products**: Coffee showcase with pricing
   - **Location/Hours**: Contact information and map
   - **Customer Reviews**: Social proof testimonials

4. **Visual Design**
   - Professional coffee shop branding
   - Consistent color scheme and typography
   - High-quality imagery with proper alt text
   - Smooth hover effects and micro-interactions

### Technical Constraints

- **No Framework**: Pure HTML5, CSS3, and vanilla JavaScript only
- **Responsive Design**: Mobile-first, works on all screen sizes
- **Performance**: Page load under 3 seconds, optimized images
- **Accessibility**: WCAG 2.1 AA compliance, screen reader friendly
- **Cross-browser**: Chrome, Firefox, Safari, Edge support
- **SEO Optimized**: Proper meta tags, semantic structure

### Accessibility Requirements

- **Semantic HTML**: Proper landmark elements and heading hierarchy
- **Alt Text**: Descriptive alt text for all images
- **Color Contrast**: 4.5:1 for normal text, 3:1 for large text
- **Keyboard Navigation**: All interactive elements accessible via keyboard
- **Screen Reader**: Tested with NVDA/VoiceOver
- **Focus Management**: Visible focus indicators throughout

## Input Specifications

Create these files:
- `index.html` - Main homepage
- `styles.css` - All styling (mobile-first)
- `script.js` - Interactive functionality
- `images/` - Optimized image assets
- `README.md` - Setup and deployment guide

## Expected Output

### HTML Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Brew & Bean - Artisan Coffee Shop | Fresh Roasted Daily</title>
    <meta name="description" content="Premium artisan coffee shop serving fresh roasted beans, specialty drinks, and pastries. Visit our cozy location in downtown for the perfect coffee experience.">
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <nav aria-label="Main navigation">
            <div class="nav-container">
                <a href="#" class="logo" aria-label="Brew & Bean Coffee Shop Home">
                    <img src="images/logo.svg" alt="Brew & Bean Logo">
                </a>
                
                <button class="mobile-menu-toggle" aria-expanded="false" aria-controls="main-menu">
                    <span class="sr-only">Toggle navigation menu</span>
                    <span class="hamburger-line"></span>
                    <span class="hamburger-line"></span>
                    <span class="hamburger-line"></span>
                </button>
                
                <ul id="main-menu" class="nav-menu">
                    <li><a href="#home">Home</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#menu">Menu</a></li>
                    <li><a href="#location">Location</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </div>
        </nav>
    </header>

    <main>
        <section id="home" class="hero">
            <div class="hero-content">
                <h1>Artisan Coffee, Crafted with Passion</h1>
                <p>Experience the perfect blend of tradition and innovation in every cup</p>
                <a href="#menu" class="cta-button">Explore Our Menu</a>
            </div>
            <div class="hero-image">
                <img src="images/hero-coffee.jpg" alt="Barista carefully preparing artisan coffee with latte art">
            </div>
        </section>

        <section id="about" class="about">
            <div class="container">
                <h2>Our Story</h2>
                <div class="about-content">
                    <div class="about-text">
                        <p>Since 2015, Brew & Bean has been dedicated to sourcing the finest coffee beans from sustainable farms worldwide...</p>
                    </div>
                    <figure class="about-image">
                        <img src="images/coffee-roasting.jpg" alt="Coffee beans being roasted in traditional roasting machine">
                        <figcaption>Fresh roasting daily in our downtown location</figcaption>
                    </figure>
                </div>
            </div>
        </section>

        <section id="menu" class="featured-products">
            <div class="container">
                <h2>Featured Coffees</h2>
                <div class="product-grid">
                    <article class="product-card">
                        <img src="images/espresso.jpg" alt="Rich espresso shot in white ceramic cup">
                        <h3>Signature Espresso</h3>
                        <p>Bold and smooth with notes of dark chocolate</p>
                        <span class="price">$3.50</span>
                    </article>
                    <!-- More product cards... -->
                </div>
            </div>
        </section>

        <section id="location" class="location-hours">
            <div class="container">
                <h2>Visit Us</h2>
                <div class="location-content">
                    <address>
                        <h3>Location</h3>
                        <p>123 Coffee Street<br>
                        Downtown District<br>
                        City, State 12345</p>
                    </address>
                    <div class="hours">
                        <h3>Hours</h3>
                        <dl>
                            <dt>Monday - Friday</dt>
                            <dd>6:00 AM - 8:00 PM</dd>
                            <dt>Saturday - Sunday</dt>
                            <dd>7:00 AM - 9:00 PM</dd>
                        </dl>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer>
        <div class="container">
            <p>&copy; 2024 Brew & Bean Coffee Shop. All rights reserved.</p>
            <div class="social-links">
                <a href="#" aria-label="Follow us on Instagram">
                    <img src="images/instagram-icon.svg" alt="">
                </a>
                <a href="#" aria-label="Like us on Facebook">
                    <img src="images/facebook-icon.svg" alt="">
                </a>
            </div>
        </div>
    </footer>

    <script src="script.js"></script>
</body>
</html>
```

### CSS Structure (Mobile-First)
```css
/* Reset and base styles */
*, *::before, *::after {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: 'Georgia', serif;
    line-height: 1.6;
    color: #2c1810;
}

/* Accessibility utilities */
.sr-only {
    position: absolute;
    width: 1px;
    height: 1px;
    padding: 0;
    margin: -1px;
    overflow: hidden;
    clip: rect(0, 0, 0, 0);
    white-space: nowrap;
    border: 0;
}

/* Focus indicators */
:focus {
    outline: 3px solid #d4a574;
    outline-offset: 2px;
}

/* Mobile-first navigation */
.nav-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    background: #2c1810;
}

.logo img {
    height: 40px;
    width: auto;
}

.mobile-menu-toggle {
    display: flex;
    flex-direction: column;
    background: none;
    border: none;
    cursor: pointer;
    padding: 0.5rem;
}

.hamburger-line {
    width: 25px;
    height: 3px;
    background: #d4a574;
    margin: 2px 0;
    transition: 0.3s;
}

.nav-menu {
    display: none;
    position: absolute;
    top: 100%;
    left: 0;
    width: 100%;
    background: #2c1810;
    list-style: none;
    margin: 0;
    padding: 0;
}

.nav-menu.active {
    display: block;
}

.nav-menu a {
    display: block;
    color: #d4a574;
    text-decoration: none;
    padding: 1rem;
    border-bottom: 1px solid #3d2317;
}

.nav-menu a:hover,
.nav-menu a:focus {
    background: #3d2317;
}

/* Hero section */
.hero {
    display: flex;
    flex-direction: column;
    min-height: 70vh;
    background: linear-gradient(135deg, #2c1810 0%, #3d2317 100%);
    color: #f5f5f5;
}

.hero-content {
    padding: 2rem 1rem;
    text-align: center;
}

.hero h1 {
    font-size: 2rem;
    margin-bottom: 1rem;
    line-height: 1.2;
}

.hero p {
    font-size: 1.1rem;
    margin-bottom: 2rem;
    opacity: 0.9;
}

.cta-button {
    display: inline-block;
    background: #d4a574;
    color: #2c1810;
    padding: 1rem 2rem;
    text-decoration: none;
    border-radius: 5px;
    font-weight: bold;
    transition: all 0.3s ease;
}

.cta-button:hover,
.cta-button:focus {
    background: #e6b885;
    transform: translateY(-2px);
}

.hero-image img {
    width: 100%;
    height: 300px;
    object-fit: cover;
}

/* Responsive design */
@media (min-width: 768px) {
    .mobile-menu-toggle {
        display: none;
    }
    
    .nav-menu {
        display: flex;
        position: static;
        width: auto;
        background: none;
    }
    
    .nav-menu a {
        border-bottom: none;
        padding: 0.5rem 1rem;
    }
    
    .hero {
        flex-direction: row;
        align-items: center;
    }
    
    .hero-content {
        flex: 1;
        padding: 4rem 2rem;
        text-align: left;
    }
    
    .hero h1 {
        font-size: 3rem;
    }
    
    .hero-image {
        flex: 1;
    }
    
    .hero-image img {
        height: 500px;
    }
}

@media (min-width: 1024px) {
    .container {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 2rem;
    }
    
    .hero h1 {
        font-size: 3.5rem;
    }
}
```

### JavaScript Functionality
```javascript
// Mobile menu toggle
class MobileMenu {
    constructor() {
        this.toggle = document.querySelector('.mobile-menu-toggle');
        this.menu = document.querySelector('.nav-menu');
        this.init();
    }
    
    init() {
        this.toggle.addEventListener('click', () => this.toggleMenu());
        
        // Close menu when clicking on links
        this.menu.querySelectorAll('a').forEach(link => {
            link.addEventListener('click', () => this.closeMenu());
        });
        
        // Close menu on escape key
        document.addEventListener('keydown', (e) => {
            if (e.key === 'Escape' && this.menu.classList.contains('active')) {
                this.closeMenu();
                this.toggle.focus();
            }
        });
    }
    
    toggleMenu() {
        const isOpen = this.menu.classList.contains('active');
        
        if (isOpen) {
            this.closeMenu();
        } else {
            this.openMenu();
        }
    }
    
    openMenu() {
        this.menu.classList.add('active');
        this.toggle.setAttribute('aria-expanded', 'true');
        
        // Focus first menu item
        const firstLink = this.menu.querySelector('a');
        if (firstLink) firstLink.focus();
    }
    
    closeMenu() {
        this.menu.classList.remove('active');
        this.toggle.setAttribute('aria-expanded', 'false');
    }
}

// Smooth scrolling for anchor links
class SmoothScroll {
    constructor() {
        this.init();
    }
    
    init() {
        document.querySelectorAll('a[href^="#"]').forEach(link => {
            link.addEventListener('click', (e) => {
                e.preventDefault();
                const target = document.querySelector(link.getAttribute('href'));
                
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    }
}

// Initialize components
document.addEventListener('DOMContentLoaded', () => {
    new MobileMenu();
    new SmoothScroll();
});
```

## Test Cases

### Test Case 1: Responsive Design
```javascript
// Automated responsive testing
describe('Responsive Design', () => {
    test('mobile layout works correctly', () => {
        // Set viewport to mobile size
        cy.viewport(375, 667);
        cy.visit('/');
        
        // Check mobile menu is visible
        cy.get('.mobile-menu-toggle').should('be.visible');
        cy.get('.nav-menu').should('not.be.visible');
        
        // Test menu toggle
        cy.get('.mobile-menu-toggle').click();
        cy.get('.nav-menu').should('be.visible');
    });
    
    test('desktop layout works correctly', () => {
        cy.viewport(1024, 768);
        cy.visit('/');
        
        // Check desktop menu is visible
        cy.get('.mobile-menu-toggle').should('not.be.visible');
        cy.get('.nav-menu').should('be.visible');
    });
});
```

### Test Case 2: Accessibility Compliance
```javascript
// Accessibility testing
describe('Accessibility', () => {
    test('passes axe accessibility tests', () => {
        cy.visit('/');
        cy.injectAxe();
        cy.checkA11y();
    });
    
    test('keyboard navigation works', () => {
        cy.visit('/');
        
        // Tab through navigation
        cy.get('body').tab();
        cy.focused().should('have.class', 'logo');
        
        cy.focused().tab();
        cy.focused().should('contain', 'Home');
    });
});
```

### Test Case 3: Performance Requirements
```
# Performance testing checklist
## Page Load Speed
- [ ] First Contentful Paint < 1.5s
- [ ] Largest Contentful Paint < 2.5s
- [ ] Total page load < 3s

## Image Optimization
- [ ] All images under 500KB
- [ ] WebP format with fallbacks
- [ ] Proper alt text for all images
- [ ] Lazy loading for below-fold images

## Code Optimization
- [ ] CSS minified and optimized
- [ ] JavaScript minified
- [ ] No unused CSS/JS
- [ ] Efficient selectors used
```

## Acceptance Criteria

### Design & Layout ✅
- [ ] Professional coffee shop branding and visual design
- [ ] Responsive design works on all screen sizes (320px+)
- [ ] Mobile-first approach implemented
- [ ] Consistent typography and color scheme
- [ ] Smooth animations and hover effects

### Functionality ✅
- [ ] Mobile hamburger menu with smooth animations
- [ ] Smooth scrolling navigation
- [ ] All interactive elements work correctly
- [ ] Form validation (if contact form included)
- [ ] Cross-browser compatibility verified

### Accessibility ✅
- [ ] WCAG 2.1 AA compliance achieved
- [ ] Semantic HTML structure throughout
- [ ] All images have descriptive alt text
- [ ] Keyboard navigation fully functional
- [ ] Screen reader tested and optimized
- [ ] Color contrast ratios meet requirements

### Performance ✅
- [ ] Page loads under 3 seconds
- [ ] Images optimized and properly sized
- [ ] CSS and JavaScript minified
- [ ] No console errors or warnings
- [ ] Lighthouse score 90+ for Performance and Accessibility

### Code Quality ✅
- [ ] Clean, maintainable HTML/CSS/JS
- [ ] Proper commenting and documentation
- [ ] Consistent code formatting
- [ ] No deprecated or obsolete code
- [ ] Follows web standards and best practices

## Advanced Features (Bonus)

1. **Progressive Web App**: Add service worker and manifest
2. **Advanced Animations**: CSS animations and transitions
3. **Contact Form**: Working contact form with validation
4. **Google Maps Integration**: Interactive location map
5. **Online Ordering**: Basic menu ordering system

## Common Pitfalls to Avoid

- Non-semantic HTML structure
- Poor mobile experience
- Inaccessible navigation menus
- Missing alt text on images
- Poor color contrast ratios
- Slow loading images
- Broken responsive design
- JavaScript errors in console

## Submission Format

```
coffee-shop-homepage/
├── index.html              # Main homepage
├── styles.css              # All styling (mobile-first)
├── script.js               # Interactive functionality
├── images/                 # Optimized image assets
│   ├── logo.svg
│   ├── hero-coffee.jpg
│   ├── coffee-roasting.jpg
│   └── product-images/
├── tests/                  # Testing files
│   ├── accessibility-test.js
│   ├── responsive-test.js
│   └── performance-test.js
├── screenshots/            # Visual documentation
│   ├── desktop-view.png
│   ├── mobile-view.png
│   ├── accessibility-audit.png
│   └── lighthouse-score.png
└── README.md              # Setup and deployment guide
```

## Evaluation Criteria

- **Visual Design (25%)**: Professional appearance, branding consistency
- **Responsive Design (25%)**: Mobile-first, works on all devices
- **Accessibility (25%)**: WCAG compliance, screen reader friendly
- **Code Quality (25%)**: Clean, maintainable, performant code