# Simple Blog Layout Implementation Challenge

## Problem Statement

Build a production-ready blog layout featuring article listings, tag filtering, and responsive design. The blog must demonstrate modern content organization, semantic HTML structure, and excellent user experience for content discovery and reading.

## Requirements

### Core Features
Implement a complete blog layout with:

1. **Article List Page**
   - Grid/list view of blog posts
   - Article previews with excerpts
   - Publication dates and author information
   - Read time estimates
   - Featured image thumbnails

2. **Tag System**
   - Visual tag display on articles
   - Clickable tag filtering
   - Tag cloud or category sidebar
   - Active tag state indication

3. **Article Detail View**
   - Full article content with proper typography
   - Author bio and publication info
   - Related articles suggestions
   - Social sharing buttons

4. **Navigation & Search**
   - Pagination for article lists
   - Search functionality (client-side)
   - Breadcrumb navigation
   - Archive/category organization

### Technical Constraints

- **Pure HTML/CSS/JS**: No frameworks or libraries
- **Responsive Design**: Mobile-first approach
- **Performance**: Fast loading, optimized images
- **Accessibility**: WCAG 2.1 AA compliance
- **SEO Optimized**: Proper meta tags and structure

## Input Specifications

Create these files:
- `index.html` - Main blog listing page
- `article.html` - Individual article template
- `styles.css` - All styling
- `blog.js` - Filtering and search functionality
- `articles/` - Sample article content
- `README.md` - Setup guide

## Expected Output

### HTML Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tech Insights Blog - Latest Web Development Articles</title>
    <meta name="description" content="Discover the latest trends in web development, JavaScript tutorials, and programming best practices.">
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <nav aria-label="Main navigation">
            <h1><a href="/">Tech Insights</a></h1>
            <ul class="nav-menu">
                <li><a href="#home">Home</a></li>
                <li><a href="#categories">Categories</a></li>
                <li><a href="#about">About</a></li>
            </ul>
        </nav>
        
        <div class="search-container">
            <label for="search-input" class="sr-only">Search articles</label>
            <input type="search" id="search-input" placeholder="Search articles...">
            <button type="button" class="search-btn">Search</button>
        </div>
    </header>

    <main>
        <section class="blog-header">
            <h2>Latest Articles</h2>
            <p>Insights and tutorials on modern web development</p>
        </section>

        <div class="blog-container">
            <aside class="sidebar">
                <section class="tag-filter">
                    <h3>Filter by Tags</h3>
                    <div class="tag-cloud">
                        <button class="tag-btn active" data-tag="all">All Posts</button>
                        <button class="tag-btn" data-tag="javascript">JavaScript</button>
                        <button class="tag-btn" data-tag="css">CSS</button>
                        <button class="tag-btn" data-tag="html">HTML</button>
                        <button class="tag-btn" data-tag="react">React</button>
                        <button class="tag-btn" data-tag="nodejs">Node.js</button>
                    </div>
                </section>

                <section class="recent-posts">
                    <h3>Recent Posts</h3>
                    <ul class="recent-list">
                        <li><a href="articles/css-grid-guide.html">Complete CSS Grid Guide</a></li>
                        <li><a href="articles/js-async-await.html">Mastering Async/Await</a></li>
                    </ul>
                </section>
            </aside>

            <section class="articles-grid">
                <article class="article-card" data-tags="javascript,tutorial">
                    <figure class="article-image">
                        <img src="images/js-fundamentals.jpg" alt="JavaScript code on computer screen">
                    </figure>
                    
                    <div class="article-content">
                        <header class="article-header">
                            <div class="article-meta">
                                <time datetime="2024-01-15">January 15, 2024</time>
                                <span class="read-time">5 min read</span>
                            </div>
                            <h3><a href="articles/js-fundamentals.html">JavaScript Fundamentals Every Developer Should Know</a></h3>
                        </header>
                        
                        <p class="article-excerpt">
                            Master the core concepts of JavaScript including closures, hoisting, and the event loop...
                        </p>
                        
                        <footer class="article-footer">
                            <div class="article-tags">
                                <span class="tag">JavaScript</span>
                                <span class="tag">Tutorial</span>
                            </div>
                            <div class="article-author">
                                <img src="images/author-jane.jpg" alt="Jane Smith" class="author-avatar">
                                <span>Jane Smith</span>
                            </div>
                        </footer>
                    </div>
                </article>

                <article class="article-card" data-tags="css,design">
                    <figure class="article-image">
                        <img src="images/css-grid.jpg" alt="CSS Grid layout examples">
                    </figure>
                    
                    <div class="article-content">
                        <header class="article-header">
                            <div class="article-meta">
                                <time datetime="2024-01-12">January 12, 2024</time>
                                <span class="read-time">8 min read</span>
                            </div>
                            <h3><a href="articles/css-grid-guide.html">Complete Guide to CSS Grid Layout</a></h3>
                        </header>
                        
                        <p class="article-excerpt">
                            Learn how to create complex layouts with CSS Grid, from basic concepts to advanced techniques...
                        </p>
                        
                        <footer class="article-footer">
                            <div class="article-tags">
                                <span class="tag">CSS</span>
                                <span class="tag">Design</span>
                            </div>
                            <div class="article-author">
                                <img src="images/author-john.jpg" alt="John Doe" class="author-avatar">
                                <span>John Doe</span>
                            </div>
                        </footer>
                    </div>
                </article>
            </section>
        </div>

        <nav class="pagination" aria-label="Article pagination">
            <a href="#" class="pagination-btn" aria-label="Previous page">← Previous</a>
            <span class="pagination-info">Page 1 of 5</span>
            <a href="#" class="pagination-btn" aria-label="Next page">Next →</a>
        </nav>
    </main>

    <footer>
        <p>&copy; 2024 Tech Insights Blog. All rights reserved.</p>
    </footer>

    <script src="blog.js"></script>
