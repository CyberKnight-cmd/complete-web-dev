# Head Metadata (SEO/OG/Twitter) & Favicon - Notes

## Core Concepts

### Essential Meta Tags

The HTML `<head>` section contains metadata that doesn't display on the page but provides crucial information to browsers, search engines, and social media platforms.

#### Basic Meta Tags
```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title - Brand Name</title>
    <meta name="description" content="Concise description of page content (150-160 characters)">
    <meta name="keywords" content="keyword1, keyword2, keyword3">
    <meta name="author" content="Author Name">
</head>
```

### SEO Meta Tags

#### Title Tag Best Practices
- Keep under 60 characters
- Include primary keyword
- Make it unique and descriptive
- Format: "Primary Keyword - Secondary Keyword | Brand"

#### Meta Description
- 150-160 characters optimal
- Include call-to-action
- Summarize page content
- Avoid duplicate descriptions

```html
<title>HTML Meta Tags Guide - Complete Tutorial | WebDev Learning</title>
<meta name="description" content="Master HTML meta tags for SEO, social media, and performance. Complete guide with examples and best practices for developers.">
```

### Open Graph Protocol

Open Graph tags control how content appears when shared on social media platforms like Facebook, LinkedIn, and others.

```html
<!-- Open Graph Meta Tags -->
<meta property="og:type" content="website">
<meta property="og:title" content="HTML Meta Tags Guide">
<meta property="og:description" content="Complete guide to HTML meta tags for SEO and social media">
<meta property="og:image" content="https://example.com/images/meta-guide-preview.jpg">
<meta property="og:url" content="https://example.com/html-meta-guide">
<meta property="og:site_name" content="WebDev Learning">
<meta property="og:locale" content="en_US">
```

#### Open Graph Image Requirements
- Minimum 1200x630 pixels
- Aspect ratio 1.91:1
- Maximum 8MB file size
- JPG or PNG format

### Twitter Cards

Twitter Cards provide rich media attachments for tweets containing your links.

```html
<!-- Twitter Card Meta Tags -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:site" content="@yourtwitterhandle">
<meta name="twitter:creator" content="@authorhandle">
<meta name="twitter:title" content="HTML Meta Tags Guide">
<meta name="twitter:description" content="Complete guide to HTML meta tags">
<meta name="twitter:image" content="https://example.com/images/twitter-preview.jpg">
```

#### Twitter Card Types
- `summary`: Default card with title, description, thumbnail
- `summary_large_image`: Large image card
- `app`: Mobile app card
- `player`: Video/audio player card

### Favicon Implementation

Favicons are small icons that appear in browser tabs, bookmarks, and mobile home screens.

```html
<!-- Modern Favicon Implementation -->
<link rel="icon" type="image/x-icon" href="/favicon.ico">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon-16x16.png">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
<link rel="manifest" href="/site.webmanifest">
```

#### Favicon Sizes and Formats
- **favicon.ico**: 16x16, 32x32, 48x48 (multi-size ICO)
- **PNG favicons**: 16x16, 32x32, 96x96, 192x192
- **Apple Touch Icon**: 180x180 PNG
- **Android Chrome**: 192x192, 512x512 (via manifest)

### Additional Meta Tags

#### Robots Meta Tag
```html
<meta name="robots" content="index, follow">
<meta name="robots" content="noindex, nofollow">
<meta name="robots" content="index, nofollow">
```

#### Canonical URL
```html
<link rel="canonical" href="https://example.com/preferred-url">
```

#### Language and Locale
```html
<html lang="en">
<meta http-equiv="content-language" content="en-US">
```

## Mental Models

### Search Engine Processing
1. Crawlers read title and description first
2. Meta tags influence search result appearance
3. Social media platforms use OG/Twitter tags for previews
4. Proper metadata improves click-through rates

### Social Media Sharing Flow
1. User shares link on social platform
2. Platform scrapes Open Graph/Twitter Card data
3. Rich preview generated using meta tag content
4. Fallback to title/description if OG tags missing

## Common Pitfalls

1. **Duplicate Titles**: Same title across multiple pages
2. **Missing Descriptions**: Empty or auto-generated descriptions
3. **Oversized Images**: OG images too large, slow loading
4. **Broken Image URLs**: Relative paths in OG image tags
5. **Missing Favicon**: No favicon or broken favicon links
6. **Inconsistent Data**: OG title differs from page title

## Testing and Validation

### SEO Testing Tools
- Google Search Console
- SEMrush Site Audit
- Screaming Frog SEO Spider

### Social Media Debuggers
- Facebook Sharing Debugger
- Twitter Card Validator
- LinkedIn Post Inspector

### Favicon Testing
- RealFaviconGenerator.net
- Browser developer tools
- Multiple device testing

## Best Practices

1. **Keep titles unique** and descriptive
2. **Write compelling descriptions** that encourage clicks
3. **Use high-quality images** for social sharing
4. **Test on multiple platforms** before publishing
5. **Update meta tags** when content changes
6. **Monitor performance** using analytics tools