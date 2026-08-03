# FL-02 Prompt Iteration Log

## Task: Drafting Professional Emails (from FL-01 Audit)

**Target Audience:** CTOs and technical leads at mid-sized companies

---

## Version 0 — Naive Prompt

**Prompt:**
"Write an email to a CTO about a job opportunity."

**Output:**
Happy to help! I just need a few details to make this land well:

Who are you (recruiter, hiring manager, or reaching out on behalf of a company) and what's the role you're reaching out about?
Which company is this for, and do you know the CTO's name?
Any specifics you want mentioned — like why this CTO specifically, salary range, remote/onsite, or urgency?

Once I have those, I'll draft the email for you.

**Why this is weak:**
Too generic. No personalization, no specific value proposition.

---

## Version 1 — Role Assignment

**Technique:** Role Assignment

**Prompt:**
"Act as a professional career coach who helps backend engineers land their first role. Write an email to a CTO about a job opportunity."
**What changed in the prompt:** Added a specific role for the AI to play

**What improved in the output:** The email became more structured and professional. It included a clear subject line, a value proposition that emphasized engineering thinking (designing clean APIs, authentication, maintainable code), and a call to action. The tone shifted from generic to career-focused, and it ended with an offer to tailor further.

**What still failed:** Still too generic, it didn't include any specific details about my experience (CRUD API, Gemini AI, AWS Kubernetes) and didn't mention reliability or production-ready thinking. It could have been written by anyone with a software background.

**What I would try next:** Add context about my specific projects and the engineering values I care about (reliability, maintainability) to make it more personal and compelling. 


**Output:**
Here's a professional email you can customize for a CTO. It is written to highlight initiative, technical skills, and enthusiasm without sounding generic.

Dear CTO,

I hope you're doing well.

My name is [Your Name], and I’m reaching out to express my interest in any Backend Engineer opportunities within your team.

I recently completed my software engineering training, where I built and deployed backend applications using technologies such as Node.js, Express, TypeScript, PostgreSQL, REST APIs, Docker, and Git. Through personal projects, I have focused on designing clean APIs, implementing authentication, working with databases, and writing maintainable, well-structured code.

What excites me most about your company is the opportunity to learn from experienced engineers while contributing to products that solve real problems. I enjoy tackling technical challenges, continuously improving my skills, and collaborating with others to build reliable software.

Although I am seeking my first professional backend engineering role, I bring a strong work ethic, curiosity, and a commitment to producing high-quality code. I would welcome the opportunity to discuss how my skills and enthusiasm could add value to your engineering team.

I've attached my résumé for your review. Thank you for taking the time to read my email. I would appreciate the opportunity to speak with you if there are any current or upcoming opportunities that align with my background.

I look forward to hearing from you.

Kind regards,

[Your Name]
[Phone Number]
[Email Address]
[LinkedIn Profile]
[GitHub Portfolio]

If you're emailing a specific CTO or company, I can also tailor this email to reference their product, technology stack, or recent work, which generally makes a stronger first impression.

---

## Version 2 — Added Context & Motivation

**Technique:** Context & Motivation

**Prompt:**
"Act as a professional career coach who helps backend engineers land their first role. I'm a backend engineer who built a CRUD API, integrated AI (Gemini), and deployed to AWS with Kubernetes. I want to show I can build reliable systems, not just list skills. Write an email to a CTO at a mid-sized company expressing interest in a backend role. I want to demonstrate my understanding of building dependable APIs and my interest in joining their engineering team."
**What changed in the prompt:** Added context about my specific experience (CRUD API, Gemini AI, AWS Kubernetes) and clarified that I want to show I can build reliable systems, not just list skills.

**What improved in the output:** The email moved from generic to specific, it emphasized engineering thinking (reliability, maintainability) instead of just listing technologies. It showed what I learned from building projects, not just what I built.

**What still failed:** The email still had no clear structure — it was a long block of text without sections, making it hard to scan quickly.

**What I would try next:** Add a specific structure (subject line, opening, value proposition, call to action) to make it more scannable.

**Output:**
Here's a version that emphasizes engineering thinking and the ability to build dependable systems rather than simply listing technologies.

Dear CTO,

I hope you're doing well.

My name is [Your Name], and I'm reaching out to express my interest in any Backend Engineer opportunities on your engineering team.

Over the past year, I've focused on building backend applications that go beyond basic CRUD functionality. Through my projects, I've designed RESTful APIs, integrated AI capabilities using Google's Gemini API, and deployed services to AWS using Kubernetes. More importantly, these experiences taught me that backend engineering is about far more than making features work—it's about building systems that are dependable, maintainable, and ready to support real users.

