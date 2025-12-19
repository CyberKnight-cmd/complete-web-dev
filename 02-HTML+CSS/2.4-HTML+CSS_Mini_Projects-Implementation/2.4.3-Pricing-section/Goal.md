# Pricing Section Implementation Challenge

## Problem Statement

Build a production-ready pricing section with three-tier cards that effectively converts visitors into customers. The design must highlight the "best value" option using accessibility-friendly colors and contrast while maintaining visual appeal and clear value proposition.

## Requirements

### Core Features
Implement a pricing section with:

1. **Three-Tier Structure**
   - Basic/Starter plan
   - Popular/Professional plan (highlighted)
   - Premium/Enterprise plan
   - Clear feature comparisons
   - Prominent pricing display

2. **Best Value Highlighting**
   - Visual emphasis on recommended plan
   - "Most Popular" or "Best Value" badge
   - Enhanced styling without compromising accessibility
   - WCAG AA compliant color contrast (4.5:1 minimum)

3. **Interactive Elements**
   - Hover effects on cards
   - Call-to-action buttons
   - Toggle between monthly/yearly pricing
   - Smooth animations and transitions

4. **Responsive Design**
   - Mobile-first approach
   - Cards stack on mobile, side-by-side on desktop
   - Readable on all screen sizes
   - Touch-friendly buttons

### Technical Constraints

- **Pure HTML/CSS/JS**: No frameworks
- **Accessibility**: WCAG 2.1 AA compliance
- **Performance**: Smooth animations, fast loading
- **Cross-browser**: Chrome, Firefox, Safari, Edge
- **Color Contrast**: 4.5:1 for text, 3:1 for UI elements

## Input Specifications

Create these files:
- `index.html` - Pricing section page
- `styles.css` - All styling with accessibility focus
- `pricing.js` - Interactive functionality
- `README.md` - Setup and accessibility notes

## Expected Output

### HTML Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pricing Plans - Choose Your Perfect Plan</title>
    <meta name="description" content="Flexible pricing plans for every need. Start free or choose from our affordable professional plans with advanced features.">
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <main>
        <section class="pricing-section">
            <header class="pricing-header">
                <h1>Choose Your Plan</h1>
                <p>Flexible pricing that grows with your business</p>
                
                <div class="billing-toggle">
                    <span class="billing-label">Monthly</span>
                    <button class="toggle-switch" 
                            role="switch" 
                            aria-checked="false"
                            aria-label="Switch to yearly billing">
                        <span class="toggle-slider"></span>
                    </button>
                    <span class="billing-label">
                        Yearly 
                        <span class="discount-badge">Save 20%</span>
                    </span>
                </div>
            </header>

            <div class="pricing-grid">
                <!-- Basic Plan -->
                <article class="pricing-card">
                    <header class="card-header">
                        <h2>Starter</h2>
                        <p class="plan-description">Perfect for individuals getting started</p>
                    </header>
                    
                    <div class="price-display">
                        <span class="currency">$</span>
                        <span class="price" data-monthly="9" data-yearly="7">9</span>
                        <span class="period">/month</span>
                    </div>
                    
                    <ul class="features-list">
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Up to 5 projects
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            10GB storage
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Email support
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Basic analytics
                        </li>
                    </ul>
                    
                    <button class="cta-button cta-secondary">Get Started</button>
                </article>

                <!-- Professional Plan (Highlighted) -->
                <article class="pricing-card featured" aria-label="Most popular plan">
                    <div class="popular-badge">Most Popular</div>
                    
                    <header class="card-header">
                        <h2>Professional</h2>
                        <p class="plan-description">Best for growing businesses and teams</p>
                    </header>
                    
                    <div class="price-display">
                        <span class="currency">$</span>
                        <span class="price" data-monthly="29" data-yearly="23">29</span>
                        <span class="period">/month</span>
                    </div>
                    
                    <ul class="features-list">
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Unlimited projects
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            100GB storage
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Priority support
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Advanced analytics
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Team collaboration
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            API access
                        </li>
                    </ul>
                    
                    <button class="cta-button cta-primary">Start Free Trial</button>
                </article>

                <!-- Enterprise Plan -->
                <article class="pricing-card">
                    <header class="card-header">
                        <h2>Enterprise</h2>
                        <p class="plan-description">Advanced features for large organizations</p>
                    </header>
                    
                    <div class="price-display">
                        <span class="currency">$</span>
                        <span class="price" data-monthly="99" data-yearly="79">99</span>
                        <span class="period">/month</span>
                    </div>
                    
                    <ul class="features-list">
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Everything in Professional
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Unlimited storage
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            24/7 phone support
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Custom integrations
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Advanced security
                        </li>
                        <li>
                            <span class="feature-icon" aria-hidden="true">✓</span>
                            Dedicated account manager
                        </li>
                    </ul>
                    
                    <button class="cta-button cta-secondary">Contact Sales</button>
                </article>
            </div>

            <footer class="pricing-footer">
                <p>All plans include a 30-day money-back guarantee</p>
                <p><a href="#faq">Have questions? Check our FAQ</a></p>
            </footer>
        </section>
    </main>

    <script src="pricing.js"></script>
