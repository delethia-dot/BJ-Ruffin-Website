# BJ Ruffin Newsletter — MailerLite Setup Guide

Everything in this folder is what you'll paste into MailerLite to create branded newsletters that match bjruffin.com. Once set up, each new issue takes ~15 minutes.

---

## What's in this folder

| File | What it is |
|---|---|
| `newsletter-header.html` | The branded top of every newsletter (BJ Ruffin wordmark + issue line) |
| `newsletter-footer.html` | The branded bottom (signature, social links, unsubscribe) |
| `sample-newsletter.html` | A complete example issue. **Open this in your browser to preview.** |
| `brand-spec.md` | One-page reference for all your colors, fonts, and links |
| `README.md` | This file |

---

## How to preview the sample first

Before you touch MailerLite, double-click `sample-newsletter.html` in Finder. It'll open in your browser and show exactly what subscribers will see. This is what you're aiming for in MailerLite.

---

## ONE-TIME SETUP (do this once, ~30 minutes)

### Step 1 — Create a master template in MailerLite

1. Log into MailerLite → **Sites & forms** → **Email templates** → **Create template**.
2. Pick **"HTML editor"** (NOT the drag-and-drop builder — we want full control of the markup).
3. Name it: **"BJ Ruffin — Master Newsletter"**.

### Step 2 — Paste the sample

1. Open `sample-newsletter.html` in any text editor (TextEdit, VS Code, even a browser's "View Source").
2. Select all (`⌘A`), copy (`⌘C`).
3. Paste into MailerLite's HTML editor.
4. Click **Save**.

### Step 3 — Send a test to yourself

In MailerLite, click **"Send test email"** → enter your own email → check it on:
- ✅ Gmail (web + phone app)
- ✅ Apple Mail (Mac/iPhone)
- ✅ Yahoo Mail or Outlook (the worst-case clients — confirm the layout still holds)

If anything looks broken in Outlook, screenshot it and send to me. I'll fix.

### Step 4 — Save it as your master

In MailerLite, mark this template as your default for the BJ Ruffin Stories list.

---

## CREATING A NEW ISSUE (every time, ~15 minutes)

1. **Duplicate** the master template (don't edit the master directly).
2. Rename the duplicate (e.g. "Issue 03 — May 13 — Book One Launch").
3. **Edit only these areas** — leave the structural HTML alone:

   | Area | What to edit |
   |---|---|
   | Top issue line | Change `VOL. 04 · ISSUE 02 · MAY 2026` to the current issue |
   | Section eyebrow | `The Editor's Letter` → swap to issue theme (`New Release`, `Behind the Scenes`, etc.) |
   | Greeting | `Dear {$fields.name},` — leave the token, change the wording around it |
   | Letter body paragraphs | Rewrite freely — stay in Fraunces/serif font |
   | Featured book section | Update title, cover image, description, button URLs |
   | Free read strip | Keep as evergreen OR swap to whatever's in season |
   | Blog post excerpt | Update title + excerpt + Substack link |
   | Footer | **Don't touch.** Especially don't touch `{$unsubscribe}` and `{$url}` |

4. **Send a test to yourself** before scheduling the real send. Always.

---

## USING JUST THE HEADER OR FOOTER (alternative workflow)

If you'd rather use MailerLite's drag-and-drop blocks for the body of each issue, you can still keep the branded header/footer:

1. Create a new campaign with the **drag-and-drop** editor.
2. At the top, drop in a **"Custom HTML"** block.
3. Open `newsletter-header.html`, copy the markup between the `START` and `END` markers, paste in.
4. Build your body using MailerLite's drag-drop blocks (text, image, button). For colors and fonts, use the values from `brand-spec.md`.
5. At the bottom, drop in another **"Custom HTML"** block.
6. Open `newsletter-footer.html`, copy between START/END, paste in.

This is more flexible for adding/removing sections issue-to-issue, at the cost of a slightly less polished body section.

---

## IMPORTANT: Don't break these MailerLite tokens

These two snippets in the footer are auto-replaced by MailerLite at send time. **Keep them exactly as-is:**

```
{$unsubscribe}    →  becomes the personal unsubscribe link
{$url}            →  becomes the "view in browser" link
{$fields.name}    →  becomes the subscriber's first name
```

If you replace `{$unsubscribe}` with a hard-coded URL, your emails will fail compliance and your account can get suspended.

---

## Image hosting

Email clients can't render images stored on your computer — they need to be on a public URL. Two options:

**Option A — MailerLite's image library (easiest)**
1. In MailerLite → **Files** → **Upload**.
2. Upload your book covers, photos, etc.
3. Right-click → **Copy URL**.
4. Paste that URL into the `<img src="...">` tags in the newsletter.

**Option B — Reuse images already on bjruffin.com**
After you deploy to Netlify, your covers will be at:
```
https://bjruffin.com/images/covers/hoss-book1.jpg
https://bjruffin.com/images/covers/blossoming-love.png
```
You can reference those URLs directly in newsletter `<img>` tags. The sample already does this.

---

## Things you'll want to update before your first real send

- [ ] **Mailing address** in the footer (replace "Charlotte, North Carolina" with your real PO box or street address — required by CAN-SPAM law for every commercial email).
- [ ] **Issue line** — `VOL. 04 · ISSUE 02 · MAY 2026` should match your current issue numbering.
- [ ] **Eyebrow** — change `The Editor's Letter` to whatever fits the issue.
- [ ] **Featured book** — update title, cover, description, buttons.

---

## When something breaks

Common issues and fixes:

- **Outlook on Windows is showing weird spacing** → expected. Outlook ignores ~30% of CSS. The layout is designed to degrade gracefully there. As long as it's readable, leave it.
- **Image is missing alt text** → MailerLite will show a broken image. Always add `alt="..."` to every `<img>` tag.
- **Whole email is in serif when I want sans** → check that the `font-family` on that `<td>` includes `'DM Sans'` first.
- **Email got cut off in Gmail** → email is over 102 KB. Trim the HTML or move some content to a Substack post and link to it.

If you hit something I haven't covered, screenshot it and ping me.
