# Collective Notes for CSS

---

# PART 1 — CSS Foundations and First Contact

## What CSS Is and Why It Exists

CSS stands for **Cascading Style Sheets**.

It is a stylesheet language used to describe the **presentation** of a document.
Most commonly applied to HTML, but not limited to it. CSS can also be used with:

* XML
* SVG
* MathML
* XHTML
* Print media
* Speech media

For this course, the focus is **HTML + CSS**.

HTML is the **structure**.
CSS is the **appearance**.

Think in terms of construction:

* HTML is the foundation, framing, walls.
* CSS is paint, carpet, wallpaper, spacing, visual polish.

CSS never replaces structure.
It decorates and presents structure.

---

## Tools Required for the Course

Browser:

* Google Chrome
* Used consistently throughout the course

Editor:

* Visual Studio Code (VS Code)
* Cross-platform
* Lightweight but powerful
* Excellent CSS tooling and extensions

Project setup:

* Each lesson can live in its own folder
* Or build incrementally in one folder
* A folder is required either way

---

## Initial HTML Setup

Create a new file:

```html
index.html
```

Use Emmet to scaffold the document:

* Type `!`
* Press Enter

Generated structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>
</body>
</html>
```

Meta tags are left in place.
They’re useful and harmless at this stage.

Add minimal content:

```html
<body>
  <p>I'm learning CSS!</p>
</body>
```

This is enough to begin.

---

## Three Ways to Apply CSS

CSS can be applied in three distinct ways:

External stylesheet
Internal stylesheet
Inline styles

All three work.
They differ in **organization**, **maintainability**, and **priority**.

---

## External Stylesheet (Preferred)

Create folder structure:

```
project-folder/
  index.html
  css/
    style.css
```

Link the stylesheet inside `<head>`:

```html
<link rel="stylesheet" href="css/style.css">
```

Notes:

* `type="text/css"` is obsolete
* Modern browsers do not require it
* Older tutorials may still show it

Add CSS:

```css
p {
  color: purple;
}
```

This is a complete rule.

---

## Live Server Setup

Install VS Code extension:

* **Live Server** by Ritwick Dey

Purpose:

* Simulates a web server
* Automatically reloads on save
* Avoids opening files directly from disk

Usage:

* Click “Go Live” (bottom-right)
* Or right-click `index.html` → Open with Live Server

---

## First Visible Styling

Add font size:

```css
p {
  font-size: 64px;
  color: purple;
}
```

Now the change is clearly visible.

---

## Internal Stylesheet

Add inside `<head>`:

```html
<style>
  p {
    color: limegreen;
  }
</style>
```

Result:

* Font size remains large
* Color changes to lime green

Key concept:

* This is not “stronger” by default
* It is simply **read later**

Order matters more than location.

---

## Demonstrating the Cascade

Move external link **below** internal style:

```html
<style>
  p {
    color: limegreen;
  }
</style>

<link rel="stylesheet" href="css/style.css">
```

Now:

* Purple wins
* External CSS is read last

CSS reads **top → bottom**, last matching rule wins.

---

## Inline Styles (Demonstration Only)

Inline styles use the `style` attribute:

```html
<p style="color: blue;">I'm learning CSS!</p>
```

Notes:

* No selector needed
* Applied directly to element
* Overrides internal and external styles

Strongly discouraged.

Reason:

* Breaks separation of concerns
* Hard to maintain
* Not reusable

Inline styles are demonstrated, then removed.

---

## Cleaning Back to Best Practice

Remove:

* Inline styles
* `<style>` block

Keep:

* External stylesheet only

This is how the rest of the course proceeds.

---

## Anatomy of a CSS Rule

Structure:

```css
selector {
  property: value;
}
```

Terminology:

* Selector → what is being targeted
* Property → what is being changed
* Value → how it’s changed
* Declaration → property + value
* Rule / Rule set → selector + declarations

Example:

```css
p {
  color: purple;
}
```

---

## CSS Is Forgiving — and Dangerous

CSS uses **American spelling**.

Incorrect spelling example:

```css
colour: purple;
```

Result:

* Rule is silently ignored
* No error thrown

Browsers do not warn you.

Solution:

* Use a CSS validator

---

## CSS Validation

Tool:

* W3C CSS Validation Service

Workflow:

* Upload `style.css`
* Validate
* Fix errors

Success message:

* “Congratulations! No error found.”

---

## Transition to Selectors

Next focus:

* CSS Selectors

Core idea:

* Selectors determine **what gets styled**
* Understanding selectors is foundational

---

## Basic HTML Structure Used for Selectors

HTML pattern:

```html
<header>
  <h1>CSS Selectors</h1>
</header>

<main>
  <article>
    <h2>Article One</h2>
    <p>Text here</p>
  </article>

  <article>
    <h2>Article Two</h2>
    <p class="gray" id="second">Text here</p>
  </article>

  <article>
    <h2>Article Three</h2>
    <p class="gray">Text here</p>
  </article>
</main>
```

Used consistently to demonstrate selectors.

---

## Element Selectors

Example:

```css
body {
  font-size: 22px;
}
```

Effect:

* All child elements inherit font size
* Demonstrates inheritance

Another element selector:

```css
p {
  color: purple;
}
```

Effect:

* All paragraphs are styled
* Element selectors apply globally to that tag

---

## Class Selectors

Syntax:

* Start with a dot

```css
.gray {
  color: gray;
}
```

HTML usage:

```html
<p class="gray">Text</p>
```

Characteristics:

* Reusable
* More specific than element selectors
* Most commonly used selector type

Overrides earlier paragraph color due to higher specificity.

---

## ID Selectors

Syntax:

* Start with `#`

