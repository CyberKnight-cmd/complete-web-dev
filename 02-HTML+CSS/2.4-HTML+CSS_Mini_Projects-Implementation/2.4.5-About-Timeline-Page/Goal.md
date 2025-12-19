# About/Timeline Page Implementation Challenge

## Problem Statement

Build a production-ready About page featuring an interactive timeline component that tells a compelling company story through key milestones. The page must engage visitors with visual storytelling while maintaining excellent accessibility and responsive design.

## Requirements

### Core Features
Implement an About page with:

1. **Company Story Section**
   - Compelling hero section with mission/vision
   - Founder story and company values
   - Team introduction with photos
   - Company statistics and achievements

2. **Interactive Timeline Component**
   - Chronological milestone display
   - Visual timeline with connecting lines
   - Expandable milestone details
   - Smooth animations and transitions
   - Mobile-optimized vertical layout

3. **Milestone Content**
   - Key company achievements and events
   - Product launches and major updates
   - Growth metrics and milestones
   - Awards and recognition
   - Future roadmap items

4. **Visual Elements**
   - High-quality imagery and graphics
   - Consistent branding and colors
   - Icon system for different milestone types
   - Progress indicators and visual cues

### Technical Constraints

- **Pure HTML/CSS/JS**: No timeline libraries
- **Responsive Design**: Mobile-first approach
- **Accessibility**: WCAG 2.1 AA compliance
- **Performance**: Smooth animations, optimized images
- **Cross-browser**: Chrome, Firefox, Safari, Edge

## Input Specifications

Create these files:
- `index.html` - About page with timeline
- `styles.css` - Responsive styling with animations
- `timeline.js` - Interactive timeline functionality
- `images/` - Company photos and milestone images
- `README.md` - Setup and usage guide

## Expected Output

