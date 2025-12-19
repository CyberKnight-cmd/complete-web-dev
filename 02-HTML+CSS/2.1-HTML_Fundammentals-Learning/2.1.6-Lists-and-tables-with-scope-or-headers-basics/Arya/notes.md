# Lists & Tables with Scope/Headers Basics - Notes

## Core Concepts

### HTML List Types

#### Unordered Lists (ul)
```html
<ul>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ul>
```

#### Ordered Lists (ol)
```html
<ol>
    <li>Step one</li>
    <li>Step two</li>
    <li>Step three</li>
</ol>

<!-- Custom numbering -->
<ol start="5" type="A">
    <li>Item E</li>
    <li>Item F</li>
</ol>
```

#### Description Lists (dl)
```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language</dd>
    <dt>CSS</dt>
    <dd>Cascading Style Sheets</dd>
</dl>
```

#### Nested Lists
```html
<ul>
    <li>Frontend Technologies
        <ul>
            <li>HTML</li>
            <li>CSS</li>
            <li>JavaScript</li>
        </ul>
    </li>
    <li>Backend Technologies
        <ol>
            <li>Node.js</li>
            <li>Python</li>
            <li>PHP</li>
        </ol>
    </li>
</ul>
```

### HTML Tables

#### Basic Table Structure
```html
<table>
    <caption>Monthly Sales Data</caption>
    <thead>
        <tr>
            <th scope="col">Month</th>
            <th scope="col">Sales</th>
            <th scope="col">Growth</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th scope="row">January</th>
            <td>$10,000</td>
            <td>5%</td>
        </tr>
        <tr>
            <th scope="row">February</th>
            <td>$12,000</td>
            <td>20%</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <th scope="row">Total</th>
            <td>$22,000</td>
            <td>12.5%</td>
        </tr>
    </tfoot>
</table>
```

### Table Accessibility

#### Scope Attribute
```html
<!-- Column headers -->
<th scope="col">Product</th>
<th scope="col">Price</th>

<!-- Row headers -->
<th scope="row">Laptop</th>
<th scope="row">Phone</th>

<!-- Column group headers -->
<th scope="colgroup">Q1 Sales</th>

<!-- Row group headers -->
<th scope="rowgroup">Electronics</th>
```

#### Headers Attribute (Complex Tables)
```html
<table>
    <tr>
        <th id="product">Product</th>
        <th id="q1">Q1</th>
        <th id="q2">Q2</th>
    </tr>
    <tr>
        <th id="laptops" headers="product">Laptops</th>
        <td headers="laptops q1">100</td>
        <td headers="laptops q2">150</td>
    </tr>
</table>
```

#### Table Caption and Summary
```html
<table>
    <caption>
        Quarterly Sales Report 2024
        <details>
            <summary>Table Summary</summary>
            <p>This table shows sales figures for each product category across four quarters, with totals and percentage changes.</p>
        </details>
    </caption>
    <!-- table content -->
</table>
```

## Mental Models

### Screen Reader Navigation
- Lists: Navigate by list items (L key)
- Tables: Navigate by cells (Ctrl+Alt+arrows)
- Headers provide context for data cells
- Scope defines relationship direction

### Table Structure Hierarchy
```
table
├── caption (optional)
├── colgroup (optional)
├── thead
│   └── tr
│       └── th (scope="col")
├── tbody
│   └── tr
│       ├── th (scope="row")
│       └── td
└── tfoot
    └── tr
        └── th/td
```

## Common Pitfalls

### 1. Missing List Structure
```html
<!-- WRONG -->
<div>• Item 1</div>
<div>• Item 2</div>

<!-- CORRECT -->
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
</ul>
```

### 2. Tables for Layout
```html
<!-- WRONG -->
<table>
    <tr>
        <td>Navigation</td>
        <td>Content</td>
    </tr>
</table>

<!-- CORRECT -->
<div class="layout">
    <nav>Navigation</nav>
    <main>Content</main>
</div>
```

### 3. Missing Table Headers
```html
<!-- WRONG -->
<table>
    <tr>
        <td>Name</td>
        <td>Age</td>
    </tr>
</table>

<!-- CORRECT -->
<table>
    <thead>
        <tr>
            <th scope="col">Name</th>
            <th scope="col">Age</th>
        </tr>
    </thead>
</table>
```

### 4. Incorrect Scope Usage
```html
<!-- WRONG -->
<th scope="row">Total Sales</th> <!-- Should be col -->

<!-- CORRECT -->
<th scope="col">Total Sales</th>
```

## Best Practices

### List Guidelines
- Use semantic list elements, not styled divs
- Nest lists properly within li elements
- Use ol for sequential content, ul for non-sequential
- Use dl for term-definition pairs

### Table Guidelines
- Always include thead, tbody, tfoot when appropriate
- Use th for headers, td for data
- Include scope attribute on all th elements
- Provide caption for table context
- Use headers attribute for complex relationships
- Avoid tables for layout purposes