# Chapter 2: Research Cycles & Model Development

> *Understanding the Technical Foundation Without Being an Engineer*

---

## 📖 Chapter Overview

This chapter bridges the gap between cutting-edge AI research and practical product decisions. You will learn how models are built, when to use them off-the-shelf versus fine-tuning them, what makes AI agents tick, and — critically — how context engineering has become the new competitive moat for AI PMs.

---

## 🗂️ Lessons

| Lesson | Title | Key Skills |
|--------|-------|------------|
| [Lesson 1](./lesson1/README.md) | The Agentic AI Development Lifecycle | Problem framing, ML pipeline, build vs. buy |
| [Lesson 2](./lesson2/README.md) | Evaluating Pre-trained Models | LLM landscape, benchmarking, prompt engineering |
| [Lesson 3](./lesson3/README.md) | Transfer Learning to Fine-tuning | When to fine-tune, RAG, cost-benefit analysis |
| [Lesson 4](./lesson4/README.md) | Introduction to Agentic AI | Agent architecture, model selection, use cases |
| [Lesson 5](./lesson5/README.md) | Working with Research Teams | Experiment goals, handoffs, stakeholder communication |

---

## 💡 Why This Chapter Matters

For most of the last decade, product managers operated at arm's-length from the model. You wrote a spec, handed it to an ML engineer, and waited. That world is dissolving rapidly.

As AI coding assistants, context-aware agents, and agentic pipelines compress development cycles from months to days, the bottleneck in product development is shifting. It is no longer purely in engineering — it is increasingly in **product judgment**:

- Which model to choose
- What context to supply
- When to fine-tune versus retrieve
- How to set up evaluation loops that keep quality high as systems evolve

> **Key Insight:** Product managers who understand the model development lifecycle are no longer technical curiosities — they are becoming the architects of how AI systems are shaped and deployed. The PM who can read an eval dashboard, spot a latency regression, and articulate trade-offs to a research team will consistently outperform one who cannot.

This chapter gives you the foundational mental models to hold your own in those conversations — without requiring you to write a single line of model training code.

---

## 📋 Chapter Summary Table

| Concept | PM Takeaway |
|---------|-------------|
| **Problem Framing** | The choice between classification, generation, and recommendation sets the entire development trajectory. Match the model type to the problem before selecting a model. |
| **Build vs. Buy vs. API** | Default to pre-trained API models. Fine-tune only when you have clear evidence that the base model capability is the bottleneck — not the prompt, context, or evaluation. |
| **Context Engineering** | Poor AI output is usually a context quality problem, not a model quality problem. Engineering the information environment the model sees is the AI PM's highest-leverage technical skill. |
| **Model Evaluation** | Public benchmarks are a starting point. Build task-specific evals, run human evaluations, and measure in production. Measure cost per task completion for agentic systems. |
| **RAG vs. Fine-tuning** | RAG is the better default for knowledge-intensive tasks. Fine-tuning is better for behavior and style adaptation. Most teams should try RAG first. |
| **Agent Design** | Define tool scope, authority limits, failure modes, and human-in-the-loop points before building. Model selection matters more for agents than for simple LLM use cases. |
| **Research Collaboration** | Align on user-outcome metrics before experiments. Structure handoffs with model cards, eval suites, and rollback plans. Translate technical metrics into business language for stakeholders. |

---

## 🤔 Reflection Questions

1. Think about an AI feature at your current company or a product you use. What problem type (classification, generation, recommendation) does it use? Was that the right choice?
2. If you were evaluating three LLMs for a customer support use case, what evaluation criteria would matter most? How would you design a task-specific test set?
3. Describe a scenario where RAG would be clearly superior to fine-tuning. Now describe one where fine-tuning would be clearly superior. What is the key difference?
4. What does "context engineering" mean in practice for a product you are building or familiar with? What information should the model always have access to, and what should be retrieved on demand?
5. You are presenting a new AI feature to your executive team. The model hallucinates approximately 5% of the time on a specific input type. How do you communicate this limitation in a way that is honest, actionable, and does not kill the initiative?

---

*← Chapter 1 | Chapter 3: Product Strategy for AI →*