```css
#second {
  font-style: italic;
}
```

HTML usage:

```html
<p id="second">Text</p>
```

Rules:

* IDs must be unique
* Only one per page

Best practice:

* Avoid using IDs in CSS
* Reserve IDs for:

  * Labels
  * JavaScript hooks

---

## Grouping Selectors

Multiple selectors, same styles:

```css
h1,
h2 {
  color: blue;
}
```

Comma is mandatory.

Without comma:

```css
h1 h2 {
  color: blue;
}
```

Meaning:

* Selects `h2` **inside** `h1`
* Likely matches nothing

---

## Descendant Selectors

Example:

```css
p span {
  text-transform: uppercase;
  background-color: gold;
}
```

Meaning:

* Any `span` inside a `p`

Better approach:

* Use a class instead

HTML:

```html
<span class="highlight">text</span>
```

CSS:

```css
.highlight {
  text-transform: uppercase;
  background-color: gold;
}
```

Reusable, cleaner, safer.

---

## Universal Selector

Syntax:

```css
* {
  font-family: monospace;
}
```

Selects:

* Every element

Common use:

* CSS resets (covered later)

Not for everyday styling.

---

# PART 2 — Cascade, Specificity, Inheritance, and Debugging CSS

## The Meaning of “Cascading” in CSS

CSS stands for **Cascading Style Sheets**.

The word *cascading* is literal.

CSS behaves like a waterfall:

* Rules are read **top to bottom**
* When multiple rules apply to the same element and property, **the last valid rule wins**

Example:

```css
p {
  color: purple;
}

p {
  color: red;
}
```

Result:

* Paragraphs are red
* The browser read the purple rule first, then the red rule later

Order matters.

---

## Cascade vs Specificity (Critical Distinction)

Cascade answers:

* *Which rule was read last?*

Specificity answers:

* *Which rule is more precise?*

Specificity **overrides the cascade**.

Example setup:

```css
p {
  color: red;
}

.gray {
  color: gray;
}
```

HTML:

```html
<p class="gray">Text</p>
```

Result:

* Text is gray
* Even if the `p` selector appears later
* Because `.gray` is more specific than `p`

Specificity beats order.

---

## Specificity Hierarchy (Mental Model)

From least specific to most specific:

* Element selector
* Class selector
* ID selector
* Inline styles
* `!important` (nuclear option)

This hierarchy explains nearly all CSS conflicts.

---

## Demonstrating Specificity Overriding Cascade

Example:

```css
.gray {
  color: gray;
}

p {
  color: red;
}
```

Even though `p` is read last:

* `.gray` still wins
* Because class selectors outrank element selectors

This is often confusing early on and causes frustration.

---

## Debugging CSS with DevTools

When styles don’t apply:

* Do not guess
* Inspect

Steps:

* Right-click element
* Choose **Inspect**
* Open DevTools
* Go to **Elements**
* Select the element
* Look at **Styles**

What you’ll see:

* Applied rules
* Overridden rules crossed out
* Source file and line number

This shows:

* What rules exist
* Why one wins over another

This is the single most important CSS debugging skill.

---

## Understanding Overridden Rules

In DevTools:

* Crossed-out rules still exist
* They lost to a more specific rule

Example:

* `p { color: red; }` crossed out
* `.gray { color: gray; }` applied

Meaning:

* CSS saw both
* Chose the more specific selector

---

## Inheritance in CSS

Inheritance is different from selection.

Inheritance means:

* Child elements receive certain properties from parents

Example:

```css
body {
  font-size: 22px;
}
```

Result:

* All text becomes larger
* Because font-related properties inherit

Common inherited properties:

* font-size
* font-family
* color
* line-height
* text-align

---

## Properties That Do NOT Inherit

Example:

```css
body {
  border: 3px solid black;
}
```

Result:

* Only the body has a border
* Children do not inherit borders

Non-inherited properties include:

* border
* margin
* padding
* width
* height
* background (generally)

Inheritance mostly applies to **typography**.

---

## Universal Selector Is Not Inheritance

Example:

```css
* {
  border: 1px solid red;
}
```

This is not inheritance.

This:

* Selects every element directly
* Applies styles individually

Important distinction:

* Inheritance flows downward
* Universal selector applies everywhere independently

---

## Using Inheritance to Write DRY CSS

DRY = Don’t Repeat Yourself

Instead of:

```css
p {
  font-family: Arial;
}

h1 {
  font-family: Arial;
}
```

Use:

```css
body {
  font-family: Arial;
}
```

Let inheritance do the work.

---

## Form Elements and Inheritance

Form elements do **not** inherit typography by default.

Common fix:

```css
button,
input,
textarea,
select {
  font: inherit;
}
```

This forces form controls to match the rest of the page.

---

## Choosing Where to Apply Typography

Common choices:

* `body`
* `html`

Both work.

Why `html` is often preferred:

* It is the true root element
* Makes rem-based sizing predictable

Example:

```css
html {
  font-family: Arial, sans-serif;
}
```

---

## Semantic Containers and Inheritance

Using `main`:

```css
main {
  font-family: monospace;
}
```

Only affects content inside `<main>`.

Useful when:

