# Keyboard & Focus Order Implementation Challenge

## Problem Statement

Build a production-ready interactive web application that demonstrates perfect keyboard accessibility, including logical focus order, visible focus indicators, and comprehensive keyboard navigation patterns for all interactive elements.

## Requirements

### Core Implementation
Create a complex interactive interface that includes:

1. **Interactive Components** (All must be keyboard accessible)
   - **Navigation menu** with dropdowns/submenus
   - **Modal dialogs** with focus trapping
   - **Tab panels** with arrow key navigation
   - **Custom dropdown** select components
   - **Image carousel** with keyboard controls
   - **Form elements** with validation
   - **Data table** with sortable columns
   - **Accordion** expand/collapse sections

2. **Focus Management Patterns**
   - **Logical tab order** following visual layout
   - **Focus trapping** in modal dialogs
   - **Focus restoration** when closing modals
   - **Skip links** for efficient navigation
   - **Roving tabindex** for component groups
   - **Focus indicators** visible and high contrast

3. **Keyboard Interaction Standards**
   - **Tab/Shift+Tab**: Navigate between focusable elements
   - **Enter/Space**: Activate buttons and links
   - **Arrow keys**: Navigate within component groups
   - **Escape**: Close modals, dropdowns, menus
   - **Home/End**: Jump to first/last items
   - **Page Up/Down**: Navigate large content areas

### Technical Constraints

- **No Framework Dependencies**: Pure HTML/CSS/JavaScript
- **WCAG 2.1 AA**: Meet all keyboard accessibility criteria
- **Cross-browser**: Chrome, Firefox, Safari, Edge support
- **Screen Reader Compatible**: Works with NVDA, JAWS, VoiceOver
- **Performance**: Smooth focus transitions under 100ms

### Accessibility Requirements

- **Visible Focus**: High contrast focus indicators (3:1 minimum)
- **Focus Order**: Logical sequence matching visual layout
- **Focus Trapping**: Contained within modal contexts
- **Keyboard Shortcuts**: Standard interaction patterns
- **Screen Reader**: Proper announcements and navigation

## Input Specifications

Create these files:
- `index.html` - Main interactive interface
- `keyboard-nav.js` - Focus management and keyboard handlers
- `styles.css` - Focus indicators and component styling
- `README.md` - Keyboard interaction documentation

## Expected Output

### Focus Indicator Implementation
```css
/* High contrast focus indicators */
:focus {
    outline: 3px solid #005fcc;
    outline-offset: 2px;
}

/* Custom focus for different components */
button:focus {
    outline: 3px solid #005fcc;
    outline-offset: 2px;
    box-shadow: 0 0 0 1px #ffffff;
}

.custom-dropdown:focus {
    border: 2px solid #005fcc;
    box-shadow: 0 0 0 1px #ffffff, 0 0 0 3px #005fcc;
}

/* Skip link styling */
.skip-link {
    position: absolute;
    top: -40px;
    left: 6px;
    background: #000;
    color: #fff;
    padding: 8px;
    text-decoration: none;
    border-radius: 4px;
    z-index: 1000;
}

.skip-link:focus {
    top: 6px;
}
```

### Modal Focus Trapping
```javascript
class ModalFocusTrap {
    constructor(modalElement) {
        this.modal = modalElement;
        this.focusableElements = this.getFocusableElements();
        this.firstFocusable = this.focusableElements[0];
        this.lastFocusable = this.focusableElements[this.focusableElements.length - 1];
        this.previouslyFocused = document.activeElement;
    }
    
    getFocusableElements() {
        const selectors = [
            'button:not([disabled])',
            'input:not([disabled])',
            'select:not([disabled])',
            'textarea:not([disabled])',
            'a[href]',
            '[tabindex]:not([tabindex="-1"])'
        ].join(', ');
        
        return Array.from(this.modal.querySelectorAll(selectors));
    }
    
    trapFocus(event) {
        if (event.key !== 'Tab') return;
        
        if (event.shiftKey) {
            // Shift + Tab
            if (document.activeElement === this.firstFocusable) {
                event.preventDefault();
                this.lastFocusable.focus();
            }
        } else {
            // Tab
            if (document.activeElement === this.lastFocusable) {
                event.preventDefault();
                this.firstFocusable.focus();
            }
        }
    }
    
    activate() {
        this.modal.addEventListener('keydown', this.trapFocus.bind(this));
        this.firstFocusable.focus();
    }
    
    deactivate() {
        this.modal.removeEventListener('keydown', this.trapFocus.bind(this));
        this.previouslyFocused.focus();
    }
}
```

