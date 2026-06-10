# jeremyking.co

A small web site. No JavaScript. No tracking. No ads. Now with pictures.

## Local Development

```bash
hugo server -D
```

Opens at `http://localhost:1313`. The `-D` flag includes draft posts.

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
│   └── the-build-begins.md
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

Photos live in `static/img/<section>/` and are referenced from content by their public path, e.g. `/img/dirt-rod/frame.jpg`.

- **Single captioned image** — Hugo's built-in figure shortcode:
  ```
  {{</* figure src="/img/dirt-rod/frame.jpg" caption="Bare frame after teardown" */>}}
  ```
- **A grid of photos** — the `gallery` shortcode (each arg is `src` or `src|caption`):
  ```
  {{</* gallery
    "/img/dirt-rod/teardown-01.jpg|Body coming off"
    "/img/dirt-rod/teardown-02.jpg|Bare frame"
  */>}}
  ```

Images get rounded corners, lazy loading, and a responsive 2-up gallery grid (1-up on phones). The dirt-rod entry references the following files — drop them into `static/img/dirt-rod/` and they'll render:
`donor-jeep.jpg`, `teardown-01.jpg`, `teardown-02.jpg`, `teardown-03.jpg`, `teardown-04.jpg`.
