# BJ Ruffin Stories — bjruffin.com

Static HTML site for author BJ Ruffin. Deployed via Netlify from this repo.

## Pages

| Path | File |
|---|---|
| `/` | `index.html` |
| `/library` | `library.html` |
| `/blog` | `blog.html` |
| `/audiobooks` | `audiobooks.html` |
| `/my-story` | `my-story.html` |

## Project structure

```
.
├── index.html              # Homepage
├── library.html            # Series + book grid
├── blog.html               # Coming-soon teasers tied to newsletter
├── audiobooks.html         # Audio listings
├── my-story.html           # Author letter
├── netlify.toml            # Build + redirects + security headers
├── shared/
│   ├── site.css            # Shared styling
│   └── partials.js         # Reusable nav/footer injection
├── images/
│   ├── covers/             # Book covers (HoSS + L&L)
│   └── newsletter/         # MailerLite logo assets
└── newsletter/             # Email templates (paste into MailerLite)
    ├── newsletter-header.html
    ├── newsletter-footer.html
    ├── sample-newsletter.html
    ├── brand-spec.md
    └── README.md
```

## Local preview

```bash
python3 .devserver.py 8000
# open http://localhost:8000
```

## Deploy

Netlify watches this repo's `main` branch. Pushing here triggers a rebuild automatically. Build settings:
- Publish directory: `.` (project root)
- No build command (pure static)

Configuration is in `netlify.toml`.
