# Changelog

## v2.0.0 — Awwwards-Level Rebuild (2025-02-14)

Complete rewrite of `index.html` — same single-file vanilla JS architecture, same game mechanics, but elevated to award-winning quality.

### 1. Loading Experience
- Beautiful loading screen with animated title reveal (staggered fadeSlideUp)
- Real byte-level progress bar tracking via XMLHttpRequest
- Preloads title assets + first scene image before showing title screen
- Automatically preloads next scene while playing current scene

### 2. Title Screen Polish
- Warmer, more refined typography spacing (increased letter-spacing, margins)
- Subtle parallax effect on background (mouse-responsive, desktop only)
- Floating animation on the yellow machine circle
- "10 SCENES" subtitle on start button
- Enhanced box-shadow for realistic paper depth
- Smooth fade-in transition from loading screen

### 3. Open Graph & Twitter Card Meta
- Full `og:title`, `og:description`, `og:image`, `og:url`, `og:type`, `og:site_name`
- Twitter `summary_large_image` card with all fields
- `meta description` for SEO
- `theme-color` meta tag

### 4. Inline SVG Favicon
- Gold `?` icon as data URI SVG — no external file needed
- Works across all modern browsers

### 5. Scene Transitions
- Warm cream crossfade overlay between scenes (CSS opacity transition)
- 450ms fade out → scene swap → fade in
- Transition sound effect (whoosh)

### 6. Hit/Miss Feedback
- **Found**: Dual gold ring pulse animation, 100-particle gold confetti burst, ascending chime sound, "FOUND!" banner with spring animation
- **Miss**: Expanding ripple + rotating ✕ mark with subtle thud sound
- Confetti uses physics simulation (gravity, drag, rotation, opacity decay)

### 7. Sound Design (Web Audio API)
- All sounds synthesized — zero external audio files
- **Find**: Bright ascending C5→E5→G5→C6 chime
- **Miss**: Low-frequency noise thud
- **Transition**: Bandpass-filtered noise sweep (whoosh)
- **UI clicks**: Subtle sine pop
- **End celebration**: Happy ascending arpeggio
- Mute toggle button (bottom-left, persists during session)

### 8. End Screen
- Frosted glass backdrop (backdrop-filter blur)
- Results card with slide-up entrance animation
- All scene times with emoji icons and aligned layout
- Total time prominently displayed with label
- **Share button**: Uses `navigator.share()` on mobile, clipboard fallback on desktop
- Generates formatted share text with emojis and play link
- Confirmation toast on copy
- Play Again button

### 9. Mobile Polish
- `viewport-fit=cover` for edge-to-edge on notched devices
- Safe area insets (env() CSS) on HUD, buttons
- Improved touch pan+zoom: simultaneous pan during pinch gesture
- `-webkit-tap-highlight-color: transparent`
- Responsive breakpoints for small screens (<480px)

### 10. Micro-interactions
- Crosshair cursor on game area, grabbing cursor when dragging
- Hover states on all buttons (color shifts, border highlights)
- Start button press effect (translateY + shadow reduction)
- Scene progress dots with pulse animation on current scene
- Smooth transitions on all interactive elements
- Spring easing on "FOUND!" banner (cubic-bezier overshoot)

### 11. Hint System
- Directional vignette overlay pointing toward machine area
- Uses radial-gradient positioned at machine's screen coordinates
- Progressive intensity: each hint click darkens further (0.15 → 0.23 → 0.31...)
- Auto-fades after 3 seconds
- Still pans 30% toward machine on each click

### 12. Performance
- `requestAnimationFrame` for all animations (game loop, confetti)
- Debounced resize handler (100ms)
- `will-change: transform` on scene canvas
- Image preloading with `URL.createObjectURL` for efficient memory
- Confetti canvas uses device pixel ratio for crisp rendering
- Lazy scene loading — only loads what's needed + next

### 13. Accessibility
- Semantic HTML: `<header>`, `<main>`, `<h1>`, `role="dialog"`, `role="application"`
- ARIA labels on all interactive elements and regions
- `aria-live="polite"` on scene name, `aria-live="assertive"` on found banner
- `role="progressbar"` with `aria-valuenow` on loading bar
- `aria-modal="true"` on end screen dialog
- `focus-visible` styles on all buttons (gold ring)
- `prefers-reduced-motion: reduce` — disables all animations and transitions
- Tab-accessible floating buttons

### Architecture
- Same single-file vanilla JS — no build tools, no dependencies, no frameworks
- CSS custom properties for all colors and design tokens
- Clean section organization with comment headers
- `'use strict'` mode
- All original scene data, coordinates, and file paths preserved exactly
