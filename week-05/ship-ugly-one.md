# Week 5: Ship the Ugly One

---

## Live URL

**Portfolio:** https://millyanne93-portfolio.netlify.app/

---

## Sitemap Check

All pages from my sitemap are reachable:

| Page | URL | Status |
|------|-----|--------|
| Home | / | ✅ Reachable |
| Projects | /#projects | ✅ Reachable |
| About | /#about | ✅ Reachable |
| Contact | /#contact | ✅ Reachable |

---

### Project Cases

The Projects section contains my three main case studies:

- **PlanIt** — Cloud-Native Task Management
- **EduAdapt** — AI-Powered Adaptive Learning
- **Trackr** — Equipment Tracking System

Each project case can be opened from the Projects section.

Trackr also includes a link to its live deployment:
**Trackr:** https://trackr-kd45.vercel.app/

---

## Real Person Feedback

### Round 1

**Who I Asked**
I shared the live portfolio with a backend developer friend who has
approximately four years of experience working in cloud infrastructure.

**What They Said**
> "I can see you're a backend engineer right away from the hero section,
> which is good. The projects look real, you actually built and deployed
> these things. The Trackr live demo is impressive. What confused me was
> the chat widget — it's there but doesn't do anything. I wasn't sure if
> I was supposed to click it or if it was broken."

**What Confused Them**
The chat widget appeared to be non-functional and was distracting. They
were unsure whether it was supposed to be interactive or whether it was
broken.

**Did the Work Land?**
Yes. They immediately understood that I was positioning myself as a
backend engineer and found the deployed projects credible, particularly
the Trackr project and its live demo.

**Fix applied:** Switched the chat widget's backend from the Claude API
to Gemini's free tier — the widget is now functional and responding to
visitor questions.

---

### Round 2 — after the fix

**Who I Asked**
A second engineer, after re-sharing the updated portfolio.

**What They Said**
> "The site is clean and functional, and you have hosted it on Netlify.
> The chat widget works well. So far not bad."

**Did the Fix Land?**
Yes — the specific issue from Round 1 (a visibly broken, confusing chat
widget) was not mentioned as a problem this time; instead it was called
out as working well.

---

## "Still Ugly" List

1. **Missing PlanIt screenshots:** The infrastructure was taken down to avoid costs, so I need to redeploy it or find alternative visual evidence (e.g., Terraform code screenshots).
2. **Chat widget:** Was broken (Claude API credit issue) as of Round 1 feedback. Fixed by switching to Gemini's free tier; a second reviewer confirmed it working well in Round 2. Still watching for stability under real traffic, since it hasn't been tested at scale.
3. **Metrics are missing:** I don't have performance metrics for PlanIt yet; I'll add them after redeployment.
4. **Mobile responsiveness could be better:** The projects section is a bit cramped on smaller screens.
5. **Navigation could be more intuitive:** The mobile menu is functional but not as polished as I'd like.

---

## How My Site Is Built

### Frontend

The portfolio uses a simple frontend structure:

- **HTML:** The main portfolio structure is contained in `index.html`.
- **CSS:** The styling is used to control the layout, typography, colors, spacing, responsive behavior, and overall visual design.
- **JavaScript:** Frontend interactions such as navigation and the chat widget interface are handled with JavaScript.

No mystery code — I understand everything because I built it section by section with AI as my build partner.

### AI Chat Widget

The AI chat widget uses TypeScript for its backend serverless function.

The implementation is:

```text
Visitor
   ↓
Portfolio chat widget
   ↓
Netlify serverless function
   ↓
netlify/functions/chat.ts
   ↓
Gemini API (free tier)
   ↓
AI response
   ↓
Chat widget
```
