---
name: open-graph-preview
description: >-
  Configure, generate, and audit Open Graph (og:*) meta tags, Twitter/X Cards (summary_large_image),
  and 1200x630 social media link preview banners for websites and web apps. Use this skill whenever
  the user mentions Open Graph, OG tags, social media link preview, share card, link thumbnail,
  Messenger/Facebook/Discord/Telegram/WhatsApp/Viber/LinkedIn/iMessage/Twitter link preview, or wants
  a custom preview title and banner when sharing a deployed GitHub Pages, Vercel, Netlify, or custom URL.
argument-hint: "[preview-title] [deployed-url]"
---

# Open Graph (OG) & Social Media Link Preview Skill

End-to-end workflow for adding reliable, rich **Social Media Link Previews** across Messenger, Facebook, Discord, Telegram, Viber, WhatsApp, X/Twitter, LinkedIn, Slack, and iMessage.

---

## Non-Negotiable Crawler Rules

1. **Absolute `https://` URLs Only:** Social crawlers (`facebookexternalhit`, `Twitterbot`, `Discordbot`, `TelegramBot`, `WhatsApp`) frequently reject relative paths (`/assets/og.jpg` or `./og.png`). Every `og:image`, `og:image:secure_url`, `twitter:image`, `og:url`, and `<link rel="canonical">` **must** use the full `https://...` production URL.
2. **Server / Static `<head>` Rendering Required:** Most social crawlers do **not** execute client-side JavaScript. Inject tags directly into static `index.html` (vanilla HTML / Vite / CRA) or server-rendered metadata (`app/layout.tsx` in Next.js, SSR/SSG), never solely via client-side `useEffect` or un-prerendered `react-helmet`.
3. **GitHub Pages Case-Sensitivity:** GitHub Pages serves project repositories via a case-sensitive CDN (`https://<user>.github.io/<ExactRepoName>/`). If the repo is `CHECKLIST`, `/checklist/` returns `404` to crawlers. Always match exact repository casing.
4. **Universal Image Format & Weight:** Use **JPEG (`.jpg`)** or **PNG (`.png`)** at **`1200 × 630` px (`1.91:1`)** and keep file size **under `250 KB`** (`< 300 KB` strict ceiling for WhatsApp/mobile Messenger). Avoid `.svg`, `.avif`, or `.webp` for `og:image` because several chat crawlers silently skip them.

---

## Step-by-Step Workflow

### Step 1: Resolve the Canonical Production URL

Before writing any tags, determine the exact deployed URL:
1. Inspect `git remote -v`, `package.json` (`homepage`), `vite.config.*` (`base`), `next.config.*`, `CNAME`, or `vercel.json`.
2. **For GitHub Pages:** Construct `https://<owner>.github.io/<ExactRepoName>/` preserving exact uppercase/lowercase repo characters from the remote URL (or `https://<custom-domain>/` if `CNAME` exists).
3. **For Vercel / Netlify / Custom Domains:** Use the production `https://` domain (or `process.env.NEXT_PUBLIC_SITE_URL` with the production fallback in Next.js).
4. If the project has no remote or known domain yet, ask the user for the target URL (or use a clearly marked `https://your-domain.com` placeholder and tell them to update it upon deployment).

### Step 2: Prepare or Generate the `1200 × 630` Preview Image

1. Check whether the project already has a dedicated OG image or hero banner.
2. **Create or crop a `1200 × 630` px (`1.91:1`) `.jpg` or `.png` image:**
   - **Safe Zone:** Keep primary text, logos, and character faces centered within the middle **`630 × 630` px** region (leave `~120px–250px` side padding) so square `1:1` mobile chat thumbnails never clip text.
   - **Compression:** Optimize JPEG quality (`82–88`) so the final file is **`< 250 KB`**.
   - If cropping/compositing from an existing project image, use a quick Python `Pillow` (`PIL`) script (`ImageOps.fit` or centered gradient card) or generate an artwork banner matching the project's theme and requested tag title.
3. **Save to the public static output path:**
   - Vanilla HTML: `assets/og-preview.jpg` (served at `<PROD_URL>/assets/og-preview.jpg`)
   - Vite / React / Next.js: `public/og-preview.jpg` (served at `<PROD_URL>/og-preview.jpg` or `<PROD_URL>/<base>/og-preview.jpg`)

### Step 3: Inject Complete Synchronized Meta Tags

Synchronize the requested preview headline (e.g., `"DAY WITH ME"`) across all five title surfaces: `<title>`, `og:title`, `og:site_name`, `twitter:title`, and `apple-mobile-web-app-title`.

