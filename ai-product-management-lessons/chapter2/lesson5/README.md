# Lesson 5: Working with Research Teams

> **Chapter 2 · AI Product Management Certification Course**

[← Lesson 4](../lesson4/README.md) | [Chapter Overview →](../README.md)

---

## Overview

For many PMs, the research team relationship is where technical understanding meets organizational reality. Research teams operate on timelines, incentives, and success metrics that are **fundamentally different** from product teams.

Understanding those differences — and building bridges across them — is one of the highest-leverage skills an AI PM can develop.

---

## 1. Setting Experiment Goals and Success Metrics

The single most common failure point in PM-research collaboration is **misaligned success metrics.**

- Research teams often measure **proxy metrics** — benchmark scores, perplexity, BLEU, model accuracy on a test set
- Product teams care about **user outcomes** — task completion, satisfaction, retention, revenue impact

Neither is wrong. They operate at different levels of abstraction. **Your job is to connect them.**

### Before Any Experiment Begins, Align On:

1. **The user problem being solved** — not the model capability being developed
2. **How improvement will be measured** — both technically (eval metrics) and in product (user metrics)
3. **The threshold for "good enough" to ship** — so you are not endlessly iterating
4. **The resource budget** — compute time, data labeling cost, engineering time
5. **What "failed experiment" looks like** — and what you will do if you get there

---

> 📋 **Pre-Experiment Alignment Checklist**
>
> Write down and get sign-off on all five before work begins:
>
> - [ ] The user problem this experiment is solving
> - [ ] The success metric (technical and product)
> - [ ] The minimum acceptable threshold to ship
> - [ ] The experiment duration and resource budget
> - [ ] What happens if the experiment fails
>
> This document becomes your **post-experiment review baseline.**

---

## 2. The Research-to-Production Handoff

Research prototypes and production systems are **fundamentally different artifacts.** A model that performs well in a controlled experiment can fail badly in production.

### Common Failure Modes at Handoff

| Failure Mode | What Happens | How to Prevent It |
|-------------|-------------|-------------------|
| **Distribution shift** | Real user inputs are messier and more varied than the research test set. Edge cases the research setup never saw start causing failures. | Include real production samples in your eval set. Run shadow mode before full launch. |
| **Latency and throughput** | A model that takes 30 seconds to respond may be acceptable in research. It is almost never acceptable in production. | Set latency budgets before training starts, not after. |
| **Integration complexity** | The model needs authentication, rate limits, error handling, and observability instrumentation. | Involve an engineer in research reviews to flag integration risk early. |
| **Offline-online eval gap** | Offline eval metrics often don't transfer to online metrics. | Build a plan for measuring model quality in production from day one. |

### The Structured Handoff Package

At minimum, every research-to-production handoff should include:

**1. Model Card**
- What the model does and what it does not do
- What data it was trained or fine-tuned on
- Known failure modes and edge cases
- Performance benchmarks on the eval set

**2. Eval Suite**
- The test set and scoring scripts used during research
- Packaged and documented for ongoing use in production monitoring

**3. Operational Runbook**
- How to monitor the model in production
- What alerts to set and at what thresholds
- What to do when quality degrades

**4. Rollback Plan**
- How to revert to a previous model version
- What constitutes a rollback trigger (quality regression threshold, error rate spike)

---

## 3. Communicating Model Limitations to Stakeholders

One of the most politically sensitive aspects of the AI PM role is **setting accurate expectations** about what AI can and cannot do — particularly with stakeholders who have been oversaturated with AI hype.

### The Effective Approach Has Three Elements

**Anchor on user outcomes, not model benchmarks**

Stakeholders don't care that the model scores 87% on MMLU. They care that it resolves customer support tickets 40% faster. Always translate technical metrics into business and user impact.

```
❌  "The model achieves 91.3% accuracy on our eval set."
✅  "In testing, the model correctly handled 9 out of 10 customer 
    questions without human escalation — reducing support cost by 
    an estimated $X per month at current volume."
```

**Be specific about failure modes**

Vague limitations erode trust. Specific limitations enable risk management.

```
❌  "The model occasionally hallucinates."

✅  "The model produces incorrect citations approximately 8% of 
    the time when asked about events after 2023. We have added 
    a source-verification layer for citation-heavy queries."
```

**Separate capability limitations from context limitations**

Many stakeholders assume poor model output means a bad model. Help them understand that output quality is often a function of **context quality** — what information the model is given — not just model capability.

This reframing opens the door to product-level improvements (better RAG, better prompts, better data) rather than an immediate request for a model upgrade.

---

> 💬 **Stakeholder Communication Template**
>
> *"Our current system performs well on [specific strengths] but has limitations around [specific failure modes]. We believe [X%] of these can be addressed through [context / data / prompt improvements] in the next [timeframe]. The remaining [Y%] represent model-level constraints that we will address by [model upgrade / human review layer / scope reduction]."*

---

## 4. The Research-PM Relationship Over Time

Beyond individual experiments and handoffs, investing in the long-term relationship with your research team pays compounding dividends.

### Practices That Build Trust

**Attend research reviews, even when you don't understand everything**
Your presence signals that product cares about the work. Ask questions about user relevance. Over time, researchers begin to self-filter for user impact.

**Share user feedback systematically**
Research teams often lack direct access to how their models perform in the wild. A monthly summary of production failure patterns, user complaints, and edge cases is genuinely valuable to them.

**Celebrate research contributions in product launches**
Attribution matters. When a model improvement ships and drives outcomes, make sure the research team is credited in product reviews and launch communications.

**Protect research time from product urgency**
The fastest way to erode a research relationship is to constantly pull researchers into "urgent" product fires. Agree on how much research time is protected from ad hoc requests.

---

## Key Takeaways

- Misaligned success metrics are the most common PM-research failure point — align on user-outcome metrics before any experiment begins
- Use the pre-experiment alignment checklist: user problem, success metric, threshold, budget, failure definition
- Structure handoffs with a model card, eval suite, operational runbook, and rollback plan
- Translate technical metrics into business impact when communicating with stakeholders
- Separate capability limitations from context limitations — most "model problems" are actually context or integration problems
- Invest in the long-term research relationship, not just individual project handoffs

---

[← Lesson 4: Introduction to Agentic AI](../lesson4/README.md) | [Chapter Overview →](../README.md)