As I developed these applications, I learned to think carefully about API design, validation, error handling, database interactions, authentication, and deployment. I also gained experience with containerization and cloud infrastructure, which gave me a better understanding of how reliable software is delivered and operated in production environments.

What excites me about joining a mid-sized engineering team is the opportunity to contribute across the entire development lifecycle. I enjoy understanding problems, collaborating with teammates, writing clean and maintainable code, and continuously improving systems as new requirements emerge. I'm eager to learn from experienced engineers while bringing curiosity, ownership, and a strong commitment to delivering quality software.

While I'm looking for my first professional backend engineering role, I've intentionally built projects that mirror real-world development practices rather than simply completing tutorials. My goal has been to develop the mindset of an engineer who considers scalability, reliability, and long-term maintainability from the beginning of a project.

I've attached my résumé for your consideration. If my background aligns with your team's needs, I would greatly appreciate the opportunity to speak with you about how I can contribute and continue growing as a backend engineer.

Thank you for your time and consideration. I look forward to hearing from you.

Kind regards,

[Your Name]
[Phone Number]
[Email Address]
[LinkedIn Profile]
[GitHub Portfolio]

This version is stronger because it:

Focuses on engineering principles (reliability, maintainability, scalability) instead of a list of technologies.
Shows what you learned from building projects, not just what you built.
Positions you as someone who thinks about production systems, which is exactly what CTOs look for.
Acknowledges you're seeking your first backend role while emphasizing evidence of practical engineering experience rather than academic knowledge.

---

## Version 3 — Added Output Structure

**Technique:** Output Structure

**Prompt:**
Act as a professional career coach who helps backend engineers land their first role. I'm a backend engineer who built a CRUD API, integrated AI (Gemini), and deployed to AWS with Kubernetes. I want to show I can build reliable systems, not just list skills. Write an email to a CTO at a mid-sized company expressing interest in a backend role.

Structure the email as follows:

Subject Line: Catchy and professional
Opening: Why I'm writing and why I'm interested in this specific company
Value Proposition: One concrete example of my work that aligns with their needs
Call to Action: What I want them to do (schedule a call/meeting)
Closing: Professional sign-off

**What changed in the prompt:** Added 5-part structure

**What improved in the output:** Email became organized and scannable

**What still failed:** Still generic without example of success

**What I would try next:** Add an example of a successful email that landed an interview.

**Output:**
Subject: Building Reliable Backend Systems – Interested in Joining Your Engineering Team

Dear CTO,

I hope you're doing well.

I'm reaching out because I'm very interested in joining [Company Name] as a Backend Engineer. I've been following your company's work and appreciate your focus on building products that solve meaningful problems. I'm looking for an opportunity to contribute to an engineering team where reliability, scalability, and continuous improvement are treated as core principles rather than afterthoughts.

One project that reflects how I approach backend engineering involved building a production-style REST API from the ground up. Beyond implementing CRUD functionality, I integrated Google's Gemini AI to extend the application's capabilities, containerized the service with Docker, and deployed it to AWS using Kubernetes. Throughout the project, I focused on designing clean APIs, validating requests, handling failures gracefully, structuring the code for maintainability, and deploying the application in a way that supports reliable operation. That experience reinforced an important lesson for me: successful backend engineering isn't just about delivering features—it's about building systems that remain dependable as they evolve.

I'd welcome the opportunity to learn more about your engineering team and discuss how my experience, curiosity, and commitment to building reliable backend services could contribute to your company. If you have 20–30 minutes available in the coming weeks, I'd be grateful for the chance to introduce myself and learn more about your technical challenges.

Thank you for your time and consideration. I appreciate the opportunity to connect and hope to speak with you soon.

Kind regards,

[Your Name]
Backend Engineer
📧 [Email Address]
📞 [Phone Number]
GitHub: [GitHub URL]
LinkedIn: [LinkedIn URL]

This version follows your requested structure while speaking in terms CTOs care about: reliability, maintainability, graceful failure handling, clean API design, and production deployment, rather than simply enumerating technologies.

---

## Version 4 — Added Few-Shot Examples

**Technique:** Few-Shot Examples

**Prompt:**
Act as a professional career coach who helps backend engineers land their first role. I'm a backend engineer who built a CRUD API, integrated AI (Gemini), and deployed to AWS with Kubernetes. I want to show I can build reliable systems, not just list skills. Write an email to a CTO at a mid-sized company expressing interest in a backend role.