* Header/footer need different styles
* Main content should be visually distinct

---

## Revisiting Specificity (Quick Review)

Specificity ranking recap:

* `p` → weakest
* `.class` → stronger
* `#id` → stronger still

IDs work — but should be avoided in CSS.

---

## The `!important` Flag (The Nuclear Option)

Example:

```css
p {
  color: purple !important;
}
```

Result:

* Overrides everything
* Even class selectors
* Even ID selectors

Why this is dangerous:

* Breaks natural cascade
* Makes code brittle
* Signals poor organization

Rule:

* Do not use `!important` while learning
* Do not use it unless you fully understand why

---

## Why `!important` Breaks Everything

Example:

```css
.gray {
  color: gray;
}

p {
  color: purple !important;
}
```

Result:

* All paragraphs become purple
* Including those with `.gray`

This destroys intentional styling.

---

## Specificity Calculator

Tool:

* CSS Specificity Calculator

Purpose:

* Compare selectors numerically
* Understand why one wins

Example scores:

* `h2` → 0-0-1
* `.gray` → 0-1-0
* `#second` → 1-0-0

Classes beat elements.
IDs beat classes.

Multiple classes add up:

* `.highlight.gray` → 0-2-0

Still weaker than an ID.

---

## Transition to Color Theory in CSS

Now that selectors, cascade, specificity, and inheritance are understood:

* Move to **colors**
* Focus shifts from *what gets styled* to *how it looks*

---

## Default Browser Colors

Default styles:

* White background
* Black text

These come from:

* User agent stylesheet (browser defaults)

CSS overrides these defaults.

---

## Setting Background Color

Primary property:

```css
background-color: blue;
```

Shorthand version:

```css
background: blue;
```

Both work.
Shorthand is preferred.

---

## Visual Studio Code Color Assistance

VS Code:

* Suggests 140 named colors
* Shows color preview square
* Alphabetical autocomplete

Example:

```css
background: papayawhip;
```

---

## Color Contrast Awareness

Color choice must consider:

* Readability
* Accessibility

Poor contrast = unreadable content.

---

## Setting Text Color

Property:

```css
color: darkblue;
```

Applies to text only.

Background and text color must be considered together.

---

## RGB Color Model

Syntax:

```css
color: rgb(255, 0, 0);
```

Meaning:

* Red, Green, Blue
* Values from 0 to 255

Examples:

* `rgb(0, 0, 0)` → black
* `rgb(255, 255, 255)` → white
* `rgb(0, 0, 255)` → blue

---

## RGBA (Alpha Channel)

Adds transparency:

```css
color: rgba(0, 0, 0, 0.5);
```

Alpha:

* 0 → fully transparent
* 1 → fully opaque

Useful for:

* Subtle text
* Overlays

---

## Hexadecimal Colors

Syntax:

```css
color: #000000;
```

Structure:

* RR GG BB
* Hex digits 0–9, A–F

Examples:

* `#000000` → black
* `#ffffff` → white
* `#ff0000` → red

---

## Hex Shorthand

Allowed when pairs match:

```css
#000 → #000000
#fff → #ffffff
#f00 → #ff0000
```

Not allowed:

* `#808080` (no matching pairs)

---

## VS Code Color Picker

Hover color square → picker opens.

Capabilities:

* RGB
* RGBA
* HEX
* HSL
* HSLA

Transparency slider auto-switches to RGBA / HSLA.

---

## HSL Color Model

HSL = Hue, Saturation, Lightness

Example:

```css
color: hsl(0, 100%, 50%);
```

Hue:

* 0–360 (color wheel)

Saturation:

* 0% → gray
* 100% → full color

Lightness:

* 0% → black
* 50% → normal
* 100% → white

Often preferred for:

* Theming
* CSS variables

---

## Choosing Near-Black Text

Common professional choice:

```css
color: #333;
```

Softer than pure black
Easier on the eyes

---

## Color Palette Tools

Coolors.co:

* Generate palettes
* Lock colors
* Copy hex values

---

## Contrast Checking Tools

Coolors Contrast Checker
WebAIM Contrast Checker

WCAG Guidelines:

* Normal text: 4.5:1 minimum
* Large text: 3:1 minimum
* AAA: 7:1

Accessibility is not optional.

---

## Transition to CSS Units

With colors established:

* Move to **units**
* Units define size, spacing, layout

This section explains *why* some units should never be used for fonts.

Continuing seamlessly.

---

# PART 3 — CSS Units: Absolute, Relative, and Viewport-Based Sizing

## What CSS Units Control

Units determine:

* Font size
* Spacing
* Layout width and height
* Responsiveness

Choosing the wrong unit can:

* Break accessibility
* Override user preferences
* Cause layout bugs

This section focuses only on **commonly used units**, not every unit CSS supports.

---

## Absolute Units

Absolute units have a fixed size.

CSS technically supports many absolute units, but in practice **only one matters**.

### Pixels (`px`)

Definition:

* One pixel maps to one device pixel (conceptually)

Example:

```css
p {
  font-size: 32px;
}
```

Pixels are:

* Predictable
* Fixed
* Not user-scalable

---

## Why Pixels Should NOT Be Used for Font Size

Browsers have a default font size:

* Usually 16px

Users can change this in browser settings.

Demonstration:

* Chrome → Settings → Appearance → Font Size
* Set to “Very Large”

If font size is defined in pixels:

```css
html {
  font-size: 16px;
}
```

