# Little Cloud Blog Content Repository

This repository stores blog posts as Markdown files for the Little Web Co website. Posts are edited via Decap CMS from the main Next.js site (littlecloud-www) and pulled during the build process.

## Repository Structure

```
little-blog/
├── posts/              # All blog post Markdown files
│   └── *.md           # Individual post files
└── .github/
    └── workflows/
        └── notify-main.yml  # Auto-rebuild workflow
```

## Blog Post Format

Each blog post is a Markdown file with YAML frontmatter. The file naming convention is:

```
YYYY-MM-DD-slug.md
```

Example: `2025-01-15-welcome.md`

### Required Frontmatter Fields

- `title` (string) - The title of the blog post
- `date` (string) - Publication date in `YYYY-MM-DD` format
- `author` (string) - Author name

### Optional Frontmatter Fields

- `tags` (array) - List of tags for categorization
  ```yaml
  tags:
    - technology
    - updates
  ```
- `excerpt` (string) - Short description for previews and meta descriptions
- `draft` (boolean) - Set to `true` to mark posts as drafts (filtered out in production)
- `feature_image` (string) - URL to the featured image for the post (used in previews and social sharing)

### Example Post

```markdown
---
title: My First Blog Post
date: 2025-01-15
author: John Doe
tags:
  - welcome
  - getting-started
excerpt: This is my first blog post about getting started.
draft: false
feature_image: https://example.com/image.jpg
---

# My First Blog Post

This is the body of the post. Supports **Markdown** formatting.

## Features

- Easy to write
- Version controlled
- Edit via CMS or directly

Happy writing!
```

## Editing Posts

### Via Decap CMS

1. Navigate to `/admin` on your main site (littlecloud-www)
2. Log in with GitHub OAuth
3. Create or edit posts through the CMS interface
4. Changes are committed directly to this repository

### Via Git

1. Clone this repository
2. Edit Markdown files in the `posts/` directory
3. Commit and push changes
4. The main site will rebuild automatically (if workflow is configured)

## Auto-Rebuild Workflow

The `.github/workflows/notify-main.yml` workflow automatically triggers a rebuild of the main site when content is updated.

**Setup Requirements:**

1. Create a Personal Access Token (PAT) with `repo` scope
2. Add the PAT as a secret named `MAIN_REPO_PAT` in this repository's settings
3. Update the workflow file with your main repository name (`littlewebco/littlecloud-www`)
4. Ensure the main repository listens for `repository_dispatch` events with type `content-updated`

## Content Guidelines

- Use clear, descriptive titles
- Include an excerpt for better previews
- Tag posts appropriately for easier discovery
- Use Markdown formatting for readability
- Keep file names lowercase with hyphens (e.g., `my-post-title.md`)

## Support

For questions or issues, please contact the Little Cloud team or open an issue in the main repository.