Structure the email as follows:

Subject Line
Opening
Value Proposition
Call to Action
Closing

Here is an example of a good email that landed an interview:

'Subject: Full-Stack Developer with DevOps Experience

Dear [Hiring Manager],

I've been following [Company]'s work on their healthcare platform. I'm a full-stack developer with 3 years of experience building React apps and deploying to AWS. I know you're looking for someone who can bridge frontend and infrastructure — that's exactly what I enjoy doing. I recently led a migration from manual EC2 deployment to ECS with Terraform, cutting deployment time by 40%.

I'd be grateful for 15 minutes to discuss how I can contribute. Would you be available next Tuesday?

Best,
[Name]'

Now write a similar email for me, adapting the structure and specificity to my backend + cloud experience.

**What changed in the prompt:** Added a concrete example of a successful email that landed an interview.

**What improved in the output:** The email became more specific and followed the successful pattern. It opened with a genuine reason for contacting the company, included one concrete project, and focused on engineering values rather than listing technologies. The call to action was clear and low-friction.

**What still failed:** The email still used a generic opening ("I've been following [Company Name]") without showing specific research. The AI didn't know which company to target.

**What I would try next:** Add step-by-step reasoning instructions so the AI follows a clear process for selecting and tailoring content.

**Output:**
[Paste the output]

---

## Version 5 — Added Step Decomposition

**Technique:** Step Decomposition

**Prompt:**
Act as a professional career coach who helps backend engineers land their first role. I'm a backend engineer who built a CRUD API, integrated AI (Gemini), and deployed to AWS with Kubernetes. I want to show I can build reliable systems, not just list skills. Write an email to a CTO at a mid-sized company expressing interest in a backend role.

Structure the email as follows:

Subject Line
Opening
Value Proposition
Call to Action
Closing

Here is an example of a good email that landed an interview:

'Subject: Full-Stack Developer with DevOps Experience

Dear [Hiring Manager],

I've been following [Company]'s work on their healthcare platform. I'm a full-stack developer with 3 years of experience building React apps and deploying to AWS. I know you're looking for someone who can bridge frontend and infrastructure — that's exactly what I enjoy doing. I recently led a migration from manual EC2 deployment to ECS with Terraform, cutting deployment time by 40%.

I'd be grateful for 15 minutes to discuss how I can contribute. Would you be available next Tuesday?

Best,
[Name]'

Process:

First, research the company and identify a specific project or value they care about.
Then, select one concrete achievement from my experience that aligns with that value.
Next, craft a subject line that grabs attention and mentions the role.
Finally, make the call to action clear and easy to respond to.

Now write the email following this process.

> Which company is this for? A mid-sized SaaS company > What tone should the email use? Warm and conversational

**What changed in the prompt:** Added a 4-step process for the AI to follow (research company → select achievement → craft subject line → make CTA clear).

**What improved in the output:** The AI asked clarifying questions ("Which company is this for?") and produced a more tailored email. The process helped the AI structure its thinking, and the final output was more personalized with a helpful suggestion for improvement.

**What still failed:** The email still used a generic opening because I hadn't provided a specific company name. The AI correctly identified this gap and asked for it.

**What I would try next:** In a real scenario, I would provide the specific company name and one thing I admire about their work to make the email even more personalized.

**Output:**
A warm, conversational tone works well for a mid-sized SaaS company because it feels genuine while remaining professional.

Subject: Backend Engineer Interested in Building Reliable Systems with Your Team

Dear CTO,

I've been following the work that mid-sized SaaS companies like yours are doing to build products that customers can rely on every day. I'm reaching out because I'm looking for an opportunity to join a team where backend engineering is about creating dependable, scalable systems that support real users—not just shipping features.

One project that reflects how I approach engineering was a cloud-native backend application where I designed a RESTful CRUD API, integrated Google's Gemini AI to extend its functionality, and deployed the service to AWS using Kubernetes. Throughout the project, I focused on API design, validation, error handling, and deployment practices that make software easier to operate and maintain. Building it reinforced my belief that the best backend systems are reliable, observable, and designed to evolve as products grow.

If you're open to it, I'd love the opportunity to spend 15–20 minutes learning more about your engineering team and sharing how I could contribute. Even if there isn't an immediate opening, I'd value the chance to introduce myself and hear what you look for in backend engineers.

