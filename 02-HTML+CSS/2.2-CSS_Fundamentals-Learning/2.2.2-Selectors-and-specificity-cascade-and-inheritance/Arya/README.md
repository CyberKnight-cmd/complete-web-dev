# CSS Selectors & Specificity Demo

## Setup Instructions

1. Open `demo.html` in any modern web browser
2. Open browser DevTools (F12) to inspect computed styles
3. Test interactive elements (hover, focus)
4. Use Elements panel to see specificity in action

## Key Features Demonstrated

### Selector Types
- **Basic selectors**: element, class, ID, universal
- **Attribute selectors**: exact match, contains, starts/ends with
- **Pseudo-classes**: :hover, :focus, :nth-child, :first-child
- **Pseudo-elements**: ::before, ::after
- **Combinators**: descendant, child, adjacent sibling

### Specificity Calculation
- Visual examples with calculated specificity values
- Demonstration of specificity hierarchy
- Interactive table showing calculation breakdown

### Cascade & Inheritance
- Source order demonstration
- Inherited vs non-inherited properties
- Parent-child relationship examples

## Testing Procedures

### DevTools Inspection
1. Right-click any element → Inspect
2. View Styles panel to see:
   - Applied styles and their sources
   - Crossed-out overridden styles
   - Computed values
   - Specificity conflicts

### Interactive Testing
- Hover over elements to see :hover effects
- Click input field to see :focus styles
- Observe structural pseudo-class effects

### Specificity Verification
- Compare elements with different specificity
- Use DevTools to see which styles win
- Test cascade order with same specificity

## Expected Results
- Higher specificity styles override lower ones
- Inline styles have highest specificity
- Later rules win when specificity is equal
- Inherited properties flow from parent to child
- Non-inherited properties (borders, margins) don't inherit