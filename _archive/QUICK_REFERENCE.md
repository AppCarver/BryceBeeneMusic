# Quick Reference Guide - Bryce Beene Website

## 📁 File Structure

```
website/
├── index.html              ← Main public website (single-page)
├── booking.html            ← TO CREATE (hidden booking page)
├── admin.html             ← Admin dashboard (protected)
├── 404.html               ← Error page
├── admin-login.html       ← ⚠️ Possibly unused
├── setup-data.html        ← Dev utility (excluded from hosting)
├── firebase-check.html    ← Dev utility (excluded from hosting)
├── firebase.json          ← Firebase hosting config
├── firestore.rules        ← Database security rules
├── images/                ← All image assets
├── videos/                ← Empty (videos are YouTube embeds)
└── documents/             ← PDFs (stage plot, rider)
```

## 🎨 Styling System

**Framework:** Tailwind CSS (CDN)  
**Custom Colors:**
- Primary: `#0b2447` (Deep Navy)
- Secondary: `#f8f0e5` (Cream)
- Accent: `#576f72` (Charcoal Green)

**Fonts:**
- Headlines: 'Lora' (serif)
- Body: 'Inter' (sans-serif)

**Custom Classes:**
- `.section-title` - Underlined headings
- `.font-headline` - Lora font
- `.bg-primary`, `.bg-secondary`, `.bg-accent` - Background colors

## 📄 Pages Overview

| Page | Route | Purpose | Access |
|------|-------|---------|--------|
| Main Site | `/` | Public EPK | Public |
| Booking | `/booking` | Booking form | Hidden (no nav link) |
| Admin | `/admin.html` | Dashboard | Protected (Firebase Auth) |
| 404 | `/404` | Error page | Auto (Firebase) |

## 🧭 Navigation Structure

### Main Site (index.html)
- Store (external)
- About → `#about`
- Music → `#music` (password-protected section)
- Videos → `#videos`
- Press → `#press`
- Photos → `#photos`
- Technical → `#technical`
- Contact → `#contact`

### Admin (admin.html)
- Emails → `#emails`
- EPK Password → `#epk`
- Admin Password → `#admin-pass`

## 🔥 Firebase Integration

**Project:** `bryce-beene-website`

**Firestore Collections:**
```
artifacts/{appId}/public/data/
  ├── newsletter_emails/        ← Subscriber emails
  └── epk/unreleased_password    ← Password hash
```

**Authentication:**
- Admin: Email/password
- Public: Anonymous (for newsletter signup)

## ✅ How to Add /booking Page

1. **Create `booking.html`** in root directory
2. **Copy structure from `index.html`:**
   - Head section (fonts, Tailwind, styles)
   - Navigation (but DON'T add booking link)
   - Footer
3. **Add booking content** in main section
4. **Use same styling** (copy `<style>` block)
5. **Optional:** Add rewrite in `firebase.json` for clean URL

**Example structure:**
```html
<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
    <!-- Copy from index.html -->
</head>
<body>
    <nav><!-- Same nav, NO booking link --></nav>
    <main>
        <section>
            <h2 class="section-title">Booking</h2>
            <!-- Your content -->
        </section>
    </main>
    <footer><!-- Same footer --></footer>
</body>
</html>
```

## ⚠️ Issues to Address

### High Priority
- [ ] Code duplication (nav, footer, styles in every file)
- [ ] Remove unused files (`admin-login.html`, dev utilities)
- [ ] Centralize CSS (create `styles.css`)

### Medium Priority
- [ ] Image optimization
- [ ] Add sitemap.xml and robots.txt
- [ ] Clean up commented code

## 📊 Site Statistics

- **Total HTML Files:** 7 (including utilities)
- **Public Pages:** 1 (index.html)
- **Admin Pages:** 1 (admin.html)
- **Image Assets:** ~10 files
- **PDF Documents:** 2 files
- **Lines of Code:** ~2,500+ (with duplication)

## 🔗 Key URLs

- **Live Site:** brycebeenemusic.com
- **Store:** store.brycebeenemusic.com (external)
- **Admin:** brycebeenemusic.com/admin.html
- **Booking:** brycebeenemusic.com/booking.html (after creation)

---

*For detailed information, see `SITE_AUDIT_REPORT.md`*
