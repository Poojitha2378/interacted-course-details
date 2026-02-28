# Lesson 4: Introduction to Agentic AI

> **Chapter 2 · AI Product Management Course**

[← Lesson 3](../lesson3/README.md) | [Lesson 5 →](../lesson5/README.md)

---

## Overview

The shift from "AI that answers questions" to "AI that takes actions" is the most significant product design transition of the current era. Agentic AI systems are **autonomous, goal-directed systems** that can plan, use tools, and operate across multi-step tasks with minimal human oversight.

For AI PMs, understanding agent architecture is no longer optional. The products shipping in 2025–2026 are predominantly agentic in some form — and the product failures that matter most will trace back to poor architectural decisions made at the PM level.

---

## 1. What Are AI Agents?

An AI agent is a system that can **pursue a goal across multiple steps**, using tools and memory to adapt its approach based on intermediate results.

Unlike a simple chatbot (one input → one output), an agent operates in a **reasoning loop:**

```
┌─────────────────────────────────────────┐
│                                         │
│   1. Receive goal from user             │
│           ↓                             │
│   2. Reason about what to do next       │
│           ↓                             │
│   3. Use a tool (search, code,          │
│      API call, database query)          │
│           ↓                             │
│   4. Observe the result                 │
│           ↓                             │
│   5. Reason again → take another        │
│      action OR return result to user    │
│           ↑_________________________    │
│                                         │
└─────────────────────────────────────────┘
```

This loop can run for many steps, enabling agents to complete tasks that would require significant human time — researching a topic, writing and testing code, analyzing a dataset, or managing a multi-step workflow.

---

## 2. Agent Architecture: Reasoning + Tools + Memory

Every production-grade agent system has three foundational components:

### 🧠 Reasoning (the LLM)

The model that decides **what to do next.** This is why model selection matters more for agents than for simple chatbots: reasoning capability, reliability, and instruction-following quality determine whether the agent successfully navigates complex multi-step tasks.

Frontier reasoning models significantly outperform speed models for non-trivial agentic tasks.

### 🔧 Tools

The **actions the agent can take:**

- Web search
- Code execution
- Database queries
- File system operations
- API calls to external services
- Email/calendar/CRM actions

> **PM Design Decision:** Defining the tool set is a core product decision. Each tool added increases capability *and* risk surface simultaneously. Be deliberate about which tools to expose and in what context.

### 💾 Memory

How the agent **retains and recalls information** across its reasoning loop:

| Memory Type | What It Is | Example |
|-------------|------------|---------|
| **In-context memory** | Recent conversation and task history within the current session | The steps taken so far in a multi-step research task |
| **Retrieved memory** | External knowledge base queried at inference time (RAG) | Pulling relevant company policies when answering an HR question |
| **External memory** | Data written to a database mid-task for later retrieval | Saving intermediate results from a long data analysis task |

> **Memory design is where most agentic failures occur in production.** If an agent can't reliably recall what it has already done, it will loop, contradict itself, or duplicate actions.

---

## 3. Why Model Selection Matters More for Agents

In simple chatbot use cases, model quality differences are meaningful but forgiving — a suboptimal response is annoying, not catastrophic. In agentic systems, **the stakes are different:**

| Risk | Impact in Agents |
|------|-----------------|
| **Inconsistent instruction-following** | Agent takes wrong actions — and those actions may be difficult or impossible to reverse (a sent email, a deleted file, a submitted form) |
| **Poor multi-step reasoning** | Agent gets "stuck" in loops, pursues the wrong subgoal, or fails to recognize when a task is complete |
| **Confident hallucination** | False information passed to downstream tools compounds errors across multiple steps |

---

> 🎯 **Agent Model Selection Principle**
>
> For high-stakes agentic tasks, always prefer **reliability and reasoning capability** over speed and cost.
>
> A reasoning model that costs 10× more per call but completes a task in 3 steps is cheaper than a speed model that takes 12 steps and fails.
>
> **Measure cost per task completion, not cost per token.**

---

## 4. Real-World Agent Use Cases

Understanding agent architecture through concrete use cases helps translate technical concepts into product requirements:

### 🎧 Customer Service Agents

Handle multi-turn conversations, look up order history, process returns, escalate to humans when confidence is low.

**Key PM design challenge:** Defining when to escalate versus proceed. The escalaion policy is a product decision, not just an engineering one.

---

### 📊 Data Analysis Agents

Accept a natural-language question, write and execute SQL or Python code, iterate on the analysis, and return a polished result.

**Key PM design challenge:** Preventing hallucinated data interpretations. Agents should show their work (the code they ran, the data they queried) so humans can verify results.

---

### ⚙️ Workflow Automation Agents

Connect to enterprise software (CRM, ERP, HRIS), execute multi-step business processes, and handle exceptions.

**Key PM design challenge:** Defining the **blast radius** if the agent makes a mistake. What is the worst-case outcome of an incorrect action, and is there a human checkpoint before irreversible steps?

---

### 🔍 Research and Synthesis Agents

Search the web, read documents, reconcile conflicting information, and produce structured reports.

**Key PM design challenge:** Source quality and citation reliability. Agents that synthesize information from the web can confidently cite unreliable sources.

---

## 5. PM Responsibilities in Agentic Systems

In every agentic use case, the PM's most important contributions are:

1. **Define the scope of agent authority** — What can the agent do without approval? What requires human sign-off?
2. **Design graceful failure modes** — What happens when the agent is uncertain, encounters an error, or reaches the edge of its competence?
3. **Establish human-in-the-loop checkpoints** — Where in the task flow must a human approve before irreversible actions are taken?
4. **Set blast radius limits** — What is the maximum harm that can result from a single agent mistake? Design the system to bound this.
5. **Define observability requirements** — What logging, tracing, and monitoring must be in place so that you can diagnose failures after the fact?

---

> ⚠️ **The Agentic PM Checklist**
>
> Before shipping any agentic feature, confirm you have answered:
> - [ ] What tools does the agent have access to, and why each one?
> - [ ] What is the most harmful action the agent could take if it makes a mistake?
> - [ ] Where are the human approval checkpoints?
> - [ ] What is the rollback or undo capability for agent actions?
> - [ ] How will we monitor agent behavior in production?
> - [ ] What does the agent do when it is uncertain?

---

## Key Takeaways

- Agents operate in a loop: reason → act → observe → reason again
- Three foundational components: reasoning (LLM), tools, and memory
- Memory design is where most production agentic failures occur
- Model reliability and reasoning capability matter more for agents than for simple LLM use cases
- Measure cost per task completion for agents, not cost per token
- The PM's job in agent design: scope authority, design failure modes, set human-in-the-loop checkpoints

---

[← Lesson 3: Transfer Learning to Fine-tuning](../lesson3/README.md) | [Lesson 5: Working with Research Teams →](../lesson5/README.md)
