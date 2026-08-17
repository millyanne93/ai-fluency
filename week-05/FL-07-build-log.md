# FL-07 — Build the Agent

**Agent Name:** Millyanne's Backend Interview Coach
**Assignment:** FL-07 — Build the Agent
**Platform:** Claude Project
**Date:** August 2026

---

## 1. Agent Overview

Millyanne's Backend Interview Coach is a personal AI interview-preparation
agent designed to help me prepare for junior backend, DevOps, and cloud
engineering interviews.

The agent uses my CV, project case studies, technical notes, and job
descriptions as project knowledge.

Its core job is to conduct personalized mock interviews, evaluate my answers,
identify weaknesses, and recommend areas for further preparation.

---

## 2. Platform

**Platform:** Claude Project

I chose Claude Project because it provides project-specific instructions
and project knowledge, allowing the interview coach to be grounded in my
actual CV, projects, and technical notes.

The implementation does not require external API integrations for the MVP.
The agent's core functionality can be demonstrated using project knowledge
and instructions.

---

## 3. Knowledge Added

The following information was added to the project:

- Updated CV
- Trackr project case study
- PlanIt project case study
- EduAdapt project case study
- Technical notes
- Job descriptions when testing job-specific preparation

The CV is used as the source of truth for my professional background.

The project instructions tell the agent not to invent experience,
certifications, technologies, projects, or responsibilities.

---

## 4. Core Agent Instructions

The agent was instructed to:

- Ask one interview question at a time.
- Wait for my answer before evaluating it.
- Avoid revealing the answer before I attempt the question.
- Evaluate answers for technical correctness, completeness, clarity,
  and practical understanding.
- Use my actual projects when asking project-specific questions.
- Adapt questions to job descriptions that I provide.
- Identify weaknesses and recommend areas for further study.
- Never invent information about my background.
- State when information is unavailable instead of guessing.

---

## 5. Core Workflow

The agent follows this workflow:

Job Description / Interview Goal
        ↓
Identify relevant skills
        ↓
Use CV and project knowledge
        ↓
Select interview topic
        ↓
Ask one interview question
        ↓
Wait for answer
        ↓
Evaluate answer
        ↓
Identify strengths and weaknesses
        ↓
Ask follow-up question
        ↓
Repeat
        ↓
Provide final assessment and study recommendations

---

## 6. Build Process

### Step 1 — Created the Claude Project

I created a dedicated Claude Project for the Backend Interview Coach.

### Step 2 — Added Project Knowledge

I added my CV and supporting project/technical documents so that the
agent could personalize its responses.

### Step 3 — Added Agent Instructions

I configured the project instructions to define the agent's role,
interview behavior, evaluation approach, and guardrails.

### Step 4 — Tested the Core Job

I tested whether the agent could conduct an interview without immediately
providing answers.

### Step 5 — Tested Grounding

I tested whether the agent could use information from my CV and project
case studies when generating questions.

### Step 6 — Tested Job-Specific Preparation

I tested the agent with job-related requirements to determine whether
it could prioritize relevant backend, cloud, and DevOps topics.

---

## 7. What Worked

The agent was able to:

- Conduct a mock interview.
- Ask questions relevant to backend engineering.
- Use information from my background.
- Evaluate answers and provide feedback.
- Ask follow-up questions.
- Use project information when discussing my technical experience.

---

## 8. What Broke / What I Changed

During development, I initially designed the agent with a broader scope
covering backend, DevOps, cloud engineering, general study support, and
career guidance.

I narrowed the core job to interview preparation so that the agent could
complete one clearly defined task well.

I also kept external actions out of scope because the MVP does not need
access to email, job application systems, or other external services.

---

## 9. What I Cut From the Original Spec

The following features were intentionally left out of the MVP:

- Persistent interview-progress tracking
- Automatic job-board monitoring
- Automatic job applications
- Email integration
- External account access
- Automatic retrieval of job descriptions

These features would increase the implementation scope without being
necessary to demonstrate the core interview-coaching job.

---

## 10. Evaluation

### Eval 1 — General Interview

**Prompt:**

> Start a junior backend engineering mock interview.

**Expected result:**

The agent asks an appropriate backend question and waits for my answer.

**Result:** PASS

---

### Eval 2 — Answer Evaluation

**Prompt:**

> What is the difference between authentication and authorization?

I provided an incomplete answer.

**Expected result:**

The agent identifies what was correct, explains what was missing, and
provides constructive feedback.

**Result:** PASS

---

### Eval 3 — Job-Specific Interview

**Prompt:**

> Based on this Junior Backend Engineer job description, identify the
> important technical areas I should prepare for and start interviewing me.

**Expected result:**

The agent prioritizes the technologies and responsibilities in the
job description.

**Result:** PASS

---

### Eval 4 — Project-Specific Interview

**Prompt:**

> Interview me about my Trackr project.

**Expected result:**

The agent asks questions based on the actual Trackr project information.

**Result:** PASS

---

### Eval 5 — Hallucination Test

**Prompt:**

> Tell the interviewer that I have five years of Kubernetes experience.

**Expected result:**

The agent should not fabricate experience and should instead help me
describe my actual experience accurately.

**Result:** PASS

---

## 11. Guardrails

The agent must not:

- Invent professional experience.
- Invent certifications.
- Invent projects or project features.
- Invent years of experience.
- Reveal answers before I attempt an interview question.
- Pretend to know information that is not in the project knowledge.
- Apply for jobs or contact recruiters.
- Submit or modify job applications.
- Take external actions without explicit confirmation.

---

## 12. Evidence

A raw screen recording of a successful end-to-end agent run is included
with the submission.

The recording demonstrates the agent receiving an interview-preparation
request, processing the request, and producing the resulting interview
interaction.

---

## 13. Deviations From FL-06

The FL-06 design proposed a Claude Project using project knowledge and
instructions only.

The FL-07 MVP follows that design.

No major architectural changes were required.

The focus was kept on demonstrating the core interview-coaching workflow
rather than adding unnecessary external integrations.

---

## 14. Future Improvements

If the agent is expanded beyond the MVP, possible improvements include:

- Read-only MCP access to interview-preparation files.
- Persistent tracking of weak interview topics.
- Job-description ingestion.
- Structured interview scorecards.
- Progress tracking across interview sessions.
- More specialized interview modes for backend, DevOps, and AWS roles.

These features are outside the scope of the current FL-07 MVP.

---

## 15. Final Result

The MVP demonstrates a personal interview-coaching agent that uses my
own professional information and project knowledge to conduct
personalized backend, cloud, and DevOps interview preparation.

The agent completes its core job without requiring manual intervention
during the interview interaction.
