# Week 1: Draw the Path — Sitemap & AI Workspace

**Voice Card:** Technical, clear, honest, no buzzwords, warm.

---

## 1. Proof Statement & One-Line Why

**Proof Statement:**
> "I build backend APIs that stay correct and dependable even when things go wrong — validating input, returning useful errors instead of crashes, and gracefully handling failures in external services. I am proving this to a CTO or technical lead at a growing mid-sized company who needs an engineer who ships reliable features without creating fire drills for the ops team, so they will email me to schedule a technical interview."

**One-Line Why:**
> "My CV lists technologies and project names, but it cannot show that I designed and built an API that actually handles real-world failures gracefully — it cannot prove I think about error handling and defensive design."

---

## 2. Sitemap Sketch & Description

### Sketch

![Sitemap Sketch]
┌─────────────────────────────────────────────────────────────┐
│                    VISITOR ARRIVES                         │
│                                                             │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  HERO PAGE                                         │   │
│  │  • Headline: "I build dependable backend APIs."    │   │
│  │  • Subtext: "APIs that stay correct when things   │   │
│  │    go wrong."                                      │   │
│  │  • CTA: "Email me to schedule a technical         │   │
│  │    interview."                                     │   │
│  └─────────────────────────────────────────────────────┘   │
│                         │                                  │
│                         ▼                                  │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  WORK PAGE                                        │   │
│  │  • EduAdapt: Problem → What I Did → Result        │   │
│  │  • PlanIt: Problem → What I Did → Result          │   │
│  │  • Trackr: Problem → What I Did → Result          │   │
│  └─────────────────────────────────────────────────────┘   │
│                         │                                  │
│                         ▼                                  │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  ABOUT PAGE                                       │   │
│  │  • "I'm a backend engineer who prioritizes        │   │
│  │     reliability and clear error handling."        │   │
│  │  • Brief story + why I care about dependability   │   │
│  └─────────────────────────────────────────────────────┘   │
│                         │                                  │
│                         ▼                                  │
│  ┌─────────────────────────────────────────────────────┐   │
│  │  CONTACT PAGE                                     │   │
│  │  • "Email me to schedule a technical interview."  │   │
│  │  • Email: millyanne254@gmail.com                  │   │
│  │  • LinkedIn link                                  │   │
│  └─────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────┘

### Description

The sitemap is designed to walk a CTO or tech lead from landing to action in under 30 seconds:

1. **Hero:** Immediately states the claim ("I build dependable APIs") and the action ("Email me for a technical interview").
2. **Work/Case Studies:** Proves the claim with specific projects (Planit, EduAdapt, Trackr) framed as three-beat cases.
3. **About:** Briefly tells my story and reinforces my audience fit (mid-sized company).
4. **Contact:** Simple, clear call-to-action, repeating the one action.

---

## 3. Configured Claude Project

### Screenshot

![Claude Project Configuration]<img width="1366" height="728" alt="2026-07-20 (3)" src="https://github.com/user-attachments/assets/730973c6-a979-425d-a8aa-9100ae4dd119" />


### Custom Instructions (Summary)

- **Project Name:** Portfolio Build — Millyanne
- **Instructions:** Contains my background, proof statement, voice card, and a request to act as a tutor that explains its reasoning.

---

## 4. Pressure-Test Prompt & Output

### Prompt Used

> "This is my proof statement: I build and deploy secure, scalable full-stack web applications from design to production using modern frameworks and cloud infrastructure. My one action is getting visitors to contact me for full-stack or cloud/DevOps roles. This is my sitemap: Hero → Work → About → Contact. Does this sitemap walk my one person from landing, to believing me, to taking my one action, and does it actually prove my claim? Tell me which pages earn their place, which are wasted, and what is missing. Be specific, not encouraging."

### Claude's Output (Excerpt)

> "The sitemap is lean and purposeful, which is good. The 'Hero' page is essential for stating the claim immediately. Your 'Work' page is the strongest part of your proof — it will carry the case. The 'About' page is a potential weakness. It risks being a generic bio. To serve your claim, it must explain your specific journey (e.g., your learning approach, your pragmatic engineering mindset), not just your skills.
>
> *Suggestion for change:* I would rename 'About' to something more specific like 'My Process' or 'Engineering Philosophy' to make it prove your claim."

### What I Will Change

> I will change the 'About' page to 'My Approach' and write a brief section that explains my emphasis on error handling, code reviews, and building dependable systems — making the page earn its place by directly supporting my proof statement.