</body>
</html>
```

### CSS with Accessibility Focus
```css
/* Color system with WCAG AA compliance */
:root {
    --primary-color: #2563eb;      /* 4.56:1 on white */
    --primary-hover: #1d4ed8;      /* 5.93:1 on white */
    --secondary-color: #64748b;    /* 4.54:1 on white */
    --success-color: #059669;      /* 4.52:1 on white */
    --text-primary: #1f2937;       /* 16.75:1 on white */
    --text-secondary: #6b7280;     /* 4.69:1 on white */
    --border-color: #d1d5db;       /* 3.28:1 on white */
    --background-light: #f9fafb;
    --white: #ffffff;
    
    /* Featured card colors */
    --featured-bg: #eff6ff;        /* Light blue background */
    --featured-border: #2563eb;    /* Primary blue border */
    --featured-badge: #1d4ed8;     /* Badge background */
}

/* Reset and base styles */
*, *::before, *::after {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    line-height: 1.6;
    color: var(--text-primary);
    background: var(--background-light);
}

/* Focus indicators */
:focus {
    outline: 3px solid var(--primary-color);
    outline-offset: 2px;
}

/* Pricing section */
.pricing-section {
    max-width: 1200px;
    margin: 0 auto;
    padding: 4rem 1rem;
}

.pricing-header {
    text-align: center;
    margin-bottom: 3rem;
}

.pricing-header h1 {
    font-size: 2.5rem;
    margin-bottom: 1rem;
    color: var(--text-primary);
}

.pricing-header p {
    font-size: 1.25rem;
    color: var(--text-secondary);
    margin-bottom: 2rem;
}

/* Billing toggle */
.billing-toggle {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1rem;
    margin-bottom: 2rem;
}

.billing-label {
    font-weight: 500;
    color: var(--text-primary);
}

.toggle-switch {
    position: relative;
    width: 60px;
    height: 30px;
    background: var(--border-color);
    border: none;
    border-radius: 15px;
    cursor: pointer;
    transition: background-color 0.3s ease;
}

.toggle-switch[aria-checked="true"] {
    background: var(--primary-color);
}

.toggle-slider {
    position: absolute;
    top: 3px;
    left: 3px;
    width: 24px;
    height: 24px;
    background: var(--white);
    border-radius: 50%;
    transition: transform 0.3s ease;
}

.toggle-switch[aria-checked="true"] .toggle-slider {
    transform: translateX(30px);
}

.discount-badge {
    background: var(--success-color);
    color: var(--white);
    padding: 0.25rem 0.5rem;
    border-radius: 12px;
    font-size: 0.75rem;
    font-weight: 600;
    margin-left: 0.5rem;
}

/* Pricing grid */
.pricing-grid {
    display: grid;
    grid-template-columns: 1fr;
    gap: 2rem;
    margin-bottom: 3rem;
}

@media (min-width: 768px) {
    .pricing-grid {
        grid-template-columns: repeat(3, 1fr);
        gap: 1.5rem;
    }
}

/* Pricing cards */
.pricing-card {
    background: var(--white);
    border: 2px solid var(--border-color);
    border-radius: 12px;
    padding: 2rem;
    position: relative;
    transition: all 0.3s ease;
}

.pricing-card:hover {
    transform: translateY(-4px);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.1);
}

/* Featured card styling */
.pricing-card.featured {
    background: var(--featured-bg);
    border-color: var(--featured-border);
    border-width: 3px;
    transform: scale(1.05);
}

.pricing-card.featured:hover {
    transform: scale(1.05) translateY(-4px);
}

.popular-badge {
    position: absolute;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    background: var(--featured-badge);
    color: var(--white);
    padding: 0.5rem 1.5rem;
    border-radius: 20px;
    font-size: 0.875rem;
    font-weight: 600;
}

