# Mantel Interview — Slide Outline

Paste each slide section into Google Slides / PowerPoint.
Executive audience: lead with impact, keep bullets short.

---

## SLIDE 1 — Code Review: Top 5 Recommendations

**Title:** Kohonen SOM — Code Review & Top 5 Recommendations

**Sub-title:** Sam's implementation is a correct and readable first pass.
Five targeted changes would make it production-grade.

| # | Recommendation | Why It Matters |
|---|---|---|
| 1 | **Vectorise the node-update loop** | 20–45× faster; no hardware upgrade needed |
| 2 | **Remove hardcoded input dimension** | Generalises to any dataset, not just RGB |
| 3 | **Wrap in a class (sklearn-style)** | Enables serialisation, testing, and pipeline integration |
| 4 | **Add reproducibility controls** | Required for debugging, compliance, and CI/CD |
| 5 | **Define a productionisation path** | Serialisation → REST API → observability → scale |

**Speaker notes:**
- Full working notebook: [GitHub link]
- Benchmark shows 20–45× speedup from rec #1 alone (measured on 10×10 to 30×30 grids)
- Recs #2–4 are each 1–5 lines of code; rec #5 is a design conversation

---

## SLIDE 2 — Experience: LLM-Powered Gambling Review Copilot (Cash App)

**Title:** Automating High-Stakes Financial Case Review with LLMs

**The Problem**
- Operations team manually reviewed every gambling-flagged account
- Each case: ~2–3 minutes of reading free-text notes and making a decision
- Not scalable as case volume grows; human review is the bottleneck

**The Solution**
- Led a cross-functional team (MLOps lead + Ops lead) to ship an LLM-powered batch processing pipeline
- Core workflow: **initiator notes processing** — LLM reads free-text case notes and identifies gambling patterns using few-shot examples
- LLMs excel at this: unstructured text analysis that would require complex rule engineering otherwise

**Guardrails (responsible AI in a regulated context)**
- **PK matching:** Primary keys in the LLM's output must exactly match those from the input — no hallucinated case IDs
- **Evidence grounding:** Every reference or citation the LLM makes must appear verbatim in the source text — prevents confabulation
- Both checks run automatically before any LLM output is acted on

**Outcome**
- Batch processing replaces manual one-by-one review
- Ops team focuses on edge cases and oversight rather than routine classification
- *(Add specific throughput / time-saved numbers here if shareable)*

**Speaker notes:**
- Emphasise the guardrails — shows awareness of LLM failure modes in production
- Be ready to go deep on: prompt design, few-shot selection strategy, how PK matching works technically, how you evaluated accuracy

---

## SLIDE 3 — Questions for Mantel

*(Use the last 5–10 min of the Q&A)*

Suggested questions to ask the panel:

1. **Team & stack:** What does the ML engineering team look like today, and what does the model lifecycle look like from experimentation to production?

2. **Biggest challenge:** What is the hardest ML problem Mantel is working on right now, and where is the bottleneck — data, compute, or productionisation?

3. **Impact:** How does Mantel measure the business impact of its ML work — is there a direct feedback loop from deployed models back to the team?

---

*Note: If you have a second project to highlight, replace Slide 3 with that project (same structure as Slide 2) and move the questions to a verbal close.*
