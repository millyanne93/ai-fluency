# Framed Case Studies

**Voice Card:** Technical, clear, honest, no buzzwords, warm.

---

## Before / After Example

**Generic AI Line:**
> "I am a results-driven software engineer with a passion for building scalable, innovative solutions and a proven track record of delivering high-impact projects."

**My Edited Version:**
> "I build backend APIs that stay correct and dependable when things go wrong — with validation, useful error responses, and graceful handling of third-party failures."

---

## 1. PlanIt: Production-Grade Cloud Infrastructure for a Multi-Service Application

**Why this project:** I built this to prove I can deploy a multi-service application to the cloud with Infrastructure as Code.

### The Problem

PlanIt was a strategic learning project. I wanted hands-on, production-level experience with Kubernetes, Terraform, and AWS that tutorials don't provide. I chose a familiar domain (task management) to focus my learning entirely on cloud infrastructure rather than splitting attention between application logic and deployment.

Most cloud-native demos are either too simple (a single container) or enterprise-scale with no clear learning path in between. Planit sits in the middle: a realistic, multi-service application (React frontend, Python backend, MongoDB database) fully containerized and deployed to AWS with infrastructure as code. The intended user was me, building DevOps skills, with the goal of proving I can take code from development to a deployed, scalable cloud environment.

### What I Built

**Architecture:** React frontend, Python backend, and MongoDB database, each component containerized in Docker and packaged as a Helm chart.

**Orchestration:** Amazon EKS, with each service defined as a Kubernetes Deployment and Service. The frontend and backend share a `frontend` namespace for communication; the database sits in an isolated `database` namespace for security. An NGINX Ingress Controller routes external traffic into the cluster.

**Infrastructure as code:** Terraform manages the VPC, EKS cluster, node groups, EBS CSI driver, and IAM roles, with a remote S3 backend and DynamoDB locking for safe, shared state management.

**Deployment pipeline:** fully automated and modular. Terraform provisions AWS → Helm installs MongoDB → Helm deploys the Python backend → Helm deploys the React frontend → Ingress exposes services → monitoring and logging layer on top. Each component is defined in its own Terraform module or Helm chart, so pieces can be updated independently.

### What Went Wrong

Three real problems surfaced:

- **EBS volumes not cleaning up.** MongoDB was configured to use EBS volumes via Helm, and everything worked during deployment, but `terraform destroy` didn't clean them up automatically. I only discovered this when an unexpected AWS bill showed up. I had to manually delete the orphaned volumes from the console.

- **Database password rotation breaking deployments.** Terraform regenerated the database password on every `apply`, which meant the backend periodically lost its connection to MongoDB and broke the deployment.

- **GitHub Actions timing issues.** Workflows failed intermittently due to Helm and database readiness; the pipeline would try to proceed before dependencies were actually ready.

None were catastrophic, but together they taught me: resource lifecycle management, secret stability, and CI/CD error handling aren't optional extras — they're core to whether a deployment is production-ready or just "works on the first try."

### Results

After validating the core architecture and extracting the lessons I set out to learn, I tore down the Planit infrastructure — partly because the goals were met and partly as a direct response to the billing issue, to avoid ongoing costs.

The Terraform code, Helm charts, and Kubernetes manifests remain version-controlled. Anyone with the code and AWS credentials could stand the entire environment back up in minutes, which is itself the proof point: reproducible, IaC-driven infrastructure, not a one-off manual setup.

**What Planit demonstrates:**

- Multi-service app (React + Python + MongoDB) successfully deployed to EKS
- Infrastructure as code covering VPC, EKS, node groups, and EBS CSI driver via Terraform
- Kubernetes deployment and dependency management via Helm
- Automated CI/CD pipeline via GitHub Actions
- Early-stage monitoring setup with Prometheus and Grafana

The tangible result is capability, not a live URL — but it's capability paired with the judgment to shut infrastructure down responsibly rather than let it run up costs.

