# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal academic website for Rishi Jaiswal, built with Hugo static site generator and the PaperMod theme. The site is deployed to GitHub Pages at https://rjaiswal.com/.

## Build and Development Commands

### Local Development
```bash
# Start local development server with live reload
hugo server

# Build the site (output to ./public/)
hugo

# Build with minification (production build)
hugo --minify
```

### Theme Management
The PaperMod theme is included as a git submodule. When cloning or updating:
```bash
# Initialize submodules after clone
git submodule update --init --recursive

# Update theme to latest version
cd themes/PaperMod
git pull origin master
cd ../..
```

## Architecture

### Site Configuration
- `config.yml`: Main Hugo configuration file
  - **Critical**: `markup.goldmark.renderer.unsafe: true` is required because the homepage (`content/_index.md`) uses raw HTML with custom styling
  - Contains site metadata, navigation menu, social icons, and PaperMod theme parameters
  - Base URL is set to custom domain: https://rjaiswal.com/

### Content Structure
- `content/_index.md`: Custom homepage with raw HTML and inline styles (requires unsafe HTML rendering)
- `content/about.md`: Professional bio, research interests, technical expertise
- `content/research.md`: Research projects, industry experience, course projects
- `content/publications.md`: Academic publications, patents, Google Scholar link
- `resume_risi.pdf`: CV (stored in root directory, accessible via `/resume_risi.pdf`)

### Deployment
- Automated deployment via GitHub Actions (`.github/workflows/deploy.yml`)
- Triggers on push to `main` branch
- Uses Hugo extended version with `--minify` flag
- Deploys to GitHub Pages automatically

### Theme Customization
The site uses the PaperMod theme as a submodule. Custom styling in `_index.md` includes:
- Gradient text effects
- Research cards with animations
- Custom CSS classes (e.g., `neural-bg`, `gradient-text`, `glow-text`)
- These styles are embedded directly in the markdown file

## Important Notes

### HTML Rendering
The homepage uses extensive raw HTML for visual effects. The `unsafe: true` setting in config.yml is essential - do not remove it or the homepage will not render properly.

### Menu Links
The CV menu item currently points to `/cv/` but the actual PDF is at `/resume_risi.pdf`. Verify which approach is preferred (a dedicated CV page vs. direct PDF link).

### Social Links
The site includes links to:
- Google Scholar: https://scholar.google.com/citations?user=cxYoZb8AAAAJ
- GitHub: https://github.com/nextquanta
- LinkedIn: https://www.linkedin.com/in/risi-jaiswal-08b4215b/
- Email: rjaiswa@purdue.edu
