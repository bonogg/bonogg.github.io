# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an academic personal website built with Jekyll using the academicpages template (forked from Minimal Mistakes theme). It's deployed via GitHub Pages and features collections for research, teaching, talks, and portfolio items.

## Development Commands

### Local Development
```bash
# Install dependencies
bundle install

# Serve site locally at localhost:4000 with live reload
bundle exec jekyll serve

# Clean build directory
bundle clean
```

Note: If you encounter errors with `bundle install`, delete `Gemfile.lock` and try again.

### Development Configuration
- `_config.yml` - Main site configuration
- `_config.dev.yml` - Development-specific overrides

## Architecture

### Jekyll Collections
The site uses Jekyll collections to organize academic content:
- `_research/` - Research papers and publications
- `_talks/` - Conference talks and presentations
- `_teaching/` - Teaching materials and courses
- `_portfolio/` - Portfolio projects
- `_posts/` - Blog posts
- `_drafts/` - Draft posts (not published)

Each collection has default front matter settings defined in `_config.yml` under the `defaults` section.

### Layout System
- `_layouts/` - Page templates (default, single, talk, archive, etc.)
- `_includes/` - Reusable components (header, footer, author-profile, etc.)
- `_sass/` - SCSS stylesheets

### Content Organization
- `_pages/` - Static pages (about, CV, contacts, etc.)
- `_data/navigation.yml` - Site navigation menu configuration
- `_data/ui-text.yml` - Internationalization text strings
- `files/` - Static files (PDFs, documents) accessible at `/files/filename.pdf`
- `images/` - Image assets

### Markdown Generation
The `markdown_generator/` directory contains tools to bulk-generate collection items from structured data:

**Python scripts:**
- `publications.py` - Generate `_publications/` from `publications.tsv`
- `talks.py` - Generate `_talks/` from `talks.tsv`
- `pubsFromBib.py` - Generate publications from BibTeX files

**Jupyter notebooks:**
- `publications.ipynb` - Interactive version of publications.py with documentation
- `talks.ipynb` - Interactive version of talks.py with documentation
- `PubsFromBib.ipynb` - Interactive BibTeX converter

These scripts read TSV files with structured data (title, date, venue, etc.) and create individual markdown files with proper front matter for each item.

### Configuration Files
- `_config.yml` - Primary site configuration including:
  - Site metadata (title, description, URL)
  - Author information and social links
  - Jekyll settings (markdown processor, plugins, permalinks)
  - Collection definitions
  - Default front matter values
  - Analytics and SEO settings

### Theme Customization
This site uses a customized version of Minimal Mistakes. Key customization points:
- Author profile in `_includes/author-profile.html`
- Custom archive layouts in `_includes/archive-single*.html`
- Site navigation in `_includes/masthead.html`

## Working with Content

### Adding New Content
1. Create markdown files in the appropriate collection directory (`_research/`, `_talks/`, etc.)
2. Include required front matter (layout, title, date, permalink)
3. Follow existing content files as templates

### Using Markdown Generators
For bulk content creation:
1. Edit the TSV file in `markdown_generator/` with your data
2. Run the corresponding Python script: `python markdown_generator/talks.py`
3. Or open the Jupyter notebook for interactive use
4. Generated markdown files will be created in the appropriate collection directory

### Modifying Navigation
Edit `_data/navigation.yml` to add/remove menu items in the site header.

### Updating Author Profile
Modify the `author` section in `_config.yml` to change bio, avatar, and social links.