### Tab Panel Navigation
```javascript
class TabPanel {
    constructor(container) {
        this.container = container;
        this.tabs = container.querySelectorAll('[role="tab"]');
        this.panels = container.querySelectorAll('[role="tabpanel"]');
        this.currentIndex = 0;
        
        this.setupKeyboardNavigation();
        this.setupTabIndex();
    }
    
    setupKeyboardNavigation() {
        this.tabs.forEach((tab, index) => {
            tab.addEventListener('keydown', (event) => {
                switch (event.key) {
                    case 'ArrowRight':
                        event.preventDefault();
                        this.focusTab((index + 1) % this.tabs.length);
                        break;
                    case 'ArrowLeft':
                        event.preventDefault();
                        this.focusTab((index - 1 + this.tabs.length) % this.tabs.length);
                        break;
                    case 'Home':
                        event.preventDefault();
                        this.focusTab(0);
                        break;
                    case 'End':
                        event.preventDefault();
                        this.focusTab(this.tabs.length - 1);
                        break;
                    case 'Enter':
                    case ' ':
                        event.preventDefault();
                        this.activateTab(index);
                        break;
                }
            });
        });
    }
    
    setupTabIndex() {
        this.tabs.forEach((tab, index) => {
            tab.setAttribute('tabindex', index === 0 ? '0' : '-1');
        });
    }
    
    focusTab(index) {
        this.tabs[this.currentIndex].setAttribute('tabindex', '-1');
        this.tabs[index].setAttribute('tabindex', '0');
        this.tabs[index].focus();
        this.currentIndex = index;
    }
    
    activateTab(index) {
        // Update ARIA states
        this.tabs.forEach((tab, i) => {
            tab.setAttribute('aria-selected', i === index ? 'true' : 'false');
        });
        
        this.panels.forEach((panel, i) => {
            panel.hidden = i !== index;
        });
        
        this.currentIndex = index;
    }
}
```

### Dropdown Menu Navigation
```javascript
class DropdownMenu {
    constructor(trigger, menu) {
        this.trigger = trigger;
        this.menu = menu;
        this.menuItems = menu.querySelectorAll('[role="menuitem"]');
        this.currentIndex = -1;
        this.isOpen = false;
        
        this.setupEventListeners();
    }
    
    setupEventListeners() {
        this.trigger.addEventListener('keydown', (event) => {
            switch (event.key) {
                case 'Enter':
                case ' ':
                case 'ArrowDown':
                    event.preventDefault();
                    this.openMenu();
                    this.focusFirstItem();
                    break;
                case 'ArrowUp':
                    event.preventDefault();
                    this.openMenu();
                    this.focusLastItem();
                    break;
            }
        });
        
        this.menu.addEventListener('keydown', (event) => {
            switch (event.key) {
                case 'ArrowDown':
                    event.preventDefault();
                    this.focusNextItem();
                    break;
                case 'ArrowUp':
                    event.preventDefault();
                    this.focusPreviousItem();
                    break;
                case 'Home':
                    event.preventDefault();
                    this.focusFirstItem();
                    break;
                case 'End':
                    event.preventDefault();
                    this.focusLastItem();
                    break;
                case 'Escape':
                    event.preventDefault();
                    this.closeMenu();
                    this.trigger.focus();
                    break;
                case 'Tab':
                    this.closeMenu();
                    break;
            }
        });
    }
    
    openMenu() {
        this.isOpen = true;
        this.menu.hidden = false;
        this.trigger.setAttribute('aria-expanded', 'true');
    }
    
    closeMenu() {
        this.isOpen = false;
        this.menu.hidden = true;
        this.trigger.setAttribute('aria-expanded', 'false');
        this.currentIndex = -1;
    }
    
    focusFirstItem() {
        this.currentIndex = 0;
        this.menuItems[0].focus();
    }
    
    focusLastItem() {
        this.currentIndex = this.menuItems.length - 1;
        this.menuItems[this.currentIndex].focus();
    }
    
    focusNextItem() {
        this.currentIndex = (this.currentIndex + 1) % this.menuItems.length;
        this.menuItems[this.currentIndex].focus();
    }
    
    focusPreviousItem() {
        this.currentIndex = (this.currentIndex - 1 + this.menuItems.length) % this.menuItems.length;
        this.menuItems[this.currentIndex].focus();
    }
}
```

## Test Cases

### Test Case 1: Tab Order Validation
```javascript
// Automated tab order testing
function validateTabOrder() {
    const focusableElements = document.querySelectorAll(
        'button:not([disabled]), input:not([disabled]), select:not([disabled]), ' +
        'textarea:not([disabled]), a[href], [tabindex]:not([tabindex="-1"])'
    );
    
    const tabOrder = Array.from(focusableElements).map(el => ({
        element: el,
        tabIndex: el.tabIndex,
        rect: el.getBoundingClientRect()
    }));
    
    // Check for logical visual order
    return validateVisualTabOrder(tabOrder);
}
```