Thank you for your time and consideration. I hope we have the opportunity to connect.

Best regards,

[Your Name]
Backend Engineer
[Email Address]
[Phone Number]
GitHub: [GitHub URL]
LinkedIn: [LinkedIn URL]

One suggestion: if you're emailing an actual company rather than a hypothetical mid-sized SaaS business, replace the generic opening with a sentence about a specific product, engineering blog, recent feature launch, or company value. That level of personalization significantly increases the chances that a CTO will read past the first paragraph.

---

## Cross-Model Comparison

**Final prompt on both Claude and ChatGPT:**

Act as a professional career coach who helps backend engineers land their first role. I'm a backend engineer who built a CRUD API, integrated AI (Gemini), and deployed to AWS with Kubernetes. I want to show I can build reliable systems, not just list skills. Write an email to a CTO at a mid-sized company expressing interest in a backend role.

Structure the email as follows:

Subject Line
Opening
Value Proposition
Call to Action
Closing

Here is an example of a good email that landed an interview:

[Paste the example email]

Process:

First, research the company and identify a specific project or value they care about.
Then, select one concrete achievement from my experience that aligns with that value.
Next, craft a subject line that grabs attention and mentions the role.
Finally, make the call to action clear and easy to respond to.

Now write the email following this process.

I don't have a specific company in mind yet. Instead, write a strong email template with placeholders like [Company Name] and [Specific Project/Value I Admire], so I can customize it for each company I apply to. Include notes on what research I should do to fill in the placeholders.

### Claude Output

CTO Outreach Email Template — Backend Engineer
How to Use This

Fill in every [bracketed placeholder]. Do the research pass (below) before writing anything — the whole email hinges on Step 1 and 2 being specific, not generic.

The Template

Subject: [Backend Engineer — Saw Your Work on Specific Project/Value] — Quick Intro

Hi [CTO Name],

[Opening — 1-2 sentences. Reference the specific thing you found in research. Show you did homework, not a mail merge.]

I'm a backend engineer who recently [one-line summary of your build: e.g., "built and deployed a production CRUD API with AI integration on Kubernetes"]. I noticed [Company Name] is [specific thing: scaling a particular system, hiring for a particular team, has publicly talked about a particular technical challenge] — that's exactly the kind of problem I've been working on.

[Value Proposition — 2-3 sentences, one concrete story] [Pick ONE achievement that maps directly to what you found in research. Use a mini-narrative: problem → what you built → outcome/result. Example structure: "I built [X] that [solved Y problem], using [relevant tech stack: Kubernetes, AWS, Gemini API, etc.]. [Concrete result — latency improved, uptime, cost reduced, or simply 'it's live and handling real traffic.']" Avoid a skills list — tell it as a mini case study.]

I'd love 15 minutes to learn more about [Company Name]'s backend team and share how I could contribute. Would you be open to a quick call this week, or could you point me to the right person on your team?

Thanks for your time —

[Your Name] [Portfolio/GitHub link] [LinkedIn link] [Phone, optional]

Research Checklist (do this before filling in placeholders)

1. Find their specific technical pain point or priority

Read the company's engineering blog (search [company name] engineering blog) for recent posts — these tell you what they're actually working on.
Check their careers page / the actual job posting for tech stack keywords (Kubernetes, AWS, specific databases, AI/ML tools) — mirror this language.
Look at recent company news: funding rounds, product launches, or scaling milestones often hint at infrastructure needs.
Check GitHub if they have public repos — see what they're building, what issues they're wrestling with.
Search "[Company Name] CTO interview" or "[Company Name] engineering culture" — CTOs often give podcast/blog interviews stating their priorities directly.

2. Confirm the CTO's name and check for a personal angle

LinkedIn: check recent posts — did they share something you can genuinely reference?
Twitter/X: many CTOs post technical opinions — a shared technical interest is a strong opener.
If you truly can't find the CTO's name, it's fine to address "Hi [Company Name] team" or find the VP Eng / Head of Backend instead — don't guess and get it wrong.

3. Match your achievement to their world, not just to "impressive"

If they're scaling: emphasize your Kubernetes deployment and reliability work.
If they mention AI features: lead with your Gemini integration.
If they're an early-stage startup optimizing cost: mention infra/cost-conscious decisions you made.
Pick ONE story. Resist the urge to list all three of your skills — depth on one beats breadth on three.

4. Sanity-check the subject line