Result:

* User preference is ignored
* Accessibility is broken

Conclusion:

* Do **not** use pixels for font sizing

---

## Where Pixels ARE Appropriate

Pixels are useful for:

* Borders
* Shadows
* Fine-grained layout details

Example:

```css
h1 {
  border: 2px dashed red;
}
```

Pixel borders remain consistent regardless of zoom or viewport size.

---

## Relative Units Overview

Relative units scale based on something else:

* Parent element
* Root element
* Viewport
* Font metrics

These are preferred for responsive design.

---

## Percentages (`%`)

Percentages are always relative.

Example:

```css
h1 {
  width: 50%;
}
```

Meaning:

* 50% of the **parent’s width**

If parent is 100% of page → element is 50% of page
If parent is 50% of page → element is 25% of page

Percentages are most commonly used for:

* Width
* Sometimes height (with care)

---

## Percentage and Block-Level Elements

Block elements:

* Default width = 100%

Setting:

```css
width: 100%;
```

Is usually unnecessary.

---

## Understanding Parent-Child Relationships

HTML structure matters.

Example:

```html
<header>
  <h1>Title</h1>
</header>
```

```css
header {
  width: 50%;
}

h1 {
  width: 50%;
}
```

Result:

* `h1` = 50% of `header`
* Total = 25% of viewport

Percentages always look **upward** to parent.

---

## Root-Relative Units (`rem`)

`rem` = root em
Root = `<html>` element

Default:

* Browser sets root font size (usually 16px)

Example:

```css
p {
  font-size: 1rem;
}
```

Equals:

* Browser default size

Example:

```css
p {
  font-size: 2rem;
}
```

Equals:

* Twice the root size

---

## Why `rem` Is Preferred for Font Sizes

Advantages:

* Respects user settings
* Predictable
* Not affected by nesting

Even if parent changes font size:

* `rem` still references root

This avoids accidental compounding.

---

## Why `em` Can Be Dangerous for Font Size

`em` is relative to the **parent’s font size**.

Example:

```css
main {
  font-size: 2em;
}

p {
  font-size: 2em;
}
```

Effect:

* Main doubles root
* Paragraph doubles main
* Result = 4× root size

This compounding effect is often unintentional.

---

## Proper Use of `em`

Best use cases:

* Padding
* Margin
* Element-relative spacing

Example:

```css
h1 {
  font-size: 3rem;
  padding: 0.5em;
}
```

Meaning:

* Padding scales with the element’s font size
* Makes components self-contained

---

## Character Unit (`ch`)

Definition:

* Width of the `0` character in the current font

Use case:

* Text readability
* Column widths

Example:

```css
p {
  width: 40ch;
}
```

Result:

* About 40 characters per line
* Comfortable reading width

This originates from print typography.

---

## Default Browser Styles (User Agent Stylesheet)

Browsers apply default CSS:

* Margins
* Font sizes
* Line heights

Visible in DevTools as:

* “user agent stylesheet”

These defaults explain unexpected spacing.

---

## Viewport Units

Viewport = visible browser area.

Units:

* `vw` → viewport width
* `vh` → viewport height

### Viewport Width (`vw`)

```css
main {
  width: 50vw;
}
```

Meaning:

* 50% of viewport width

---

## When `vw` Causes Problems

Example:

```css
body {
  width: 100vw;
}
```

Problem:

* Vertical scrollbar appears
* Horizontal scrollbar appears unintentionally

Reason:

* `100vw` ignores scrollbar width
* Page becomes slightly wider than visible area

Better choice:

```css
width: 100%;
```

---

## Viewport Height (`vh`)

Used when element should fill screen vertically.

Incorrect:

```css
body {
  height: 100vh;
}
```

Problem:

* Content can overflow
* Layout breaks

Correct approach:

```css
body {
  min-height: 100vh;
}
```

Result:

* Body fills screen
* Still grows with content

---

## Summary of Unit Best Practices (Implicit)

* Fonts → `rem`
* Spacing → `em`
* Widths → `%`
* Borders → `px`
* Viewport layouts → `vh`, `vw` (with care)

---

## Transition to Box Model

Understanding units leads directly to:

* Spacing
* Layout
* Sizing

Next concept:

* **Everything in CSS is a box**

This is foundational.

---

# PART 4 — The CSS Box Model

## Everything Is a Box

Every HTML element:

* Is rectangular
* Has dimensions
* Participates in layout as a box

The box model defines:

* How size is calculated
* How spacing works

---

## The Four Layers of the Box Model

From inside to outside:

* Content
* Padding
* Border
* Margin

These layers control spacing and size.

---

## Inspecting the Box Model

Use DevTools:

* Right-click element → Inspect
* Select element
* Open **Computed** tab

Visual overlay:

* Blue → content
* Green → padding
* Yellow/Orange → margin
* Border clearly outlined

This visualization is essential for debugging layout issues.

---

## Default Margins and Padding

Example:

* `h1` has default margins
* Set by browser

Visible in:

* User agent stylesheet

Margins often use `em` units:

* Scale with font size

---

## Why Font Size Affects Default Spacing

Example:

* `h1` default margin = `0.67em`
* Increase font size → margin increases

This explains unexpected spacing changes.

---

## CSS Reset (Basic)

Purpose:

* Remove browser defaults
* Start from a clean slate

