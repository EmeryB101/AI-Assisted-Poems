# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI-Assisted-Poems is a creative/artistic portfolio exploring AI as a digital companion to creative works. The project showcases three distinct poem types (erasure, visual, and interactive/kinetic) created through collaboration with Claude Code. This is NOT a traditional software application - it's a collection of self-contained HTML files with embedded CSS animations and JavaScript visual effects.

## Project Structure

```
AI-Assisted-Poems/
├── index.html               # Landing page with artist statement and poem navigation
├── erasure_poem (1).html    # "Connected/Disconnected" erasure poem (cyberpunk theme)
├── visual_poem.html         # "Songs of Digital Innocence Lost" visual poem (vintage theme)
├── interactive_poem.html    # "When Pixels Cry" interactive/kinetic poem (terminal theme)
└── README.md                # Project title only
```

**Important**: `erasure_poem (1).html` has a space and parentheses in the filename. Always use quotes when referencing it in commands: `"erasure_poem (1).html"`

## Site Architecture

### index.html - Portfolio Landing Page
- **Purpose**: Entry point showcasing the artist statement and providing navigation to poems
- **Design**: Cyberpunk aesthetic with glowing card-based navigation
- **Content**:
  - Artist statement explaining AI-human collaboration in creative work
  - Two interactive poem cards with hover effects
  - Direct links (not iframes) to individual poems
- **External Font**: Uses Google Fonts (Cinzel) for headings
- **Navigation**: Click cards to view individual poems

