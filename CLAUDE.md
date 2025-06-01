# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is Igor Savelev's (@leonspok) portfolio website showcasing his macOS and iOS applications. The site is a static HTML website hosted on GitHub Pages at leonspok.com.

## Repository Structure

The repository follows a simple pattern where each app has its own directory containing:
- `app_icon.png` - Application icon
- `preview.mp4` - Demo video (optional)
- `<app>/<subfolder>/index.html` contains subpages for the given app. Common example is `irvue/privacy_policy/index.html` which contains Privacy Policy for Irvue.
- `utils` subfolder may contain some technical pages. For example `auth_callback.html` allows redirection back to the Irvue macOS app after oAuth authorisation in Unsplash.

### Key Files
- `/index.html` - Main portfolio page listing all applications
- `/CNAME` - GitHub Pages domain configuration (leonspok.com)

## Development Workflow

This is a static website with no build process. To make changes:
1. Edit HTML files directly
2. Keep CSS inline where it is
3. Test locally by opening index.html in a browser
4. Do not commit changes and ask for review before proceeding

## Common Tasks

### Adding a New App
1. Create a new directory with the app name
2. Add required assets (app_icon.png, preview.mp4, etc.)
3. Update index.html to include the new app in the appropriate section

### Updating App Information
- Edit the relevant section in index.html
- Update app icons or preview videos by replacing files in the app directory
- Add links to the subpages from the corresponding folder to the list

## Architecture Notes

- The site uses pure HTML/CSS with no JavaScript framework
- No build process to keep files easily readable and maintainable by hand
- No external dependencies used
- Responsive design is achieved through CSS media queries
- Dark mode support is implemented via `prefers-color-scheme` media query
- The Irvue landing page uses Bootstrap 3.3.5 (located at /irvue/landing/)