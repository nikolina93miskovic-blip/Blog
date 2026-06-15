# Bloom & Grow Learning — Blog setup & writing guide

This adds a **Journal (blog)** to your existing site at `yourdomain.com/blog`, with a
simple editor you log into to write posts. When you publish, your post is saved to
your code, Netlify rebuilds automatically, and it goes live a minute or two later.
**You never touch Netlify by hand.**

Your existing pages (`index.html`, `portal.html`, `privacy.html`) are kept exactly as
they are — same URLs, same content. Nothing about the current site changes.

---

## The everyday flow (once it's set up)

1. Go to `yourdomain.com/admin` and log in.
2. Click **New → Blog post**.
3. Fill in the title, date, a short description, an optional cover image, and write the body.
4. Click **Publish**.
5. ~1–2 minutes later it's live at `yourdomain.com/blog/your-post-title/`.

That's it. Write → Publish. The rebuild happens for you.

---

## One-time setup (~30 minutes — a good moment to grab technical help)

This is the only fiddly part, and you only do it once.

### 1. Put the project in a GitHub repository
Create a free GitHub account if you don't have one, make a new repository, and upload
the contents of this folder to it (everything except `node_modules` and `_site`, which
are generated automatically).

### 2. Connect the repo to Netlify
In Netlify, link the GitHub repo. The included `netlify.toml` already sets the right
build settings (`npm run build`, publishing the `_site` folder), so Netlify will build
the site correctly on every change. Point your domain at this Netlify site.

### 3. Fill in your real details (3 quick edits)
- **`src/_data/site.js`** — replace the placeholder `url` with your real domain, and add
  your Instagram and Facebook links.
- **`src/robots.txt`** — replace the domain in the `Sitemap:` line.
- **`src/admin/config.yml`** — replace `OWNER/REPO` with your GitHub repo
  (e.g. `nikki/bloom-and-grow`).

### 4. Connect the editor to GitHub
The editor (Sveltia CMS) needs permission to save posts to your repo. Sveltia uses a
GitHub sign-in; follow its short setup docs (search **"Sveltia CMS GitHub backend"**) to
register the authentication once. After that, logging in at `/admin` is one click.
*(If you'd rather, Decap CMS is a drop-in alternative — see the note in `src/admin/index.html`.)*

### 5. Add a default preview image (optional but nice)
Drop an image at `src/assets/og-default.jpg` (around 1200×630px, on-brand). It's the
picture that shows when a post with no cover image is shared on WhatsApp/Facebook.

---

## Get it on Google (do this once the blog is live)

1. Verify the site in **Google Search Console**.
2. Submit your sitemap: `yourdomain.com/sitemap.xml`.
3. For a new post, you can paste its URL into Search Console and click **Request indexing**.

The sitemap and `robots.txt` (both included here, both previously missing) are what let
Google find and crawl your pages.

---

## Want to preview locally first? (optional, for a developer)
```
npm install
npm run serve
```
Then open the local address it prints. Live-reloads as you edit.

---

## What's included
- `src/index.html`, `portal.html`, `privacy.html` — your existing pages, untouched.
- `src/blog/` — the Journal listing + your posts (Markdown).
- `src/_includes/` — the page templates, styled in your exact brand (Fraunces + Hanken,
  your forest/clay/cream palette, your flower mark).
- `src/admin/` — the writing editor and its configuration.
- `src/sitemap.njk`, `src/robots.txt` — SEO essentials.
- A first sample post: the Queensland registration guide — edit or delete it freely.

> Note: your main site's homepage doesn't yet have Open Graph tags (so sharing the
> homepage link shows no preview). The blog pages all have them. Adding them to the
> homepage is a small separate fix.
