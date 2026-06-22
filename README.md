# Benji Personal Site

A Hugo + PaperMod personal site for essays, notes, projects, and reading.

## Local workflow

Create a new draft:

```sh
hugo new posts/my-essay.md
```

Preview drafts locally:

```sh
hugo server -D
```

Build production output:

```sh
hugo --gc --minify
```

## Publishing

Push to `main` and GitHub Actions deploys the site to GitHub Pages.

In the GitHub repository settings, set **Pages > Build and deployment > Source** to **GitHub Actions**.

The first deployment target is:

```text
https://benj2o.github.io/personal-site/
```

## Editorial bar

Keep the site small and curated:

- Write thesis-first introductions.
- Prefer stable tags and categories over many one-off labels.
- Publish only when the piece has a clear reason to exist.
- Use `notes/` for fragments and `posts/` for finished essays.
