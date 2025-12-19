# Sitemaps & robots.txt (intro) - Notes

## Core Concepts

### XML Sitemaps
XML sitemaps help search engines discover and understand your website structure.

#### Basic Sitemap Structure
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <url>
        <loc>https://example.com/</loc>
        <lastmod>2024-01-15</lastmod>
        <changefreq>weekly</changefreq>
        <priority>1.0</priority>
    </url>
    <url>
        <loc>https://example.com/about</loc>
        <lastmod>2024-01-10</lastmod>
        <changefreq>monthly</changefreq>
        <priority>0.8</priority>
    </url>
</urlset>
```

#### Sitemap Elements
- `<loc>`: URL of the page (required)
- `<lastmod>`: Last modification date (optional)
- `<changefreq>`: How frequently page changes (optional)
- `<priority>`: Relative priority (0.0 to 1.0, optional)

#### Change Frequency Values
- `always`: Changes every time accessed
- `hourly`: Changes hourly
- `daily`: Changes daily
- `weekly`: Changes weekly
- `monthly`: Changes monthly
- `yearly`: Changes yearly
- `never`: Archived content

### Robots.txt
Controls search engine crawler access to your website.

#### Basic robots.txt Structure
```
User-agent: *
Disallow: /admin/
Disallow: /private/
Allow: /public/

User-agent: Googlebot
Disallow: /temp/

Sitemap: https://example.com/sitemap.xml
```

#### Robots.txt Directives
- `User-agent`: Specifies which crawler the rules apply to
- `Disallow`: Blocks access to specified paths
- `Allow`: Explicitly allows access (overrides Disallow)
- `Sitemap`: Location of XML sitemap
- `Crawl-delay`: Delay between requests (seconds)

### Common User-Agent Values
```
User-agent: *              # All crawlers
User-agent: Googlebot       # Google's crawler
User-agent: Bingbot         # Bing's crawler
User-agent: Slurp           # Yahoo's crawler
User-agent: facebookexternalhit  # Facebook's crawler
```

## Implementation Examples

### Complete Sitemap Example
```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
    <!-- Homepage -->
    <url>
        <loc>https://example.com/</loc>
        <lastmod>2024-01-15T10:30:00Z</lastmod>
        <changefreq>weekly</changefreq>
        <priority>1.0</priority>
    </url>
    
    <!-- Main pages -->
    <url>
        <loc>https://example.com/about</loc>
        <lastmod>2024-01-10T14:20:00Z</lastmod>
        <changefreq>monthly</changefreq>
        <priority>0.8</priority>
    </url>
    
    <!-- Blog posts -->
    <url>
        <loc>https://example.com/blog/html-tutorial</loc>
        <lastmod>2024-01-12T09:15:00Z</lastmod>
        <changefreq>monthly</changefreq>
        <priority>0.6</priority>
    </url>
    
    <!-- Product pages -->
    <url>
        <loc>https://example.com/products/web-course</loc>
        <lastmod>2024-01-08T16:45:00Z</lastmod>
        <changefreq>weekly</changefreq>
        <priority>0.7</priority>
    </url>
</urlset>
```

### Comprehensive robots.txt Example
```
# Allow all crawlers to access most content
User-agent: *
Disallow: /admin/
Disallow: /private/
Disallow: /temp/
Disallow: /cgi-bin/
Disallow: /*.pdf$
Allow: /public/

# Specific rules for Googlebot
User-agent: Googlebot
Disallow: /search/
Crawl-delay: 1

# Block specific bad bots
User-agent: BadBot
Disallow: /

# Sitemap location
Sitemap: https://example.com/sitemap.xml
Sitemap: https://example.com/sitemap-images.xml
```

## Mental Models

### Search Engine Discovery Process
1. Crawler reads robots.txt first
2. Follows allowed paths and restrictions
3. Discovers sitemap location from robots.txt
4. Parses sitemap for additional URLs
5. Crawls and indexes allowed content

### Sitemap vs Robots.txt Relationship
- **Robots.txt**: Controls what can be crawled
- **Sitemap**: Suggests what should be crawled
- **Together**: Provide complete crawling guidance

## Best Practices

### Sitemap Guidelines
- Include only canonical URLs
- Update lastmod dates when content changes
- Don't include redirected or blocked URLs
- Keep individual sitemaps under 50MB
- Use sitemap index for large sites

### Robots.txt Guidelines
- Place at domain root (/robots.txt)
- Test with Google Search Console
- Be specific with disallow patterns
- Include sitemap location
- Monitor for crawl errors

## Common Pitfalls

### Sitemap Mistakes
```xml
<!-- WRONG: Including blocked URLs -->
<url>
    <loc>https://example.com/admin/dashboard</loc>
</url>

<!-- WRONG: Non-canonical URLs -->
<url>
    <loc>https://example.com/page?utm_source=google</loc>
</url>

<!-- CORRECT: Clean canonical URLs -->
<url>
    <loc>https://example.com/dashboard</loc>
</url>
```

### Robots.txt Mistakes
```
# WRONG: Blocking important content
User-agent: *
Disallow: /

# WRONG: Blocking CSS/JS (hurts rendering)
User-agent: *
Disallow: /*.css$
Disallow: /*.js$

# CORRECT: Selective blocking
User-agent: *
Disallow: /admin/
Disallow: /private/
Allow: /css/
Allow: /js/
```

## Testing and Validation

### Sitemap Testing
- Google Search Console Sitemap tool
- XML sitemap validators
- Check for proper encoding and format
- Verify all URLs are accessible

### Robots.txt Testing
- Google Search Console robots.txt Tester
- Check syntax and directives
- Test specific URL blocking
- Monitor crawl statistics

## File Locations
- **Sitemap**: `/sitemap.xml` (or any location declared in robots.txt)
- **Robots.txt**: `/robots.txt` (must be at domain root)