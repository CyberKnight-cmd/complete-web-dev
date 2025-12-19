# Internationalization: lang, dir, entities - Notes

## Core Concepts

### Language Declaration
```html
<!-- Document language -->
<html lang="en">
<html lang="es">
<html lang="fr">

<!-- Section-specific language -->
<p>English text</p>
<p lang="es">Texto en español</p>
<p lang="fr">Texte en français</p>
```

### Language Codes
- `en` - English
- `es` - Spanish  
- `fr` - French
- `de` - German
- `ja` - Japanese
- `zh` - Chinese
- `ar` - Arabic

### Regional Variants
```html
<html lang="en-US">  <!-- US English -->
<html lang="en-GB">  <!-- British English -->
<html lang="es-ES">  <!-- Spain Spanish -->
<html lang="es-MX">  <!-- Mexican Spanish -->
```

### Text Direction
```html
<!-- Left-to-right (default) -->
<html dir="ltr">

<!-- Right-to-left -->
<html dir="rtl" lang="ar">

<!-- Auto-detect direction -->
<p dir="auto">Mixed content with عربي text</p>
```

### Bidirectional Text
```html
<p>English text with <span lang="ar" dir="rtl">النص العربي</span> embedded</p>
<p dir="auto">Auto-direction: Hello مرحبا World</p>
```

### HTML Entities

#### Common Entities
```html
&lt;    <!-- < -->
&gt;    <!-- > -->
&amp;   <!-- & -->
&quot;  <!-- " -->
&apos; <!-- ' -->
&nbsp; <!-- non-breaking space -->
```

#### Accented Characters
```html
&aacute; <!-- á -->
&eacute; <!-- é -->
&iacute; <!-- í -->
&oacute; <!-- ó -->
&uacute; <!-- ú -->
&ntilde; <!-- ñ -->
&ccedil; <!-- ç -->
```

#### Symbols and Special Characters
```html
&copy;   <!-- © -->
&reg;    <!-- ® -->
&trade;  <!-- ™ -->
&euro;   <!-- € -->
&pound;  <!-- £ -->
&yen;    <!-- ¥ -->
&sect;   <!-- § -->
&para;   <!-- ¶ -->
```

#### Numeric Entities
```html
&#8364;  <!-- € (decimal) -->
&#x20AC; <!-- € (hexadecimal) -->
&#169;   <!-- © -->
&#8482;  <!-- ™ -->
```

## Mental Models

### Screen Reader Behavior
- `lang` attribute changes pronunciation
- `dir` attribute affects navigation order
- Proper language markup improves accessibility

### Browser Processing
1. Parse lang attribute
2. Apply appropriate fonts and rendering
3. Enable spell-checking in correct language
4. Handle text direction and layout

## Best Practices

### Language Declaration
```html
<!-- Always declare document language -->
<html lang="en">

<!-- Mark language changes -->
<p>The French word <span lang="fr">bonjour</span> means hello.</p>
```

### Text Direction
```html
<!-- For RTL languages -->
<html dir="rtl" lang="ar">

<!-- For mixed content -->
<p dir="auto">Content with mixed directions</p>
```

### Character Encoding
```html
<meta charset="UTF-8">
<!-- Supports all Unicode characters -->
```

## Common Pitfalls

### Missing Language Declaration
```html
<!-- WRONG -->
<html>

<!-- CORRECT -->
<html lang="en">
```

### Incorrect Direction
```html
<!-- WRONG for Arabic -->
<html lang="ar">

<!-- CORRECT -->
<html lang="ar" dir="rtl">
```

### Unnecessary Entities
```html
<!-- WRONG: Over-encoding -->
&lt;p&gt;Hello&lt;/p&gt;

<!-- CORRECT: Only encode when necessary -->
<p>Hello</p>
<p>Use &lt; and &gt; in text content</p>
```