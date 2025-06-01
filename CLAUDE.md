# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is Igor Savelev's (@leonspok) portfolio website showcasing his macOS and iOS applications. The site is a static HTML website hosted on GitHub Pages at leonspok.com.

## Repository Structure

The repository follows a simple pattern where each app has its own directory containing:
- `landing/` - Individual landing page for the app
- `privacy_policy/` - Privacy policy page (optional)
- `utils/` subfolder may contain technical pages (e.g., `auth_callback.html` for OAuth redirection) but these should NOT be included in the "More" sections as they are not user-facing content.

### Key Files
- `/index.html` - Main portfolio page listing all applications (uses `styles/main.css`)
- `/styles/` - Shared CSS files
  - `main.css` - Styles for the main portfolio page
  - `landing.css` - Shared styles for all app landing pages
- `/resources/` - Shared resources organized by app
  - `app_name/app_icon.png` (+ @2x, @3x) - Icons for main portfolio (100px)
  - `app_name/icon_128x128.png` (+ @2x, @3x) - Icons for landing pages (128px)
  - `app_name/preview.mp4` - Demo videos
  - `app_name/screenshot_1.png` - Screenshots (for apps without videos)
- `/templates/` - Template files for creating new pages
  - `landing.html` - Template for new app landing pages
- `/CNAME` - GitHub Pages domain configuration (leonspok.com)

## Development Workflow

This is a static website with no build process. To make changes:
1. Edit HTML files directly
2. Use shared CSS files in `/styles/` (avoid inline CSS)
3. Test locally by opening index.html in a browser
4. Do not commit changes and ask for review before proceeding

## Common Tasks

### Adding a New App
1. Create a new directory with the app name
2. Add resources to `/resources/app_name/`:
   - `app_icon.png` (100x100), `app_icon@2x.png` (200x200), `app_icon@3x.png` (300x300) - For main portfolio
   - `icon_128x128.png` (128x128), `icon_128x128@2x.png` (256x256), `icon_128x128@3x.png` (384x384) - For landing page
   - `preview.mp4` (optional demo video) OR `screenshot_1.png` (screenshot)
3. Create landing page:
   - Copy `templates/landing.html` to `app_name/landing/index.html`
   - Replace all `{{PLACEHOLDER}}` values with app-specific content
4. Update index.html to include the new app in the appropriate section

### Creating a Landing Page
1. Copy `templates/landing.html` to your app's `landing/` directory
2. Replace placeholders:
   - `{{APP_NAME}}` → Your app name (e.g., "Irvue")
   - `{{PLATFORM}}` → Platform (e.g., "macOS", "iOS")
   - `{{TAGLINE}}` → Short tagline (e.g., "QR Code Generator")
   - `{{DESCRIPTION}}` → Hero section description
   - `{{META_DESCRIPTION}}` → SEO meta description
   - `{{META_KEYWORDS}}` → SEO keywords (comma-separated)
   - `{{APP_FOLDER}}` → Your app's folder name (must match `/resources/app_folder/`)
   - `{{CTA_URL}}` → App Store or GitHub URL
   - `{{CTA_TEXT}}` → Button text
   - `{{CTA_ARIA_DESCRIPTION}}` → Accessibility description
   - `{{MEDIA_ELEMENT}}` → Video or image HTML (see examples below)
3. Ensure resources exist in `/resources/app_name/`:
   - Icons: `icon_128x128.png` + @2x, @3x variants  
   - Video: `preview.mp4` or screenshot image

### Media Element Examples for Landing Pages
```html
<!-- For apps with video demos -->
<video preload="metadata" controls autoplay loop muted aria-label="App demo video">
    <source src="../../resources/app_name/preview.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<!-- For apps with screenshots -->
<img src="../../resources/app_name/screenshot_1.png" alt="App screenshot description">
```

### Updating App Information
- Edit the relevant section in index.html
- Update app icons or preview videos by replacing files in the app directory
- Add links to user-facing subpages in the "More" sections (exclude utils folders)

## Architecture Notes

- The site uses pure HTML/CSS with no JavaScript framework
- No build process to keep files easily readable and maintainable by hand
- No external dependencies used
- Shared CSS files in `/styles/` for consistency:
  - `main.css` - Main portfolio page styles
  - `landing.css` - All app landing page styles
- Responsive design is achieved through CSS media queries
- Dark mode support is implemented via `prefers-color-scheme` media query
- All landing pages use the same design system for consistency

## CSS Architecture

### Main Portfolio Page (`/index.html`)
- Uses `styles/main.css` for all styling
- No inline CSS

### App Landing Pages (`app/landing/index.html`)
- All use shared `styles/landing.css` 
- Consistent hero layout, typography, and responsive behavior
- Dark mode support included
- Video autoplay with controls for apps with demo videos
- Optimized for accessibility (WCAG AA compliance)

### Template System
- `templates/landing.html` provides a reusable template
- Uses `{{PLACEHOLDER}}` syntax for easy find/replace
- Pre-configured with proper meta tags, accessibility features, and responsive design