### Test Case 2: Focus Indicator Visibility
```javascript
// Test focus indicator contrast
function testFocusIndicators() {
    const focusableElements = document.querySelectorAll('[tabindex]:not([tabindex="-1"])');
    
    focusableElements.forEach(element => {
        element.focus();
        const styles = getComputedStyle(element, ':focus');
        const outlineColor = styles.outlineColor;
        const backgroundColor = styles.backgroundColor;
        
        // Test contrast ratio
        const contrast = calculateContrast(outlineColor, backgroundColor);
        console.assert(contrast >= 3, `Focus indicator contrast too low: ${contrast}`);
    });
}
```

### Test Case 3: Keyboard Navigation Patterns
```
# Manual testing checklist
## Navigation Menu
- [ ] Tab reaches menu trigger
- [ ] Enter/Space opens menu
- [ ] Arrow keys navigate menu items
- [ ] Escape closes menu and returns focus
- [ ] Tab moves to next focusable element

## Modal Dialog
- [ ] Focus moves to modal when opened
- [ ] Tab cycles within modal only
- [ ] Escape closes modal
- [ ] Focus returns to trigger element

## Tab Panel
- [ ] Arrow keys navigate between tabs
- [ ] Enter/Space activates tab
- [ ] Tab moves into panel content
- [ ] Home/End jump to first/last tab
```

## Acceptance Criteria

### Focus Management ✅
- [ ] Logical tab order follows visual layout
- [ ] Focus indicators visible and high contrast (3:1 minimum)
- [ ] Focus trapping works in modal contexts
- [ ] Focus restoration after modal close
- [ ] Skip links provide navigation shortcuts

### Keyboard Interaction ✅
- [ ] All interactive elements keyboard accessible
- [ ] Standard keyboard shortcuts implemented
- [ ] Arrow key navigation in component groups
- [ ] Escape key closes overlays and menus
- [ ] Enter/Space activates buttons and links

### Component Accessibility ✅
- [ ] Modal dialogs trap focus properly
- [ ] Dropdown menus navigate with arrow keys
- [ ] Tab panels use roving tabindex
- [ ] Accordion sections keyboard accessible
- [ ] Data tables support keyboard sorting

### Screen Reader Support ✅
- [ ] Focus changes announced properly
- [ ] Component states communicated clearly
- [ ] Keyboard shortcuts don't interfere with screen reader
- [ ] Navigation landmarks work with keyboard
- [ ] Error states announced when focused

## Detailed Testing Scenarios

### Scenario 1: Modal Dialog Workflow
```
User Journey: Open modal, interact with form, close modal

Steps:
1. Tab to "Open Modal" button
2. Press Enter to open modal
3. Verify focus moves to modal
4. Tab through modal form fields
5. Verify focus stays within modal
6. Press Escape to close modal
7. Verify focus returns to trigger button

Success Criteria:
- Focus never leaves modal when open
- All form fields accessible via Tab
- Escape key closes modal
- Focus restoration works correctly
```

### Scenario 2: Complex Navigation Menu
```
User Journey: Navigate multi-level menu with keyboard

Steps:
1. Tab to main navigation
2. Use arrow keys to navigate menu items
3. Press Enter to open submenu
4. Use arrow keys in submenu
5. Press Escape to close submenu
6. Continue navigation

Success Criteria:
- Arrow keys work in both directions
- Enter opens submenus
- Escape closes current level
- Focus indicators always visible
```

## Performance Requirements

- **Focus Transitions**: Under 100ms response time
- **Visual Feedback**: Immediate focus indicator display
- **Smooth Animation**: 60fps for focus transitions
- **Memory Usage**: No memory leaks from event listeners

## Bonus Challenges

1. **Custom Focus Indicators**: Unique styling per component type
2. **Focus History**: Remember and restore complex focus states
3. **Keyboard Shortcuts**: Global application shortcuts
4. **Touch Integration**: Keyboard accessibility on touch devices
5. **High Contrast Mode**: Optimize for Windows High Contrast

## Common Issues to Avoid

- Invisible or low-contrast focus indicators
- Illogical tab order
- Focus traps that can't be escaped
- Missing keyboard shortcuts for complex components
- Focus indicators that break component layout
- Inconsistent keyboard interaction patterns
- Focus lost when content updates dynamically

## Submission Format

```
keyboard-focus-challenge/
├── index.html              # Main interactive interface
├── keyboard-nav.js         # Focus management logic
├── styles.css              # Focus indicators and styling
├── components/             # Individual component files
│   ├── modal.js
│   ├── dropdown.js
│   ├── tabs.js
│   └── accordion.js
├── test-results/           # Testing documentation
│   ├── keyboard-testing.md
│   ├── focus-order-test.md
│   └── screen-reader-test.md
├── screenshots/            # Visual documentation
│   ├── focus-indicators.png
│   ├── modal-focus-trap.png
│   └── navigation-flow.png
└── README.md              # Keyboard interaction guide
```