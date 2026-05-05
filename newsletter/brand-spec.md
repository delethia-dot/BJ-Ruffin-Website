# BJ Ruffin Stories — Brand Spec for Newsletter

A single-page reference for designing newsletter content in MailerLite (or any email tool) so it stays consistent with bjruffin.com.

---

## 1. Color palette

Paste these hex codes anywhere a color picker asks for them.

| Role | Hex | Use it for |
|---|---|---|
| Paper | `#F8F2EC` | Newsletter background (warm off-white) |
| Paper warm | `#F1E7DD` | Section dividers, light cards |
| Ivory | `#FBF7F2` | Block backgrounds with content |
| Rose | `#C58892` | Accents, links, eyebrows, hairlines |
| Rose soft | `#E6C2C7` | Light text on dark plum, secondary accents |
| Rose tint | `#F2DDE0` | Backgrounds for "free read" callouts |
| Plum | `#5A2F3A` | Primary buttons, dark headings, top strip |
| Plum deep | `#3D1F27` | Footer background |
| Ink | `#1F1A1B` | Primary body text |
| Ink soft | `#564B4D` | Secondary body text |
| Ink faint | `#8B7F81` | Captions, labels, tertiary text |

---

## 2. Fonts

All three are free Google Fonts. Email clients will fall back to system fonts where Google Fonts aren't supported (mostly Outlook Windows desktop), which is fine — the fallbacks below are chosen to look reasonable.

| Role | Primary | Fallback stack |
|---|---|---|
| Headings, pull quotes, signatures | **Fraunces** (variable serif) | `Georgia, 'Times New Roman', serif` |
| Body, buttons, nav | **DM Sans** | `-apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif` |
| Eyebrows, labels, footer headings, top strip | **DM Mono** | `ui-monospace, Menlo, Consolas, monospace` |

Google Fonts URL (for any web context — not needed in email itself):
```
https://fonts.googleapis.com/css2?family=Fraunces:ital,opsz,wght@0,9..144,300..600;1,9..144,300..400&family=DM+Sans:wght@300..600&family=DM+Mono:wght@400;500&display=swap
```

In MailerLite's font dropdown, select **"Fraunces"** for headings if available; otherwise pick **Georgia**. Pick **DM Sans** or fall back to **Helvetica** for body.

---

## 3. Typographic patterns

### Eyebrow (the small all-caps label above headings)
```
font-family: DM Mono
font-size:   11px
letter-spacing: 0.3em
text-transform: uppercase
color: #C58892
```
Examples: `THE EDITOR'S LETTER`, `NEW RELEASE`, `BEHIND THE SCENES`, `FREE READ`

### Heading (display)
```
font-family: Fraunces
font-weight: 300
font-size:   clamp(28px, 5vw, 48px)   ← in email use 36px or 42px
letter-spacing: -0.02em
color: #1F1A1B
italic accents in #5A2F3A
```

### Pull quote
```
font-family: Fraunces (italic)
font-size: 22px
color: #5A2F3A
border-left: 2px solid #C58892
padding-left: 24px
```

### Body paragraph
```
font-family: Fraunces (for "letter from BJ" voice)
            OR DM Sans (for newsy/feature voice)
font-size: 17–19px
line-height: 1.5–1.6
color: #1F1A1B
```

---

## 4. Buttons

Always pill-shaped (border-radius: 999px). Two variants:

### Primary button (main call-to-action)
```
background: #5A2F3A
color:      #F8F2EC
padding:    14px 24px
font-family: DM Sans
font-size:   13px
font-weight: 500
letter-spacing: 0.04em
border-radius: 999px
```
HTML to paste in a MailerLite HTML block:
```html
<a href="REPLACE_WITH_URL"
   style="display:inline-block;background:#5A2F3A;color:#F8F2EC;
          padding:14px 24px;font-family:'DM Sans',Helvetica,Arial,sans-serif;
          font-size:13px;font-weight:500;letter-spacing:.04em;
          border-radius:999px;text-decoration:none;">
  BUTTON TEXT
</a>
```

### Secondary button (outlined)
```
background: transparent
color:      #1F1A1B
padding:    14px 24px
border:     1px solid rgba(90,47,58,0.14)
border-radius: 999px
```

### Rose button (used on plum backgrounds)
```
background: #C58892
color:      #3D1F27
font-weight: 600
```

---

## 5. Section dividers

Use a thin rose hairline (1px solid `#C58892`) at 64–80px wide, centered, between major sections. NEVER a heavy solid line across the full width — too aggressive for the brand.

HTML pattern:
```html
<table role="presentation" width="64" cellpadding="0" cellspacing="0" border="0" align="center">
  <tr><td style="border-top:1px solid #C58892;height:1px;font-size:0;line-height:0;">&nbsp;</td></tr>
</table>
```

---

## 6. Brand voice (one paragraph)

> Sweet, clean romances about love, family, and the resilience of the human spirit — from the mountains of Vermont to the ranches of Sugar Springs. Slow burns. Soft landings. Always a happy ever after.

Use this verbatim in:
- Email footer tagline
- Social profiles
- Author bio sections

---

## 7. Standard links

| Where | URL |
|---|---|
| Website | `https://bjruffin.com` |
| Free read (BookFunnel) | `https://dl.bookfunnel.com/5ak59tk5wf` |
| Reader quiz | `https://quiz.bjruffin.com/sf/67cf92ee` |
| Amazon author page | `https://www.amazon.com/author/bjruffinstories` |
| L&L Book 3 (live) | `https://www.amazon.com/Love-Legacy-Saving-Maple-Grove-ebook/dp/B0D5BV4Z7W/` |
| Email | `mailto:bj@bjruffin.com` |
| Privacy policy | `https://www.freeprivacypolicy.com/live/c646f873-2a65-494b-8584-55ae36ba83bc` |
| Instagram | `https://instagram.com/bjruffinauthor` |
| Facebook | `https://www.facebook.com/bjruffinromance/` |
| Pinterest | `https://pin.it/5ar5LzB8l` |
| Goodreads | `https://www.goodreads.com/author/show/49152576.B_J_Ruffin` |

---

## 8. MailerLite-specific tokens

Drop these into your email content and MailerLite auto-fills them at send time. Don't replace with hard-coded values.

| Token | What it becomes |
|---|---|
| `{$unsubscribe}` | Personal unsubscribe link (REQUIRED in every email) |
| `{$url}` | "View this email in browser" link |
| `{$email}` | The subscriber's own email address |
| `{$fields.name}` | The subscriber's first name (for greeting) |

Example greeting line: `Dear {$fields.name},`

---

## 9. Email size & compatibility rules of thumb

- Lock content width to **600 px max**. Anything wider clips on iPhone.
- Use **inline CSS only** — `<style>` tags get stripped in Gmail.
- Use **table-based layout** (not divs/flex/grid) — Outlook desktop ignores modern CSS.
- Image alt text **always** — image blockers (~30% of recipients) need it.
- Test in Gmail web AND Apple Mail before sending. MailerLite has a free test-send feature.
- Keep total email size **under 102 KB** (Gmail clips after that, hiding your unsubscribe link).