Basic reset:

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
```

This is extremely common.

---

## Box Sizing: `content-box` vs `border-box`

Default:

```css
box-sizing: content-box;
```

Meaning:

* Width applies to content only
* Padding and border add extra size

Example:

```css
width: 400px;
padding: 24px;
border: 2px solid black;
```

Actual size > 400px

---

## `border-box` (Preferred)

```css
box-sizing: border-box;
```

Meaning:

* Width includes content + padding + border

Now:

* Total width = exactly 400px
* Easier mental math
* Predictable layout

Margins remain outside the calculation.

---

## Applying Box Model Styles to Containers

Instead of styling individual elements:

* Create container classes

HTML:

```html
<header class="container"></header>
<main class="container"></main>
```

CSS:

```css
.container {
  padding: 1.5rem;
  margin: 1.5rem;
  border: 2px dashed blue;
}
```

Reusable and scalable.

---

## Margin vs Padding

Padding:

* Inside border
* Pushes content inward

Margin:

* Outside border
* Pushes elements apart

Margins collapse vertically
Padding never collapses

---

## Margin and Padding Shorthand

Order:

* Top → Right → Bottom → Left

Examples:

```css
margin: 1.5em;
```

Applies to all sides.

```css
margin: 1.5em 2em;
```

Top/Bottom → 1.5em
Left/Right → 2em

```css
margin: 1.5em 2em 3em 4em;
```

All sides explicitly defined.

Same rules apply to padding.

---

## Individual Side Control

Example:

```css
margin-top: 1.5em;
margin-right: 2em;
margin-bottom: 3em;
margin-left: 4em;
```

Useful for fine control, but verbose.

Shorthand is preferred when possible.

---

## Border Shorthand

```css
border: 2px dashed red;
```

Order:

* Width
* Style
* Color

---

## Individual Border Sides

Example:

```css
border-top: 5px solid green;
border-right: 10px dotted yellow;
```

Each side can differ.

---

## Breaking Border Properties Apart

Each side supports:

* Width
* Style
* Color

Example:

```css
border-top-width: 5px;
border-top-style: dashed;
border-top-color: blue;
```

This level of control is rarely needed but exists.

---

# PART 5 — Borders, Border Radius, Overflow, and Shaping Boxes

## Borders as Part of the Box Model

Borders sit between padding and margin.

They:

* Visually define an element’s boundary
* Contribute to size when using `content-box`
* Are included in size when using `border-box`

Most borders are written using shorthand:

```css
border: 2px solid black;
```

This shorthand defines:

* Border width
* Border style
* Border color

---

## Default Border Behavior

If border width is omitted:

```css
border: solid black;
```

The browser applies a default width (usually 3px).

This can lead to unexpected thickness.

Best practice:

* Always specify width explicitly

---

## Border Styles

Common styles:

* solid
* dashed
* dotted
* double
* groove
* ridge
* inset
* outset

Example:

```css
border: 4px ridge blue;
```

Some styles are more decorative and rarely used in production, but they exist.

---

## Individual Border Sides

Borders can be controlled per side:

```css
border-top: 5px solid green;
border-right: 10px dotted blue;
```

Each side behaves independently.

---

## Breaking Borders into Properties

Each side supports:

```css
border-top-width
border-top-style
border-top-color
```

Example:

```css
border-top-width: 5px;
border-top-style: dashed;
border-top-color: blue;
```

This level of granularity is useful for advanced layouts but uncommon in everyday styling.

---

## Border Radius

Border radius rounds corners of boxes.

Example:

```css
border-radius: 10px;
```

Applies to all corners equally.

---

## Individual Corner Control

Corners can be styled independently:

```css
border-top-left-radius: 20px;
border-bottom-right-radius: 40px;
```

This allows asymmetric shapes.

---

## Turning a Box into a Circle

Key requirement:

* Width and height must be equal

Example:

```css
div {
  width: 200px;
  height: 200px;
  border-radius: 50%;
}
```

Result:

* Perfect circle

This works because:

* 50% radius equals half of the box’s size

---

## Border Radius with Percentages

Percentages are relative to the box dimensions.

Example:

```css
border-radius: 50%;
```

Creates:

* Circles for squares
* Ovals for rectangles

---

## Overflow: What Happens When Content Exceeds the Box

By default:

```css
overflow: visible;
```

Meaning:

* Content spills outside the box

---

## Overflow Hidden

```css
overflow: hidden;
```

Effect:

* Clips overflowing content
* Useful for rounded corners
* Common with images

---

## Overflow Scroll and Auto

```css
overflow: scroll;
```

Always shows scrollbars.

```css
overflow: auto;
```

Shows scrollbars only when needed.

Auto is preferred.

---

## Directional Overflow

Overflow can be controlled per axis:

```css
overflow-x: hidden;
overflow-y: auto;
```

Useful for:

* Horizontal layout control
* Preventing sideways scrolling

---

## Overflow and Rounded Corners

Rounded corners do not clip content by default.

To enforce clipping:

```css
border-radius: 10px;
overflow: hidden;
```

This is essential for:

* Image containers
* Cards
* UI components

---

## Visual Debugging with Borders

Borders are often used temporarily to:

* Visualize layout
* Understand spacing
* Debug alignment

They are usually removed afterward.

---

## Preparing for Layout Concepts

At this stage, the following are now understood:

* Units
* Inheritance
* Box model
* Borders
* Spacing
* Overflow

These are prerequisites for layout systems.

---

## Transition to Display and Layout

Next concepts rely on box behavior:

* `display`
* Block vs inline
* Inline-block
* None

Understanding these is required before Flexbox or Grid.

---

# PART 6 — Display Property and Element Flow

## The Default Display Behavior

Every element has a default `display` value.

Common defaults:

* `block`
* `inline`
* `inline-block`

---

## Block-Level Elements

Examples:

* `div`
* `p`
* `h1`–`h6`
* `header`
* `main`
* `section`
* `article`

Behavior:

* Start on a new line
* Take full available width
* Respect width and height

Example:

```css
p {
  width: 50%;
}
```

Works as expected.

---

## Inline Elements

Examples:

* `span`
* `a`
* `strong`
* `em`

Behavior:

* Flow with text
* Ignore width and height
* Padding applies horizontally
* Vertical padding affects line height but not layout

Example:

```css
span {
  width: 200px;
}
```

Has no effect.

---

## Inline-Block Elements

Inline-block combines behaviors:

* Flows inline
* Accepts width and height

Example:

```css
span {
  display: inline-block;
  width: 200px;
}
```

This now works.

---

## Why Inline-Block Exists

Inline-block is useful for:

* Buttons
* Badges
* UI elements inside text flow

It was heavily used before Flexbox.

---

## Display None

```css
display: none;
```

Effect:

* Element removed from layout
* Takes up no space

Different from:

```css
visibility: hidden;
```

Which:

* Hides element
* Preserves space

---

## Visibility Hidden

```css
visibility: hidden;
```

Element:

* Invisible
* Still occupies layout space

Useful for:

* Temporary hiding without layout shift

---

## Debugging Display Issues

If layout looks wrong:

* Check display type
* Inspect element
* Confirm whether width/height should apply

Many “CSS bugs” are display misunderstandings.

---

## Transition Toward Layout Systems

Classic layout tools:

* display
* float (legacy)
* positioning

Modern layout tools:

* Flexbox
* Grid

Before Flexbox:

* Positioning must be understood.

---

# PART 7 — Positioning Fundamentals

## Position Property Overview

Position controls:

* How elements are placed
* How they interact with normal flow

Values:

* static
* relative
* absolute
* fixed
* sticky

---

## Static Positioning

Default behavior:

```css
position: static;
```

Characteristics:

* Normal document flow
* Top, left, right, bottom have no effect

Most elements remain static unless changed.

---

## Relative Positioning

```css
position: relative;
```

Effect:

* Element stays in normal flow
* Can be offset visually

Example:

```css
h1 {
  position: relative;
  top: 20px;
  left: 10px;
}
```

Space is preserved in original location.

---

## Why Relative Is Important

Relative positioning:

* Establishes positioning context
* Enables absolute children to reference it

Rarely used alone for layout.

---

## Absolute Positioning

```css
position: absolute;
```

Behavior:

* Removed from normal flow
* Positioned relative to nearest positioned ancestor
* Falls back to viewport if none exists

Example:

```css
div {
  position: absolute;
  top: 0;
  right: 0;
}
```

---

## Positioning Context

Absolute elements look for:

* Nearest ancestor with `position` not static

Common pattern:

```css
.container {
  position: relative;
}