#### Template A — Static HTML / Vite + React (`index.html` inside `<head>`)

```html
  <!-- Primary Meta Tags -->
  <title>PREVIEW_TITLE</title>
  <meta name="title" content="PREVIEW_TITLE" />
  <meta name="description" content="CONCISE_DESCRIPTION_110_TO_160_CHARS" />
  <meta name="apple-mobile-web-app-title" content="PREVIEW_TITLE" />
  <link rel="canonical" href="https://EXACT_DOMAIN_AND_PATH/" />

  <!-- Open Graph / Facebook / Messenger / Discord / Telegram / WhatsApp -->
  <meta property="og:type" content="website" />
  <meta property="og:site_name" content="PREVIEW_TITLE" />
  <meta property="og:url" content="https://EXACT_DOMAIN_AND_PATH/" />
  <meta property="og:title" content="PREVIEW_TITLE" />
  <meta property="og:description" content="CONCISE_DESCRIPTION_110_TO_160_CHARS" />
  <meta property="og:image" content="https://EXACT_DOMAIN_AND_PATH/og-preview.jpg" />
  <meta property="og:image:secure_url" content="https://EXACT_DOMAIN_AND_PATH/og-preview.jpg" />
  <meta property="og:image:type" content="image/jpeg" />
  <meta property="og:image:width" content="1200" />
  <meta property="og:image:height" content="630" />
  <meta property="og:image:alt" content="ACCESSIBLE_IMAGE_DESCRIPTION" />
  <meta property="og:locale" content="en_US" />

  <!-- Twitter / X Large Summary Card -->
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:url" content="https://EXACT_DOMAIN_AND_PATH/" />
  <meta name="twitter:title" content="PREVIEW_TITLE" />
  <meta name="twitter:description" content="CONCISE_DESCRIPTION_110_TO_160_CHARS" />
  <meta name="twitter:image" content="https://EXACT_DOMAIN_AND_PATH/og-preview.jpg" />
  <meta name="twitter:image:alt" content="ACCESSIBLE_IMAGE_DESCRIPTION" />
```

#### Template B — Next.js App Router (`app/layout.tsx`)

```tsx
import type { Metadata } from "next";

const SITE_URL = process.env.NEXT_PUBLIC_SITE_URL || "https://EXACT_DOMAIN_AND_PATH";
const PREVIEW_TITLE = "PREVIEW_TITLE";
const PREVIEW_DESC = "CONCISE_DESCRIPTION_110_TO_160_CHARS";

export const metadata: Metadata = {
  metadataBase: new URL(SITE_URL),
  title: PREVIEW_TITLE,
  description: PREVIEW_DESC,
  applicationName: PREVIEW_TITLE,
  appleWebApp: { title: PREVIEW_TITLE },
  alternates: { canonical: "/" },
  openGraph: {
    type: "website",
    url: SITE_URL,
    siteName: PREVIEW_TITLE,
    title: PREVIEW_TITLE,
    description: PREVIEW_DESC,
    locale: "en_US",
    images: [
      {
        url: "/og-preview.jpg",
        width: 1200,
        height: 630,
        alt: "ACCESSIBLE_IMAGE_DESCRIPTION",
        type: "image/jpeg",
      },
    ],
  },
  twitter: {
    card: "summary_large_image",
    title: PREVIEW_TITLE,
    description: PREVIEW_DESC,
    images: ["/og-preview.jpg"],
  },
};
```

### Step 4: Verify & Bust Social Caches

Before finishing, verify all items:
- [ ] Preview image exists on disk at the public path (`1200 × 630` px, `.jpg`/`.png`, `< 250 KB`).
- [ ] `og:image:type` matches actual MIME type (`image/jpeg` for `.jpg`, `image/png` for `.png`).
- [ ] Every URL in `og:url`, `og:image`, `og:image:secure_url`, `twitter:image`, and `canonical` uses `https://` and matches exact repository/route casing.
- [ ] No duplicate conflicting `<title>` or `og:*` tags remain in `<head>`.
- [ ] **If updating an already-deployed link:** Append a cache-busting query parameter (e.g., `?v=2`) to the `og:image` and `twitter:image` URLs so Messenger, Discord, and Telegram fetch the new banner immediately, or re-scrape using:
  - Facebook / Messenger: `https://developers.facebook.com/tools/debug/`
  - LinkedIn: `https://www.linkedin.com/post-inspector/`
  - Telegram: `@WebpageBot`