### HTML Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About TechFlow - Our Journey of Innovation</title>
    <meta name="description" content="Learn about TechFlow's mission to revolutionize productivity tools. Discover our journey from startup to industry leader through key milestones.">
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header class="page-header">
        <nav aria-label="Main navigation">
            <a href="/" class="logo">TechFlow</a>
            <ul class="nav-menu">
                <li><a href="/">Home</a></li>
                <li><a href="/about" aria-current="page">About</a></li>
                <li><a href="/products">Products</a></li>
                <li><a href="/contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <!-- Hero Section -->
        <section class="hero-section">
            <div class="hero-content">
                <h1>Building the Future of Productivity</h1>
                <p class="hero-subtitle">We're on a mission to help teams work smarter, not harder, through innovative technology solutions.</p>
                
                <div class="company-stats">
                    <div class="stat-item">
                        <span class="stat-number">50K+</span>
                        <span class="stat-label">Active Users</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">150+</span>
                        <span class="stat-label">Countries</span>
                    </div>
                    <div class="stat-item">
                        <span class="stat-number">99.9%</span>
                        <span class="stat-label">Uptime</span>
                    </div>
                </div>
            </div>
            
            <figure class="hero-image">
                <img src="images/team-collaboration.jpg" alt="TechFlow team collaborating in modern office space">
            </figure>
        </section>

        <!-- Mission & Values -->
        <section class="mission-section">
            <div class="container">
                <h2>Our Mission</h2>
                <p class="mission-statement">To empower teams worldwide with intuitive tools that eliminate friction, enhance collaboration, and unlock human potential in the digital workplace.</p>
                
                <div class="values-grid">
                    <article class="value-card">
                        <div class="value-icon">
                            <svg width="48" height="48" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                                <path d="M12 2L2 7L12 12L22 7L12 2Z" stroke="currentColor" stroke-width="2"/>
                                <path d="M2 17L12 22L22 17" stroke="currentColor" stroke-width="2"/>
                                <path d="M2 12L12 17L22 12" stroke="currentColor" stroke-width="2"/>
                            </svg>
                        </div>
                        <h3>Innovation First</h3>
                        <p>We constantly push boundaries to create solutions that don't just meet today's needs, but anticipate tomorrow's challenges.</p>
                    </article>
                    
                    <article class="value-card">
                        <div class="value-icon">
                            <svg width="48" height="48" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                                <path d="M17 21V19C17 16.7909 15.2091 15 13 15H5C2.79086 15 1 16.7909 1 19V21" stroke="currentColor" stroke-width="2"/>
                                <circle cx="9" cy="7" r="4" stroke="currentColor" stroke-width="2"/>
                                <path d="M23 21V19C23 18.1645 22.7155 17.3541 22.2094 16.7018C21.7033 16.0494 20.9999 15.5901 20.2 15.4" stroke="currentColor" stroke-width="2"/>
                                <path d="M16 3.13C16.8003 3.35 17.5037 3.80929 18.0098 4.46163C18.5159 5.11396 18.8004 5.92436 18.8004 6.76C18.8004 7.59564 18.5159 8.40604 18.0098 9.05837C17.5037 9.71071 16.8003 10.17 16 10.39" stroke="currentColor" stroke-width="2"/>
                            </svg>
                        </div>
                        <h3>People Centered</h3>
                        <p>Every decision we make starts with understanding how it impacts the real people using our products every day.</p>
                    </article>
                    
                    <article class="value-card">
                        <div class="value-icon">
                            <svg width="48" height="48" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                                <circle cx="12" cy="12" r="10" stroke="currentColor" stroke-width="2"/>
                                <path d="M8 14S9.5 16 12 16S16 14 16 14" stroke="currentColor" stroke-width="2"/>
                                <line x1="9" y1="9" x2="9.01" y2="9" stroke="currentColor" stroke-width="2"/>
                                <line x1="15" y1="9" x2="15.01" y2="9" stroke="currentColor" stroke-width="2"/>
                            </svg>
                        </div>
                        <h3>Transparency</h3>
                        <p>We believe in open communication, honest feedback, and building trust through consistent, reliable actions.</p>
                    </article>
                </div>
            </div>
        </section>

        <!-- Timeline Section -->
        <section class="timeline-section">
            <div class="container">
                <header class="timeline-header">
                    <h2>Our Journey</h2>
                    <p>From a small startup to a global platform, here are the key milestones that shaped TechFlow.</p>
                </header>

                <div class="timeline-container">
                    <div class="timeline-line" aria-hidden="true"></div>
                    
                    <article class="timeline-item" data-year="2019">
                        <div class="timeline-marker">
                            <div class="timeline-icon">
                                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                                    <path d="M12 2L2 7L12 12L22 7L12 2Z" stroke="currentColor" stroke-width="2"/>
                                </svg>
                            </div>
                        </div>
                        
                        <div class="timeline-content">
                            <header class="timeline-item-header">
                                <time datetime="2019-03">March 2019</time>
                                <h3>The Beginning</h3>
                            </header>
                            
                            <div class="timeline-details">
                                <p>TechFlow was founded by three college friends who were frustrated with existing productivity tools. Starting in a small garage, we set out to build something better.</p>
                                
                                <div class="timeline-stats">
                                    <span class="stat">3 Founders</span>
                                    <span class="stat">$50K Initial Investment</span>
                                </div>
                            </div>
                            
                            <button class="timeline-toggle" aria-expanded="false" aria-controls="timeline-2019-details">
                                <span class="sr-only">Show more details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                                    <path d="M6 9L12 15L18 9" stroke="currentColor" stroke-width="2"/>
                                </svg>
                            </button>
                            
                            <div id="timeline-2019-details" class="timeline-expanded" hidden>
                                <figure class="timeline-image">
                                    <img src="images/garage-startup.jpg" alt="Three founders working on laptops in garage office">
                                    <figcaption>Our humble beginnings in Sarah's garage</figcaption>
                                </figure>
                                <p>The idea came during a particularly frustrating group project in our final semester. We spent more time managing our workflow than actually working. That's when we knew there had to be a better way.</p>
                            </div>
                        </div>
                    </article>

                    <article class="timeline-item" data-year="2020">
                        <div class="timeline-marker">
                            <div class="timeline-icon">
                                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                                    <path d="M14.7 6.3C15.1 6.7 15.1 7.3 14.7 7.7L11.4 11L14.7 14.3C15.1 14.7 15.1 15.3 14.7 15.7C14.3 16.1 13.7 16.1 13.3 15.7L9.3 11.7C8.9 11.3 8.9 10.7 9.3 10.3L13.3 6.3C13.7 5.9 14.3 5.9 14.7 6.3Z" fill="currentColor"/>
                                </svg>
                            </div>
                        </div>
                        
                        <div class="timeline-content">
                            <header class="timeline-item-header">
                                <time datetime="2020-08">August 2020</time>
                                <h3>First Product Launch</h3>
                            </header>
                            
                            <div class="timeline-details">
                                <p>After 18 months of development, we launched TechFlow 1.0 with basic project management features. The response exceeded our wildest expectations.</p>
                                
                                <div class="timeline-stats">
                                    <span class="stat">1,000 Beta Users</span>
                                    <span class="stat">$100K ARR</span>
                                </div>
                            </div>
                            
                            <button class="timeline-toggle" aria-expanded="false" aria-controls="timeline-2020-details">
                                <span class="sr-only">Show more details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                                    <path d="M6 9L12 15L18 9" stroke="currentColor" stroke-width="2"/>
                                </svg>
                            </button>
                            
                            <div id="timeline-2020-details" class="timeline-expanded" hidden>
                                <p>The launch was both thrilling and terrifying. We had prepared for maybe 100 users in the first month, but we got 1,000 in the first week. Our servers crashed twice, but our users were incredibly patient and supportive.</p>
                            </div>
                        </div>
                    </article>

                    <article class="timeline-item" data-year="2021">
                        <div class="timeline-marker">
                            <div class="timeline-icon">
                                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                                    <path d="M12 2L2 7L12 12L22 7L12 2Z" stroke="currentColor" stroke-width="2"/>
                                    <path d="M2 17L12 22L22 17" stroke="currentColor" stroke-width="2"/>
                                </svg>
                            </div>
                        </div>
                        
                        <div class="timeline-content">
                            <header class="timeline-item-header">
                                <time datetime="2021-05">May 2021</time>
                                <h3>Series A Funding</h3>
                            </header>
                            
                            <div class="timeline-details">
                                <p>Secured $5M in Series A funding led by Innovation Ventures. This allowed us to expand our team and accelerate product development.</p>
                                
                                <div class="timeline-stats">
                                    <span class="stat">$5M Raised</span>
                                    <span class="stat">15 Team Members</span>
                                </div>
                            </div>
                            
                            <button class="timeline-toggle" aria-expanded="false" aria-controls="timeline-2021-details">
                                <span class="sr-only">Show more details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                                    <path d="M6 9L12 15L18 9" stroke="currentColor" stroke-width="2"/>
                                </svg>
                            </button>
                            
                            <div id="timeline-2021-details" class="timeline-expanded" hidden>
                                <p>The funding round was led by Sarah Chen from Innovation Ventures, who became not just an investor but a trusted advisor. With the new capital, we moved out of the garage and into our first real office.</p>
                            </div>
                        </div>
                    </article>

                    <article class="timeline-item" data-year="2022">
                        <div class="timeline-marker">
                            <div class="timeline-icon">
                                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                                    <circle cx="12" cy="12" r="10" stroke="currentColor" stroke-width="2"/>
                                    <path d="M8 14S9.5 16 12 16S16 14 16 14" stroke="currentColor" stroke-width="2"/>
                                </svg>
                            </div>
                        </div>
                        
                        <div class="timeline-content">
                            <header class="timeline-item-header">
                                <time datetime="2022-11">November 2022</time>
                                <h3>10,000 Customers</h3>
                            </header>
                            
                            <div class="timeline-details">
                                <p>Reached the milestone of 10,000 paying customers across 50 countries. Launched advanced analytics and team collaboration features.</p>
                                
                                <div class="timeline-stats">
                                    <span class="stat">10K Customers</span>
                                    <span class="stat">50 Countries</span>
                                </div>
                            </div>
                            
                            <button class="timeline-toggle" aria-expanded="false" aria-controls="timeline-2022-details">
                                <span class="sr-only">Show more details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                                    <path d="M6 9L12 15L18 9" stroke="currentColor" stroke-width="2"/>
                                </svg>
                            </button>
                            
                            <div id="timeline-2022-details" class="timeline-expanded" hidden>
                                <p>This was a huge milestone for us. We celebrated by flying the entire team to our first company retreat in Costa Rica. It was amazing to finally meet some of our remote team members in person.</p>
                            </div>
                        </div>
                    </article>

                    <article class="timeline-item" data-year="2024">
                        <div class="timeline-marker">
                            <div class="timeline-icon">
                                <svg width="24" height="24" viewBox="0 0 24 24" fill="none" aria-hidden="true">
                                    <path d="M13 2L3 14H12L11 22L21 10H12L13 2Z" stroke="currentColor" stroke-width="2"/>
                                </svg>
                            </div>
                        </div>
                        
                        <div class="timeline-content">
                            <header class="timeline-item-header">
                                <time datetime="2024-01">January 2024</time>
                                <h3>AI Integration Launch</h3>
                            </header>
                            
                            <div class="timeline-details">
                                <p>Launched TechFlow AI, bringing intelligent automation and insights to our platform. Now serving 50,000+ users worldwide.</p>
                                
                                <div class="timeline-stats">
                                    <span class="stat">50K Users</span>
                                    <span class="stat">AI-Powered</span>
                                </div>
                            </div>
                            
                            <button class="timeline-toggle" aria-expanded="false" aria-controls="timeline-2024-details">
                                <span class="sr-only">Show more details</span>
                                <svg width="16" height="16" viewBox="0 0 24 24" fill="none">
                                    <path d="M6 9L12 15L18 9" stroke="currentColor" stroke-width="2"/>
                                </svg>
                            </button>
                            
                            <div id="timeline-2024-details" class="timeline-expanded" hidden>
                                <p>The AI integration represents our biggest technical achievement yet. Our smart automation features can now predict project bottlenecks and suggest optimizations, saving teams an average of 10 hours per week.</p>
                            </div>
                        </div>
                    </article>
                </div>
            </div>
        </section>

        <!-- Team Section -->
        <section class="team-section">
            <div class="container">
                <h2>Meet Our Team</h2>
                <p>The passionate people behind TechFlow's success</p>
                
                <div class="team-grid">
                    <article class="team-member">
                        <figure class="member-photo">
                            <img src="images/ceo-sarah.jpg" alt="Sarah Johnson, CEO and Co-founder">
                        </figure>
                        <div class="member-info">
                            <h3>Sarah Johnson</h3>
                            <p class="member-role">CEO & Co-founder</p>
                            <p class="member-bio">Former product manager at Google with 8 years of experience building user-centric software solutions.</p>
                        </div>
                    </article>
                    
                    <article class="team-member">
                        <figure class="member-photo">
                            <img src="images/cto-mike.jpg" alt="Mike Chen, CTO and Co-founder">
                        </figure>
                        <div class="member-info">
                            <h3>Mike Chen</h3>
                            <p class="member-role">CTO & Co-founder</p>
                            <p class="member-bio">Full-stack engineer with expertise in scalable architecture and machine learning systems.</p>
                        </div>
                    </article>
                    
                    <article class="team-member">
                        <figure class="member-photo">
                            <img src="images/cpo-alex.jpg" alt="Alex Rodriguez, CPO and Co-founder">
                        </figure>
                        <div class="member-info">
                            <h3>Alex Rodriguez</h3>
                            <p class="member-role">CPO & Co-founder</p>
                            <p class="member-bio">UX designer and product strategist focused on creating intuitive, delightful user experiences.</p>
                        </div>
                    </article>
                </div>
            </div>
        </section>
    </main>

    <footer class="page-footer">
        <div class="container">
            <p>&copy; 2024 TechFlow. All rights reserved.</p>
        </div>
    </footer>

    <script src="timeline.js"></script>
