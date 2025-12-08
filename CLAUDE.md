# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

AI-Assisted-Poems is a creative/artistic project featuring an interactive erasure poem titled "Connected/Disconnected". This is NOT a traditional software application - it's a single self-contained HTML file with embedded CSS animations and JavaScript visual effects.

## Project Structure

```
AI-Assisted-Poems/
├── erasure_poem (1).html    # Main (and only) project file
└── README.md                # Project title only
```

**Note**: The HTML filename contains a space and parentheses. When referencing it in commands, use quotes: `"erasure_poem (1).html"`

## Development Workflow

### Viewing the Poem

Open the HTML file directly in any modern web browser:

```bash
# Linux/macOS
xdg-open "erasure_poem (1).html"
open "erasure_poem (1).html"

# Or use a local server for more realistic testing
python3 -m http.server 8000
# Then navigate to: http://localhost:8000/erasure_poem%20(1).html
```

### Testing Changes

No automated tests exist. To verify changes:
1. Open the HTML file in a browser
2. Manually test visual effects (animations, hover states, Matrix background)
3. Check responsive behavior by resizing the browser window
4. Verify all text is readable and animations perform smoothly

## Technical Architecture

### HTML Structure
- Phone-shaped container with top/bottom bezels and a home button
- Poem text divided into stanzas inside the phone screen
- Erased context displayed below the phone in faded, strikethrough text
- Decorative elements: pixel corners, data streams, grid overlay

### CSS Architecture
- **Animations**: 10+ keyframe animations (glitch, flicker, pulse, fade-in, scanning effects)
- **Color Palette**: Cyberpunk theme with cyan (#00d4ff), magenta (#ff006e), purple (#7b2cbf)
- **Effects**: Glow shadows, gradients, opacity transitions, text effects
- **Responsive**: Flexbox-based centering, fixed max-width container

### JavaScript
- **Matrix Rain Effect**: Canvas-based background animation using binary digits and Japanese katakana
- **Character Set**: `'01アイウエオカキクケコサシスセソタチツテトナニヌネノハヒフヘホマミムメモヤユヨラリルレロワヲン'`
- **Resize Handling**: Canvas automatically adjusts to window dimensions

## Making Changes

When modifying the HTML file:

1. **CSS Changes**: All styles are in the `<style>` tag in the `<head>` section (lines 7-396)
2. **Poem Content**: Located in the `.poem` div (lines 415-508)
3. **Visual Effects**: JavaScript for Matrix rain is at the bottom (lines 526-572)

### Common Modifications

**Adjusting animations**: Look for `@keyframes` definitions in the CSS section

**Changing colors**: Update hex values in the CSS (current theme: cyan, magenta, purple, dark backgrounds)

**Modifying the poem**: Edit text within the phone screen container div (lines 424-487)

**Canvas effects**: Modify the `drawMatrix()` function for different visual patterns

## Important Notes

- **No Build Process**: This is a static HTML file - no compilation, bundling, or transpilation needed
- **No Dependencies**: All code is vanilla HTML/CSS/JavaScript with no external libraries
- **No Package Manager**: No npm, pip, or other dependency management
- **Self-Contained**: Everything (structure, styles, scripts) is in one file

## Git Workflow

The current branch is `claude/init-project-setup-012EoUziYRNahtTK4ACPmuXR`.

When committing changes:
```bash
git add "erasure_poem (1).html"
git commit -m "Your descriptive message"
git push -u origin claude/init-project-setup-012EoUziYRNahtTK4ACPmuXR
```

## Browser Compatibility

Requires a modern browser with support for:
- Canvas API (for Matrix effect)
- CSS animations and keyframes
- CSS custom animations (multiple simultaneous animations)
- Flexbox layout
