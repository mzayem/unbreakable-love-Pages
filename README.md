# Unbreakable Love – Deep Origin Static Pages

Static landing pages for the **Deep Origin** program by [Unbreakable Love](https://www.unbreakablelove.com).  
Three self-contained HTML files — no build step, no framework, no dependencies beyond Google Fonts and a CDN image.

---

## Pages

| File            | Route (clean URL) | Title                                                |
| --------------- | ----------------- | ---------------------------------------------------- |
| `index.html`    | `/`               | Deep Origin – Starter Module                         |
| `complete.html` | `/complete`       | Deep Origin – Complete Discovery + Free Consultation |
| `ultimate.html` | `/ultimate`       | Deep Origin – Ultimate Bundle                        |

---

## Project Structure

```
/
├── index.html          # Starter Module landing page
├── complete.html       # Complete Discovery + Free Consultation page
├── ultimate.html       # Ultimate Bundle page
├── .htaccess           # Apache clean-URL rewrite rules
└── README.md
```

---

## Tech Stack

- Pure HTML5 + CSS (no preprocessor)
- Vanilla JavaScript (inline, no external scripts)
- **Fonts:** [Geist](https://vercel.com/font) + [Lora](https://fonts.google.com/specimen/Lora) via Google Fonts
- **Color system:** CSS custom properties (`--primary: #a02021`, stone palette)
- **Layout:** Flexbox + CSS Grid, fully responsive
- No npm, no bundler, no build process required

---

## Clean URLs

By default, browsers require the full filename (`/complete.html`).  
Server config is included so `/complete`, `/ultimate`, and `/` all resolve correctly — see below.

### Apache

Place the included `.htaccess` in the root alongside the HTML files.  
Requires `mod_rewrite` to be enabled on your server.

```
/complete   → complete.html
/ultimate   → ultimate.html
/           → index.html
```

### Static Hosts (Hostinger)

| Host                 | What to do                                                                 |
| -------------------- | -------------------------------------------------------------------------- |
| **Netlify**          | Add a `_redirects` file (included below) or use `netlify.toml`             |
| **Vercel**           | Add a `vercel.json` with rewrites (included below)                         |
| **Cloudflare Pages** | Add a `_redirects` file — same as Netlify format                           |
| **GitHub Pages**     | Does **not** support server-side rewrites; use symlinks or duplicate files |

---

## Deployment

### Any Static Host

1. Upload all HTML files + the config file matching your server type.
2. No build command needed.
3. No environment variables needed.

### Local Preview (Python)

```bash
python -m http.server 8080
# Visit http://localhost:8080/complete.html
# (clean URLs only work with a real server config)
```

### Local Preview (Node – `http-server`)

```bash
npx http-server -p 8080
```

---

## Pages Overview

### `/` — Starter Module (`index.html`)

Entry-level offering. Covers the core Deep Origin program introduction, what's included, and a primary CTA to purchase or book.

### `/complete` — Complete Discovery (`complete.html`)

Mid-tier page. Promotes the Complete Discovery assessment package with a free consultation add-on. Key sections: hero, what's included card, program breakdown, testimonials, FAQ, and booking CTA.

### `/ultimate` — Ultimate Bundle (`ultimate.html`)

Top-tier page. The full Ultimate Bundle offer with the most comprehensive package details, pricing, and a high-intent CTA flow.

---

## Customization

All three pages share the same CSS variable system. To change the brand color across all pages, find and update:

```css
--primary: #a02021;
--primary-dk: #7f191a;
```

Fonts are loaded from Google Fonts. To self-host them, download from [fonts.google.com](https://fonts.google.com) and update the `<link>` tags.

---

## Notes

- All pages are fully self-contained — CSS and JS are inlined, so each file works standalone.
- Hero background image loads from `https://www.unbreakablelove.com/images/backgrounds/hero-couple.png`. If you move to a different domain, update the `background-image` URL in the `.hero-bg::after` CSS rule.
- No cookies, no tracking scripts, no third-party analytics included.
