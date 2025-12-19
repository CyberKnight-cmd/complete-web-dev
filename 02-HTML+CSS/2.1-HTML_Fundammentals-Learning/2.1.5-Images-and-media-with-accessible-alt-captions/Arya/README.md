# Images & Media Accessibility Demo

## Setup Instructions

1. Open `demo.html` in any modern web browser
2. Test with screen readers to hear alt text announcements
3. Use accessibility testing tools to validate implementation
4. Test responsive images by resizing browser window

## Running the Demo

### Basic Viewing
- Open `demo.html` in your browser
- Observe different types of images and media elements
- Notice how alt text and captions are implemented
- Test video controls and caption functionality

### Accessibility Testing

#### Screen Reader Testing
1. **Enable screen reader** (NVDA, JAWS, VoiceOver)
2. **Navigate through images** using screen reader shortcuts
3. **Listen to alt text** announcements
4. **Verify decorative images** are skipped
5. **Test video captions** with screen reader

#### Visual Testing
1. **Disable images** in browser settings
2. **Verify alt text** displays properly
3. **Check layout** doesn't break without images
4. **Test responsive behavior** at different screen sizes

## Key Features Demonstrated

### Image Accessibility
- **Informative images**: Descriptive alt text
- **Decorative images**: Empty alt attribute
- **Functional images**: Alt text describes function
- **Complex images**: Detailed descriptions provided
- **Figure/figcaption**: Proper semantic structure

### Responsive Images
- **srcset attribute**: Multiple image resolutions
- **sizes attribute**: Responsive sizing hints
- **picture element**: Art direction control
- **Lazy loading**: Performance optimization

### Video Accessibility
- **Controls**: User-controlled playback
- **Captions**: Text alternatives for audio
- **Subtitles**: Multiple language support
- **Transcripts**: Full text alternatives
- **Poster images**: Preview thumbnails

### Audio Accessibility
- **Controls**: User-controlled playback
- **Transcripts**: Full text alternatives
- **Multiple formats**: Browser compatibility
- **Fallback content**: Unsupported browser handling

## Testing Procedures

### 1. Alt Text Validation
```bash
# Check all images have alt attributes
# Use browser DevTools or WAVE extension
```

### 2. Screen Reader Testing
- Navigate by images (G key in NVDA)
- Verify alt text is announced correctly
- Check decorative images are skipped
- Test figure captions are associated properly

### 3. Keyboard Accessibility
- Tab to video/audio controls
- Use Space/Enter to play/pause
- Test all control buttons are accessible
- Verify focus indicators are visible

### 4. Caption Testing
- Enable captions on video
- Verify captions sync with audio
- Test multiple language options
- Check caption styling and readability

## Expected Results

### Image Accessibility
- All images have appropriate alt text
- Decorative images have empty alt
- Screen readers announce image content correctly
- Images don't break layout when disabled

### Media Accessibility
- Videos have working captions
- Audio has transcripts available
- Controls are keyboard accessible
- Fallback content works in unsupported browsers

### Performance
- Lazy loading reduces initial page load
- Responsive images serve appropriate sizes
- Modern formats (WebP, AVIF) used when supported
- Media doesn't auto-play unexpectedly

## Common Issues to Avoid

1. **Missing alt attributes** on images
2. **Generic alt text** like "image" or "photo"
3. **Videos without captions** or subtitles
4. **Audio without transcripts**
5. **Auto-playing media** without user control
6. **Missing keyboard accessibility** for controls
7. **Incorrect srcset syntax** for responsive images
8. **No fallback content** for unsupported formats

## Browser Compatibility

- All modern browsers support demonstrated features
- Lazy loading supported in Chrome 76+, Firefox 75+, Safari 15.4+
- WebVTT captions supported in all modern browsers
- Picture element supported in all current browsers

## Tools for Testing

- **WAVE**: Web accessibility evaluation tool
- **axe DevTools**: Accessibility testing extension
- **Lighthouse**: Performance and accessibility audits
- **Screen readers**: NVDA, JAWS, VoiceOver, TalkBack
- **Browser DevTools**: Inspect alt text and attributes