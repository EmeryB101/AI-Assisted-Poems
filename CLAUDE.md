# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI-Assisted-Poems is a creative/artistic portfolio exploring AI as a digital companion to creative works. The project showcases multiple poem types (erasure and visual) created through collaboration with Claude Code. This is NOT a traditional software application - it's a collection of self-contained HTML files with embedded CSS animations and JavaScript visual effects.

## Project Structure

```
AI-Assisted-Poems/
├── index.html               # Landing page with artist statement and poem navigation
├── erasure_poem (1).html    # "Connected/Disconnected" erasure poem (cyberpunk theme)
├── visual_poem.html         # "Songs of Digital Innocence Lost" visual poem (vintage theme)
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
- **Artist Statement**: Now includes the artist statement at the top
- **Lines of Interest**:
  - CSS: lines 7-422
  - Artist Statement: lines 415-422
  - Poem Content: lines 424-508
  - JavaScript (Matrix effect): lines 526-572

### visual_poem.html - Visual Poem
- **Theme**: "Songs of Digital Innocence Lost" - William Blake inspired, digital age commentary
- **Design**: Vintage parchment aesthetic with ornate borders
- **Structure**:
  - Ornate corner decorations with circular accents
  - Central empty swing as metaphor (SVG)
  - Animated falling leaves
  - Quote: "In every cry of every Man, In every Infant's cry of fear..."
- **External Font**: Uses Google Fonts (Cinzel, Crimson Text)
- **Animation**: CSS-based falling leaf animation with staggered delays

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
- **Landing Page**: No JavaScript required

## Making Changes

### Modifying the Landing Page (index.html)
- **Artist Statement**: lines 235-242
- **Poem Cards**: lines 244-256
- **Styling**: Inline in `<style>` tag, lines 7-228

### Modifying the Erasure Poem
- **Artist Statement**: lines 415-422
- **Poem Text**: lines 426-486 (inside phone screen container)
- **Erased Context**: lines 497-507 (below phone)
- **Animations**: Look for `@keyframes` definitions
- **Matrix Effect**: Modify `drawMatrix()` function (lines 543-564)

### Modifying the Visual Poem
- **Main Content**: lines 232-257 (title, word "AGAIN?", swing, quote)
- **Swing SVG**: lines 248-253
- **Falling Leaves**: lines 237-241 (adjust count by adding/removing `<div class="leaf"></div>`)
- **Ornate Borders**: lines 233-235 (corner decorations)

### Color Scheme Changes
- **Erasure Poem**: Search for hex codes: `#00d4ff` (cyan), `#ff006e` (magenta), `#7b2cbf` (purple)
- **Visual Poem**: Search for hex codes: `#8b7355` (brown), `#b8a489` (tan), `#5a4a3a` (dark brown)

## Git Workflow

When committing changes:
```bash
# Add files (use quotes for the erasure poem filename)
git add index.html "erasure_poem (1).html" visual_poem.html

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
