# FL-04 Workflow — Research Paper Summarizer

## Overview

A 4-step workflow for summarizing research papers and technical articles using Claude. The workflow takes a PDF or text input and produces: structured notes (Problem → Method → Results → Limitations → Why It Matters), a 300-word plain-language summary, and review flags (what to verify, what questions to ask).

---

## Tools Used

- **Claude Project:** Workflow instructions (see below)
- **Input sources:** arXiv research papers (computer science/AI)

---

## Workflow Steps

| Step | What Happens | Output |
|------|--------------|--------|
| **1. Extract** | Claude reads the source and pulls out key information | Problem, Method, Results, Limitations, Why It Matters |
| **2. Synthesize** | Claude organizes the extracted information into a structured format | Structured notes (5 sections) |
| **3. Draft** | Claude writes a concise, plain-language summary | 300-word summary |
| **4. Review** | Claude flags what to verify and asks a critical question | Review flags + question |

---

## Claude Project Instructions
Research Paper Summarizer Workflow
Your Role
You are a research assistant helping me summarize academic papers and technical articles.

Step 1: Extract
When I give you a source (URL, text, or PDF content), extract:

The main problem the paper addresses

The methodology used

Key findings or results

Notable limitations

Why this matters (in plain language)

Step 2: Synthesize
Organize the extracted information into this exact structure:

Problem: [1 sentence]

Method: [1-2 sentences]

Results: [1-2 sentences]

Limitations: [1 sentence]

Why This Matters: [1 sentence]

Step 3: Draft
Write a concise summary (under 300 words) that:

Captures the main argument

Explains why it's important

Uses plain language (no jargon unless necessary)

Step 4: Review
After drafting, flag:

Any areas where you had to guess

Anything that needs human verification

One question I should ask about this paper

Output Format
For each run, provide:

Structured notes (Problem → Method → Results → Limitations → Why It Matters)

300-word summary

Review flags (what to verify)

text

---

## Five Runs

### Run 1: CogVis — Open-Vocabulary Change Detection

