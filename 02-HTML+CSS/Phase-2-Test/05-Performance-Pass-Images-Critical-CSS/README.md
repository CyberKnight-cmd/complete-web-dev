# Performance Pass (Images & Critical CSS)

## Challenge Overview
Deliver a complete artifact for 'Performance Pass (Images & Critical CSS)'. Optimize images and implement critical CSS inlining for above-the-fold content to achieve optimal loading performance.

## Objective
Implement comprehensive performance optimizations focusing on image compression, format selection, and critical CSS extraction to minimize initial page load times.

## Requirements

### Core Deliverables
- [ ] Image compression and optimization
- [ ] Responsive image implementation
- [ ] Critical CSS extraction and inlining
- [ ] Above-the-fold content prioritization
- [ ] Lazy loading for below-the-fold images
- [ ] Performance budget compliance

### Technical Specifications
- [ ] WebP/AVIF format support with fallbacks
- [ ] Responsive images with srcset
- [ ] Critical CSS under 14KB
- [ ] Image compression >70% size reduction
- [ ] Core Web Vitals optimization
- [ ] Resource loading prioritization

### Edge Cases & Error Handling
- [ ] Slow network connection handling
- [ ] Image loading failure fallbacks
- [ ] Critical CSS extraction errors
- [ ] Browser compatibility for modern formats
- [ ] Progressive enhancement for performance features

## File Structure
```
05-Performance-Pass-Images-Critical-CSS/
├── README.md
├── images/
│   ├── original/
│   ├── optimized/
│   └── formats/
├── css/
│   ├── critical.css
│   ├── non-critical.css
│   └── inline-critical.html
├── tools/
│   ├── image-optimizer.js
│   └── critical-css-extractor.js
├── performance-reports/
└── tests/
```

## Acceptance Criteria
- Submit repository link
- README with setup/run instructions
- Before/after performance screenshots
- Lighthouse performance reports
- Image optimization metrics

## Constraints
- Deterministic performance improvements
- Graceful degradation for older browsers
- Automated performance testing
- Budget constraints for resource sizes