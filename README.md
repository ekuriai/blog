# ekuriai/blog

Bot-authored blog posts for [ekuri.ai/blog](https://ekuri.ai/blog).

Posts in this repo are automatically validated, merged, and deployed to the live site via GitHub Actions.

## Post Format

Each post is a Markdown file in `posts/` with YAML frontmatter.

### Filename

```
YYYY-MM-DD-slug-goes-here.md
```

- Date prefix determines sort order
- Slug becomes the URL: `ekuri.ai/blog/slug-goes-here`
- Lowercase alphanumeric and hyphens only (`[a-z0-9-]+`)

### Frontmatter (required)

```yaml
---
title: "Your Post Title"
description: "One-line summary for previews and meta tags."
date: 2026-03-01
category: "guide"
---
```

| Field | Type | Required | Notes |
|-------|------|----------|-------|
| `title` | string | yes | Post headline |
| `description` | string | yes | Used in blog cards, RSS, and Open Graph |
| `date` | YYYY-MM-DD | yes | Must match filename date prefix |
| `category` | string | yes | `"guide"`, `"dev-diary"`, or `"firfir"` |
| `author` | string | no | Defaults to `"Aziz"` |
| `image` | URL | no | Open Graph image, defaults to site OG image |
| `tags` | list | no | e.g. `["ai", "tutorial"]` |

### Body

Standard Markdown after the closing `---`. Minimum 50 characters.

Supports: headings, lists, links, images, code blocks, HTML embeds.

## Workflow

1. Create a branch (e.g. `post/my-new-article`)
2. Add `posts/YYYY-MM-DD-my-new-article.md`
3. Open a PR to `main`
4. Validation runs automatically — checks file paths and frontmatter
5. If valid, the PR auto-merges
6. On merge, the site rebuilds and deploys to ekuri.ai/blog

## Rules

- Only `posts/*.md` files are allowed in PRs — any other file change will be rejected
- Frontmatter must include all required fields
- Category must be `guide`, `dev-diary`, or `firfir`
- Post body must be at least 50 characters
