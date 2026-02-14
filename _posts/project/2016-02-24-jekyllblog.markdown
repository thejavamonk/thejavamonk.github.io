---
layout: post
title:  "thejavamonk.github.io"
date:   2016-02-21 17:48:44 +0530
categories: project
featured_image: "/images/jekyll.png"
---

This is my personal blog + portfolio site where I write about things I build and keep a curated list of projects in one place.

### What it includes

- Blog articles on software engineering topics (written for practical learning)
- A projects section that highlights the things I’ve shipped
- A simple, clean layout focused on readability

### Why I built it

I wanted a single home on the internet that I fully control—somewhere I can publish writeups, document projects, and point people to my work without relying on any third‑party platform.

### Highlights

- Lightweight site that’s easy to maintain
- Clear separation between articles and projects
- Hosted on GitHub Pages

### Technologies used

- Jekyll (static site generator)
- Markdown for writing posts and pages
- Liquid templates for layouts and reusable includes
- Sass/SCSS for styling
- Kramdown + Rouge for Markdown + syntax highlighting
- Plugins: `jekyll-feed` (RSS) and `jekyll-paginate-v2` (pagination)

### Architecture (high level)

This site follows a simple static-site workflow:

- **Content** lives in Markdown (posts + pages)
- **Presentation** is handled by layouts and includes (shared header/footer, post template)
- **Build step** generates a fully static site (HTML/CSS) from content + templates
- **Deployment** publishes the generated site via GitHub Pages

In repo terms, the important pieces are:

- `_posts/` for blog + project entries
- `_layouts/` and `_includes/` for the site structure
- `_sass/` and `css/` for styling

### Links

- Source code: [thejavamonk.github.io on GitHub](https://github.com/thejavamonk/thejavamonk.github.io)
- Live site: [https://thejavamonk.github.io](https://thejavamonk.github.io)