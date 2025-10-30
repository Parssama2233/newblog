# Production Readiness Checklist

## ✅ Completed Optimizations

The following improvements have been made to the template:

1. **Configuration**
   - Settings centralised in `src/config/site.ts` and locale metadata in `src/config/locales.ts`.
   - Navigation, categories, projects, and contact links resolve per-locale automatically.
   - Dynamic manifest (`src/pages/manifest.webmanifest.ts`) and robots.txt (`src/pages/robots.txt.js`).

2. **SEO & Metadata**
   - ✅ Security headers (CSP upgrade, X-Content-Type-Options, Referrer-Policy).
   - ✅ Theme-color media queries, canonical links, prev/next pagination tags.
   - ✅ Locale-aware RSS feeds (`/rss.xml`, `/{lang}/rss.xml`) and sitemap index.
   - ✅ OpenGraph/Twitter tags resolved from config and post metadata.

3. **Performance**
   - ✅ CSS purging via `astro-purgecss` and CSSO minification in post-build script.
   - ✅ Critical client bundle assembled with esbuild (`scripts/build-client.mjs`).
   - ✅ Medium-zoom classes whitelisted to avoid PurgeCSS false positives.
   - ✅ Category/search data injected once per page to keep client scripts lean.

4. **Internationalization**
   - ✅ Locale detection in layouts, alternate links, and search.
   - ✅ Language switcher with persisted preference + redirect handling.
   - ✅ URL structure mirrors locale folders (e.g., `/ru/...`), fallback content for missing translations.

## 📋 Required User Actions Before Production

### 1. **Update Configuration**

Edit `src/config/site.ts`:

- [ ] Update `title` with your blog name (currently: "Morethan-Log")
- [ ] Update `description` (both English and Russian)
- [ ] Replace `"https://morethan-log-astro.sereja.com"` with your actual domain
- [ ] Update author information (currently: "Sereja", "demo@morethan-log.com")
- [ ] Update `contactLinks` with your social or contact profiles
- [ ] Configure features (dark mode, search, RSS, etc.)
- [ ] Update categories or add new ones
- [ ] Set your Google Analytics ID (if using)

Edit `src/config/locales.ts`:

- [ ] Confirm locale codes, labels, and switcher order
- [ ] Update `langTag`, `ogLocale`, and `flag` values for each locale
- [ ] Mark the correct default locale with `isDefault: true`

#### `package.json`
- [ ] Update `name` field (currently: "morethan-log-astro")
- [ ] Update `description` 
- [ ] Update `author` field (currently: "Sereja <demo@morethan-log.com>")
- [ ] Update `repository` URL (currently points to demo repo)
- [ ] Update `homepage` URL

#### Manifest (`src/pages/manifest.webmanifest.ts`)
- [ ] Update `name`, `short_name`, and `description`
- [ ] Adjust `start_url` / `scope` if deploying under a sub-path
- [ ] Point icon definitions to your real favicons (ensure both PNG + SVG as needed)
- [ ] Set `theme_color` and `background_color` to match your brand palette

#### Footer & Branding
- [ ] Update `src/components/layout/FooterCopy.astro` with your preferred attribution or replace with a custom component
- [ ] Swap out any placeholder logos / emojis in navigation, contact, and project links

### 2. **Replace Assets**

#### Favicon
- [ ] Replace `/public/favicon.ico`
- [ ] Replace `/public/favicon.svg`
- [ ] Replace `/public/favicon-16x16.png`
- [ ] Replace `/public/favicon-32x32.png`

#### Images
- [ ] Replace `/public/img/avatar.svg` with your avatar
- [ ] Replace `/public/img/og-image.svg` with your Open Graph image
- [ ] Replace `/public/img/rss-logo.svg` with your RSS channel logo (144x144px)
  - **Note**: For better RSS reader compatibility, also create `/public/img/rss-logo.png`
  - PNG format is more universally supported by RSS readers
  - The system checks for PNG first, then falls back to SVG
  - You can convert SVG to PNG using online tools or image editors
  - Common RSS readers may cache images, so changes might not appear immediately
- [ ] Consider replacing placeholder images in posts

### 3. **Content Updates**
- [ ] Update or remove example blog posts
- [ ] Update About page content
- [ ] Add your own blog posts
- [ ] Review and update categories as needed

### 4. **Optional Enhancements**

#### Accessibility Improvements
- [ ] Add proper alt text to all images (not "Description")
- [ ] Add aria-labels to interactive elements
- [ ] Test with screen readers
- [ ] Ensure color contrast meets WCAG standards

#### Security
- [ ] Consider adding Content Security Policy headers
- [ ] Enable HTTPS on your hosting
- [ ] Configure proper CORS if needed

#### Performance
- [ ] Optimize images (WebP format, proper sizing)
- [ ] Consider CDN for static assets
- [ ] Enable HTTP/2 on your server
- [ ] Configure proper caching headers
- [ ] If you remove third-party CDNs, host highlight.js styles/scripts locally via the client bundle

#### Analytics & Monitoring
- [ ] Set up Google Analytics or alternative
- [ ] Configure error tracking (e.g., Sentry)
- [ ] Set up uptime monitoring
- [ ] Configure performance monitoring

## 🚀 Deployment Checklist

1. [ ] Run `npm run build` locally and verify no errors
2. [ ] Test all pages and features locally
3. [ ] Verify RSS feed validates at https://validator.w3.org/feed/
4. [ ] Test sitemap at Google Search Console
5. [ ] Check all meta tags with social media debuggers
6. [ ] Test on multiple devices and browsers
7. [ ] Set up automated deployment (GitHub Actions, Netlify, Vercel, etc.)
8. [ ] Configure custom domain and SSL
9. [ ] Submit sitemap to search engines
10. [ ] Monitor Core Web Vitals after launch

## 📝 Post-Launch Tasks

1. [ ] Monitor 404 errors and fix broken links
2. [ ] Check Google Search Console for issues
3. [ ] Monitor page load performance
4. [ ] Gather user feedback
5. [ ] Regular content updates
6. [ ] Keep dependencies updated

### 5. **Verify Functionality**

1. [ ] Test language switching on all pages
2. [ ] Check all category pages load correctly
3. [ ] Verify RSS feeds:
   - [ ] Main feed at `/rss.xml` (default language)
   - [ ] Locale-specific feeds for every additional language (e.g. `/ru/rss.xml`)
   - [ ] Validate all feeds at https://validator.w3.org/feed/
4. [ ] Test sitemap generation at `/sitemap-index.xml`
5. [ ] Verify robots.txt at `/robots.txt`
6. [ ] Test theme switcher functionality

---

**Note**: This template is now production-ready from a technical standpoint. The remaining tasks are mostly customization and content updates specific to your use case. 
