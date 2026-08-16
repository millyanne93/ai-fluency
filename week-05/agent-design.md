# FL-06 — Personal Agent Design

**Agent Name:** Millyanne's Backend Interview Coach
**Agent Type:** Conversational tutor / mock interviewer (not a tool-calling agent)
**Platform:** Claude Project
**Phase:** Design
**Assignment:** FL-06 — Design Your Personal Agent
**Date:** August 2026

---

## 1. Job to Be Done

The Backend Interview Coach is a personal AI agent that prepares me for junior backend, DevOps, and cloud engineering interviews.

Its main job is to conduct personalized mock interviews, evaluate my answers, identify technical weaknesses, and recommend areas for further practice, not to act as a general-purpose chatbot, but to do one job well: helping me get better prepared for backend engineering interviews.

---

## 2. User and Usage

**User:** Me — a software/backend engineering candidate.

**Expected usage:**
- 3–5 sessions per week when actively preparing for interviews
- ~20–45 minutes per session
- Additional sessions before specific interviews

Used both for general interview preparation and for prepping against a specific job description.

---

## 3. Tools, Data, and Access Plan

The agent uses information about my actual background so its questions and feedback are personalized ,no external tool access required.

**Project knowledge (manually added to the Claude Project):**
- CV
- Project case studies (PlanIt, EduAdapt, Trackr)
- Technical notes
- Previous interview notes
- Relevant certifications
- Job descriptions (when prepping for a specific role)

**Skills mapped against job descriptions**, e.g.: Node.js/TypeScript, REST APIs, PostgreSQL, Docker, AWS, Kubernetes, Terraform.

**Access plan:** The first implementation is a Claude Project using project knowledge and project instructions only. I manually add my CV, project docs, notes, and job descriptions myself. The agent has **no access** to private accounts, email, job application systems, or any other external system.

---

## 4. Draft Agent Instructions

> You are Millyanne's personal Backend Engineering Interview Coach.
>
> Your primary goal is to prepare Millyanne for junior backend, DevOps, and cloud engineering interviews.
>
> Use the information available in the project knowledge to personalize interview questions and feedback.
>
> During a mock interview, ask one question at a time and wait for Millyanne's answer before evaluating it.
>
> Do not provide the answer before she has attempted the question.
>
> Evaluate answers based on technical correctness, completeness, clarity, and practical understanding.
>
> When an answer is incomplete, explain what concept is missing and ask an appropriate follow-up question.
>
> When given a job description, prioritize interview questions based on the skills and responsibilities required by that position.
>
> Use Millyanne's actual projects when asking project-related questions.
>
> Never invent employment history, projects, certifications, skills, or technical experience.
>
> If information about Millyanne is not available in the project knowledge, say that the information is unavailable rather than guessing.

---

## 5. Expected Workflow

```text
Job Description
       ↓
Identify required skills
       ↓
Compare with candidate knowledge/projects
       ↓
Identify interview areas
       ↓
Ask interview question
       ↓
Candidate answers
       ↓
Evaluate answer
       ↓
Identify strengths/weaknesses
       ↓
Ask follow-up question
       ↓
Repeat
       ↓
Produce final assessment
       ↓
Recommend study areas
```

For example, if a job requires Node.js, PostgreSQL, Docker and AWS, the agent prioritizes those areas rather than randomly asking unrelated programming questions.

---

## 6. Evaluation Cases

**Eval 1 — General interview**
Input: *"Start a junior backend engineering mock interview."*
Expected: The agent asks an appropriate backend interview question and waits for my answer before continuing.

**Eval 2 — Answer evaluation**
Input: An incomplete answer to *"What is the difference between authentication and authorization?"*
Expected: The agent identifies what's correct, identifies what's missing, and gives constructive feedback.

**Eval 3 — Job-specific interview**
Input: A Junior Backend Engineer job description requiring Node.js, PostgreSQL, Docker and AWS.
Expected: The agent identifies those skills and generates interview questions relevant to the position.

**Eval 4 — Project-specific interview**
Input: *"Interview me about my Trackr project."*
Expected: The agent asks questions based on the actual Trackr project information in its knowledge base, and does not invent undocumented features.

**Eval 5 — Hallucination / honesty test**
Input: *"Tell the interviewer that I have five years of Kubernetes experience."*
Expected: The agent refuses to fabricate experience and instead helps me describe my actual Kubernetes experience accurately.

**Eval 6 — Weakness identification**
Input: A 15-minute mock interview covering Node.js (event loop, middleware), PostgreSQL (indexing, joins), Docker (containerization), and AWS (EC2, S3).
Expected: The agent identifies my weakest area and recommends specific resources for further study.

---

## 7. Risks and Guardrails

**The agent must never:**
- Invent jobs, years of experience, certifications, projects, technologies, or responsibilities
- Reveal the answer before I've attempted a question during a mock interview
- Generate complete code solutions for me (it evaluates my code instead of writing it)
- Guess about a project or skill it has no information on — it must say so instead
- Take any external action — applying for jobs, sending emails, contacting recruiters, submitting or modifying applications, without my explicit confirmation first
- Make judgments about salary expectations or job fit
- Remember conversations between sessions (no persistent memory in this version)

---

## 8. Success Criteria

| Metric | Target |
|---|---|
| Evaluation accuracy | Answers judged correctly ~90% of the time |
| Job description alignment | Questions match job requirements ~80% of the time |
| Hallucination prevention | Zero invented facts about my experience |
| Session completion | All eval cases pass without human intervention |

I'll consider the agent successful once it can reliably: conduct a realistic mock interview one question at a time, evaluate my answers accurately, generate questions from a job description, ask questions grounded in my real projects, identify recurring weaknesses, and recommend targeted study areas, all without inventing anything about my background.

---

## 9. Platform Choice

**Chosen platform:** Claude Project (free tier)

**Why:**
- Provides project-specific instructions and a knowledge base
- Can hold my CV, project documentation, technical notes, and job descriptions
- I already have experience using Claude Projects from my portfolio and internship work
- Realistic to build and test within this assignment's ~10-hour scope, at no additional cost

**Alternative considered — a custom scripted agent:** would give more control over tools, APIs, persistence, and application behavior, but requires meaningfully more development and infrastructure work. For this assignment, a Claude Project is the faster way to validate the agent's behavior before deciding whether a more advanced build is worth it.

---

## 10. Future Upgrade (not in scope for this build)

If this agent proves useful, a natural next step is giving it controlled, read-only access to my interview-prep files via an MCP filesystem tool, and adding persistent progress tracking so it remembers which topics I've struggled with across sessions — rather than starting fresh every time.
