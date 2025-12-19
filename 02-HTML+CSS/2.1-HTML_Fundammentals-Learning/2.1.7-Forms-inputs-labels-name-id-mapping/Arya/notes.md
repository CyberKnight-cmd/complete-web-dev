# Forms (Foundation): Inputs, Labels, Name/ID Mapping - Notes

## Core Concepts

### Form Structure
```html
<form action="/submit" method="post">
    <fieldset>
        <legend>Personal Information</legend>
        
        <label for="name">Full Name:</label>
        <input type="text" id="name" name="fullName" required>
        
        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>
    </fieldset>
    
    <button type="submit">Submit</button>
</form>
```

### Label-Input Association

#### Explicit Labeling (Recommended)
```html
<label for="username">Username:</label>
<input type="text" id="username" name="username">
```

#### Implicit Labeling
```html
<label>
    Username:
    <input type="text" name="username">
</label>
```

### Input Types
```html
<!-- Text inputs -->
<input type="text" name="name">
<input type="email" name="email">
<input type="password" name="password">
<input type="tel" name="phone">
<input type="url" name="website">

<!-- Number inputs -->
<input type="number" name="age" min="0" max="120">
<input type="range" name="rating" min="1" max="5">

<!-- Date/time inputs -->
<input type="date" name="birthdate">
<input type="time" name="appointment">
<input type="datetime-local" name="event">

<!-- Selection inputs -->
<input type="checkbox" name="newsletter" id="newsletter">
<input type="radio" name="size" value="small" id="size-small">
<input type="radio" name="size" value="large" id="size-large">

<!-- File input -->
<input type="file" name="upload" accept=".pdf,.doc">
```

### Form Controls

#### Textarea
```html
<label for="message">Message:</label>
<textarea id="message" name="message" rows="4" cols="50"></textarea>
```

#### Select Dropdown
```html
<label for="country">Country:</label>
<select id="country" name="country">
    <option value="">Choose a country</option>
    <option value="us">United States</option>
    <option value="ca">Canada</option>
    <option value="uk">United Kingdom</option>
</select>
```

#### Fieldset and Legend
```html
<fieldset>
    <legend>Shipping Address</legend>
    <label for="street">Street:</label>
    <input type="text" id="street" name="street">
    
    <label for="city">City:</label>
    <input type="text" id="city" name="city">
</fieldset>
```

### Name/ID Mapping Best Practices

#### Consistent Naming
```html
<!-- Good: Consistent and descriptive -->
<label for="user-email">Email Address:</label>
<input type="email" id="user-email" name="userEmail">

<!-- Bad: Inconsistent -->
<label for="email1">Email:</label>
<input type="email" id="email1" name="user_email_address">
```

#### Radio Button Groups
```html
<fieldset>
    <legend>Preferred Contact Method</legend>
    
    <input type="radio" id="contact-email" name="contactMethod" value="email">
    <label for="contact-email">Email</label>
    
    <input type="radio" id="contact-phone" name="contactMethod" value="phone">
    <label for="contact-phone">Phone</label>
</fieldset>
```

#### Checkbox Groups
```html
<fieldset>
    <legend>Interests</legend>
    
    <input type="checkbox" id="interest-web" name="interests" value="web">
    <label for="interest-web">Web Development</label>
    
    <input type="checkbox" id="interest-mobile" name="interests" value="mobile">
    <label for="interest-mobile">Mobile Development</label>
</fieldset>
```

## Mental Models

### Form Accessibility Flow
1. User encounters form control
2. Screen reader announces label text
3. User understands purpose and requirements
4. User provides input
5. Validation feedback is announced

### Label-Input Relationship
- `for` attribute on label matches `id` on input
- `name` attribute groups related inputs (radio buttons)
- `id` must be unique on page
- `name` can be shared for grouped inputs

## Common Pitfalls

### 1. Missing Labels
```html
<!-- WRONG -->
<input type="text" placeholder="Enter your name">

<!-- CORRECT -->
<label for="name">Name:</label>
<input type="text" id="name" name="name" placeholder="Enter your name">
```

### 2. Incorrect Label Association
```html
<!-- WRONG -->
<label for="email">Email:</label>
<input type="email" id="user-email" name="email">

<!-- CORRECT -->
<label for="user-email">Email:</label>
<input type="email" id="user-email" name="email">
```

### 3. Missing Fieldset for Radio Groups
```html
<!-- WRONG -->
<input type="radio" name="size" value="small" id="small">
<label for="small">Small</label>
<input type="radio" name="size" value="large" id="large">
<label for="large">Large</label>

<!-- CORRECT -->
<fieldset>
    <legend>Size</legend>
    <input type="radio" name="size" value="small" id="small">
    <label for="small">Small</label>
    <input type="radio" name="size" value="large" id="large">
    <label for="large">Large</label>
</fieldset>
```

### 4. Duplicate IDs
```html
<!-- WRONG -->
<input type="text" id="name" name="firstName">
<input type="text" id="name" name="lastName">

<!-- CORRECT -->
<input type="text" id="first-name" name="firstName">
<input type="text" id="last-name" name="lastName">
```

## Best Practices

### Accessibility Guidelines
- Every input must have an associated label
- Use fieldset/legend for grouped inputs
- Provide clear, descriptive labels
- Include required field indicators
- Use appropriate input types for better UX

### Form Validation
```html
<label for="email">Email (required):</label>
<input type="email" 
       id="email" 
       name="email" 
       required 
       aria-describedby="email-error">
<div id="email-error" role="alert"></div>
```

### Progressive Enhancement
```html
<form action="/submit" method="post" novalidate>
    <!-- HTML5 validation with JavaScript fallback -->
    <label for="age">Age:</label>
    <input type="number" id="age" name="age" min="18" max="100" required>
</form>
```