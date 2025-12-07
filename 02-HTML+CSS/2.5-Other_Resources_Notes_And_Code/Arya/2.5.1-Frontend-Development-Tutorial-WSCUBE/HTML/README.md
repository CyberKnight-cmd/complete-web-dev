# HTML Comprehensive Guide

## Table of Contents
1. [Introduction to HTML](#introduction-to-html)
2. [HTML Document Structure](#html-document-structure)
3. [Text Formatting Elements](#text-formatting-elements)
4. [Headings](#headings)
5. [Lists](#lists)
6. [Links and Anchors](#links-and-anchors)
7. [Images](#images)
8. [Tables](#tables)
9. [Forms](#forms)
10. [HTML5 Form Elements](#html5-form-elements)
11. [Modern HTML5 Elements](#modern-html5-elements)
12. [Semantic HTML5](#semantic-html5)
13. [Accessibility and ARIA](#accessibility-and-aria)
14. [JavaScript Integration](#javascript-integration)
15. [HTML Attributes Reference](#html-attributes-reference)

---

## Introduction to HTML

**HTML (HyperText Markup Language)** is the standard markup language for creating web pages. It describes the structure and content of a webpage using elements and tags.

### Key Concepts
- **Elements**: Building blocks of HTML (e.g., `<p>`, `<div>`, `<h1>`)
- **Tags**: Markers that define elements (opening `<tag>` and closing `</tag>`)
- **Attributes**: Additional information about elements (e.g., `id`, `class`, `src`)
- **Content**: Text or other elements between opening and closing tags

### HTML Syntax
```html
<tagname attribute="value">Content</tagname>
```

---

## HTML Document Structure

Every HTML document follows a standard structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Title</title>
</head>
<body>
    <!-- Content goes here -->
</body>
</html>
```

### Document Structure Elements

| Element | Purpose | Required |
|---------|---------|----------|
| `<!DOCTYPE html>` | Declares HTML5 document type | Yes |
| `<html>` | Root element of HTML page | Yes |
| `<head>` | Contains metadata and links | Yes |
| `<meta>` | Defines metadata (charset, viewport) | Recommended |
| `<title>` | Sets page title (shown in browser tab) | Yes |
| `<body>` | Contains visible page content | Yes |

### Meta Tags

| Meta Tag | Purpose | Example |
|----------|---------|---------|
| `charset` | Character encoding | `<meta charset="UTF-8">` |
| `viewport` | Responsive design settings | `<meta name="viewport" content="width=device-width, initial-scale=1.0">` |
| `description` | Page description for SEO | `<meta name="description" content="Page description">` |
| `keywords` | Keywords for SEO | `<meta name="keywords" content="HTML, CSS, JavaScript">` |

---

## Text Formatting Elements

HTML provides various tags for formatting text content.

### Basic Text Tags

| Tag | Purpose | Example |
|-----|---------|---------|
| `<p>` | Paragraph | `<p>This is a paragraph</p>` |
| `<br>` | Line break (self-closing) | `Line 1<br>Line 2` |
| `<hr>` | Horizontal rule/line | `<hr>` |
| `<strong>` | Bold text (semantic importance) | `<strong>Important</strong>` |
| `<b>` | Bold text (visual only) | `<b>Bold</b>` |
| `<em>` | Italic text (semantic emphasis) | `<em>Emphasized</em>` |
| `<i>` | Italic text (visual only) | `<i>Italic</i>` |
| `<u>` | Underlined text | `<u>Underlined</u>` |
| `<del>` | Deleted/strikethrough text | `<del>Deleted</del>` |
| `<mark>` | Highlighted text | `<mark>Highlighted</mark>` |
| `<small>` | Smaller text | `<small>Small text</small>` |
| `<sub>` | Subscript | `H<sub>2</sub>O` |
| `<sup>` | Superscript | `x<sup>2</sup>` |

### Example Usage
```html
<p>
    <strong>Bold text</strong> and <em>italic text</em>.
    <mark>Highlighted</mark> and <del>deleted</del> text.
    Chemical formula: H<sub>2</sub>O
    Mathematical expression: x<sup>2</sup> + y<sup>2</sup>
</p>
```

---

## Headings

HTML provides six levels of headings, from `<h1>` (most important) to `<h6>` (least important).

### Heading Hierarchy

| Tag | Purpose | Typical Use |
|-----|---------|-------------|
| `<h1>` | Main page heading | Page title (use once per page) |
| `<h2>` | Major section heading | Main sections |
| `<h3>` | Subsection heading | Subsections within h2 |
| `<h4>` | Minor heading | Subsections within h3 |
| `<h5>` | Detailed heading | Further subdivisions |
| `<h6>` | Smallest heading | Rarely used |

### Best Practices
- Use only one `<h1>` per page
- Don't skip heading levels (h1 → h2 → h3, not h1 → h3)
- Use headings for structure, not styling
- Headings help with SEO and accessibility

### Example
```html
<h1>Main Title</h1>
<h2>Section 1</h2>
<h3>Subsection 1.1</h3>
<h3>Subsection 1.2</h3>
<h2>Section 2</h2>
```

---

## Lists

HTML supports three types of lists: ordered, unordered, and description lists.

### Ordered Lists (Numbered)

```html
<ol type="1">
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ol>
```

### Ordered List Types

| Type Attribute | Result | Example |
|----------------|--------|---------|
| `type="1"` | Numbers (default) | 1, 2, 3 |
| `type="A"` | Uppercase letters | A, B, C |
| `type="a"` | Lowercase letters | a, b, c |
| `type="I"` | Uppercase Roman | I, II, III |
| `type="i"` | Lowercase Roman | i, ii, iii |

### Unordered Lists (Bulleted)

```html
<ul type="disc">
    <li>Item one</li>
    <li>Item two</li>
    <li>Item three</li>
</ul>
```

### Unordered List Types

| Type Attribute | Result |
|----------------|--------|
| `type="disc"` | Filled circle (default) |
| `type="circle"` | Empty circle |
| `type="square"` | Filled square |
| `type="none"` | No marker |

### Nested Lists

```html
<ul>
    <li>HTML
        <ul>
            <li>Elements</li>
            <li>Attributes</li>
        </ul>
    </li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

### Description Lists

```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
    <dt>CSS</dt>
    <dd>Cascading Style Sheets</dd>
</dl>
```

---

## Links and Anchors

The `<a>` (anchor) tag creates hyperlinks to other pages, files, or locations.

### Basic Link Syntax
```html
<a href="URL">Link Text</a>
```

### Link Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `href` | Destination URL | `href="https://example.com"` |
| `target` | Where to open link | `target="_blank"` |
| `rel` | Relationship to linked document | `rel="noopener noreferrer"` |
| `title` | Tooltip text | `title="Click here"` |
| `download` | Download file instead of navigate | `download="filename.pdf"` |

### Target Attribute Values

| Value | Behavior |
|-------|----------|
| `_blank` | Opens in new tab/window |
| `_self` | Opens in same frame (default) |
| `_parent` | Opens in parent frame |
| `_top` | Opens in full window |

### Link Types

```html
<!-- External link -->
<a href="https://www.example.com" target="_blank" rel="noopener noreferrer">External Site</a>

<!-- Internal link (same site) -->
<a href="about.html">About Page</a>

<!-- Email link -->
<a href="mailto:email@example.com">Send Email</a>

<!-- Phone link -->
<a href="tel:+1234567890">Call Us</a>

<!-- Anchor link (same page) -->
<a href="#section1">Go to Section 1</a>

<!-- Download link -->
<a href="document.pdf" download>Download PDF</a>
```

### Security Best Practice
Always use `rel="noopener noreferrer"` with `target="_blank"` to prevent security vulnerabilities.

---

## Images

The `<img>` tag embeds images in HTML documents.

### Image Syntax
```html
<img src="path/to/image.jpg" alt="Description" title="Tooltip">
```

### Image Attributes

| Attribute | Purpose | Required | Example |
|-----------|---------|----------|---------|
| `src` | Image source path/URL | Yes | `src="image.jpg"` |
| `alt` | Alternative text (accessibility) | Yes | `alt="Mountain landscape"` |
| `title` | Tooltip on hover | No | `title="Beautiful view"` |
| `width` | Image width | No | `width="500"` |
| `height` | Image height | No | `height="300"` |
| `loading` | Lazy loading | No | `loading="lazy"` |

### Image Formats

| Format | Use Case | Transparency | Animation |
|--------|----------|--------------|-----------|
| JPG/JPEG | Photos, complex images | No | No |
| PNG | Graphics, logos | Yes | No |
| GIF | Simple animations | Yes | Yes |
| SVG | Scalable vector graphics | Yes | Yes |
| WebP | Modern format (smaller size) | Yes | Yes |

### Best Practices
- Always include `alt` text for accessibility
- Use descriptive alt text (not "image" or "photo")
- Optimize image sizes for web
- Use appropriate image formats
- Consider lazy loading for performance

```html
<img src="assets/photo.jpg" 
     alt="Sunset over mountains with orange sky" 
     title="Mountain Sunset"
     width="800" 
     height="600"
     loading="lazy">
```


## Tables

Tables organize data in rows and columns using the `<table>` element.

### Table Structure

```html
<table>
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Data 1</td>
            <td>Data 2</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Footer 1</td>
            <td>Footer 2</td>
        </tr>
    </tfoot>
</table>
```

### Table Elements

| Element | Purpose |
|---------|---------|
| `<table>` | Container for entire table |
| `<thead>` | Table header section |
| `<tbody>` | Table body section |
| `<tfoot>` | Table footer section |
| `<tr>` | Table row |
| `<th>` | Table header cell (bold, centered) |
| `<td>` | Table data cell |
| `<caption>` | Table caption/title |

### Table Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `border` | Border width | `border="1"` |
| `cellpadding` | Space inside cells | `cellpadding="5"` |
| `cellspacing` | Space between cells | `cellspacing="2"` |
| `width` | Table width | `width="100%"` |
| `height` | Table height | `height="500"` |
| `align` | Table alignment | `align="center"` |
| `bgcolor` | Background color | `bgcolor="yellow"` |

### Cell Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `colspan` | Span multiple columns | `colspan="2"` |
| `rowspan` | Span multiple rows | `rowspan="3"` |
| `align` | Horizontal alignment | `align="center"` |
| `valign` | Vertical alignment | `valign="top"` |
| `bgcolor` | Cell background color | `bgcolor="red"` |

### Colspan and Rowspan Example

```html
<table border="1">
    <tr>
        <th>Name</th>
        <th>Age</th>
        <th>City</th>
    </tr>
    <tr>
        <!-- This cell spans 2 columns -->
        <td colspan="2">John Doe</td>
        <td>New York</td>
    </tr>
    <tr>
        <!-- This cell spans 2 rows -->
        <td rowspan="2">Jane Smith</td>
        <td>25</td>
        <td>London</td>
    </tr>
    <tr>
        <td>Developer</td>
        <td>UK</td>
    </tr>
</table>
```

### Complete Table Example

```html
<table border="5" align="center" cellpadding="5" cellspacing="2" width="800">
    <caption>Student Records</caption>
    <thead>
        <tr bgcolor="lightblue" align="center">
            <th>ID</th>
            <th>Name</th>
            <th>Grade</th>
            <th>Status</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>Alice</td>
            <td>A</td>
            <td rowspan="2">Pass</td>
        </tr>
        <tr>
            <td>2</td>
            <td>Bob</td>
            <td>B</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td colspan="4" align="center">End of Records</td>
        </tr>
    </tfoot>
</table>
```

---

## Forms

Forms collect user input and send it to a server for processing.

### Basic Form Structure

```html
<form action="submit.php" method="post">
    <!-- Form elements go here -->
</form>
```

### Form Attributes

| Attribute | Purpose | Values |
|-----------|---------|--------|
| `action` | URL where form data is sent | URL or file path |
| `method` | HTTP method for sending data | `get`, `post` |
| `enctype` | Encoding type for form data | `application/x-www-form-urlencoded`, `multipart/form-data`, `text/plain` |
| `target` | Where to display response | `_blank`, `_self`, `_parent`, `_top` |
| `autocomplete` | Enable/disable autocomplete | `on`, `off` |
| `novalidate` | Skip form validation | No value needed |

### Form Methods

| Method | Purpose | Data Visibility | Use Case |
|--------|---------|-----------------|----------|
| `GET` | Retrieve data | Visible in URL | Search forms, filters |
| `POST` | Submit data | Hidden in request body | Login, registration, file uploads |

### Form Encoding Types

| Enctype | Purpose |
|---------|---------|
| `application/x-www-form-urlencoded` | Default, URL-encoded data |
| `multipart/form-data` | Required for file uploads |
| `text/plain` | Plain text (rarely used) |

### Input Types

| Type | Purpose | Example |
|------|---------|---------|
| `text` | Single-line text | `<input type="text">` |
| `password` | Password field (hidden) | `<input type="password">` |
| `email` | Email address | `<input type="email">` |
| `number` | Numeric input | `<input type="number">` |
| `tel` | Telephone number | `<input type="tel">` |
| `url` | URL address | `<input type="url">` |
| `search` | Search field | `<input type="search">` |
| `date` | Date picker | `<input type="date">` |
| `time` | Time picker | `<input type="time">` |
| `datetime-local` | Date and time | `<input type="datetime-local">` |
| `month` | Month picker | `<input type="month">` |
| `week` | Week picker | `<input type="week">` |
| `color` | Color picker | `<input type="color">` |
| `range` | Slider | `<input type="range">` |
| `file` | File upload | `<input type="file">` |
| `checkbox` | Checkbox | `<input type="checkbox">` |
| `radio` | Radio button | `<input type="radio">` |
| `submit` | Submit button | `<input type="submit">` |
| `reset` | Reset button | `<input type="reset">` |
| `button` | Generic button | `<input type="button">` |
| `hidden` | Hidden field | `<input type="hidden">` |

### Input Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `name` | Field name (sent to server) | `name="username"` |
| `id` | Unique identifier | `id="email"` |
| `value` | Default/current value | `value="John"` |
| `placeholder` | Hint text | `placeholder="Enter name"` |
| `required` | Field must be filled | `required` |
| `readonly` | Cannot be edited | `readonly` |
| `disabled` | Field is disabled | `disabled` |
| `maxlength` | Maximum character length | `maxlength="50"` |
| `min` | Minimum value (numbers/dates) | `min="1"` |
| `max` | Maximum value (numbers/dates) | `max="100"` |
| `step` | Increment step | `step="5"` |
| `pattern` | Regex validation pattern | `pattern="[0-9]{3}"` |
| `autofocus` | Auto-focus on page load | `autofocus` |
| `autocomplete` | Enable/disable autocomplete | `autocomplete="off"` |
| `multiple` | Allow multiple values | `multiple` |
| `checked` | Pre-checked (checkbox/radio) | `checked` |

### Text Input Example

```html
<label for="username">Username:</label>
<input type="text" 
       id="username" 
       name="username" 
       placeholder="Enter username"
       required
       minlength="3"
       maxlength="20">
```

### Textarea Element

```html
<label for="message">Message:</label>
<textarea id="message" 
          name="message" 
          rows="4" 
          cols="50" 
          placeholder="Enter your message"
          required></textarea>
```

### Select Dropdown

```html
<label for="country">Country:</label>
<select id="country" name="country" required>
    <option value="">Select a country</option>
    <option value="usa">United States</option>
    <option value="uk">United Kingdom</option>
    <option value="canada">Canada</option>
</select>
```

### Select with Optgroup

```html
<select id="country" name="country">
    <option value="">Please select</option>
    <optgroup label="North America">
        <option value="usa">USA</option>
        <option value="canada">Canada</option>
    </optgroup>
    <optgroup label="Europe">
        <option value="uk">UK</option>
        <option value="france">France</option>
    </optgroup>
</select>
```

### Radio Buttons

```html
<p>Gender:</p>
<input type="radio" id="male" name="gender" value="male" checked>
<label for="male">Male</label>

<input type="radio" id="female" name="gender" value="female">
<label for="female">Female</label>
```

### Checkboxes

```html
<p>Hobbies:</p>
<input type="checkbox" id="reading" name="hobbies[]" value="reading">
<label for="reading">Reading</label>

<input type="checkbox" id="sports" name="hobbies[]" value="sports">
<label for="sports">Sports</label>

<input type="checkbox" id="music" name="hobbies[]" value="music" checked>
<label for="music">Music</label>
```

### File Upload

```html
<label for="photo">Upload Photo:</label>
<input type="file" 
       id="photo" 
       name="photo" 
       accept="image/*"
       required>
```

### Fieldset and Legend

```html
<fieldset>
    <legend>Personal Information</legend>
    
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email">
</fieldset>
```

### Complete Form Example

```html
<form action="submit.php" method="post" enctype="multipart/form-data">
    <fieldset>
        <legend>Registration Form</legend>
        
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required><br><br>
        
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>
        
        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required><br><br>
        
        <label for="dob">Date of Birth:</label>
        <input type="date" id="dob" name="dob"><br><br>
        
        <label for="country">Country:</label>
        <select id="country" name="country">
            <option value="">Select</option>
            <option value="usa">USA</option>
            <option value="uk">UK</option>
        </select><br><br>
        
        <p>Gender:</p>
        <input type="radio" id="male" name="gender" value="male">
        <label for="male">Male</label>
        <input type="radio" id="female" name="gender" value="female">
        <label for="female">Female</label><br><br>
        
        <input type="checkbox" id="terms" name="terms" required>
        <label for="terms">I agree to terms</label><br><br>
        
        <input type="submit" value="Register">
        <input type="reset" value="Clear">
    </fieldset>
</form>
```


## HTML5 Form Elements

HTML5 introduced new input types and form elements for better user experience and validation.

### HTML5 Input Types

#### Color Picker
```html
<label for="color">Choose Color:</label>
<input type="color" id="color" name="color" value="#ff0000">
```

#### Date Inputs
```html
<!-- Date -->
<input type="date" name="date" min="2024-01-01" max="2024-12-31">

<!-- Time -->
<input type="time" name="time">

<!-- Date and Time -->
<input type="datetime-local" name="datetime">

<!-- Month -->
<input type="month" name="month">

<!-- Week -->
<input type="week" name="week">
```

#### Number Input
```html
<input type="number" 
       name="quantity" 
       min="1" 
       max="100" 
       step="5" 
       value="10">
```

#### Range Slider
```html
<label for="volume">Volume:</label>
<input type="range" 
       id="volume" 
       name="volume" 
       min="0" 
       max="100" 
       value="50">
```

#### Email Input
```html
<input type="email" 
       name="email" 
       placeholder="user@example.com"
       required>
```

#### URL Input
```html
<input type="url" 
       name="website" 
       placeholder="https://example.com"
       pattern="https://.*">
```

#### Search Input
```html
<input type="search" 
       name="search" 
       placeholder="Search...">
```

#### Tel Input
```html
<input type="tel" 
       name="phone" 
       pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"
       placeholder="123-456-7890">
```

### HTML5 Form Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `required` | Field must be filled | `<input required>` |
| `placeholder` | Hint text | `<input placeholder="Enter text">` |
| `autofocus` | Auto-focus on load | `<input autofocus>` |
| `autocomplete` | Enable/disable autocomplete | `<input autocomplete="off">` |
| `pattern` | Regex validation | `<input pattern="[A-Za-z]{3}">` |
| `min` | Minimum value | `<input type="number" min="0">` |
| `max` | Maximum value | `<input type="number" max="100">` |
| `step` | Value increment | `<input type="number" step="5">` |
| `multiple` | Multiple values | `<input type="file" multiple>` |
| `form` | Associate with form | `<input form="myform">` |
| `formaction` | Override form action | `<input type="submit" formaction="alt.php">` |
| `formmethod` | Override form method | `<input type="submit" formmethod="get">` |
| `novalidate` | Skip validation | `<form novalidate>` |

### Hidden Input Fields

Hidden fields store data that users don't see but gets submitted with the form.

#### Common Uses of Hidden Fields

1. **Session Tokens**: Security tokens for form submissions
2. **User IDs**: Track which user submitted the form
3. **Timestamps**: Record when form was loaded/submitted
4. **Tracking Data**: Analytics and tracking information
5. **Form Versions**: Track which version of form was used

```html
<input type="hidden" name="user_id" value="12345">
<input type="hidden" name="session_token" value="abc123xyz">
<input type="hidden" name="form_version" value="2.0">
```

### Datalist Element

Provides autocomplete suggestions for input fields.

```html
<label for="browser">Choose Browser:</label>
<input list="browsers" id="browser" name="browser">
<datalist id="browsers">
    <option value="Chrome">
    <option value="Firefox">
    <option value="Safari">
    <option value="Edge">
    <option value="Opera">
</datalist>
```

### Output Element

Displays the result of a calculation.

```html
<form oninput="result.value=parseInt(a.value)+parseInt(b.value)">
    <input type="number" id="a" value="0"> +
    <input type="number" id="b" value="0"> =
    <output name="result" for="a b">0</output>
</form>
```

### Progress Element

Shows progress of a task.

```html
<label for="progress">Download Progress:</label>
<progress id="progress" value="70" max="100">70%</progress>
```

### Meter Element

Represents a scalar measurement within a known range.

```html
<label for="disk">Disk Usage:</label>
<meter id="disk" 
       min="0" 
       max="100" 
       low="30" 
       high="80" 
       optimum="20" 
       value="65">65%</meter>
```

### Form Validation

HTML5 provides built-in validation without JavaScript.

#### Validation Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `required` | Field cannot be empty | `<input required>` |
| `minlength` | Minimum text length | `<input minlength="5">` |
| `maxlength` | Maximum text length | `<input maxlength="20">` |
| `min` | Minimum number/date | `<input type="number" min="1">` |
| `max` | Maximum number/date | `<input type="number" max="100">` |
| `pattern` | Regex pattern | `<input pattern="[0-9]{5}">` |
| `type` | Input type validation | `<input type="email">` |

#### Pattern Examples

```html
<!-- US Zip Code -->
<input type="text" pattern="[0-9]{5}" title="5-digit zip code">

<!-- Phone Number -->
<input type="tel" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}" title="Format: 123-456-7890">

<!-- Username (alphanumeric, 3-16 chars) -->
<input type="text" pattern="[A-Za-z0-9]{3,16}" title="3-16 alphanumeric characters">

<!-- Hex Color -->
<input type="text" pattern="#[0-9A-Fa-f]{6}" title="Hex color code">
```

### Complete HTML5 Form Example

```html
<form action="process.php" method="post">
    <fieldset>
        <legend>HTML5 Form Demo</legend>
        
        <!-- Color Picker -->
        <label for="color">Favorite Color:</label>
        <input type="color" id="color" name="color"><br><br>
        
        <!-- Date -->
        <label for="date">Select Date:</label>
        <input type="date" id="date" name="date" required><br><br>
        
        <!-- Email with validation -->
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required><br><br>
        
        <!-- Number with range -->
        <label for="age">Age (18-100):</label>
        <input type="number" id="age" name="age" min="18" max="100" required><br><br>
        
        <!-- Range slider -->
        <label for="rating">Rating:</label>
        <input type="range" id="rating" name="rating" min="1" max="10" value="5"><br><br>
        
        <!-- Datalist autocomplete -->
        <label for="city">City:</label>
        <input list="cities" id="city" name="city">
        <datalist id="cities">
            <option value="New York">
            <option value="London">
            <option value="Tokyo">
        </datalist><br><br>
        
        <!-- Progress bar -->
        <label>Profile Completion:</label>
        <progress value="60" max="100">60%</progress><br><br>
        
        <!-- Hidden fields -->
        <input type="hidden" name="user_id" value="12345">
        <input type="hidden" name="timestamp" value="2024-01-01">
        
        <input type="submit" value="Submit">
    </fieldset>
</form>
```

---

## Modern HTML5 Elements

HTML5 introduced semantic elements and interactive components.

### Details and Summary

Creates collapsible/expandable content sections.

```html
<details>
    <summary>Click to expand</summary>
    <p>This content is hidden by default.</p>
    <p>It appears when you click the summary.</p>
</details>

<details open>
    <summary>This is open by default</summary>
    <p>Use the 'open' attribute to show content initially.</p>
</details>
```

### Dialog Element

Creates modal dialog boxes.

```html
<dialog id="myDialog">
    <h2>Dialog Title</h2>
    <p>This is a modal dialog.</p>
    <button onclick="document.getElementById('myDialog').close()">Close</button>
</dialog>

<button onclick="document.getElementById('myDialog').showModal()">Open Dialog</button>
```

#### Dialog Methods

| Method | Purpose |
|--------|---------|
| `showModal()` | Opens as modal (blocks background) |
| `show()` | Opens as non-modal |
| `close()` | Closes the dialog |

### Mark Element

Highlights text for reference or emphasis.

```html
<p>Search results for "HTML":</p>
<p>Learn <mark>HTML</mark> and CSS for web development.</p>
```

### Time Element

Represents dates and times in machine-readable format.

```html
<!-- Date -->
<time datetime="2024-12-25">December 25, 2024</time>

<!-- Date and time -->
<time datetime="2024-12-25T10:00">December 25, 2024 at 10:00 AM</time>

<!-- Duration -->
<time datetime="PT2H30M">2 hours 30 minutes</time>
```

### Figure and Figcaption

Groups media content with captions.

```html
<figure>
    <img src="chart.png" alt="Sales chart">
    <figcaption>Figure 1: Annual sales data for 2024</figcaption>
</figure>
```

### Picture Element

Provides responsive images with multiple sources.

```html
<picture>
    <source media="(min-width: 800px)" srcset="large.jpg">
    <source media="(min-width: 400px)" srcset="medium.jpg">
    <img src="small.jpg" alt="Responsive image">
</picture>
```

### Template Element

Holds HTML content that won't be rendered until activated by JavaScript.

```html
<template id="myTemplate">
    <div class="card">
        <h3>Title</h3>
        <p>Content goes here</p>
    </div>
</template>
```

### Canvas Element

Provides a drawing surface for graphics via JavaScript.

```html
<canvas id="myCanvas" width="400" height="200">
    Your browser does not support canvas.
</canvas>
```

### Video Element

Embeds video content.

```html
<video width="640" height="360" controls>
    <source src="video.mp4" type="video/mp4">
    <source src="video.webm" type="video/webm">
    Your browser does not support video.
</video>
```

#### Video Attributes

| Attribute | Purpose |
|-----------|---------|
| `controls` | Shows play/pause controls |
| `autoplay` | Starts playing automatically |
| `loop` | Loops the video |
| `muted` | Mutes audio |
| `poster` | Thumbnail image before play |
| `preload` | How to preload (`none`, `metadata`, `auto`) |

### Audio Element

Embeds audio content.

```html
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    <source src="audio.ogg" type="audio/ogg">
    Your browser does not support audio.
</audio>
```


## Semantic HTML5

Semantic HTML uses meaningful tags that describe their content, improving accessibility, SEO, and code readability.

### Why Use Semantic HTML?

1. **Accessibility**: Screen readers understand page structure
2. **SEO**: Search engines better understand content
3. **Maintainability**: Code is easier to read and maintain
4. **Consistency**: Standard meaning across all websites

### Semantic vs Non-Semantic

| Non-Semantic | Semantic | Purpose |
|--------------|----------|---------|
| `<div>` | `<header>` | Page/section header |
| `<div>` | `<nav>` | Navigation links |
| `<div>` | `<main>` | Main content |
| `<div>` | `<article>` | Independent content |
| `<div>` | `<section>` | Thematic grouping |
| `<div>` | `<aside>` | Side content |
| `<div>` | `<footer>` | Page/section footer |
| `<span>` | `<time>` | Date/time |
| `<span>` | `<mark>` | Highlighted text |

### Semantic Structure Elements

#### Header
Contains introductory content, logo, navigation.

```html
<header>
    <h1>Website Title</h1>
    <nav>
        <a href="#home">Home</a>
        <a href="#about">About</a>
    </nav>
</header>
```

#### Nav
Contains navigation links.

```html
<nav>
    <ul>
        <li><a href="#home">Home</a></li>
        <li><a href="#services">Services</a></li>
        <li><a href="#contact">Contact</a></li>
    </ul>
</nav>
```

#### Main
Primary content of the page (only one per page).

```html
<main>
    <h1>Main Content</h1>
    <p>This is the primary content area.</p>
</main>
```

#### Article
Self-contained, independently distributable content.

```html
<article>
    <h2>Blog Post Title</h2>
    <p>Published: <time datetime="2024-01-15">January 15, 2024</time></p>
    <p>Article content goes here...</p>
</article>
```

#### Section
Thematic grouping of content, typically with a heading.

```html
<section>
    <h2>About Us</h2>
    <p>Information about the company...</p>
</section>
```

#### Aside
Content tangentially related to main content (sidebar, related links).

```html
<aside>
    <h3>Related Articles</h3>
    <ul>
        <li><a href="#">Article 1</a></li>
        <li><a href="#">Article 2</a></li>
    </ul>
</aside>
```

#### Footer
Footer for page or section (copyright, links, contact).

```html
<footer>
    <p>&copy; 2024 Company Name. All rights reserved.</p>
    <nav>
        <a href="#privacy">Privacy</a>
        <a href="#terms">Terms</a>
    </nav>
</footer>
```

### Complete Semantic Page Structure

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Semantic HTML Example</title>
</head>
<body>
    
    <!-- Page Header -->
    <header>
        <h1>My Website</h1>
        <nav>
            <a href="#home">Home</a>
            <a href="#about">About</a>
            <a href="#blog">Blog</a>
            <a href="#contact">Contact</a>
        </nav>
    </header>
    
    <!-- Main Content -->
    <main>
        
        <!-- Hero Section -->
        <section id="home">
            <h2>Welcome to Our Site</h2>
            <p>This is the hero section.</p>
        </section>
        
        <!-- About Section -->
        <section id="about">
            <h2>About Us</h2>
            <p>Information about the company.</p>
        </section>
        
        <!-- Blog Articles -->
        <section id="blog">
            <h2>Latest Blog Posts</h2>
            
            <article>
                <h3>First Blog Post</h3>
                <p>Published: <time datetime="2024-01-15">January 15, 2024</time></p>
                <p>Blog post content...</p>
            </article>
            
            <article>
                <h3>Second Blog Post</h3>
                <p>Published: <time datetime="2024-01-20">January 20, 2024</time></p>
                <p>Blog post content...</p>
            </article>
        </section>
        
        <!-- Sidebar -->
        <aside>
            <h3>Quick Links</h3>
            <ul>
                <li><a href="#">Link 1</a></li>
                <li><a href="#">Link 2</a></li>
            </ul>
        </aside>
        
    </main>
    
    <!-- Page Footer -->
    <footer>
        <p>&copy; 2024 My Website. All rights reserved.</p>
        <nav>
            <a href="#privacy">Privacy Policy</a>
            <a href="#terms">Terms of Service</a>
        </nav>
    </footer>
    
</body>
</html>
```

### When to Use Each Element

| Element | Use When |
|---------|----------|
| `<header>` | Top of page or section with title/nav |
| `<nav>` | Group of navigation links |
| `<main>` | Primary page content (once per page) |
| `<article>` | Content makes sense independently (blog post, news article) |
| `<section>` | Thematic grouping with heading |
| `<aside>` | Related but separate content (sidebar) |
| `<footer>` | Bottom of page or section with metadata |

### Semantic Text Elements

| Element | Purpose | Example |
|---------|---------|---------|
| `<strong>` | Important text (semantic) | `<strong>Warning!</strong>` |
| `<em>` | Emphasized text (semantic) | `<em>Really</em> important` |
| `<mark>` | Highlighted/referenced text | `<mark>search term</mark>` |
| `<time>` | Date/time | `<time datetime="2024-01-15">Jan 15</time>` |
| `<abbr>` | Abbreviation | `<abbr title="HyperText Markup Language">HTML</abbr>` |
| `<cite>` | Citation/reference | `<cite>Book Title</cite>` |
| `<code>` | Code snippet | `<code>console.log()</code>` |
| `<kbd>` | Keyboard input | `Press <kbd>Ctrl</kbd>+<kbd>C</kbd>` |
| `<samp>` | Sample output | `<samp>Error 404</samp>` |
| `<var>` | Variable | `<var>x</var> = 10` |
| `<blockquote>` | Long quotation | `<blockquote>Quote text</blockquote>` |
| `<q>` | Short inline quotation | `<q>Short quote</q>` |
| `<address>` | Contact information | `<address>123 Main St</address>` |

---

## Accessibility and ARIA

Accessibility ensures websites are usable by everyone, including people with disabilities.

### What is ARIA?

**ARIA (Accessible Rich Internet Applications)** provides additional attributes to make web content more accessible to assistive technologies like screen readers.

### Core Accessibility Principles (POUR)

| Principle | Meaning |
|-----------|---------|
| **Perceivable** | Information must be presentable to users in ways they can perceive |
| **Operable** | Interface components must be operable by all users |
| **Understandable** | Information and operation must be understandable |
| **Robust** | Content must work with current and future technologies |

### Basic Accessibility Best Practices

1. **Use semantic HTML** (header, nav, main, etc.)
2. **Add alt text to images**
3. **Use proper heading hierarchy** (h1 → h2 → h3)
4. **Label form inputs**
5. **Ensure keyboard navigation works**
6. **Maintain sufficient color contrast**
7. **Don't rely solely on color to convey information**
8. **Provide text alternatives for non-text content**

### ARIA Attributes

#### ARIA Roles

Define what an element is or does.

| Role | Purpose | Example |
|------|---------|---------|
| `button` | Clickable button | `<div role="button">Click</div>` |
| `navigation` | Navigation section | `<div role="navigation">` |
| `search` | Search functionality | `<div role="search">` |
| `alert` | Important message | `<div role="alert">Error!</div>` |
| `dialog` | Dialog/modal | `<div role="dialog">` |
| `menu` | Menu widget | `<ul role="menu">` |
| `tab` | Tab in tab list | `<button role="tab">` |
| `tabpanel` | Content for tab | `<div role="tabpanel">` |

#### ARIA Properties

Describe characteristics of elements.

| Property | Purpose | Example |
|----------|---------|---------|
| `aria-label` | Accessible name | `<button aria-label="Close">X</button>` |
| `aria-labelledby` | References label element | `<input aria-labelledby="label1">` |
| `aria-describedby` | References description | `<input aria-describedby="help1">` |
| `aria-required` | Field is required | `<input aria-required="true">` |
| `aria-invalid` | Field has error | `<input aria-invalid="true">` |
| `aria-hidden` | Hide from screen readers | `<span aria-hidden="true">★</span>` |
| `aria-live` | Announces dynamic changes | `<div aria-live="polite">` |
| `aria-current` | Current item in set | `<a aria-current="page">Home</a>` |
| `aria-expanded` | Expandable state | `<button aria-expanded="false">` |
| `aria-controls` | Controls another element | `<button aria-controls="menu1">` |
| `aria-haspopup` | Has popup menu | `<button aria-haspopup="true">` |

#### ARIA States

Describe current state of elements.

| State | Purpose | Values |
|-------|---------|--------|
| `aria-checked` | Checkbox/radio state | `true`, `false`, `mixed` |
| `aria-disabled` | Disabled state | `true`, `false` |
| `aria-expanded` | Expanded/collapsed | `true`, `false` |
| `aria-hidden` | Hidden from screen readers | `true`, `false` |
| `aria-pressed` | Toggle button state | `true`, `false`, `mixed` |
| `aria-selected` | Selected state | `true`, `false` |

### Accessible Form Example

```html
<form>
    <!-- Label association -->
    <label for="username">Username:</label>
    <input type="text" 
           id="username" 
           name="username" 
           aria-required="true"
           aria-describedby="usernameHelp">
    <small id="usernameHelp">Must be 5-20 characters</small>
    
    <!-- aria-label for icon buttons -->
    <button type="submit" aria-label="Submit form">
        →
    </button>
    
    <!-- Error state -->
    <label for="email">Email:</label>
    <input type="email" 
           id="email" 
           aria-invalid="true"
           aria-describedby="emailError">
    <span id="emailError" role="alert">Please enter a valid email</span>
</form>
```

### Accessible Navigation

```html
<nav aria-label="Main navigation">
    <ul>
        <li><a href="#home" aria-current="page">Home</a></li>
        <li><a href="#about">About</a></li>
        <li><a href="#contact">Contact</a></li>
    </ul>
</nav>
```

### Accessible Images

```html
<!-- Informative image -->
<img src="chart.png" alt="Bar chart showing 50% increase in sales">

<!-- Decorative image (empty alt) -->
<img src="decoration.png" alt="">

<!-- Complex image with description -->
<figure>
    <img src="complex-chart.png" alt="Sales data chart" aria-describedby="chartDesc">
    <figcaption id="chartDesc">
        Detailed description of the chart data...
    </figcaption>
</figure>
```

### Accessible Buttons

```html
<!-- Text button (accessible by default) -->
<button>Click Me</button>

<!-- Icon button (needs aria-label) -->
<button aria-label="Close dialog">
    <span aria-hidden="true">×</span>
</button>

<!-- Toggle button -->
<button aria-pressed="false" aria-label="Toggle dark mode">
    🌙
</button>
```

### Live Regions

Announce dynamic content changes to screen readers.

```html
<!-- Polite: announces when user is idle -->
<div aria-live="polite" aria-atomic="true">
    <p>Status: Loading...</p>
</div>

<!-- Assertive: announces immediately -->
<div aria-live="assertive" role="alert">
    <p>Error: Form submission failed!</p>
</div>
```

#### aria-live Values

| Value | Behavior |
|-------|----------|
| `off` | No announcements (default) |
| `polite` | Announces when user is idle |
| `assertive` | Announces immediately |

### Keyboard Navigation

Ensure all interactive elements are keyboard accessible.

```html
<!-- tabindex="0" makes element focusable -->
<div tabindex="0" role="button" aria-label="Custom button">
    Click me
</div>

<!-- tabindex="-1" removes from tab order but allows programmatic focus -->
<div tabindex="-1" id="skipTarget">
    Content
</div>

<!-- Skip link for keyboard users -->
<a href="#main-content" class="skip-link">Skip to main content</a>
```

### Accessible Modal Dialog

```html
<button onclick="openDialog()" aria-haspopup="dialog">
    Open Dialog
</button>

<div role="dialog" 
     aria-labelledby="dialogTitle" 
     aria-describedby="dialogDesc"
     aria-modal="true"
     hidden>
    <h2 id="dialogTitle">Dialog Title</h2>
    <p id="dialogDesc">Dialog description text.</p>
    <button onclick="closeDialog()" aria-label="Close dialog">
        Close
    </button>
</div>
```

### Accessible Tabs

```html
<div role="tablist" aria-label="Content tabs">
    <button role="tab" 
            aria-selected="true" 
            aria-controls="panel1"
            id="tab1">
        Tab 1
    </button>
    <button role="tab" 
            aria-selected="false" 
            aria-controls="panel2"
            id="tab2">
        Tab 2
    </button>
</div>

<div role="tabpanel" 
     id="panel1" 
     aria-labelledby="tab1">
    Content for tab 1
</div>

<div role="tabpanel" 
     id="panel2" 
     aria-labelledby="tab2"
     hidden>
    Content for tab 2
</div>
```

### Accessibility Checklist

- [ ] All images have descriptive alt text
- [ ] Form inputs have associated labels
- [ ] Heading hierarchy is logical (h1 → h2 → h3)
- [ ] Links have descriptive text (not "click here")
- [ ] Color contrast meets WCAG standards (4.5:1 for text)
- [ ] All functionality works with keyboard only
- [ ] Focus indicators are visible
- [ ] ARIA attributes used where needed
- [ ] Page has proper language attribute (`<html lang="en">`)
- [ ] Dynamic content changes are announced
- [ ] Error messages are clear and associated with fields
- [ ] Skip links provided for keyboard users


## JavaScript Integration

JavaScript can interact with HTML to get input values, modify content, and handle events.

### Getting Form Input Values

#### Using getElementById

```html
<input type="text" id="username" value="John">

<script>
    // Get the input element
    let input = document.getElementById("username");
    
    // Get the value
    let value = input.value;
    console.log(value); // Output: John
    
    // Set a new value
    input.value = "Jane";
</script>
```

#### Getting Different Input Types

```html
<form id="myForm">
    <!-- Text input -->
    <input type="text" id="name" value="John">
    
    <!-- Number input -->
    <input type="number" id="age" value="25">
    
    <!-- Checkbox -->
    <input type="checkbox" id="subscribe" checked>
    
    <!-- Radio buttons -->
    <input type="radio" name="gender" value="male" id="male" checked>
    <input type="radio" name="gender" value="female" id="female">
    
    <!-- Select dropdown -->
    <select id="country">
        <option value="usa">USA</option>
        <option value="uk" selected>UK</option>
    </select>
    
    <!-- Textarea -->
    <textarea id="message">Hello</textarea>
</form>

<script>
    // Text input
    let name = document.getElementById("name").value;
    console.log("Name:", name); // John
    
    // Number input
    let age = document.getElementById("age").value;
    console.log("Age:", age); // 25
    
    // Checkbox (checked property)
    let subscribed = document.getElementById("subscribe").checked;
    console.log("Subscribed:", subscribed); // true
    
    // Radio button (find checked one)
    let gender = document.querySelector('input[name="gender"]:checked').value;
    console.log("Gender:", gender); // male
    
    // Select dropdown
    let country = document.getElementById("country").value;
    console.log("Country:", country); // uk
    
    // Textarea
    let message = document.getElementById("message").value;
    console.log("Message:", message); // Hello
</script>
```

### Form Submission Handling

```html
<form id="myForm">
    <input type="text" id="username" required>
    <input type="email" id="email" required>
    <button type="submit">Submit</button>
</form>

<script>
    let form = document.getElementById("myForm");
    
    form.addEventListener("submit", function(event) {
        // Prevent default form submission
        event.preventDefault();
        
        // Get form values
        let username = document.getElementById("username").value;
        let email = document.getElementById("email").value;
        
        // Display values
        console.log("Username:", username);
        console.log("Email:", email);
        
        // Or show in alert
        alert("Username: " + username + "\nEmail: " + email);
    });
</script>
```

### Modifying HTML Content

#### innerHTML vs textContent

```html
<div id="content">Original text</div>

<script>
    let div = document.getElementById("content");
    
    // textContent: sets plain text only
    div.textContent = "New text";
    
    // innerHTML: can include HTML tags
    div.innerHTML = "<strong>Bold text</strong>";
</script>
```

### Creating and Adding Elements

```html
<div id="container"></div>

<script>
    // Create new element
    let newDiv = document.createElement("div");
    newDiv.textContent = "New content";
    newDiv.id = "newElement";
    
    // Add to container
    let container = document.getElementById("container");
    container.appendChild(newDiv);
</script>
```

### Modifying Attributes

```html
<img id="myImage" src="old.jpg" alt="Old image">

<script>
    let img = document.getElementById("myImage");
    
    // Get attribute
    let src = img.getAttribute("src");
    console.log(src); // old.jpg
    
    // Set attribute
    img.setAttribute("src", "new.jpg");
    img.setAttribute("alt", "New image");
    
    // Or use direct property
    img.src = "another.jpg";
    img.alt = "Another image";
</script>
```

### Event Handling

```html
<button id="myButton">Click Me</button>
<input type="text" id="myInput">

<script>
    // Click event
    let button = document.getElementById("myButton");
    button.addEventListener("click", function() {
        alert("Button clicked!");
    });
    
    // Input event (fires on every keystroke)
    let input = document.getElementById("myInput");
    input.addEventListener("input", function() {
        console.log("Current value:", input.value);
    });
    
    // Change event (fires when input loses focus)
    input.addEventListener("change", function() {
        console.log("Final value:", input.value);
    });
</script>
```

### Form Validation with JavaScript

```html
<form id="registrationForm">
    <label for="username">Username (5-20 chars):</label>
    <input type="text" id="username" required>
    <span id="usernameError"></span><br>
    
    <label for="email">Email:</label>
    <input type="email" id="email" required>
    <span id="emailError"></span><br>
    
    <button type="submit">Register</button>
</form>

<script>
    let form = document.getElementById("registrationForm");
    
    form.addEventListener("submit", function(event) {
        event.preventDefault();
        
        let username = document.getElementById("username").value;
        let email = document.getElementById("email").value;
        let isValid = true;
        
        // Clear previous errors
        document.getElementById("usernameError").textContent = "";
        document.getElementById("emailError").textContent = "";
        
        // Validate username length
        if (username.length < 5 || username.length > 20) {
            document.getElementById("usernameError").textContent = 
                "Username must be 5-20 characters";
            isValid = false;
        }
        
        // Validate email format
        let emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        if (!emailPattern.test(email)) {
            document.getElementById("emailError").textContent = 
                "Invalid email format";
            isValid = false;
        }
        
        // Submit if valid
        if (isValid) {
            alert("Form submitted successfully!");
            console.log("Username:", username);
            console.log("Email:", email);
        }
    });
</script>
```

### Dynamic Content Updates

```html
<button id="loadBtn">Load Data</button>
<div id="output"></div>

<script>
    document.getElementById("loadBtn").addEventListener("click", function() {
        // Simulate loading data
        let data = {
            name: "John Doe",
            age: 30,
            city: "New York"
        };
        
        // Display data
        let output = document.getElementById("output");
        output.innerHTML = `
            <h3>User Information</h3>
            <p>Name: ${data.name}</p>
            <p>Age: ${data.age}</p>
            <p>City: ${data.city}</p>
        `;
    });
</script>
```

### Working with Multiple Checkboxes

```html
<form>
    <input type="checkbox" name="hobby" value="reading" id="reading">
    <label for="reading">Reading</label>
    
    <input type="checkbox" name="hobby" value="sports" id="sports">
    <label for="sports">Sports</label>
    
    <input type="checkbox" name="hobby" value="music" id="music">
    <label for="music">Music</label>
    
    <button type="button" onclick="getHobbies()">Get Selected</button>
</form>

<script>
    function getHobbies() {
        // Get all checked checkboxes
        let checkboxes = document.querySelectorAll('input[name="hobby"]:checked');
        
        // Extract values
        let hobbies = [];
        checkboxes.forEach(function(checkbox) {
            hobbies.push(checkbox.value);
        });
        
        console.log("Selected hobbies:", hobbies);
        alert("You selected: " + hobbies.join(", "));
    }
</script>
```

### Hidden Field Usage Example

```html
<form id="trackingForm">
    <input type="text" id="username" placeholder="Username">
    
    <!-- Hidden fields for tracking -->
    <input type="hidden" id="timestamp">
    <input type="hidden" id="userAgent">
    <input type="hidden" id="sessionId">
    
    <button type="submit">Submit</button>
</form>

<script>
    // Set hidden field values on page load
    document.getElementById("timestamp").value = new Date().toISOString();
    document.getElementById("userAgent").value = navigator.userAgent;
    document.getElementById("sessionId").value = "session_" + Date.now();
    
    // Handle form submission
    document.getElementById("trackingForm").addEventListener("submit", function(e) {
        e.preventDefault();
        
        let username = document.getElementById("username").value;
        let timestamp = document.getElementById("timestamp").value;
        let userAgent = document.getElementById("userAgent").value;
        let sessionId = document.getElementById("sessionId").value;
        
        console.log("Username:", username);
        console.log("Timestamp:", timestamp);
        console.log("User Agent:", userAgent);
        console.log("Session ID:", sessionId);
    });
</script>
```

### Common JavaScript Methods for HTML

| Method | Purpose | Example |
|--------|---------|---------|
| `getElementById()` | Get element by ID | `document.getElementById("myId")` |
| `querySelector()` | Get first matching element | `document.querySelector(".class")` |
| `querySelectorAll()` | Get all matching elements | `document.querySelectorAll("p")` |
| `createElement()` | Create new element | `document.createElement("div")` |
| `appendChild()` | Add child element | `parent.appendChild(child)` |
| `removeChild()` | Remove child element | `parent.removeChild(child)` |
| `setAttribute()` | Set attribute | `element.setAttribute("src", "img.jpg")` |
| `getAttribute()` | Get attribute | `element.getAttribute("src")` |
| `addEventListener()` | Add event listener | `element.addEventListener("click", fn)` |
| `preventDefault()` | Prevent default action | `event.preventDefault()` |

---

## HTML Attributes Reference

### Global Attributes

These attributes can be used on any HTML element.

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `id` | Unique identifier | `<div id="header">` |
| `class` | CSS class name(s) | `<div class="container main">` |
| `style` | Inline CSS styles | `<p style="color: red;">` |
| `title` | Tooltip text | `<abbr title="HyperText Markup Language">HTML</abbr>` |
| `lang` | Language code | `<p lang="es">Hola</p>` |
| `dir` | Text direction | `<p dir="rtl">` (right-to-left) |
| `hidden` | Hide element | `<div hidden>` |
| `tabindex` | Tab order | `<div tabindex="0">` |
| `contenteditable` | Editable content | `<div contenteditable="true">` |
| `draggable` | Draggable element | `<div draggable="true">` |
| `spellcheck` | Spell checking | `<textarea spellcheck="true">` |
| `translate` | Translation behavior | `<p translate="no">` |
| `data-*` | Custom data attributes | `<div data-user-id="123">` |

### Event Attributes

| Attribute | Event | Example |
|-----------|-------|---------|
| `onclick` | Click event | `<button onclick="alert('Hi')">` |
| `onchange` | Value changed | `<input onchange="handleChange()">` |
| `onsubmit` | Form submitted | `<form onsubmit="return validate()">` |
| `onload` | Page/image loaded | `<body onload="init()">` |
| `oninput` | Input value changing | `<input oninput="update()">` |
| `onfocus` | Element focused | `<input onfocus="highlight()">` |
| `onblur` | Element lost focus | `<input onblur="validate()">` |
| `onmouseover` | Mouse over element | `<div onmouseover="show()">` |
| `onmouseout` | Mouse leaves element | `<div onmouseout="hide()">` |
| `onkeydown` | Key pressed | `<input onkeydown="handleKey()">` |
| `onkeyup` | Key released | `<input onkeyup="handleKey()">` |

### Link Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `href` | Link destination | `<a href="page.html">` |
| `target` | Where to open | `<a target="_blank">` |
| `rel` | Relationship | `<a rel="noopener">` |
| `download` | Download file | `<a download="file.pdf">` |
| `hreflang` | Link language | `<a hreflang="es">` |
| `type` | MIME type | `<a type="application/pdf">` |

### Image Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `src` | Image source | `<img src="photo.jpg">` |
| `alt` | Alternative text | `<img alt="Description">` |
| `width` | Image width | `<img width="500">` |
| `height` | Image height | `<img height="300">` |
| `loading` | Loading behavior | `<img loading="lazy">` |
| `srcset` | Responsive sources | `<img srcset="small.jpg 500w">` |
| `sizes` | Image sizes | `<img sizes="(max-width: 600px) 100vw">` |
| `crossorigin` | CORS settings | `<img crossorigin="anonymous">` |
| `decoding` | Decode behavior | `<img decoding="async">` |
| `ismap` | Server-side image map | `<img ismap>` |
| `usemap` | Client-side image map | `<img usemap="#map1">` |

### Form Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `action` | Form submission URL | `<form action="submit.php">` |
| `method` | HTTP method | `<form method="post">` |
| `enctype` | Encoding type | `<form enctype="multipart/form-data">` |
| `target` | Response target | `<form target="_blank">` |
| `autocomplete` | Autocomplete | `<form autocomplete="off">` |
| `novalidate` | Skip validation | `<form novalidate>` |
| `accept-charset` | Character encoding | `<form accept-charset="UTF-8">` |

### Input Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `type` | Input type | `<input type="text">` |
| `name` | Field name | `<input name="username">` |
| `value` | Field value | `<input value="default">` |
| `placeholder` | Hint text | `<input placeholder="Enter text">` |
| `required` | Required field | `<input required>` |
| `readonly` | Read-only | `<input readonly>` |
| `disabled` | Disabled field | `<input disabled>` |
| `maxlength` | Max characters | `<input maxlength="50">` |
| `minlength` | Min characters | `<input minlength="5">` |
| `min` | Minimum value | `<input type="number" min="0">` |
| `max` | Maximum value | `<input type="number" max="100">` |
| `step` | Value increment | `<input type="number" step="5">` |
| `pattern` | Validation pattern | `<input pattern="[0-9]{3}">` |
| `autofocus` | Auto-focus | `<input autofocus>` |
| `autocomplete` | Autocomplete | `<input autocomplete="email">` |
| `multiple` | Multiple values | `<input type="file" multiple>` |
| `accept` | File types | `<input type="file" accept="image/*">` |
| `checked` | Pre-checked | `<input type="checkbox" checked>` |
| `size` | Visible width | `<input size="30">` |
| `list` | Datalist reference | `<input list="options">` |

### Table Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `border` | Border width | `<table border="1">` |
| `cellpadding` | Cell padding | `<table cellpadding="5">` |
| `cellspacing` | Cell spacing | `<table cellspacing="2">` |
| `colspan` | Column span | `<td colspan="2">` |
| `rowspan` | Row span | `<td rowspan="3">` |
| `headers` | Header cells | `<td headers="h1 h2">` |
| `scope` | Header scope | `<th scope="col">` |

### Media Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `src` | Media source | `<video src="video.mp4">` |
| `controls` | Show controls | `<video controls>` |
| `autoplay` | Auto-play | `<video autoplay>` |
| `loop` | Loop playback | `<video loop>` |
| `muted` | Muted audio | `<video muted>` |
| `poster` | Thumbnail image | `<video poster="thumb.jpg">` |
| `preload` | Preload behavior | `<video preload="metadata">` |
| `width` | Media width | `<video width="640">` |
| `height` | Media height | `<video height="360">` |

### Meta Attributes

| Attribute | Purpose | Example |
|-----------|---------|---------|
| `charset` | Character encoding | `<meta charset="UTF-8">` |
| `name` | Metadata name | `<meta name="description">` |
| `content` | Metadata content | `<meta content="Page description">` |
| `http-equiv` | HTTP header | `<meta http-equiv="refresh">` |
| `property` | Open Graph property | `<meta property="og:title">` |

---

## Best Practices Summary

### HTML Structure
- Use proper DOCTYPE declaration
- Include lang attribute on html element
- Use semantic HTML5 elements
- Maintain proper heading hierarchy
- Keep code properly indented

### Accessibility
- Add alt text to all images
- Use labels with form inputs
- Ensure keyboard navigation works
- Use ARIA attributes when needed
- Maintain sufficient color contrast

### Forms
- Always use labels with inputs
- Use appropriate input types
- Add validation attributes
- Provide helpful error messages
- Use fieldset for grouping

### Performance
- Optimize image sizes
- Use lazy loading for images
- Minimize inline styles
- Keep HTML clean and minimal
- Use semantic elements over divs

### SEO
- Use descriptive page titles
- Add meta descriptions
- Use proper heading hierarchy
- Include alt text on images
- Use semantic HTML structure

---

## File Reference

This folder contains the following HTML examples:

| File | Topics Covered |
|------|----------------|
| `hello.html` | Basic HTML structure, br, hr tags |
| `heading.html` | Heading hierarchy (h1-h6) |
| `textTags.html` | Text formatting (strong, em, del, mark, u) |
| `listTags.html` | Ordered and unordered lists, nesting |
| `anchorTag.html` | Links, target attributes, internal/external links |
| `imageTags.html` | Image embedding, alt text, title |
| `divTags.html` | Div containers and grouping |
| `tableTag.html` | Tables, colspan, rowspan, table attributes |
| `form.html` | Form elements, inputs, select, textarea |
| `html5form.html` | HTML5 input types (color, date, email, number) |
| `html5FormAttributes.html` | HTML5 form attributes and validation |
| `html5HiddenFieldUses.html` | Hidden fields with JavaScript tracking |
| `calendarElements.html` | Date/time input types |
| `superscript_subscript_center_meter_tags.html` | Superscript, subscript, meter elements |
| `modernHTML5Elements.html` | Progress, datalist, output, details, dialog |
| `semanticHTML5.html` | Semantic structure (header, nav, main, article) |
| `accessibilityARIA.html` | Accessibility best practices and ARIA attributes |

---

## Additional Resources

### HTML Validators
- [W3C HTML Validator](https://validator.w3.org/)
- [HTML5 Validator](https://html5.validator.nu/)

### Accessibility Testing
- [WAVE Web Accessibility Tool](https://wave.webaim.org/)
- [axe DevTools](https://www.deque.com/axe/devtools/)

### Documentation
- [MDN Web Docs - HTML](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [W3Schools HTML Tutorial](https://www.w3schools.com/html/)
- [HTML Living Standard](https://html.spec.whatwg.org/)

### Learning Paths
1. Start with basic structure and text formatting
2. Learn forms and input handling
3. Master tables and lists
4. Understand semantic HTML5
5. Implement accessibility features
6. Integrate with JavaScript

---

**End of HTML Comprehensive Guide**

*Last Updated: 2024*
