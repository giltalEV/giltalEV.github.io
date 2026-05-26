# Publishing Guide — Gil Tal Media Hub

Claude can handle all ongoing edits via the Chrome extension. This file describes the four workflows.

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
featured_image: /assets/img/posts/my-image.jpg      # optional
featured_image_alt: "Description of the image"       # required if image set
featured_image_caption: "Figure 1: EV sales by state, 2025. Source: IHS." # optional
---

Post body in Markdown.
```

Claude prompt: "Draft a blog post about [topic] in my voice" → review → paste → commit.

---

## 4. Add a Photo or Figure

Images live in `assets/img/posts/`. There are two ways to add them.

### Option A — Featured (hero) image at the top of a post

1. Upload the image to `assets/img/posts/` (see upload steps below).
2. Add to the post's front matter:
```yaml
featured_image: /assets/img/posts/your-image.jpg
featured_image_alt: "Brief description for screen readers"
featured_image_caption: "Optional caption shown below image"  # leave out if none
```
The image will appear full-width below the post title.

### Option B — Inline figure inside the post body

After uploading the image, add this tag anywhere in your Markdown:
```liquid
{% include figure.html
   src="/assets/img/posts/ev-sales-chart.png"
   alt="Bar chart showing EV sales by state"
   caption="Q1 2026 EV registrations by state. Source: IHS Markit." %}
```

Add `width="wide"` to break out of the text column for wide charts:
```liquid
{% include figure.html src="/assets/img/posts/wide-chart.png" alt="..." caption="..." width="wide" %}
```

You can also use plain Markdown for quick inline images (no caption):
```markdown
![Alt text](/assets/img/posts/my-chart.png)
```

### How to upload an image to the repo

**Via GitHub web (easiest):**
1. Navigate to `assets/img/posts/` in the repo (create the folder by uploading a first image).
2. Click **Add file → Upload files**.
3. Drag your image in, write a commit message, commit to `main` (or whichever branch).

**Via Claude + Chrome extension:**
Say "upload this image to assets/img/posts/ and call it ev-sales-chart.png" and attach the file to the chat. Claude will handle the upload.

**File guidelines:**
- Format: JPEG for photos, PNG for charts/diagrams (transparent background)
- Width: aim for 1200px wide at 72dpi — good quality, reasonable file size
- Filename: lowercase, hyphens only, descriptive (e.g., `feebate-pivot-diagram.png`)

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
3. Merge → site rebuilds in ~45 seconds
