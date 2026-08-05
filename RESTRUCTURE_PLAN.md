# Site Restructuring Plan — bonogg.github.io

Goal
- Make the site structure clearer and easier to maintain by:
  - Separating content (collections/data) from presentation (layouts/includes/assets)
  - Consolidating styles and JS into a modular SCSS/JS structure
  - Centralizing navigation and metadata in _data and _config.yml
  - Introducing a small migration plan with minimal downtime

Branch
- Name: restructure/site-structure (branch used for planning: copilot/restructuresite-structure)

Proposed repository layout (high-level)
- _config.yml
- _data/
  - navigation.yml
  - authors.yml
  - site.yml
- _layouts/
  - default.html
  - home.html
  - page.html
  - post.html
- _includes/
  - header.html
  - footer.html
  - nav.html
  - meta.html
- _sass/
  - _variables.scss
  - _mixins.scss
  - base.scss
  - components/
    - _header.scss
    - _cards.scss
- assets/
  - css/ (compiled CSS)
  - js/
  - images/
- _posts/ (blog posts remain here)
- _projects/ (collection for project pages)
- pages/ (standalone pages, e.g., about.md, contact.md)
- README.md
- RESTRUCTURE_PLAN.md

Concrete steps (priority order)
1. Create branch `restructure/site-structure` (done on branch copilot/restructuresite-structure).
2. Add/update _data/navigation.yml and other data files for central navigation.
3. Move and consolidate includes:
   - Move header/nav/footer into _includes/.
   - Update layouts to render includes.
4. Reorganize SCSS:
   - Create _sass/partials and move CSS/SCSS there. Add base and components imports.
   - Update build instructions (if using GitHub Pages, keep to supported Sass).
5. Introduce collections:
   - Add `projects` collection in _config.yml and create a few example project files in `_projects/`.
6. Update _config.yml:
   - Add collection settings, defaults, global variables, baseurl/permalink patterns.
7. Update navigation usage:
   - Replace hard-coded nav with _data/navigation.yml-driven include.
8. Migrate content:
   - Move page files into `pages/` where appropriate and update front matter.
   - Update all internal links/permalinks.
9. Test locally or via a preview action:
   - Run `bundle exec jekyll serve` (or the project's build command).
   - Smoke test pages, navigation, assets, and responsive layout.
10. Open a PR with changes, a short description, and migration notes.

Testing & QA
- Provide a checklist in the PR (rendered site link if available, screenshots of key pages).
- Ask reviewers to check: navigation, header/footer, post layout, project pages, CSS regressions.

Notes
- Keep commits small and focused: one commit per conceptual change (data, includes, layouts, styles, migration).
- If you use custom plugins not supported on GitHub Pages, consider GitHub Actions to build and publish.