### erasure_poem (1).html - Erasure Poem
- **Theme**: "Connected/Disconnected" - commentary on digital technology and human connection
- **Design**: Cyberpunk aesthetic (cyan #00d4ff, magenta #ff006e, purple #7b2cbf)
- **Structure**:
  - Phone-shaped container with bezels and home button
  - Kept words displayed in magenta inside the phone screen
  - Full original text below in faded strikethrough (hover to reveal)
  - Matrix rain background effect (Canvas API)
  - Multiple animated decorative elements
- **Note**: Artist statement appears ONLY on index.html, not on this page
- **Accessibility**: Full WCAG 2.1 AA compliance with ARIA labels, semantic HTML, skip links

### visual_poem.html - Visual Poem
- **Theme**: "Songs of Digital Innocence Lost" - William Blake inspired, digital age commentary
- **Design**: Vintage parchment aesthetic with ornate borders
- **Structure**:
  - Ornate corner decorations with circular accents
  - Central empty swing as metaphor (SVG with proper title/desc tags)
  - Animated falling leaves
  - Quote: "In every cry of every Man, In every Infant's cry of fear..."
- **External Font**: Uses Google Fonts (Cinzel, Crimson Text)
- **Animation**: CSS-based falling leaf animation with staggered delays
- **Accessibility**: Full WCAG 2.1 AA compliance with SVG descriptions, ARIA labels, semantic HTML

### interactive_poem.html - Interactive/Kinetic Poem
- **Theme**: "When Pixels Cry" - childhood and technology, digital disconnection
- **Design**: Terminal/command line aesthetic with dark navy background
- **Structure**:
  - ASCII art crying emoji face
  - Sequential text reveal animations (lines appear one by one)
  - Color-coded keywords: blue-light (cyan), corrupted/emptiness (red), love (yellow)
  - Loading bar animations and cursor effects
  - Glitch effects on hover
  - Final error message: "Connection.exe has failed."
- **External Font**: Uses Google Fonts (Courier Prime)
- **Animation**: JavaScript-driven sequential reveals, CSS loading bars, glitch effects, cursor blinking
- **Interactivity**: Lines appear in timed sequence, hover triggers glitch effects
- **Accessibility**: Full WCAG 2.1 AA compliance with ARIA labels, semantic HTML, screen reader descriptions

## Development Workflow

### Viewing the Site Locally

**Recommended: Use a local server**
```bash
python3 -m http.server 8000
# Then navigate to: http://localhost:8000/
```

**Alternative: Open files directly**
```bash
# Linux
xdg-open index.html

# macOS
open index.html
```

Note: The local server method is recommended to ensure all fonts and resources load correctly, though the site is designed to work when opening files directly.

### Testing Changes

No automated tests exist. To verify changes:

1. **Landing Page (index.html)**:
   - Verify artist statement is readable
   - Test hover effects on poem cards
   - Click links to ensure navigation works
   - Check responsive behavior at different screen sizes

2. **Erasure Poem**:
   - Verify Matrix rain background animates smoothly
   - Test hover on erased text to reveal original content
   - Check phone container displays correctly
   - Ensure all animations (glitch, pulse, flicker) work

3. **Visual Poem**:
   - Verify falling leaves animate continuously
   - Check ornate corners display properly
   - Ensure fonts load correctly
   - Test on different screen sizes

4. **Interactive Poem**:
   - Verify lines appear sequentially with correct timing
   - Test loading bar animations
   - Check cursor blinking effect
   - Hover over text to test glitch effects
   - Ensure color-coded keywords display correctly
   - Verify final error message appears after all lines

### Accessibility Testing

All pages meet WCAG 2.1 AA standards for electronic literature submission. Test with:

1. **Keyboard Navigation**:
   - Press Tab to navigate through interactive elements
   - Skip-to-content link appears on first Tab press
   - All links have visible focus indicators (cyan/brown outlines)
   - Enter key activates links

2. **Screen Reader Testing**:
   - Use NVDA (Windows), JAWS (Windows), or VoiceOver (Mac)
   - All images and visual elements have descriptive labels
   - Decorative elements are properly hidden (aria-hidden="true")
   - Semantic HTML provides clear document structure

3. **What You'll See vs. What's Hidden**:
   - **Visible**: Focus outlines when tabbing, same visual design
   - **Hidden to sighted users**: Skip links (until focused), screen-reader-only descriptions
   - **For screen readers**: Descriptive text explaining visual elements, poem structure, interaction instructions

## Technical Architecture

### Shared Design Philosophy
- **No Build Process**: All files are static HTML with embedded CSS/JS
- **No Dependencies**: Vanilla HTML/CSS/JavaScript (except Google Fonts CDN)
- **Self-Contained**: Each poem works independently
- **No Package Manager**: No npm, pip, or other tooling required

### CSS Patterns
- **Erasure Poem**: Cyberpunk theme with heavy use of glow effects, cyan/magenta/purple palette
- **Visual Poem**: Vintage parchment theme with browns/tans, serif fonts
- **Both**: Extensive use of CSS animations, positioned elements, custom keyframes

### JavaScript
- **Erasure Poem**: Canvas-based Matrix rain effect (binary + Japanese katakana)
- **Visual Poem**: Pure CSS animations (no JavaScript)
- **Interactive Poem**: Sequential text reveal animations using DOM manipulation and setTimeout
- **Landing Page**: No JavaScript required

## Making Changes

### Modifying the Landing Page (index.html)
- **Artist Statement**: Search for `<section class="artist-statement"`
- **Poem Cards**: Search for `<article class="poem-card">`
- **Styling**: All styles in the `<style>` tag in `<head>`

### Modifying the Erasure Poem
- **Poem Text**: Search for `<div style="display: inline-block; border-left: 3px solid #00d4ff"` (phone screen container)
- **Erased Context**: Search for `<section style="margin-top: 60px"` (below phone)
- **Animations**: Look for `@keyframes` definitions in the `<style>` section
- **Matrix Effect**: Modify `drawMatrix()` function in the `<script>` tag
- **Note**: Do NOT add artist statement to this page - it should only appear on index.html

### Modifying the Visual Poem
- **Main Content**: Search for `<article class="main-content"`
- **Swing SVG**: Search for `<svg class="swing"`
- **Falling Leaves**: Search for `<div class="leaf"` (adjust count by adding/removing)
- **Quote**: Search for `<blockquote class="quote"`

### Modifying the Interactive Poem
- **Poem Lines**: Search for `<div class="line"` (each line has a data-delay attribute)
- **Animation Timing**: Modify `data-delay` attributes to adjust when lines appear
- **Color Keywords**: Search for class names: `blue-text`, `red-text`, `yellow-text`, `highlight`
- **ASCII Emoji**: Search for `<div class="emoji-face"`
- **Error Message**: Search for `<footer class="error-message"`
- **JavaScript**: Sequential animation logic at bottom in `<script>` tag

### Color Scheme Changes
- **Erasure Poem**: Search for hex codes: `#00d4ff` (cyan), `#ff006e` (magenta), `#7b2cbf` (purple)
- **Visual Poem**: Search for hex codes: `#8b7355` (brown), `#b8a489` (tan), `#5a4a3a` (dark brown)
- **Interactive Poem**: Search for hex codes: `#5dade2` (cyan/blue), `#e74c3c` (red), `#f1c40f` (yellow/gold)

## Git Workflow

When committing changes:
```bash
# Add files (use quotes for the erasure poem filename)
git add index.html "erasure_poem (1).html" visual_poem.html interactive_poem.html

# Commit with descriptive message
git commit -m "Your descriptive message"

# Push to current branch
git push -u origin <current-branch-name>
```

Always verify your current branch with `git branch` before pushing.

## Deployment Notes

This site is designed to work on:
- **GitHub Pages**: All files use relative paths
- **Local file system**: Can open index.html directly
- **Any static web host**: No server-side processing required

The landing page uses direct `<a href>` links instead of iframes to ensure compatibility across all hosting environments.

## Browser Compatibility

Requires a modern browser with support for:
- CSS Grid and Flexbox
- CSS animations and keyframes
- Canvas API (for Matrix effect in erasure poem)
- SVG (for swing in visual poem)
- External font loading (Google Fonts CDN)