### What I'd Do Differently

Three changes stand out, each mapped directly to a problem I hit:

1. **Use AWS Secrets Manager** instead of dynamically generated Terraform passwords, so the database connection string stays stable across deployments.

2. **Add explicit lifecycle rules for EBS volumes** so they're destroyed cleanly with `terraform destroy`, or at minimum, properly tagged for automated cleanup — directly addressing the surprise billing issue.

3. **Add retry logic to GitHub Actions**, particularly around Helm dependency ordering and database readiness checks, so pipeline failures reflect real problems rather than timing races.

Each is a direct fix for something that actually broke, not a theoretical improvement — exactly the kind of iteration a real production environment demands.

---

## 2. EduAdapt: Building a Reliable Backend for AI-Powered Adaptive Learning

**Why this project:** I built this to prove I can design a reliable API and integrate AI services effectively.

### The Problem

Traditional education tools treat every student the same way, delivering identical content regardless of individual strengths or gaps. EduAdapt was built to challenge that model: an adaptive learning platform where AI tailors content to each student's specific weaknesses, helping them close gaps faster than a one-size-fits-all curriculum ever could.

My role was to independently design and build the entire backend API layer, including the integration with Google's Gemini API that powers AI-generated question sets and personalized recommendations.

### What I Built

The backend is a Node.js/Express application backed by MongoDB, structured with a clear separation of concerns:

- **Routes, controllers, and models** organized for maintainability, with middleware handling authentication and role-based access control (teachers vs. students).
- **RESTful endpoints** for user management, assessments, and test results, with input validation and error handling to keep the API predictable.
- **Gemini API integration:** I send a structured prompt (topic, difficulty, question count, formatting instructions) and parse the JSON response into usable questions, validating and persisting them under the relevant assignment topic.
- **An adaptive feedback loop:** test results feed back into the recommendation logic, so the questions a student sees next reflect their actual performance, not a fixed syllabus.

This required decisions about where validation should live, how to structure prompts for consistent, parseable output, and how to keep the system reliable when a third-party AI service is a core dependency.

### What Went Wrong

Two real problems surfaced during development:

- **API drift.** After stepping away from the project for a few months, Google had updated the Gemini API and changed the request format. My integration broke. I worked through the migration guide and updated the integration to match the new contract — a small thing on paper, but it taught me to treat third-party API changelogs as a standing maintenance item, not a one-time setup task.

- **Rate limiting under load.** Requesting large question batches (20–30) regularly hit token limits and returned 429 errors. I reduced batch size per request and added a retry mechanism to handle transient failures gracefully instead of surfacing errors to the user.

### Results

EduAdapt is a fully functional working prototype built during my ALX Backend Specialization with all core features complete:

- Teachers can generate AI-powered question sets on demand.
- Students take personalized assessments and receive adaptive feedback.
- Authentication and role-based access control work reliably across both user types.

Validated with a small pilot group — 5–10 students and 2 teachers — who successfully created accounts, generated questions, completed assessments, and received feedback end-to-end with no blocking issues.

**Performance:**

- API response time: under 500ms on average
- Gemini-powered question generation: 2–5 seconds per set

**Next step:** deploying the frontend and backend to Vercel and the database to MongoDB Atlas over the coming weeks, moving EduAdapt from a validated prototype to a publicly accessible product.

### What I'd Do Differently

Looking back, three changes would make the system more robust from the start:

1. **Study Gemini's rate limits and versioning policy up front**, rather than discovering them under load or after a breaking API change.

2. **Decouple the AI integration into its own microservice** rather than embedding it tightly in the core backend. This would let the AI layer be updated, scaled, or even swapped independently — directly addressing the API drift and rate-limiting issues I hit.

3. **Scope tighter at the start** — build one core feature with a complete, working test-flow before layering on additional functionality, rather than building breadth early.