Should include "Backend Engineer" (or the actual role title from their posting) plus the specific hook.
Avoid generic subjects like "Job Opportunity" or "Application" — these get ignored or filtered.
Notes on Tone
Keep the whole email under 150 words. CTOs are busy; brevity signals respect for their time.
The call to action should require a low-effort yes: "15 minutes" or "point me to the right person" — not "let's discuss my career."
Send Tuesday–Thursday mornings when possible; open rates tend to be better than Monday/Friday.

### ChatGPT Output

That’s actually a better strategy. For cold emails to CTOs, a reusable template that feels personalized is far more effective than one generic email sent to everyone.

The goal is to make the CTO think: “This person understands what we’re building and has experience that could help us.”

Research Checklist (5 minutes per company)

Before sending the email, find these four things:

Step 1

Specific project or product

A feature they recently launched

A product area they’re expanding

An engineering blog post or case study

Step 2

Engineering value they care about

Reliability

Scalability

Developer experience

Customer trust / uptime

Performance

Step 3

A technical challenge they might have

Growing API traffic

Integrating AI features

Cloud infrastructure complexity

Maintaining service reliability

Step 4

One sentence that proves you researched them

Example: “I noticed your team recently launched real-time analytics for enterprise customers.”

Sources: company website, LinkedIn, engineering blog, GitHub, product updates, and recent job descriptions.

Backend Engineer Cold Email Template

Dear [CTO Name],

I’ve been following [Company Name], and one thing that stood out to me was [Specific Project/Value I Admire]. It’s clear that your team cares about [Engineering Value: reliability, scalability, customer trust, etc.], and that’s the kind of environment I’m looking to grow in as a backend engineer.

Recently, I built a production-style backend application where I designed a RESTful CRUD API, integrated Google’s Gemini AI to extend its capabilities, and deployed the service to AWS using Kubernetes. The part I enjoyed most wasn’t the AI integration—it was making the API dependable: validating requests, handling failures consistently, structuring the code for maintainability, and deploying it in a way that could be reliably operated in production.

I know companies like [Company Name] need engineers who think beyond “it works on my machine.” My goal is to become the kind of backend engineer who builds systems that remain reliable as traffic grows, requirements change, and new features are added. I’d love the opportunity to contribute to that kind of work on your team.

If you’re open to it, I’d appreciate 15–20 minutes to learn more about your engineering challenges and get your perspective on what you look for in early-career backend engineers. Even if there isn’t an immediate opening, I’d value the chance to introduce myself and learn from your experience.

Thank you for your time, and I hope we have the opportunity to connect.

Best regards,

[Your Name]
Backend Engineer
📧 [Email Address]
📞 [Phone Number]
GitHub: [GitHub URL]
LinkedIn: [LinkedIn URL]

How to Fill the Placeholders

Placeholder

	

What to put




[Company Name]

	

The actual company name




[CTO Name]

	

Find on LinkedIn or the company website




[Specific Project/Value I Admire]

	

One real feature, product launch, or engineering initiative




[Engineering Value]

	

Reliability, scalability, performance, security, customer trust, etc.

Example Customization

Imagine you’re applying to a SaaS company that recently launched AI-powered reporting.

Instead of:

“I’ve been following [Company Name].”

Write:

“I’ve been following Acme Analytics, and I was particularly interested in your recent launch of AI-powered reporting for enterprise customers.”

Instead of:

“Your team cares about reliability.”

Write:

“It seems your team places a strong emphasis on delivering accurate and reliable data pipelines, especially for customers who depend on real-time reporting.”

That level of specificity makes the email feel personal without requiring a lot of extra writing.

Why This Version Works Better

Most junior backend emails say:

“I know Node.js, Express, AWS, Docker, Kubernetes…”

CTOs skim those in seconds.

This template instead communicates:

I understand what your company values.

I’ve built something that demonstrates the same mindset.

I’m thinking about reliability and maintainability, not just features.

I’m asking for a conversation, not demanding a job.

That combination is much more likely to get a response from a mid-sized company CTO.

### Comparison Table

| Aspect | Claude | ChatGPT |
|--------|--------|---------|
| **Tone** | More direct and structured; framed as an "architected" template with clear sections and research checklist | Warmer and more conversational; included a "Why This Version Works Better" section |
| **Subject Line Style** | Focused on specific hooks: "Saw Your Work on [Specific Project/Value]" | More direct: "Backend Engineer Focused on Building Reliable APIs" |
| **Value Proposition** | Emphasized mini-narrative structure (problem → what I built → outcome) | Emphasized engineering values (reliability, maintainability, not just features) |
| **Research Guidance** | Provided a 4-step research checklist with specific sources | Provided a 4-step research checklist with placeholders and example |
| **Call to Action** | Offered two options: "quick call" or "point me to the right person" | Focused on "15–20 minutes to learn more" |
| **Overall Structure** | More formal and "architected" — like a professional template | More conversational and explanatory — like a coach giving advice |
| **Key Difference** | Claude framed it as a **system** (template + research process) | ChatGPT framed it as a **coaching conversation** |