.child {
  position: absolute;
  top: 0;
  right: 0;
}
```

---

## Fixed Positioning

```css
position: fixed;
```

Characteristics:

* Relative to viewport
* Ignores scrolling
* Common for navbars

Example:

```css
nav {
  position: fixed;
  top: 0;
}
```

---

## Sticky Positioning

Hybrid behavior:

```css
position: sticky;
top: 0;
```

Behavior:

* Acts relative until threshold
* Then sticks like fixed

Requires:

* Scrollable container
* Defined offset

---

## Positioning Pitfalls

Common mistakes:

* Forgetting positioning context
* Overusing absolute positioning
* Breaking responsiveness

Positioning is powerful but fragile.

---

## Preparing for Modern Layout

Positioning is not layout.

For layout:

* Use Flexbox
* Use Grid

Positioning is best for:

* Overlays
* Tooltips
* Modals
* Fine adjustments

---
# PART 8 — Floats (Legacy Layout Concept, Minimal but Necessary)

## Why Floats Exist

Floats were originally designed for:

* Wrapping text around images
* Magazine-style layouts

They were **not** created for full page layout, but were used that way for many years before Flexbox and Grid.

Understanding floats is important because:

* You will see them in older codebases
* Some float-related bugs still appear in maintenance work

---

## Basic Float Behavior

Example:

```css
img {
  float: left;
}
```

Effect:

* Element is taken out of normal flow
* Inline content wraps around it

Floated elements:

* Still affect inline content
* Do not affect block layout in expected ways

---

## Floating Block Elements

```css
article {
  float: left;
  width: 50%;
}
```

Result:

* Articles align side by side
* Parent collapses in height

This collapsing behavior caused many historical bugs.

---

## Clearing Floats

To fix collapsing parents:

```css
.clear {
  clear: both;
}
```

Or modern clearfix:

```css
.container::after {
  content: "";
  display: block;
  clear: both;
}
```

This forces the parent to recognize floated children.

---

## Why Floats Are Avoided for Layout

Problems:

* Fragile behavior
* Requires clearfix hacks
* Difficult to reason about
* Breaks responsiveness easily

Floats are now:

* Legacy knowledge
* Rarely used intentionally for layout

---

## Transition to Modern Layout

Floats solve problems indirectly.

Flexbox solves them **directly**.

From this point forward:

* Layout thinking changes
* Axis-based layout replaces box stacking

---

# PART 9 — Flexbox Fundamentals

## Why Flexbox Exists

Flexbox was designed to solve:

* Alignment
* Distribution
* Direction
* Spacing

It works on **one axis at a time**.

---

## Defining a Flex Container

```css
.container {
  display: flex;
}
```

Immediate effects:

* Children become flex items
* Direction defaults to row
* Items align horizontally

---

## Main Axis vs Cross Axis

Default:

* Main axis → horizontal
* Cross axis → vertical

Changing direction:

```css
flex-direction: column;
```

Now:

* Main axis → vertical
* Cross axis → horizontal

This axis concept is critical.

---

## Justifying Content (Main Axis)

```css
justify-content: flex-start;
justify-content: center;
justify-content: space-between;
justify-content: space-around;
justify-content: space-evenly;
```

Controls:

* Distribution along main axis

---

## Aligning Items (Cross Axis)

```css
align-items: stretch;
align-items: center;
align-items: flex-start;
align-items: flex-end;
```

Controls:

* Alignment perpendicular to main axis

---

## Individual Item Alignment

```css
.item {
  align-self: center;
}
```

Overrides container alignment for a single item.

---

## Flex Wrap

By default:

* Items stay on one line

Enable wrapping:

```css
flex-wrap: wrap;
```

Items move to next line when space runs out.

---

## Gap Property

Preferred spacing method:

```css
gap: 1rem;
```

Replaces margin hacks.

Works with:

* Row layouts
* Column layouts

---

## Flex Grow

```css
.item {
  flex-grow: 1;
}
```

Controls:

* How extra space is distributed

Items with higher values grow more.

---

## Flex Shrink

```css
.item {
  flex-shrink: 1;
}
```

Controls:

* How items shrink when space is tight

---

## Flex Basis

```css
.item {
  flex-basis: 200px;
}
```

Defines:

* Initial size before grow/shrink

---

## Flex Shorthand

```css
flex: 1 1 200px;
```

Order:

* grow
* shrink
* basis

Most common:

```css
flex: 1;
```

---

## Why Flexbox Is Preferred

Flexbox:

* Respects content
* Is responsive by default
* Eliminates float hacks
* Is intuitive once axes are understood

---

## Flexbox Mental Model

Ask:

* What is the main axis?
* How should items distribute?
* How should they align?

Everything else follows.

---

## Transition to Grid

Flexbox:

* One-dimensional

Grid:

* Two-dimensional

Grid handles:

* Rows AND columns simultaneously

---

# PART 10 — CSS Grid Fundamentals

## Why Grid Exists

Grid was designed for:

* Page layout
* Complex structures
* Two-dimensional control

Grid complements Flexbox, not replaces it.

---

## Defining a Grid Container

```css
.container {
  display: grid;
}
```

Children become grid items.

---

## Defining Columns

```css
grid-template-columns: 1fr 1fr 1fr;
```

Creates:

* Three equal columns

`fr` = fraction of available space.

---

## Defining Rows

```css
grid-template-rows: auto 1fr auto;
```

Common pattern:

* Header
* Content
* Footer

---

## Grid Gap

```css
gap: 1rem;
```

Controls spacing between rows and columns.

---

## Placing Items Explicitly

```css
.item {
  grid-column: 1 / 3;
  grid-row: 1 / 2;
}
```

Spans columns and rows.

---

## Grid Areas (Readable Layouts)

```css
grid-template-areas:
  "header header"
  "sidebar content"
  "footer footer";
