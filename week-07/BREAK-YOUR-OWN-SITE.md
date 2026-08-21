# Break Your Own Site — Hardening Review

**Portfolio:** Millyanne Wanjala
**Date:** 21 August 2026
**Site:** https://millyanne93-portfolio.netlify.app/

---

## Purpose

I tested my portfolio beyond the normal happy path to identify broken interactions, layout issues, accessibility problems, invalid inputs, and other edge cases before launch.

---

## Where It Breaks — Edge Case Testing

### Test: Empty chat input

**Action:** Clicked Send without entering any text.

**Expected:** No request should be sent and no empty message should appear in the conversation.

**Result:** PASS

**Fix required:** None.

### Test: Garbage input

**Action:** Submitted random text and non-question input.

**Expected:** The application should handle the input without crashing or breaking the UI.

**Result:** PASS

**Fix required:** None.

### Test: Rapid double submission

**Action:** Entered a question and clicked Send twice rapidly.

**Expected:** Only one request should be submitted.

**Result:** PASS

**Fix required:** None. The `isSending` guard and disabled button prevent duplicate submissions.

---

## Link Testing

| Link | Destination | Result |
|------|-------------|--------|
| Home | Home section | PASS |
| About | About section | PASS |
| Experience | Experience section | PASS |
| Projects | Projects section | PASS |
| Contact | Contact section | PASS |
| Updates | Updates section | PASS |
| LinkedIn | LinkedIn profile | PASS |
| GitHub | GitHub profile | PASS |
| Twitter | Twitter profile | PASS |
| Upwork | Upwork profile | PASS |
| CV | Google Drive CV | PASS |
| PlanIt GitHub | Repository | PASS |
| EduAdapt GitHub | Repository | PASS |
| Trackr GitHub | Repository | PASS |
| Trackr Live Demo | Vercel deployment | PASS |
| Email | Mail client | PASS |

---

## Cross-device Testing

### Mobile phone

**Device:** iOS phone

**Result:** PASS / findings listed below.

**Checked:**
- [x] Navigation
- [x] Mobile menu
- [x] Hero section
- [x] Projects
- [x] Project links
- [x] Contact section
- [x] Chat widget
- [x] Dark mode
- [x] Text readability

### Desktop

**Browser:** Chrome

**Result:** PASS

### Second browser

**Browser:** Firefox/Edge

**Result:** PASS

---

## SEO & Meta Tags Added

| Tag | What It Does | Added? |
|-----|--------------|--------|
| Page title | Browser tab / search result | ✅ |
| Meta description | Search snippet | ✅ |
| Keywords | Search engine keywords | ✅ |
| Open Graph title | Social sharing title | ✅ |
| Open Graph description | Social sharing description | ✅ |
| Open Graph image | Social sharing image | ✅ |
| Twitter card | Twitter sharing preview | ✅ |
| Favicon | Browser tab icon | ✅ |
| Apple Touch Icon | iPhone home screen icon | ✅ |
| Canonical URL | Preferred URL for search | ✅ |

---

## Findability & Speed

### Search Test

- "Millyanne Wanjala" — Indexing in progress
- "Millyanne Wanjala Backend Engineer" — Indexing in progress

**Status:** Known limitation — site is new, needs time and backlinks.

### Speed Check

**Tool:** [PageSpeed Insights](https://pagespeed.web.dev/)

| Metric | Score |
|--------|-------|
| Performance | [Add your score] |
| Accessibility | [Add your score] |
| Best Practices | [Add your score] |
| SEO | [Add your score] |

**Link:** [Add your PageSpeed Insights URL]

---

## Fix-Now — Fixed

### 1. Project contact CTA was redundant on mobile

**Problem:** The "Email me to schedule a technical interview" button appeared at the bottom of Projects even though the Contact section already contained the same CTA.

**Impact:** Made the mobile page feel repetitive and unnecessarily long.

**Fix:** Removed the duplicate CTA from the Projects section.

**Status:** FIXED

### 2. Contact cards were oversized on mobile

**Problem:** LinkedIn, Email, GitHub and Twitter cards occupied too much vertical space on smaller screens.

**Impact:** Contact section felt unnecessarily large.

**Fix:** Reduced card padding, icon size and spacing while maintaining usable tap targets.

**Status:** FIXED

### 3. Project action buttons were cramped on mobile

**Problem:** Code and Live Demo buttons appeared side-by-side on narrow screens.

**Impact:** Reduced available tap area and made the layout feel crowded.

**Fix:** Changed the project action container to:

    flex flex-col sm:flex-row

This stacks buttons on mobile and restores the horizontal layout on larger screens.

**Status:** FIXED

### 4. Missing SEO/Meta Tags

**Problem:** No meta description, Open Graph tags, or social sharing previews.

**Impact:** Site wasn't optimized for search engines or social sharing.

**Fix:** Added complete meta tags including description, keywords, Open Graph, Twitter cards, favicon, and Apple Touch Icon.

**Status:** FIXED

---

## Known Limitations

### 1. AI chat depends on the deployed API

The portfolio chat widget requires the `/api/chat` endpoint to be available. If the API is unavailable, the widget displays a network error rather than providing an answer.

**Status:** KNOWN LIMITATION

**Reason:** The chat depends on the backend service and cannot function without it.

### 2. Search engine indexing in progress

The portfolio does not yet appear prominently for name searches.

**Status:** KNOWN LIMITATION

**Reason:** Site is new and needs time for search engines to index and backlinks to build.

### 3. No custom domain

Currently using Netlify subdomain (`netlify.app`).

**Status:** KNOWN LIMITATION

**Plan:** Will point a custom domain in the future.

### 4. No analytics

Analytics not yet installed.

**Status:** KNOWN LIMITATION

**Plan:** Will add free analytics (e.g., Plausible, Umami) after custom domain setup.

---

## Summary

### Final Status

The portfolio has been tested beyond the happy path and the identified fix-now issues have been addressed. Remaining issues are documented as known limitations.

| Category | Count |
|----------|-------|
| **Tests Passed** | 15+ |
| **Fix-Now Issues Fixed** | 4 |
| **Known Limitations** | 4 |
| **SEO Tags Added** | 12 |

---

**This portfolio is ready for launch!** 🚀