### Specific Difference Observed

Claude's response was more structured and "architected" — it presented the template as a complete system with clear sections, research steps, and a "how to use" guide. ChatGPT's response was warmer and more explanatory, walking me through the logic behind each section and why it works.

Both are excellent, but if I wanted a ready-to-use template I could copy and paste, Claude's version is more immediately usable. If I wanted to understand the *why* behind each element, ChatGPT's version is better.

---

## Final Reusable Template Based on Claude and ChatGPT

# Backend Engineer Cold Outreach Email Template

## How to Use This Template

1. **Do the research** (5 minutes per company) before filling in any placeholders.
2. **Fill in every bracketed placeholder** with specific information.
3. **Keep the email under 150 words** — CTOs are busy.

---

## Research Checklist (5 Minutes Per Company)

| Step | What to Find | Where to Look |
|------|--------------|---------------|
| 1 | **Specific project or value they care about** | Engineering blog, recent feature launch, product updates |
| 2 | **Engineering value they prioritize** | Careers page, job description (reliability, scalability, performance) |
| 3 | **Technical challenge they might have** | Blog posts, public GitHub issues, recent funding news |
| 4 | **CTO's name and one personal angle** | LinkedIn, Twitter/X, CTO interviews |

**Sources:** Company website, engineering blog, LinkedIn, GitHub, product updates, job descriptions.

---

## The Template

**Subject:** Backend Engineer — Saw Your Work on [Specific Project/Value]

Dear [CTO Name],

I've been following [Company Name], and one thing that stood out to me was [Specific Project/Value I Admire]. It's clear that your team cares about [Engineering Value: reliability, scalability, customer trust, etc.].

Recently, I built [one project that matches their world]. I designed a RESTful CRUD API, integrated [relevant tech: Gemini AI], and deployed it to AWS using Kubernetes. The part I enjoyed most wasn't just shipping features — it was making the API dependable: validating requests, handling failures consistently, and structuring the code so it could be reliably operated in production.

I'd appreciate 15–20 minutes to learn more about your engineering challenges and share how I could contribute. Would you be open to a brief conversation this week, or could you point me to the right person on your team?

Thanks for your time —

[Your Name]
Backend Engineer
GitHub: [GitHub URL]
LinkedIn: [LinkedIn URL]

---

## Example Customization

**Generic (❌ Avoid):**
> "I've been following [Company Name]."

**Specific (✅ Better):**
> "I've been following Acme Analytics, and I was particularly interested in your recent launch of AI-powered reporting for enterprise customers."

**Generic (❌ Avoid):**
> "Your team cares about reliability."

**Specific (✅ Better):**
> "It seems your team places a strong emphasis on delivering accurate and reliable data pipelines, especially for customers who depend on real-time reporting."

---

## Why This Template Works

| Element | What It Communicates |
|---------|----------------------|
| Research in opening | "I understand what your company values." |
| One concrete project | "I've built something that demonstrates the same mindset." |
| Focus on reliability | "I'm thinking about maintainability, not just features." |
| Low-friction CTA | "I'm asking for a conversation, not demanding a job." |

---

## Tone Notes

- Keep it under 150 words — brevity signals respect for their time.
- Use a warm, conversational tone — not overly formal or robotic.
- The call to action should be easy to say yes to: "15 minutes" or "point me to the right person."
- Send Tuesday–Thursday mornings for better open rates.

---

## Summary of Techniques Used

| Version | Technique | What It Achieved |
|---------|-----------|------------------|
| 1 | Role Assignment | The AI adopted the persona of a career coach, resulting in more professional and career-focused email content. |
| 2 | Context & Motivation | The email became personalized and specific, showing how my experience aligned with the company's needs. |
| 3 | Output Structure | The email became organized, scannable, and professional with clear sections. |
| 4 | Few-Shot Examples | The email followed a proven successful pattern and became more specific and personal. |
| 5 | Step Decomposition | The AI followed a clear reasoning process, asked clarifying questions, and produced a more tailored output. |