```

Assign areas:

```css
header { grid-area: header; }
```

Extremely readable.

---

## Auto Placement

Grid places items automatically if not explicitly positioned.

This allows:

* Rapid prototyping
* Responsive layouts

---

## When to Use Grid vs Flexbox

Use Flexbox when:

* Laying out items in a line
* Components
* Navigation bars

Use Grid when:

* Structuring the page
* Defining layout regions

---

## Final Mental Model

CSS progression:

* Structure → HTML
* Presentation → CSS
* Layout → Flexbox & Grid

Everything builds on:

* Box model
* Units
* Inheritance
* Cascade


---

# Advanced CSS Selectors — Precision, Relationships, and Intent

## Why Advanced Selectors Matter

Basic selectors answer *what* to style.

Advanced selectors answer:

* *Where* the element exists
* *In relation to what*
* *Under what conditions*

They allow:

* Cleaner HTML
* Fewer classes
* More expressive CSS

Used correctly, they reduce markup clutter.
Used incorrectly, they create fragile styles.

---

## Descendant Selectors (Revisited with Intent)

Syntax:

```css
article p {
  color: #333;
}
```

Meaning:

* Selects **any** `p` inside an `article`
* Depth does not matter

This selector is broad.

Use when:

* Structure is stable
* Styling is semantic, not positional

Avoid when:

* HTML nesting may change

---

## Child Selector

Syntax:

```css
article > p {
  color: #333;
}
```

Meaning:

* Selects `p` elements that are **direct children** of `article`
* Does not select nested paragraphs

HTML:

```html
<article>
  <p>Selected</p>
  <div>
    <p>Not selected</p>
  </div>