**Input:** [arXiv:2608.06150](https://arxiv.org/abs/2608.06150) — "CogVis: Must Open-Vocabulary Change Detection Perceive the Scene Anew for Every Query?"

**Time:** 3-5 seconds

**Output:**

*Structured Notes:*
- **Problem:** Earth-surface monitoring requires change detection models capable of recognizing arbitrary semantic categories, but existing methods entangle temporal perception, semantic discrimination, and region verification, causing unstable results and redundant computation.
- **Method:** Proposes CogVis, a cognitive memory-guided framework that reformulates OVCD as a perception-memory-verification paradigm, using a Scene Change Perceptron (SCP), Semantic Memory Calibrator (SMC), and Adaptive Region Filter (ARF).
- **Results:** Achieves state-of-the-art performance across seven benchmarks and improves inference throughput by 28.50%.
- **Limitations:** None explicitly stated in the abstract.
- **Why This Matters:** By sharing scene-level change perception across queries, the framework avoids repeating category-agnostic temporal perception, making it more efficient.

*Summary:* 
Formal verification of safety-critical software depends on precise specifications like Linear Temporal Logic (LTL), but most real-world requirements are written in ambiguous, unstructured natural language that's hard to convert automatically. Producing LTL by hand requires rare, expensive formal-methods expertise, so many organizations skip formal verification altogether.

This paper tests whether today's general-purpose large language models (LLMs) can close that gap — without any special training, just a few example prompts. The researchers picked 15 real requirements of varying difficulty from public specification documents and asked six different LLMs (from OpenAI, Anthropic, Google, and NVIDIA) to translate each one into LTL, five times per requirement, producing 450 outputs to evaluate.

The results are encouraging: most requirements were translated correctly by at least one model attempt the majority of the time, and accuracy kept climbing as more attempts were allowed. Interestingly, difficulty didn't track with how complicated a requirement looked — models struggled most with subtle logical traps, like getting the direction of an "if-then" statement backwards, or requirements involving different rules for different user roles. Consistency between repeated runs varied a lot between models and wasn't linked to accuracy — some models gave different-looking but equally correct answers each time.

The authors also had models explain their translations in plain language and suggest pairing this with a visualization tool (ltl2timeline) so non-experts can double-check the AI's work without needing to read formal logic themselves.

Overall, the study argues that LLMs are becoming genuinely useful assistants for turning messy, real-world requirements into rigorous, checkable specifications — a step that could make formal verification affordable for far more projects, provided humans still review implication-heavy or role-sensitive translations carefully.

*Review Flags:*
- Needs verification: Specific benchmark numbers should be checked against the full paper.
- Question to ask: How does the approach handle edge cases where temporal perception and semantic discrimination are tightly coupled?

---

### Run 2: CLI Coding Agent Transfer

**Input:** https://arxiv.org/abs/2608.07397 — "Open-Source CLI Coding Agents: Fine-Tuned Under One Scaffold, Degraded Under Another"

**Time:** 3-5 seconds

**Output:**

*Structured Notes:*
- **Problem:** Open-source CLI coding agents fine-tuned on trajectories from one scaffold (OpenHands) degrade substantially when deployed on other CLI scaffolds, but this gap had not previously been studied.
- **Method:** Introduces DCAS, an interception layer that routes API traffic between any CLI scaffold and any backend model, enabling controlled cross-scaffold testing. Runs three experiments: (RQ1) swap only the plan, (RQ2) fine-tune on planning-aware trajectories, (RQ3) test transfer to unseen scaffolds.
- **Results:** Fine-tuning installed the gap; supplying a plan from a frontier model boosted Pass@1 from 42.8% to 57.8% (+15%). Fine-tuning on only 576 examples transferred gains to unseen scaffolds (OpenCode +3.4%, mini-swe-agent +7.0%).
- **Limitations:** All experiments use a single benchmark (SWE-bench Verified), a single 30B model, and training data collected only under Claude Code.
- **Why This Matters:** Current CLI coding-agent benchmarks are misleading when reported under only one scaffold; a small, carefully constructed training set focused on planning can make an open model reliably strong across many deployment environments.

*Summary:* 
Agile software development is widely seen as an improvement over traditional project management approaches, yet most Agile projects are still considered challenged or outright fail. Part of the problem is that prior research on what actually drives Agile success has been inconsistent — different studies point to different critical success factors, contradicting the core idea that only a "critical few" factors should matter, and most of this research has focused narrowly on North America and Europe.

This study set out to identify, from a global and more geographically diverse set of Agile practitioners, which factors genuinely predict project success. The researchers surveyed 208 practitioners (over half based in Africa) about their most recent Agile projects and used a statistical modeling technique called PLS-SEM to test 54 possible relationships between 18 candidate success factors and three ways of measuring success: cost, schedule, and stakeholder satisfaction.

The results were strikingly focused: out of 18 factors tested, only three mattered statistically — Project Governance, Project Management, and Team Effectiveness. Project Governance (oversight and control mechanisms) was linked to staying on budget and on schedule. Project Management (planning, execution, and quality practices) was linked to staying on schedule and keeping stakeholders satisfied. Team Effectiveness (how well individuals and teams function together) was the strongest predictor of stakeholder satisfaction. Notably, simply following Agile practices more closely ("Level of Agile Use") did not, by itself, significantly predict success.

This is a meaningful simplification compared to earlier studies, which often identified long, inconsistent lists of success factors. The authors argue their model gives organizations a clearer, more actionable roadmap: rather than trying to optimize dozens of variables, teams and leaders should prioritize governance, disciplined project management, and team effectiveness to improve their odds of delivering successful Agile projects.

*Review Flags:*
- Guessed/inferred: None major — the summary reflects the paper's own stated findings and numbers without added interpretation.
- Needs human verification: The effect sizes (f²) are mostly small-to-medium (e.g., 0.023–0.146), meaning the significant relationships, while statistically real, may have modest practical impact — worth double-checking how the authors and any reviewers weigh statistical vs. practical significance.
- Question worth asking: Given the purposive LinkedIn-based sampling (not random), how might self-selection bias (e.g., toward practitioners active on professional networking sites, or from certain company types) have shaped which factors emerged as significant?
---

### Run 3: Explainable Systems Requirements

**Input:** (https://arxiv.org/abs/2608.07395) — "Towards a Unified Definition and Requirements Taxonomy for Explainable Systems"

**Time:** 3-5 seconds

**Output:**

*Structured Notes:*
- **Problem:** No universally accepted definition or standard exists for building explainable systems, despite growing regulatory pressure and a fragmented research landscape.
- **Method:** Analyzes and synthesizes existing definitions into unified formal definitions, distills nine general explainability requirements (R0–R9) into a structured taxonomy, and validates through a case study of a traffic management system.
- **Results:** Proposes formal definitions of "explanation" and "explainable/self-explainable system," introduces explanation timing (ante-hoc, post-hoc, or simultaneous), and produces a nine-requirement taxonomy.
- **Limitations:** Qualitative, non-systematic literature analysis; requirements taxonomy not claimed to be complete; case study uses only two illustrative scenarios.
- **Why This Matters:** Gives software engineers and regulators a common vocabulary and practical starting point for designing, certifying, and auditing explainable systems.


*Summary:* 
AI coding agents increasingly rely on "skills" — reusable pieces of guidance drawn from past experience — to handle unfamiliar tasks without needing to be retrained. But current methods for updating these skills work one failure at a time: when the agent messes up, it patches its skill set based on that single trace, without considering how the change might clash with other skills or whether it's too narrowly tailored to that one situation. Over time, this creates a bloated, inconsistent skill bank full of overly specific rules that don't transfer well to new problems.

This paper introduces GSE (Globalized Skill Evolution), which treats skill improvement as a system-wide optimization problem rather than a series of quick fixes. It builds a graph tracking how skills depend on, complement, or conflict with each other, so that updating one skill automatically triggers a check — and if needed, an update — of related skills to keep everything compatible. It also groups similar lessons learned across many failures and distills them into general, reusable skills, then tests these new skills against a library of past cases to make sure they actually improve things rather than just patching the original problem.

Tested on two real coding-agent systems across two tasks — generating tests that catch real bugs, and filtering out false bug reports — GSE beat existing approaches, including human-expert-written skill sets, by wide margins: recall improved by as much as 180% on test generation, and precision improved by as much as 96% on bug filtering. It also worked well when deployed on a company's proprietary bug-triage agent, boosting F1-score by over 60%.

The takeaway: giving AI coding agents a way to learn from experience that accounts for how different skills interact — rather than learning skills in isolation — makes them meaningfully more reliable and better able to generalize to new code and bugs.
*Review Flags:*

- Guessed/inferred: None significant — figures and claims are drawn directly from the paper's tables and text.
- Needs human verification: The paper uses DeepSeek-V4-Flash as the underlying LLM for all compared methods; results may differ with other base models, and this dependency is worth flagging if you're assessing generalizability of the numbers.
- Question worth asking: Since GSE's evolution process itself costs ~12% more tokens than the strongest baseline (Trace2Skill), what is the total cost tradeoff (evolution + deployment) at scale in a continuously operating production system, versus the accuracy gains reported?

---

### Run 4: 

**Input:** (https://arxiv.org/abs/2608.07317)- Towards Assurance Closure in AI-Native Large-Scale Agile Software Development

**Time:** 3-5 seconds

**Output:**

*Structured Notes:*
- **Problem:** Open-source CLI coding agents are almost all fine-tuned on trajectories collected under a single scaffold (OpenHands), and while these models perform well there, they degrade substantially when deployed on any other CLI scaffold (e.g., Claude Code, OpenCode) — a gap whose cause had not previously been studied, even though practitioners often choose scaffolds for cost, licensing, or privacy reasons unrelated to training data.
- **Method:** The authors introduce DCAS, an interception layer that routes API traffic between any CLI scaffold and any backend model without modifying the scaffold, enabling controlled cross-scaffold testing and trajectory collection. Using DCAS, they run three experiments: (RQ1) swap only the source/quality of an explicit plan while holding model and scaffold fixed; (RQ2) fine-tune a 30B model on DCAS-collected planning-aware trajectories under one scaffold (Claude Code), using two dataset variants (plan-only vs. plan+execution); (RQ3) test whether the fine-tuned model's gains transfer to a newer scaffold version and to two scaffolds never seen in training (OpenCode, mini-swe-agent).
- **Results:** Untrained base models showed little variation across scaffolds, but every fine-tuned model degraded on at least one non-training scaffold — confirming the gap is installed by fine-tuning, not model capability. Supplying a plan from a frontier model (Claude Sonnet 4.5) boosted Pass@1 on SWE-bench Verified from 42.8% to 57.8% (+15%) with no other changes. Fine-tuning on only 576 planning-aware trajectories installed both implicit planning conventions (plan-only training) and, when combined with execution data, productive use of explicit plans (52.8% no-plan, 55.8% with self-plan) — and these gains transferred to a newer Claude Code version (57.2%) and to unseen scaffolds OpenCode (+3.4%) and mini-swe-agent (+7.0%).
- **Limitations:** All experiments use a single benchmark (SWE-bench Verified) and a single 30B backend model, training data was collected only under Claude Code, and other frontier scaffolds (Codex CLI, Gemini CLI) could not be tested (Codex CLI became unresponsive during evaluation attempts).
- **Why This Matters:** The findings show that current CLI coding-agent benchmarks are misleading when reported under only one scaffold, and that a small, carefully constructed training set focused on planning behavior can make an open model reliably strong across many different deployment environments — a much more practically useful and reproducible outcome than today's scaffold-locked training pipelines.

*Summary:* AI coding agents that work through a command line ("CLI agents") are usually fine-tuned using trajectories collected under just one training environment, or "scaffold" — almost always OpenHands. These fine-tuned models score well when deployed under that same scaffold, but this paper shows they lose significant performance when deployed under a different one, like Claude Code or a minimal open-source alternative. Strikingly, the original untrained models don't show this problem — only after fine-tuning does the gap appear, meaning something about the training process itself is teaching the model habits that don't transfer.

The authors argue the culprit is "planning": both the explicit step of laying out a plan before writing code, and the implicit structural habits — how work gets broken into steps, when to explore versus act — that each scaffold encourages differently. To test this, they built a tool called DCAS that can swap any backend AI model into any CLI scaffold without changing the scaffold itself, letting them run clean, controlled experiments.

First, they found that simply giving a model a better plan — generated by a stronger AI — boosted its performance by 15 percentage points, with everything else held constant. That's a bigger effect than the scaffold-switching penalty itself, suggesting planning really is the key lever. Next, they fine-tuned a model on just 576 examples of planning-aware trajectories collected under one scaffold, and found this taught the model both senses of planning as separable skills. Finally, and most importantly, when they deployed this fine-tuned model on scaffolds it had never seen during training, its gains held up — even improving further on a newer version of the training scaffold, and still delivering solid gains on two very different unseen scaffolds.

The upshot: current AI coding benchmarks that report scores under only one scaffold are misleading, and training models to internalize planning as a general skill — rather than memorizing one tool's quirks — is a practical, low-cost way to build coding agents that work reliably no matter which tool they're deployed in

*Review Flags:*
- Guessed/inferred: None substantial — the summary tracks the paper's stated hypotheses and reported numbers directly.
- Needs human verification: Table values (e.g., 57.8% vs. 54.2–56.0% for different planners, and the RQ3 transfer percentages) are dense and worth spot-checking against the original tables if used for precise citation, given how many closely-spaced percentages appear across RQ1–RQ3.
- Question worth asking: Since all training data was collected under Claude Code specifically (a scaffold with rich, explicit planning structure), would the same small-data approach work if trajectories were instead collected under a scaffold with weaker or no planning structure (like mini-swe-agent) — or does the method's success depend on starting from a scaffold that already has strong planning conventions to distill?

---

### Run 5: 

**Input:** (https://arxiv.org/abs/2608.07135)- Rust Coreutils: Rebuilding Unix Foundations in a Modern Language

**Time:** 3-5 seconds

**Output:**

*Structured Notes:*
- **Problem:** No universally accepted definition or standard exists for building "(self-)explainable systems" — software that can explain its own behavior — despite growing regulatory pressure (the EU AI Act, IEEE Transparency Standard 7001-2021) and a fragmented research landscape with many competing, inconsistent definitions and taxonomies of explainability.
- **Method:** The authors analyze and synthesize existing definitions of "explanation" and "explainable system" from prior requirements-engineering literature into unified formal definitions, then distill nine general explainability requirements (e.g., producibility, understandability, correctness, timing, scope) into a structured taxonomy showing how these requirements interconnect, and validate the taxonomy through a case study of a traffic management system with two stakeholder scenarios.
- **Results:** The paper proposes formal definitions of "explanation" and "explainable/self-explainable system" that separate the explaining system from the explained system (and their respective contexts), introduces a definition of explanation timing (ante-hoc, post-hoc, or simultaneous), and produces a nine-requirement taxonomy (R0–R9) built around a core meta-requirement of explainability; the case study confirms all requirements apply and specifically motivates folding "explanation goodness" (correctness + measurable understanding) directly into the definition of an explanation itself (Proposition 1.1).
- **Limitations:** The work relies on qualitative, non-systematic literature analysis (not a formal systematic literature review), so relevant work may have been missed; the requirements taxonomy is not claimed to be complete; and the case study uses only two small illustrative scenarios rather than a broad empirical validation.
- **Why This Matters:** By offering unified, precise definitions and a structured set of interconnected requirements, this work gives software engineers and regulators a common vocabulary and practical starting point for designing, certifying, and auditing explainable systems — a necessary step toward meeting emerging legal requirements like the EU AI Act.

*Summary:* 
As software systems — from self-driving cars to smart factories — become more complex and AI-driven, it's increasingly hard for the people who use or are affected by them to understand why they behave the way they do. Regulations like the EU AI Act and an IEEE transparency standard already call for these systems to be "explainable," but there's no agreed-upon definition of what that actually means or how to build it into a system's design.

This paper tackles that gap. The authors first review the many existing definitions of "explanation" and "explainable system" scattered across prior research, and combine them into unified, formal definitions. A key innovation is separating the "explaining" part of a system from the "explained" part — recognizing that these don't have to be the same system, or even operate in the same context or at the same time (an explanation can come before, during, or after the thing it's explaining).

From there, the authors distill nine core requirements that a system needs to satisfy to be genuinely explainable — including the ability to actually produce explanations, present them understandably, ensure their content is correct, and adapt their timing and scope to different audiences. They organize these into a taxonomy showing how the requirements depend on and connect to one another.

To test whether this framework actually captures real-world needs, the authors apply it to a traffic-management case study involving two scenarios: a driver rerouted around construction, and an emergency vehicle responder needing a fast, trustworthy explanation of how to navigate an intersection safely. The case study confirms that all nine requirements are relevant, and especially highlights that explanations must be correct and demonstrably helpful — not just present information for its own sake. Based on this, the authors revise their core definition of "explanation" to explicitly require correctness and measurable understanding, calling this combined property "explanation goodness."

The result is a more unified, practical foundation that could support future standards, and eventually formal certification or auditing processes, for building trustworthy explainable systems.

*Review Flags:*
- Guessed/inferred: None significant — the summary reflects the paper's stated definitions, propositions, and case study conclusions directly.
- Needs human verification: The nine-requirement taxonomy (R0–R9) and its interconnections (Figure 5) are dense and relational; if you plan to cite or diagram the specific dependency structure, it's worth re-checking against the original figure rather than relying solely on the prose description.
- Question worth asking: Given that the case study used only two illustrative scenarios chosen by the authors themselves, how would this taxonomy hold up against a broader or more adversarial set of real stakeholder needs — are there explainability requirements (e.g., around explanation cost, or conflicting stakeholder goals) that a larger empirical study might surface but this framework doesn't yet address?

---

## Time-Saved Estimate

| Method | Time per Input | Total (5 runs) |
|--------|----------------|----------------|
| Manual (reading + notes + summary) | 15-20 minutes | 75-100 minutes |
| Workflow (using Claude) | 3-5 seconds per step (~30 seconds total) | ~3-5 minutes |
| **Time saved** | **~15-20 minutes per input** | **~70-95 minutes saved** |

**Setup cost:** 1 hour (creating the Claude Project and instructions)

**Breakeven point:** After 3-4 uses, the time saved exceeds the setup cost.

---

## Failure Points

| Failure Point | What Goes Wrong | How to Fix |
|---------------|-----------------|------------|
| **PDF formatting** | Some PDFs are scanned or have poor text extraction | Use NotebookLM or manual copy-paste |
| **Hallucinations** | Claude may add information not in the source | Human review required |
| **Token limits** | Very long papers may exceed Claude's context window | Use NotebookLM to pre-process, or feed the paper in sections |
| **Technical depth** | Very dense papers may need a second pass | Review catches this |

## What a Human Must Still Check

- [ ] Verify key facts and numbers are accurate
- [ ] Check for hallucinated information
- [ ] Confirm the summary captures the main argument
- [ ] Spot-check any critical figures against the original source

## Conclusion

This workflow successfully processes complex academic papers and produces structured, useful output in seconds. The time saved is significant (15-20 minutes per paper), and the workflow is repeatable across different inputs. The main limitations are PDF formatting and the need for human review to catch hallucinations, but these are manageable with a simple verification step.
