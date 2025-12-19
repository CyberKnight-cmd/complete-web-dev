# SEO Basics: Titles, Descriptions, Crawlability - Notes

## Core Concepts

### Title Tags
The most important on-page SEO element:
```html
<title>Primary Keyword - Secondary Keyword | Brand Name</title>
<title>HTML SEO Guide - Best Practices for Developers | WebDev</title>
```

#### Title Tag Best Practices
- Keep under 60 characters
- Include primary keyword near beginning
- Make each page title unique
- Write for users, not just search engines
- Include brand name at end

### Meta Descriptions
Snippet that appears in search results:
```html
<meta name="description" content="Learn HTML SEO best practices including title optimization, meta descriptions, and crawlability techniques. Complete guide for developers.">
```

#### Meta Description Guidelines
- 150-160 characters optimal length
- Include primary keyword naturally
- Write compelling copy that encourages clicks
- Unique description for each page
- Include call-to-action when appropriate

### Heading Hierarchy for SEO
```html
<h1>Main Page Topic</h1>
  <h2>Primary Section</h2>
    <h3>Subsection</h3>
    <h3>Another Subsection</h3>
  <h2>Another Primary Section</h2>
    <h3>Related Subsection</h3>
```

### Semantic HTML for SEO
```html
<article>
    <header>
        <h1>Article Title</h1>
        <time datetime="2024-01-15">January 15, 2024</time>
    </header>
    
    <section>
        <h2>Introduction</h2>
        <p>Content with relevant keywords naturally integrated.</p>
    </section>
    
    <section>
        <h2>Main Content</h2>
        <p>Detailed information about the topic.</p>
    </section>
</article>
```

### Internal Linking
```html
<!-- Descriptive anchor text -->
<a href="/html-guide">Complete HTML Tutorial</a>
<a href="/css-basics">CSS Fundamentals Guide</a>

<!-- Avoid generic text -->
<a href="/guide">Click here</a> <!-- BAD -->
```

### Canonical URLs
```html
<link rel="canonical" href="https://example.com/preferred-url">
```

### Robots Meta Tag
```html
<!-- Allow indexing and following links -->
<meta name="robots" content="index, follow">

<!-- Prevent indexing -->
<meta name="robots" content="noindex, follow">

<!-- Prevent following links -->
<meta name="robots" content="index, nofollow">
```

## Crawlability Factors

### URL Structure
```html
<!-- Good: Descriptive URLs -->
https://example.com/html-seo-guide
https://example.com/tutorials/html-basics

<!-- Bad: Non-descriptive URLs -->
https://example.com/page?id=123
https://example.com/p/xyz789
```

### Site Navigation
```html
<nav aria-label="Main navigation">
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/tutorials">Tutorials</a></li>
        <li><a href="/guides">Guides</a></li>
        <li><a href="/about">About</a></li>
    </ul>
</nav>
```

### Breadcrumb Navigation
```html
<nav aria-label="Breadcrumb">
    <ol>
        <li><a href="/">Home</a></li>
        <li><a href="/tutorials">Tutorials</a></li>
        <li aria-current="page">HTML SEO</li>
    </ol>
</nav>
```

### Image SEO
```html
<img src="html-seo-guide.jpg" 
     alt="HTML SEO best practices diagram showing title tags, meta descriptions, and heading hierarchy">
```

## Mental Models

### Search Engine Crawling Process
1. Discover URLs through links and sitemaps
2. Crawl and parse HTML content
3. Extract and analyze text content
4. Follow internal and external links
5. Index relevant content
6. Rank pages based on relevance and authority

### SEO Content Hierarchy
- Title tag (highest weight)
- H1 heading
- H2-H6 headings
- Body content
- Alt text
- Meta description (for snippets)

## Best Practices

### Content Optimization
```html
<article>
    <h1>How to Optimize HTML for SEO</h1>
    
    <p>Search engine optimization (SEO) for HTML involves several key techniques including proper title tags, meta descriptions, and semantic markup.</p>
    
    <h2>Title Tag Optimization</h2>
    <p>Title tags are the most important on-page SEO element...</p>
    
    <h2>Meta Description Best Practices</h2>
    <p>Meta descriptions provide search engines with a summary...</p>
</article>
```

### Technical SEO Elements
```html
<head>
    <!-- Essential SEO meta tags -->
    <title>Page Title | Brand</title>
    <meta name="description" content="Page description">
    <link rel="canonical" href="https://example.com/page">
    <meta name="robots" content="index, follow">
    
    <!-- Language and locale -->
    <html lang="en">
    <meta name="language" content="English">
    
    <!-- Open Graph for social sharing -->
    <meta property="og:title" content="Page Title">
    <meta property="og:description" content="Page description">
    <meta property="og:url" content="https://example.com/page">
</head>
```

## Common SEO Mistakes

### Duplicate Content
```html
<!-- WRONG: Same title on multiple pages -->
<title>Welcome to Our Website</title>

<!-- CORRECT: Unique titles -->
<title>HTML Tutorial - Learn Web Development</title>
<title>CSS Guide - Styling Fundamentals</title>
```

### Missing or Poor Meta Descriptions
```html
<!-- WRONG: Generic or missing -->
<meta name="description" content="Welcome to our website">

<!-- CORRECT: Specific and compelling -->
<meta name="description" content="Learn HTML fundamentals with our comprehensive tutorial covering tags, attributes, and best practices for web development.">
```

### Poor Heading Structure
```html
<!-- WRONG: Skipping heading levels -->
<h1>Main Title</h1>
<h4>Section</h4> <!-- Skipped h2, h3 -->

<!-- CORRECT: Logical hierarchy -->
<h1>Main Title</h1>
<h2>Section</h2>
<h3>Subsection</h3>
```