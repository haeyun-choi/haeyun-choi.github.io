# Website Rebuild Notes

This note documents the current website rebuild state and the safest path for resuming work and later deploying the rebuilt site as the official live website.

## 1. Current Status

- The old website was a static HTML5 UP-based site.
- The new website has been rebuilt as a lightweight Jekyll-based academic homepage.
- The rebuilt website is saved on the `rebuild/academic-website` branch.
- The old website is preserved on the `backup/old-website` branch.
- The current live website remains on the `main` branch.
- The live website has not been changed yet.
- The WIP commit currently preserving the rebuild is:

```text
a87e828 WIP rebuild academic Jekyll website
```

## 2. Branch Strategy

- `main`: current live GitHub Pages site.
- `backup/old-website`: backup of the previous website.
- `rebuild/academic-website`: new Jekyll academic website candidate.

Editing and testing should continue on `rebuild/academic-website`.

The official live website changes only after `rebuild/academic-website` is merged into `main`.

Pushing `rebuild/academic-website` does not deploy the live site, assuming GitHub Pages is configured to deploy from `main`.

Do not modify `main` directly unless intentionally deploying the rebuilt website.

## 3. How to Resume Work Later

Use these commands to reopen the rebuild branch locally:

```bash
cd /Users/haeyun/Desktop/haeyun-choi.github.io
git switch rebuild/academic-website
git pull
git status
bundle exec jekyll serve
```

Then preview the site at:

```text
http://127.0.0.1:4000/
```

If the local Ruby/Bundler environment needs the project-local bundle path, use:

```bash
env GEM_HOME=/Users/haeyun/Desktop/haeyun-choi.github.io/vendor/bundle/ruby/2.6.0 GEM_PATH=/Users/haeyun/Desktop/haeyun-choi.github.io/vendor/bundle/ruby/2.6.0 BUNDLE_PATH=/Users/haeyun/Desktop/haeyun-choi.github.io/vendor/bundle bundle exec jekyll serve
```

## 4. Current Website Structure

The rebuilt site uses a small Jekyll structure:

```text
_config.yml
Gemfile
index.md
_layouts/default.html
_includes/nav.html
_data/news.yml
_data/publications.yml
assets/css/main.css
assets/files/
assets/images/
assets/videos/
README.md
.gitignore
```

Main content sources:

- Bio and homepage layout: `index.md`
- Navigation: `_includes/nav.html`
- Site metadata and author links: `_config.yml`
- News: `_data/news.yml`
- Publications: `_data/publications.yml`
- Styling: `assets/css/main.css`

## 5. Preserved Assets

Useful assets were migrated into cleaner paths:

- Profile image: `assets/images/profile/avatar.jpg`
- CV: `assets/files/CV_Haeyun_Choi.pdf`
- Publication images:
  - `assets/images/publications/ddrf_blur.png`
  - `assets/images/publications/ddrf_deblur.png`
  - `assets/images/publications/optical.png`
  - `assets/images/publications/autocyclevc.png`
- Videos:
  - `assets/videos/demo_shakiness.mp4`
  - `assets/videos/demo_vc.mp4`

Tracked `.DS_Store` files were removed from version control in the WIP rebuild commit, and `.gitignore` now ignores `.DS_Store`.

## 6. Build Check

Use this command to check the Jekyll build:

```bash
bundle exec jekyll build
```

If the local environment needs project-local Bundler paths:

```bash
env GEM_HOME=/Users/haeyun/Desktop/haeyun-choi.github.io/vendor/bundle/ruby/2.6.0 GEM_PATH=/Users/haeyun/Desktop/haeyun-choi.github.io/vendor/bundle/ruby/2.6.0 BUNDLE_PATH=/Users/haeyun/Desktop/haeyun-choi.github.io/vendor/bundle bundle exec jekyll build
```

The last verified build passed. A Bundler warning about `/Users/haeyun` not being writable may appear, but it is not a Jekyll build failure if the build finishes successfully.

## 7. Before Deploying Later

Before making the rebuilt site official, check:

- Desktop layout.
- Tablet layout.
- Mobile layout.
- Top navigation links.
- Bio links.
- CV link.
- News link for `DeepDeblurRF`.
- Publication links.
- DDRF hover-to-compare thumbnail behavior.
- Profile image sizing.
- No unwanted `.DS_Store` files are tracked:

```bash
git ls-files '*.DS_Store' '.DS_Store'
```

The command should return no tracked `.DS_Store` files.

## 8. How to Continue Editing Safely

Continue working only on `rebuild/academic-website`:

```bash
git switch rebuild/academic-website
```

After edits:

```bash
bundle exec jekyll build
git status --short
git add -A
git commit -m "Update rebuilt academic website"
git push
```

Do not merge into `main` until ready to deploy.

## 9. How to Deploy Later

When the rebuilt site is ready to become the official live website, open a pull request from:

```text
rebuild/academic-website -> main
```

Recommended command:

```bash
gh pr create --base main --head rebuild/academic-website --title "Rebuild academic Jekyll website" --body "Rebuild the personal website with a lightweight Jekyll academic structure."
```

Review the PR carefully. After merging the PR into `main`, GitHub Pages should deploy the rebuilt website, assuming GitHub Pages is configured to deploy from `main`.

## 10. What Not To Do Until Deployment

- Do not modify `main` directly.
- Do not merge `rebuild/academic-website` into `main`.
- Do not change GitHub Pages deployment settings.
- Do not delete `backup/old-website`.
- Do not force-push `main`.

