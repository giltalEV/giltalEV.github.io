# Publishing Guide — Gil Tal Media Hub

Claude can handle all ongoing edits via the Chrome extension. This file describes the three workflows.

---

## 1. Add a Media Item

File: `_data/media.yml` — add at the TOP (newest first):

```yaml
- date: 2026-06-15
  outlet: NPR Marketplace
  title: "Your interview title here"
  url: https://www.marketplace.org/actual-article-url
  type: radio          # radio | print | tv | podcast | online
  featured: false      # true = show on homepage (keep 4-5 max)
```

Claude prompt: "Add this media hit: [URL]" → Claude generates YAML → commit.

---

## 2. Add a Publication

File: `_data/publications.yml` — add at the TOP:

```yaml
- year: 2026
  authors: "Tal, G., & Coauthor, N."
  title: "Full paper title"
  type: peer-reviewed  # peer-reviewed | working-paper | report | book-chapter
  journal: Journal Name
  doi: "10.xxxx/xxxxx"  # optional
  url: https://link-to-paper.com
  featured: false
```

Claude prompt: "Add this paper: [DOI or URL]" → Claude generates YAML → commit.

---

## 3. Add a Blog Post

Create: `_posts/YYYY-MM-DD-slug.md`

```markdown
---
layout: post
title: "Your Post Title"
date: 2026-06-15
tags: [EV-policy, California]
excerpt: "One-sentence summary for blog index and social shares."
featured: false
---

Post body in Markdown.
```

Claude prompt: "Draft a blog post about [topic] in my voice" → review → paste → commit.

---

## Data File Reference

| File | Controls |
|------|----------|
| `_data/media.yml` | Homepage Media column + /media.html |
| `_data/publications.yml` | Homepage Research column + /publications.html |
| `_data/talks.yml` | CV page talks section |

---

## Merging to Live

1. Settings → Pages → change Branch to **main**  
2. Open a Pull Request: redesign → main  
3. Merge → site rebuilds in ~60 seconds
