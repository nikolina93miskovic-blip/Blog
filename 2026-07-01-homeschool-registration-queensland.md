# ─────────────────────────────────────────────────────────────
#  Bloom & Grow Learning — blog editor configuration
# ─────────────────────────────────────────────────────────────
#  ⚠️ ONE-TIME SETUP: replace OWNER/REPO below with your actual
#  GitHub repository (e.g. nikki/bloom-and-grow). See the README
#  for the ~30-minute wiring steps (GitHub auth + Netlify).
# ─────────────────────────────────────────────────────────────

backend:
  name: github
  repo: OWNER/REPO        # ⚠️ change me
  branch: main

# Where uploaded images are stored / how they're referenced on the live site.
media_folder: "src/assets/uploads"
public_folder: "/assets/uploads"

collections:
  - name: "blog"
    label: "Blog posts"
    label_singular: "Blog post"
    folder: "src/blog/posts"
    create: true
    # File name pattern, e.g. 2026-07-12-finding-your-rhythm.md
    slug: "{{year}}-{{month}}-{{day}}-{{slug}}"
    preview_path: "blog/{{slug}}"
    fields:
      - { label: "Title", name: "title", widget: "string" }
      - { label: "Publish date", name: "date", widget: "datetime" }
      - {
          label: "Short description",
          name: "description",
          widget: "text",
          hint: "1–2 sentences. Shows on Google and in link previews — write it for a real parent.",
        }
      - {
          label: "Cover image",
          name: "image",
          widget: "image",
          required: false,
          hint: "Optional. A calm, real photo works best.",
        }
      - { label: "Author", name: "author", widget: "string", default: "Nikki" }
      - { label: "Body", name: "body", widget: "markdown" }
