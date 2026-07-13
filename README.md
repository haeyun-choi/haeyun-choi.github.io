# Haeyun Choi Academic Website

This repository hosts the GitHub Pages website for:

<https://haeyun-choi.github.io/>

The site is a lightweight Jekyll academic homepage. Content is intentionally kept in simple data files:

- `_data/news.yml`
- `_data/publications.yml`

## Local Development

```bash
bundle install
bundle exec jekyll serve
```

Then open:

```text
http://127.0.0.1:4000/
```

## Deployment

GitHub Pages should build from the repository's configured Pages branch. For this user site repository, the production URL is preserved as long as the repository remains named `haeyun-choi.github.io` and Pages is configured to deploy from the intended branch.
