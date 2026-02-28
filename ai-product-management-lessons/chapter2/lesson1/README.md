# Lesson 1: The Agentic AI Development Lifecycle

> **Chapter 2 · AI Product Management Certification Course**

[← Chapter Overview](../README.md) | [Lesson 2 →](../lesson2/README.md)

---

## Overview

Before you can make smart product decisions about AI, you need a working map of how AI systems actually get built. The good news: you do not need to understand every mathematical detail. You need to understand the pipeline well enough to:

- Ask the right questions
- Catch misalignments early
- Know which phase creates which kinds of risk

---

## 1. Problem Framing: Choosing the Right Problem Type

Every AI product starts with a problem framing decision. The frame you choose determines the model architecture, training data requirements, evaluation approach, and ultimately the user experience.

The three fundamental problem types:

### Classification

> *"Is this email spam or not? What sentiment is this review?"*

The model assigns input to a predefined category. Works well with labeled data; evaluation is straightforward (accuracy, precision, recall).

**Best when:** There is a bounded, finite set of possible outputs.

### Generation

> *"Write a product description. Summarize this meeting. Generate code from this prompt."*

The model produces new content. Evaluation is harder — quality is often subjective. Context engineering has a massive impact here.

**Best when:** The output needs to be novel, nuanced, or tailored to the user.

### Recommendation

> *"Which product should this user see next? Which support article is most relevant?"*

The model ranks or filters options. Requires careful attention to feedback loops and bias.

**Best when:** You have a defined set of items and need to match users to the most relevant ones.

---

> ⚠️ **PM Pitfall**
>
> Teams frequently start with generation when a classification model would be faster, cheaper, and more reliable. Before defaulting to an LLM, ask: *"Is there a bounded set of outputs?"* If yes, classification may be the better frame.

---

## 2. The Traditional ML Pipeline

Even in the era of pre-trained foundation models, the core pipeline holds. Understanding it helps you know where delays happen, where quality degrades, and where your product intuition is most valuable.

| Stage | What Happens | PM's Role |
|-------|-------------|-----------|
| **Data** | Collect, clean, and label training examples. The quality and diversity of data heavily determines model behavior. | Define what "good" looks like. Catch label bias early. Prioritize data collection for edge cases that matter most to users. |
| **Training** | The model learns patterns from data through optimization. Computationally expensive; typically done by ML engineers. | Set business constraints (latency budget, cost per inference). Align on what the model should and should not do. |
| **Evaluation** | Measure model performance against benchmarks and real-world criteria. Often the most neglected phase. | Define success metrics **before** training, not after. Insist on human evaluation alongside automated evals. |
| **Deployment** | Serve the model to users. Includes infrastructure, monitoring, fallback handling, and versioning. | Define rollout strategy (shadow mode, canary, full launch). Set up feedback loops for continuous improvement. |

---

## 3. When to Build vs. Buy vs. Use Pre-trained Models

One of the most consequential product decisions you will make is how to source your model capabilities.

### 🔨 Build from Scratch

**When to consider:** You have truly unique proprietary data, massive scale, and a capability that does not exist in any pre-trained model.

This is extremely rare and rarely the right call for product teams.

### 🔧 Fine-tune a Pre-trained Model

**When to consider:** You need specialized behavior (domain vocabulary, brand voice, specific output format) but the base capability already exists.

Cost is higher than API calls but lower than training from scratch.

### 🔌 Use a Pre-trained Model via API

**When to consider:** The pre-trained model already handles your use case well enough, and you need speed to market.

This is the **right default for most product teams**. Start here and only move to fine-tuning once you have evidence the base model is the bottleneck — not the prompt, not the context, not the evaluation criteria.

---

> 📌 **Key Rule**
>
> If your model is underperforming, **fix the context before you fix the model.** In the majority of cases, poor context quality — not model capability — is the root cause of inconsistent AI output.

---

## Key Takeaways

- Match your problem type (classification / generation / recommendation) to your model before selecting one
- The ML pipeline has four stages: Data → Training → Evaluation → Deployment — know your PM role at each
- Default to pre-trained API models; only fine-tune when you have clear evidence the base model is the bottleneck
- Context quality is almost always the real bottleneck, not model capability

---

[← Chapter Overview](../README.md) | [Lesson 2: Evaluating Pre-trained Models →](../lesson2/README.md)