These aren't hypothetical lessons; they're the concrete architectural changes I'm carrying into the next phase of EduAdapt's development.

---

## 3. Trackr: A Reliable Equipment Tracking System for Small Businesses

**Why this project:** I built this to prove I can take an idea from concept to a deployed, working application.

### The Problem

The idea for Trackr came from a real signal: someone in a group chat asked if an equipment tracking tool existed for their business. Many small and mid-sized businesses still manage equipment with spreadsheets or paper logs; enterprise asset-tracking tools are overbuilt and overpriced for their needs.

Trackr targets that gap directly: a small business owner or operations manager who needs to know what equipment exists, who has it, and when it's due back — without an enterprise software budget or complexity.

### What I Built

Trackr is a full-stack application: React on the frontend, Node.js/Express on the backend, and MongoDB for storage. The backend follows an MVC pattern with a clean split between models, controllers, and routes, communicating through RESTful endpoints.

**Data model:**
- **Equipment:** name, serial number, status, checkedOutBy, checkedOutAt
- **User:** username, hashed password, role (regular user or admin)
- **History:** every borrowing event, linking equipmentId and userId with borrowedAt/returnedAt timestamps

**Core logic:** `checkedOutBy` stores a user's ObjectId when equipment is issued and resets to null on return, making availability a simple, reliable check. Before assignment, the backend checks status; if already issued, the request is rejected with a 400 error. This prevents double check-outs at the data layer rather than relying on frontend state.

**Reporting:** dashboard summary (total equipment, available equipment, and total users), personal borrowing history per user; recent activity overview of check-ins and check-outs, and a live issued-equipment list.

### What Went Wrong

Two real problems surfaced:

- **Dashboard data not populating reliably.** The equipment count would intermittently fail to load. My first instinct was to increase the loading timeout — that didn't fix anything. The real issue was architectural: the frontend code had grown large and tightly coupled, making it hard to isolate where the failure was happening. The fix was breaking the dashboard into smaller, focused components — separating the equipment list, summary stats, and user history into their own modules — which made errors traceable instead of buried in a monolith.

- **New users breaking on empty history.** When a new user registered, the borrowing history endpoint threw an error instead of loading, because it assumed a populated history array and got an empty one. The fix — still in progress — is having the API return an empty array gracefully rather than a 404, so the frontend can render a "no history yet" state instead of breaking.

### Results

Trackr is fully deployed and publicly accessible at **trackr-kd45.vercel.app**. It's a working prototype and portfolio piece demonstrating end-to-end full-stack capability: a professional UI, authentication with role-based access, equipment assignment, borrowing history, and real-time status updates.

It doesn't have active production users yet, but I've thoroughly tested the system across all core flows. One known limitation: the free-tier MongoDB Atlas instance can enter a sleep state during low activity, causing a brief delay on first load. I have a plan for this — either a keep-alive mechanism or a tier upgrade — and would implement it ahead of any live demo or real traffic.

The honest result: I took a real problem I identified myself, scoped it, and shipped a complete, deployed, functioning application — proving I can carry an idea from concept to production, not just build isolated features.

### What I'd Do Differently

The biggest lesson from Trackr is upfront planning on the frontend. The dashboard consumed a disproportionate amount of my time because I didn't plan the data flow and component structure before building.

If I started again, I'd:

1. **Design components before writing code** — a clear split into summary stats, equipment list, history log, and notifications panel from day one, not refactored in afterward.

2. **Plan state management and error handling as a system**, not per-feature, so data fetching behaves consistently across the whole app.

3. **Do real requirements gathering on what makes a dashboard useful** — beyond totals, surface overdue items, a live recent-activity feed, most-frequently-checked-out equipment, and alerts for low-stock or maintenance-needed equipment.

I'm already acting on these: the component refactor is underway, I'm standardizing API responses to return empty arrays for edge cases, and the MongoDB sleep issue is next on the list once traffic or demo needs justify the upgrade.
