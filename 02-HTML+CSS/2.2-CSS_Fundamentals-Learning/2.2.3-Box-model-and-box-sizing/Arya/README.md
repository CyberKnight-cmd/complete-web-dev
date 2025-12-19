# CSS Box Model & Box-Sizing Demo

## Setup Instructions

1. Open `demo.html` in any modern web browser
2. Open browser DevTools (F12) to inspect box model
3. Use Elements panel to see box model visualization
4. Resize browser window to test responsive boxes

## Key Features Demonstrated

### Box Model Components
- **Content**: The actual content area
- **Padding**: Space between content and border
- **Border**: Line around padding and content
- **Margin**: Space outside the border

### Box-Sizing Property
- **content-box**: Width/height apply to content only (default)
- **border-box**: Width/height include padding and border

### Margin Collapse
- Adjacent vertical margins collapse into single margin
- Demonstration of when and how collapse occurs

### Responsive Constraints
- min-width, max-width usage
- Responsive box behavior
- Border-box for predictable sizing

## Testing Procedures

### DevTools Box Model Inspection
1. Right-click any element → Inspect
2. Look at Styles panel (bottom right)
3. See box model diagram with colors:
   - Blue: Content
   - Green: Padding
   - Yellow: Border
   - Orange: Margin

### Dimension Calculation
- Measure content-box vs border-box differences
- Verify total widths match expected calculations
- Test margin collapse behavior

### Responsive Testing
- Resize browser window
- Observe responsive box adaptation
- Verify min/max constraints work

## Expected Results
- Content-box: Total width = width + padding + border
- Border-box: Total width = width (includes padding/border)
- Margin collapse: Larger margin wins, not sum
- DevTools shows accurate box model visualization