</body>
</html>
```

## Test Cases

### Test Case 1: Tag Filtering
```javascript
describe('Tag Filtering', () => {
    test('filters articles by selected tag', () => {
        cy.visit('/');
        
        // Click JavaScript tag
        cy.get('[data-tag="javascript"]').click();
        
        // Only JavaScript articles should be visible
        cy.get('.article-card:visible').should('have.length', 3);
        cy.get('.article-card:visible').each($article => {
            cy.wrap($article).should('have.attr', 'data-tags').and('contain', 'javascript');
        });
    });
});
```

### Test Case 2: Search Functionality
```javascript
describe('Search', () => {
    test('searches articles by title and content', () => {
        cy.visit('/');
        
        cy.get('#search-input').type('CSS Grid');
        cy.get('.search-btn').click();
        
        cy.get('.article-card:visible').should('have.length', 1);
        cy.get('.article-card:visible h3').should('contain', 'CSS Grid');
    });
});
```

## Acceptance Criteria

### Content Organization ✅
- [ ] Clear article listing with previews
- [ ] Functional tag filtering system
- [ ] Search functionality works correctly
- [ ] Pagination for large article lists
- [ ] Related articles suggestions

### Design & UX ✅
- [ ] Clean, readable typography
- [ ] Responsive grid layout
- [ ] Consistent visual hierarchy
- [ ] Smooth interactions and transitions
- [ ] Mobile-optimized reading experience

### Accessibility ✅
- [ ] Semantic HTML structure
- [ ] Keyboard navigation support
- [ ] Screen reader compatibility
- [ ] Proper heading hierarchy
- [ ] Alt text for all images

### Performance ✅
- [ ] Fast page load times
- [ ] Optimized images
- [ ] Efficient filtering/search
- [ ] No JavaScript errors
- [ ] Cross-browser compatibility

## Submission Format

```
simple-blog-layout/
├── index.html              # Main blog listing
├── article.html            # Article template
├── styles.css              # All styling
├── blog.js                 # Functionality
├── articles/               # Sample articles
│   ├── js-fundamentals.html
│   ├── css-grid-guide.html
│   └── react-hooks.html
├── images/                 # Optimized images
├── tests/                  # Testing files
└── README.md              # Setup guide
```