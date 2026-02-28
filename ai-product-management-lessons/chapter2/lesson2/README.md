# Lesson 2: Evaluating Pre-trained Models

> **Chapter 2 · AI Product Management Certification Course**

[← Lesson 1](../lesson1/README.md) | [Lesson 3 →](../lesson3/README.md)

---

## Overview

We are living through a remarkable period in which some of the most capable AI models in history are available to any product team via an API call. The challenge is no longer access — it is **selection, evaluation, and ongoing management.**

---

## 1. The LLM Landscape: Major Models and Their Trade-offs

The frontier model landscape evolves rapidly. As of early 2026, the key players fall into a few categories:

| Model | Strengths | Best For |
|-------|-----------|----------|
| **GPT-4o / o3** (OpenAI) | Complex reasoning, coding, instruction-following. o3 is designed for multi-step reasoning. Generally the benchmark against which others are measured. | Complex reasoning tasks; coding; high-stakes decision support |
| **Claude Sonnet / Opus** (Anthropic) | Nuanced writing, long-context tasks, following complex instructions reliably. Strong on safety-sensitive use cases. | Document analysis; content generation; safety-critical workflows |
| **Gemini** (Google) | Multimodal-first design with native image/audio/video understanding. Strong Google ecosystem integration. Gemini Flash targets high-speed, low-cost inference. | Multimodal tasks; Google Workspace integration; high-volume inference |
| **Llama 3/4** (Meta, open-weight) | Freely downloadable; deployable on your own infrastructure. No per-token API costs at scale. Requires engineering investment. | Privacy-sensitive workloads; cost-sensitive high-volume use cases |
| **Mistral / Mixtral** | European open-weight models known for efficiency. Mixture-of-experts architecture delivers near-frontier performance with lower compute. | Cost-efficient inference; European data residency requirements |

> **Note:** Model rankings shift quickly. Always run your own benchmarks on your specific task before making a selection decision.

---

## 2. Benchmarking for Your Use Case

Public benchmarks (MMLU, HumanEval, HELM) provide a starting point, but they are rarely sufficient for product decision-making. **A model that ranks first on a benchmark may rank third on your specific task.**

### The Evaluation Hierarchy Every AI PM Should Follow

```
1. Automated evals on task-specific test sets
        ↓
2. Human evaluation on a sample
        ↓
3. A/B testing in production
```

**Step 1 — Automated evals:** Build a dataset of 50–200 representative inputs with expected outputs and score model responses.

**Step 2 — Human evaluation:** Regardless of how good your automated evals are, periodically have real users or domain experts assess output quality.

**Step 3 — A/B testing in production:** The ultimate test. Real user behavior (completion rate, satisfaction, retry rate) often surfaces failure modes that offline evals miss.

### Benchmarking Dimensions for AI PMs

| Dimension | What to Measure | Why It Matters |
|-----------|----------------|----------------|
| **Accuracy / Quality** | Does the model give correct, helpful answers on your specific task? | Define "correct" before you start testing — not after. |
| **Latency** | Time to first token (interactive); total generation time (background tasks) | Sub-second matters for chat/autocomplete; less critical for async tasks |
| **Cost** | Price per million tokens at projected scale | Model your cost before committing — costs compound fast at scale |
| **Context window** | How much input can the model process? | Critical for document analysis, long threads, and agentic tasks |
| **Reliability / Consistency** | Does the model give consistent outputs for similar inputs? | Variance is often more damaging to user trust than average quality |
| **Safety / Alignment** | Will it follow instructions reliably? Refuse harmful requests? | Matters more in consumer and regulated contexts |

---

## 3. Prompt Engineering as Product Iteration

Before you write a single line of fine-tuning code, exhaust prompt engineering as a lever. Effective prompting is a **product discipline**, not just a technical one.

### Key Prompt Engineering Techniques

**System prompt design**
Clearly define the model's persona, constraints, output format, and what it should do in edge cases. This is your first line of control.

**Few-shot examples**
Showing the model 2–5 worked examples in the prompt dramatically improves consistency on specialized tasks. This is often more effective than lengthy instructions.

**Chain-of-thought instructions**
Asking the model to "think step by step" before answering significantly improves accuracy on reasoning tasks. Use this whenever correctness matters more than speed.

**Negative examples**
Explicitly showing the model what bad output looks like is often more effective than trying to describe good output abstractly.

---

> 🔑 **Context Engineering vs. Prompt Engineering**
>
> **Prompt engineering** is about crafting the right instruction.
>
> **Context engineering** is about designing the entire information environment the model sees — user history, retrieved documents, system state, relationship context, and more.
>
> The Cursor code editor maintains a $1B+ valuation not because it uses a better model than its competitors, but because its context layer — how it indexes your codebase and retrieves the right files — is the product moat. The model is almost modular. **The context is the defensibility.**
>
> When Cursor was built, it:
> - Indexed the entire codebase using embeddings computed per file
> - Split code into semantically meaningful chunks based on AST structure
> - Converted user queries into embeddings, searched a vector database, retrieved relevant file paths
> - Added that retrieved content to the LLM context at query time
>
> That system design, not the model choice, is what made Cursor defensible enough that Google tried to acquire it — and when that failed, spent $2.4B on Windsurf instead.

---

## 4. Reasoning Models vs. Speed Models

A critical product decision that emerged in 2024–2025 is the choice between reasoning-optimized and speed-optimized models.

### Reasoning Models

*Examples: GPT-o3, Claude Opus, Gemini 2.0 Pro*

- Use internal "chain-of-thought" before responding
- Dramatically better at multi-step problem solving, complex analysis, sustained logical reasoning
- Slower (seconds to minutes of "thinking") and more expensive

**Best for:** Coding assistance, complex data analysis, high-stakes decisions, agentic tasks with multiple steps

### Speed Models

*Examples: Claude Haiku, GPT-4o mini, Gemini Flash*

- Optimized for sub-second latency and low cost
- Still highly capable for most everyday tasks

**Best for:** Real-time chat, autocomplete, streaming interfaces, high-volume classification

### Deployment Pattern

> Product teams increasingly deploy **both**: a speed model for initial responses and interactive flows, with a reasoning model for background processing, complex tasks, or high-stakes decisions that can tolerate latency.

---

## Key Takeaways

- Public benchmarks are a starting point — always build task-specific evals before making a model selection decision
- Follow the evaluation hierarchy: automated evals → human evaluation → A/B testing in production
- Exhaust prompt engineering before fine-tuning; context quality is usually the bottleneck
- Deploy reasoning models for complex, high-stakes tasks; speed models for real-time and high-volume use cases
- Measure cost at projected scale before committing to a model

---

[← Lesson 1: The Agentic AI Development Lifecycle](../lesson1/README.md) | [Lesson 3: Transfer Learning to Fine-tuning →](../lesson3/README.md)