</body>
</html>
```

## Test Cases

### Test Case 1: Timeline Interaction
```javascript
describe('Timeline Functionality', () => {
    test('expands timeline items when clicked', () => {
        cy.visit('/');
        
        cy.get('.timeline-toggle').first().click();
        cy.get('.timeline-expanded').first().should('be.visible');
        cy.get('.timeline-toggle').first().should('have.attr', 'aria-expanded', 'true');
    });
    
    test('collapses expanded items', () => {
        cy.visit('/');
        
        cy.get('.timeline-toggle').first().click();
        cy.get('.timeline-toggle').first().click();
        cy.get('.timeline-expanded').first().should('not.be.visible');
    });
});
```

### Test Case 2: Responsive Timeline
```javascript
describe('Responsive Timeline', () => {
    test('displays correctly on mobile', () => {
        cy.viewport(375, 667);
        cy.visit('/');
        
        cy.get('.timeline-container').should('be.visible');
        cy.get('.timeline-item').should('have.css', 'flex-direction', 'column');
    });
});
```

## Acceptance Criteria

### Content & Storytelling ✅
- [ ] Compelling company story and mission
- [ ] Clear timeline with key milestones
- [ ] Team introduction with photos
- [ ] Company statistics and achievements
- [ ] Engaging visual storytelling

### Timeline Component ✅
- [ ] Interactive milestone expansion
- [ ] Smooth animations and transitions
- [ ] Mobile-optimized vertical layout
- [ ] Keyboard accessible interactions
- [ ] Visual timeline with connecting lines

### Design & UX ✅
- [ ] Professional, cohesive visual design
- [ ] Responsive layout (mobile-first)
- [ ] Consistent branding and typography
- [ ] High-quality imagery throughout
- [ ] Intuitive navigation and interactions

### Accessibility ✅
- [ ] WCAG 2.1 AA compliance
- [ ] Semantic HTML structure
- [ ] Keyboard navigation support
- [ ] Screen reader compatibility
- [ ] Proper ARIA labels and states

## Submission Format

```
about-timeline-page/
├── index.html              # About page with timeline
├── styles.css              # Responsive styling
├── timeline.js             # Interactive functionality
├── images/                 # Company and team photos
├── tests/                  # Accessibility tests
└── README.md              # Setup guide
```