# jeremyking.co

A small web site. No JavaScript. No tracking. No ads. Now with pictures.

## Local Development

```bash
hugo server -D
```

Opens at `http://localhost:1313`. The `-D` flag includes draft posts.

> **Use the Hugo _extended_ edition.** Photos are optimized to WebP at build
> time, which the standard build can't do. Cloudflare Pages builds with
> extended Hugo by default; locally, grab the `hugo_extended_*` release.

## Creating Content

```bash
# New blog post
hugo new writing/my-post-title.md

# New project
hugo new projects/project-name.md
```

Edit the frontmatter:
- `title` — page title
- `date` — publish date (writing posts)
- `status` — digital garden status: seedling, growing, complete (projects)
- `weight` — sort order (lower = first, for non-date sections)
- `note` — short annotation shown on homepage (workshop/links)
- `draft` — set to false when ready to publish

## Deploying to Cloudflare Pages

### First time setup:

1. Push this repo to GitHub (it mirrors to Gitea automatically)
2. Go to [Cloudflare Dashboard](https://dash.cloudflare.com) → Pages → Create a project
3. Connect your GitHub account → select this repo
4. Build settings:
   - **Framework preset:** Hugo
   - **Build command:** `hugo`
   - **Build output directory:** `public`
   - **Environment variable:** `HUGO_VERSION` = `0.145.0` (or latest)
5. Deploy

### Custom domain:

1. In Cloudflare Pages → your project → Custom domains
2. Add `jeremyking.co`
3. Cloudflare handles DNS and SSL automatically since your domain is already on Cloudflare

### After that:

Every `git push` to main triggers a rebuild. Write markdown, push, site updates in ~30 seconds.

## Structure

```
content/
├── _index.md           ← homepage about blurb
├── about.md            ← about page
├── projects/           ← digital garden projects
│   ├── 4004.md
│   ├── bmc.md
│   ├── tube-amp.md
│   ├── dap.md
│   └── sovereign-stack.md
├── dirt-rod/           ← Jeep rat-rod build log (sorted by date)
│   ├── _index.md
│   └── the-build-begins/    ← page bundle (markdown + its photos)
│       └── index.md
├── writing/            ← blog posts (sorted by date)
│   └── leaving-the-cloud.md
├── workshop/           ← tools and references (sorted by weight)
│   ├── tools.md
│   └── stack.md
└── links/              ← curated links (sorted by weight)
    ├── reading.md
    └── small-web.md
```

## Design

Georgia serif on cream (#faf8f5). Burnt orange links (#b85a1a) that darken to sienna (#a0522d) when visited. Small-caps section headers. Dotted underlines. 640px max-width. Inline CSS, kept lean but no longer chasing a hard byte budget. Zero JavaScript.

## Pictures

Photos live **inside the page** that uses them (a Hugo *page bundle*): make the
post a folder with `index.md` and drop the image files right next to it. Drop in
a full-resolution photo straight off the camera — Hugo resizes it, caps the
width, compresses it, and emits **WebP** at build time. You never hand-optimize.

```
content/dirt-rod/the-build-begins/
├── index.md
├── donor-jeep.jpg          ← drop full-size photos here
├── teardown-01.jpg
└── teardown-02.jpg
```

Reference them by bare filename:

- **Single captioned image** — the `figure` shortcode. Add `class="lead-photo"`
  to let it bleed past the text column on wide screens:
  ```
  {{</* figure src="donor-jeep.jpg" caption="Bare frame after teardown" */>}}
  {{</* figure src="hero.jpg" alt="..." class="lead-photo" */>}}
  ```
- **A grid of photos** — the `gallery` shortcode (each arg is `src` or `src|caption`):
  ```
  {{</* gallery
    "teardown-01.jpg|Body coming off"
    "teardown-02.jpg|Bare frame"
  */>}}
  ```

Each photo is emitted as WebP with a `srcset` (a smaller variant for phones),
explicit `width`/`height` to prevent layout shift, lazy loading, rounded
corners, and a responsive 2-up gallery grid (1-up on phones). Quality and
resample filter live under `[imaging]` in `hugo.toml`. Cloudflare Pages' edge
network serves the processed output.

The first dirt-rod entry already references these filenames — drop them into
`content/dirt-rod/the-build-begins/` and they render automatically:
`donor-jeep.jpg`, `teardown-01.jpg`, `teardown-02.jpg`, `teardown-03.jpg`, `teardown-04.jpg`.
