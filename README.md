# Med Student Bookshelf

Hugo site for medical textbook guides, deployed to GitHub Pages by GitHub Actions.

## Deploy

1. Push this folder to the `main` branch of a **public** GitHub repository.
2. In the repository: Settings > Pages > Source: **GitHub Actions**.
3. The workflow in `.github/workflows/hugo.yml` builds and publishes on every push. The site address is set automatically.

## Before going live

- `hugo.toml`: set `amazonTag` to your Amazon Associates tracking ID, and change `title` if you want another site name.
- `content/about.md`: add a sentence or two about who runs the site.

## Add a guide

Create `content/guides/your-topic.md`:

```
---
title: "Page title with the main keyword"
slug: "short-url-with-keyword"
description: "One sentence, under 155 characters, shown in search results."
date: 2026-11-15
lastmod: 2026-11-15
categories: ["Physiology"]
tags: ["textbook comparison", "pre-clinical"]
spine: "Short subject label for the shelf"
verdict: "The short answer, shown in a highlighted box at the top."
---
```

Amazon links (tracking tag, `rel="sponsored nofollow"` added automatically):

```
{{< amazon q="Costanzo Physiology" text="Costanzo Physiology" >}}
{{< amazon asin="PRODUCT_ID" text="Book title" >}}
```

Book card with a drawn cover and a buy button:

```
{{< book q="Costanzo Physiology" title="Costanzo Physiology" short="Costanzo Physiology" by="Linda S. Costanzo" for="learning concepts quickly" >}}
```

Category colors: set `color: "#2559b5"` in `content/categories/<name>/_index.md`. The color is used for that category's tile, covers, shelf spine and buttons. Pick a color dark enough for white text.

## Categories, tags and pagination

- **Categories**: one per guide (the subject). Each gets its own indexable page at `/categories/<name>/`. To give a new category its own intro text and meta description, add `content/categories/<name>/_index.md` with `title` and `description`.
- **Tags**: optional, a few per guide. Tag pages exist for readers but are marked `noindex` and left out of the sitemap, so they do not create thin pages in search.
- **Pagination**: guide lists, category pages and tag pages split automatically after 10 guides. Change `pagerSize` in `hugo.toml`.
- **Related guides**: chosen automatically from guides sharing a category or tags.

## Preview locally

```
hugo server
```

## SEO features included

Unique title and meta description per page, canonical URLs, Open Graph and social image, Article, Breadcrumb, ItemList and WebSite structured data, `sitemap.xml`, `robots.txt`, RSS feed, inlined minified CSS, self-hosted font, no JavaScript, light and dark mode.

Font: Literata (SIL Open Font License 1.1).