/* Card content */
.card-header h2 {
    font-size: 1.5rem;
    margin-bottom: 0.5rem;
    color: var(--text-primary);
}

.plan-description {
    color: var(--text-secondary);
    margin-bottom: 1.5rem;
}

.price-display {
    display: flex;
    align-items: baseline;
    margin-bottom: 2rem;
}

.currency {
    font-size: 1.25rem;
    color: var(--text-secondary);
}

.price {
    font-size: 3rem;
    font-weight: 700;
    color: var(--text-primary);
}

.period {
    font-size: 1rem;
    color: var(--text-secondary);
    margin-left: 0.25rem;
}

/* Features list */
.features-list {
    list-style: none;
    padding: 0;
    margin-bottom: 2rem;
}

.features-list li {
    display: flex;
    align-items: center;
    padding: 0.5rem 0;
    color: var(--text-primary);
}

.feature-icon {
    color: var(--success-color);
    font-weight: bold;
    margin-right: 0.75rem;
    width: 16px;
}

/* CTA buttons */
.cta-button {
    width: 100%;
    padding: 1rem 2rem;
    border: none;
    border-radius: 8px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
}

.cta-primary {
    background: var(--primary-color);
    color: var(--white);
}

.cta-primary:hover,
.cta-primary:focus {
    background: var(--primary-hover);
    transform: translateY(-2px);
}

.cta-secondary {
    background: var(--white);
    color: var(--primary-color);
    border: 2px solid var(--primary-color);
}

.cta-secondary:hover,
.cta-secondary:focus {
    background: var(--primary-color);
    color: var(--white);
}

/* Footer */
.pricing-footer {
    text-align: center;
    color: var(--text-secondary);
}

.pricing-footer a {
    color: var(--primary-color);
    text-decoration: none;
}

.pricing-footer a:hover,
.pricing-footer a:focus {
    text-decoration: underline;
}
```

## Test Cases

### Test Case 1: Accessibility Compliance
```javascript
describe('Accessibility', () => {
    test('meets WCAG AA color contrast requirements', () => {
        cy.visit('/');
        cy.injectAxe();
        cy.checkA11y(null, {
            rules: {
                'color-contrast': { enabled: true }
            }
        });
    });
    
    test('keyboard navigation works correctly', () => {
        cy.visit('/');
        
        // Tab through interactive elements
        cy.get('body').tab();
        cy.focused().should('have.class', 'toggle-switch');
        
        cy.focused().tab();
        cy.focused().should('contain', 'Get Started');
    });
});
```

### Test Case 2: Billing Toggle
```javascript
describe('Billing Toggle', () => {
    test('switches between monthly and yearly pricing', () => {
        cy.visit('/');
        
        // Check initial monthly pricing
        cy.get('.price').first().should('contain', '9');
        
        // Toggle to yearly
        cy.get('.toggle-switch').click();
        
        // Check yearly pricing
        cy.get('.price').first().should('contain', '7');
        cy.get('.toggle-switch').should('have.attr', 'aria-checked', 'true');
    });
});
```

## Acceptance Criteria

### Visual Design ✅
- [ ] Three distinct pricing tiers clearly presented
- [ ] Featured plan visually highlighted without accessibility issues
- [ ] Professional, modern design aesthetic
- [ ] Consistent typography and spacing
- [ ] Smooth hover effects and animations

### Accessibility ✅
- [ ] WCAG 2.1 AA color contrast compliance (4.5:1 minimum)
- [ ] Keyboard navigation fully functional
- [ ] Screen reader compatible
- [ ] Proper ARIA labels and roles
- [ ] Focus indicators visible and high contrast

### Functionality ✅
- [ ] Monthly/yearly billing toggle works
- [ ] All buttons and links functional
- [ ] Responsive design on all screen sizes
- [ ] Smooth animations and transitions
- [ ] Cross-browser compatibility

### Content & UX ✅
- [ ] Clear value proposition for each tier
- [ ] Feature comparison easy to understand
- [ ] Call-to-action buttons prominent and clear
- [ ] Pricing information clearly displayed
- [ ] Trust signals and guarantees included

## Submission Format

```
pricing-section/
├── index.html              # Pricing section page
├── styles.css              # Accessible styling
├── pricing.js              # Interactive functionality
├── tests/                  # Accessibility tests
├── screenshots/            # Visual documentation
└── README.md              # Setup and accessibility notes
```