</article>
```

Use when:

* Structure is intentional
* You want tight control

---

## Adjacent Sibling Selector

Syntax:

```css
h2 + p {
  margin-top: 0;
}
```

Meaning:

* Selects the **first paragraph immediately following** an `h2`

HTML:

```html
<h2>Title</h2>
<p>Selected</p>
<p>Not selected</p>
```

Common use:

* Typography refinement
* Removing extra spacing after headings

---

## General Sibling Selector

Syntax:

```css
h2 ~ p {
  color: #555;
}
```

Meaning:

* Selects **all** paragraphs that follow an `h2`
* Must share the same parent

More permissive than `+`.

---

## Attribute Selectors

Attribute selectors target elements based on attributes.

Basic form:

```css
input[type="text"] {
  border: 1px solid #ccc;
}
```

This avoids:

* Extra classes
* Redundant markup

---

## Attribute Presence Selector

```css
a[target] {
  color: red;
}
```

Selects:

* All links with a `target` attribute

Useful for:

* External links
* Accessibility cues

---

## Attribute Value Matching

Exact match:

```css
input[type="email"] {
  background: #f9f9f9;
}
```

Starts with:

```css
a[href^="https"] {
  color: green;
}
```

Ends with:

```css
a[href$=".pdf"] {
  font-weight: bold;
}
```

Contains:

```css
a[href*="github"] {
  color: purple;
}
```

These selectors are powerful but should be used carefully.

---

## Class Attribute Pattern Matching

Example:

```css
[class^="btn-"] {
  padding: 0.5em 1em;
}
```

Targets:

* `.btn-primary`
* `.btn-secondary`
* `.btn-danger`

Common in:

* Component libraries
* Utility systems

---

## Pseudo-Classes — State-Based Selection

Pseudo-classes describe **state**, not structure.

Syntax:

```css
selector:pseudo-class
```

---

## Link States

Order matters (LVHA):

```css
a:link
a:visited
a:hover
a:active
```

Correct usage:

```css
a:hover {
  text-decoration: underline;
}
```

Hover should always come after link/visited.

---

## Focus States (Critical for Accessibility)

```css
button:focus {
  outline: 2px solid blue;
}
```

Never remove focus outlines without replacement.

Keyboard users depend on this.

---

## Form State Pseudo-Classes

```css
input:required
input:disabled
input:checked
input:focus
```

Example:

```css
input:checked {
  accent-color: green;
}
```

Allows styling based on user interaction.

---

## Structural Pseudo-Classes

These selectors depend on document structure.

---

## First and Last Child

```css
li:first-child
li:last-child
```

Selects:

* First or last element among siblings

---

## Nth Child (Most Important Structural Selector)

Syntax:

```css
li:nth-child(2)
li:nth-child(even)
li:nth-child(odd)
li:nth-child(3n)
```

Example:

```css
li:nth-child(3n) {
  color: red;
}
```

Selects:

* Every third item

---

## Difference Between `nth-child` and `nth-of-type`

HTML:

```html
<div>
  <p>One</p>
  <span>Two</span>
  <p>Three</p>
</div>
```

```css
p:nth-child(2)       /* not selected */
p:nth-of-type(2)     /* selected */
```

`nth-child` counts **all elements**
`nth-of-type` counts **only that element type**

This distinction prevents many bugs.

---

## Only Child

```css
p:only-child {
  font-style: italic;
}
```

Applies when:

* Element has no siblings

---

## Empty Selector

```css
p:empty {
  display: none;
}
```

Matches:

* Truly empty elements
* No whitespace allowed

---

## Pseudo-Elements — Styling Parts of Elements

Pseudo-elements target **sub-parts**, not states.

Syntax:

```css
selector::pseudo-element
```

Double colon is modern syntax.

---

## `::before` and `::after`

Example:

```css
.button::before {
  content: "→ ";
}
```

Rules:

* `content` is required
* Elements are inline by default

Common uses:

* Icons
* Decorative elements
* Badges

---

## Styling First Line and First Letter

```css
p::first-line {
  font-weight: bold;
}

p::first-letter {
  font-size: 2rem;
}
```

Used for:

* Editorial layouts
* Drop caps

---

## Marker Styling

```css
li::marker {
  color: red;
}
```

Allows:

* Custom bullet styling
* Without removing list semantics

---

## Placeholder Styling

```css
input::placeholder {
  color: #999;
}
```

Improves form clarity.

---

## `:not()` — Exclusion Selector

```css
p:not(.intro) {
  color: #333;
}
```

Selects:

* All paragraphs except `.intro`

Useful for:

* Broad rules with exceptions

---

## `:has()` — Relational Selector (Modern)

Example:

```css
article:has(img) {
  border: 1px solid #ddd;
}
```

Meaning:

* Selects articles **containing** an image

This selector:

* Enables parent-based styling
* Replaces many JS hacks

Support is modern but improving.

---

## Specificity Implications of Advanced Selectors

Selector complexity increases specificity.

Example:

```css
article p.highlight
```

Is more specific than:

```css
.highlight
```

Guideline:

* Prefer simpler selectors
* Add complexity only when necessary

---

## Advanced Selector Philosophy

Selectors should express:

* Meaning
* Structure
* Intent

Avoid selectors that depend on:

* Deep nesting
* Fragile DOM structure

Prefer:

* Semantic HTML
* Light, expressive CSS

---

## Preparing for Component-Based CSS

Advanced selectors become most powerful when combined with:

* Components
* Layout systems
* Design tokens

This naturally leads into:

* CSS architecture
* Naming strategies
* Scoped styles

---
