# Personal Portfolio Site PRD

## Project Overview
- **Goal:** Build a minimal personal portfolio website using Hugo, hosted on your existing server infrastructure.
- **Purpose:** Present yourself and your projects in a clear, accessible format.

## Core Features
- **Navigation:**  
  - Static top navigation bar, always visible.
  - Toggle menu for switching between: About Me (landing page), Projects.

- **Pages/Sections:**  
  - **About Me / Overview:**  
    - Landing page with brief introduction, high-level overview of experience, and profile image (optional).
    - Social media links for GitHub and LinkedIn.
  - **Projects:**  
    - List of projects with titles, short descriptions, and links (if available).
    - Support for images/screenshots and external links for each project.

- **Design:**  
  - Clean, simple layout.
  - Responsive (works on desktop and mobile).
  - Use prebuilt Hugo themes/components as much as possible.

## Technical Requirements
- **Framework:** Hugo static site generator.
- **Theme:** Use the open-source [hello-friend-ng](https://github.com/rhazdon/hugo-theme-hello-friend-ng) Hugo theme for a minimalist, responsive design.
- **Hosting:** Self-hosted on your existing server.
- **Content Management:** Markdown files for each section.
- **Navigation:** Static menu using theme's built-in navigation.
- **Accessibility:** Basic accessibility (readable fonts, contrast, keyboard navigation).
- **Exposure:** Use Cloudflared Zero Trust Tunnel to securely expose the site to the internet.
- **Traffic:** Designed for low traffic, personal use.
- **Security:** No dynamic backend; access managed via Cloudflare Zero Trust policies.

## Non-Functional Requirements
- **Performance:** Fast load times (static HTML).
- **Maintainability:** Easy to update content via Markdown.
- **Security:** No direct exposure of server IP; access managed through Cloudflare.

## Codebase Design Aspects
- Codebase should be simple and not overly complex.
- Each script or component should be no more than 300-400 lines of code.
- Minimal comments throughout the codebase; code should be self-explanatory.
- All code and content should be tracked with Git for easy backup and collaboration.
- Project should follow a clear, logical directory structure (e.g., separating content, static assets, and configuration).
- Codebase should allow for easy addition of new sections or features in the future (extensibility).
- Use only well-maintained, open-source dependencies; keep them minimal.
- Site configuration should be centralized (e.g., in `config.toml` for Hugo).
- Build and deployment process should be simple and documented (e.g., a short README).

## Milestones
1. Select and set up Hugo theme.
2. Configure navigation/menu.
3. Create and populate About Me and Projects sections.
4. Test responsiveness and accessibility.
5. Deploy to local server and expose via Cloudflared Tunnel.

## Success Criteria
- Both sections are accessible via the static top menu.
- Content is clear, readable, and easy to update.
- Site loads quickly and works on all devices.
- Uses prebuilt solutions wherever possible.
- Securely exposed to the internet via Cloudflared Zero Trust.

## SEO Status (Verified in Google Rich Results Test + Search Console)

**Structured data validated:**
- Blog posts: BlogPosting schema, BreadcrumbList schema, article OG tags (og:type, published_time, author, tag, section)
- About page: ProfessionalService schema, BreadcrumbList schema
- All pages: WebSite schema with SearchAction
- Homepage: Person schema

**Sitemap:** Submitted and accepted — 23 pages discovered (as of Apr 2026)

**What's in place site-wide:**
- Open Graph + Twitter Card meta tags on every page
- Page-specific OG images (blog posts use `cover` param, other pages use default `og-image.png`)
- RSS feed auto-discovery link in `<head>`
- Custom sitemap with per-section priorities (home=1.0, about=0.9, posts=0.8, projects=0.7)
- robots.txt blocking thin/duplicate taxonomy pages (/tags/, /categories/)
- Custom 404 page
- Google Analytics 4 (DNS-verified in Search Console)
- HTML minification enabled

## Creating a New Blog Post — Step by Step

### 1. Create the post file
File: `content/posts/<slug>.md`

```yaml
---
title: "Post Title"
date: 2026-04-10
draft: false
description: "1-2 sentence summary. Used in meta description, OG description, and Google search results."
keywords: ["keyword1", "keyword2"]
tags: ["tag1", "tag2"]
cover: "/images/blog/<slug>/cover.png"
coverAlt: "Description of cover image"
---

Post content goes here in Markdown.
```

### 2. Add images
Create directory: `static/images/blog/<slug>/`

Place images there. Reference them inline:
```
![Alt text describing the image](/images/blog/<slug>/filename.png "Optional title text")
```

### 3. Front matter fields for SEO
| Field | Required | Purpose |
|---|---|---|
| `title` | Yes | Page `<title>`, OG title, schema headline |
| `date` | Yes | `article:published_time`, schema datePublished |
| `description` | Yes | Meta description, OG description, search result snippet |
| `tags` | Yes | Visible tag badges + `article:tag` OG tags + merged into keywords meta |
| `keywords` | No | Additional keywords merged into meta keywords tag |
| `cover` | Recommended | OG/social preview image. If omitted, default `og-image.png` is used |
| `coverAlt` | If cover set | Alt text for cover image in OG `og:image:alt` |
| `draft` | Yes | Set to `false` to publish |

### 4. Inline citations (if needed)
```markdown
Text with citation.<sup>[1](#ref-1)</sup>

---

### References

1. <a id="ref-1"></a>Author, "Title," Date. [Link](https://url)
```

### 5. Build and deploy
```bash
git add . && git commit -m "Add blog post: <title>"
git push
# Then on server: git pull && hugo --gc --minify && reload nginx && purge cloudflare
```

### 6. Post-publish SEO checks
- Google Search Console → Sitemaps → resubmit `sitemap.xml`
- Google Search Console → URL Inspection → paste new post URL → "Request indexing"
- [Rich Results Test](https://search.google.com/test/rich-results) — paste URL to verify BlogPosting + BreadcrumbList schema
- [LinkedIn Post Inspector](https://www.linkedin.com/post-inspector/) — verify OG image/title/description preview
