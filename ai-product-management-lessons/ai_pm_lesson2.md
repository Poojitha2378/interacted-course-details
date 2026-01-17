## Next Steps: Preparing for Lesson 2

Lesson 2 dives into **Research Cycles & Model Development**, where you'll learn:
- How to evaluate pre-trained models for your use case
- When to fine-tune vs. use prompt engineering vs. build custom
- The difference between reasoning models and speed models
- What agentic AI is and when to use it
- How to work effectively with ML research teams

**Pre-Reading:**
- Review your current product roadmap: Which features are deterministic? Which are AI-powered?
- Identify one feature to pilot with two-track development
- Calculate current team capacity allocation: What % goes to new features vs. maintaining existing AI models?

**Discussion Prompt for Your Team:**
"If we adopted two-track development, what would our discovery track focus on? What would stay in the delivery track?"

---

## Additional Resources

*End of Lesson 1*4: Try Model B (promising, 73% accuracy)
Week 5-6: Optimize Model B (81% accuracy)
Week 7-8: Realize Model B doesn't handle edge cases
Week 9-10: Hybrid approach (87% accuracy, ready to ship)
```

Notice: 8 weeks of research before 2 weeks of engineering delivery.

**Why This Matters:**
A research spike implies "we'll figure this out in 1-2 sprints, then build it." AI research doesn't work that way. You might:
- Discover a pre-trained model solves your problem in 3 days
- Spend 3 months fine-tuning and realize RAG would work better
- Find that no current approach meets your accuracy threshold

**The Trap:**
Teams force-fit AI research into 2-week sprints, leading to:
- **Premature convergence**: Shipping the first approach that "kind of works" to meet sprint deadlines
- **Frustrated researchers**: ML engineers feel pressured to commit to unknowable timelines
- **Scope creep**: "Just one more experiment" turns sprints into 3-4 week cycles

**The AI-Adapted Approach:**
Separate research cycles from delivery sprints (covered in Lesson 2). Research runs in variable-length cycles (1-6 weeks) while engineering maintains 2-week sprints for infrastructure, API development, and integration work.

#### 3. Defining "Done" When Accuracy Is Probabilistic

**The Traditional Definition of Done:**
```
☑ Code written and reviewed
☑ Unit tests pass (100%)
☑ Integration tests pass (100%)
☑ Documentation complete
☑ Deployed to production
```

**AI's Problem:**
What does "tests pass" mean when your model is 83% accurate? Is that "done" or "still in progress"?

**Real Scenarios That Break Traditional DoD:**

**Scenario A: The Moving Target**
Your customer support chatbot achieves 90% accuracy on test data. You ship it. Week 1 in production: 87% accuracy. Week 4: 82% accuracy. Week 8: 78% accuracy.

Why? User queries shifted, new product features launched, competitors changed the market. The model "worked" when shipped but degraded over time. Was it ever "done"?

**Scenario B: The Edge Case Explosion**
Your fraud detection model achieves 95% accuracy in testing. Production reveals:
- 98% accuracy on credit cards
- 91% accuracy on debit cards
- 67% accuracy on buy-now-pay-later transactions (which didn't exist in training data)

Overall accuracy: 95%. Business impact: thousands of false positives on BNPL transactions. Is this "done"?

**Scenario C: The Acceptable Failure Rate**
Your AI-powered document parser handles:
- 95% of invoices correctly
- 4% with minor errors (human reviews quickly)
- 1% catastrophic failures (completely wrong)

Is 95% "done"? What if that 1% costs $100K in losses?

**Why Traditional DoD Fails AI:**
- **Probabilistic success**: No test will ever be 100% pass/fail
- **Context dependency**: Performance varies by data distribution, user behavior, time of day
- **Business judgment required**: "Good enough" depends on risk tolerance, cost of errors, competitive benchmarks

**The AI-Adapted Approach:**
Define "done" with **model performance gates** and **business value milestones**:

```
Model Performance Gates:
☑ Accuracy ≥ 83% on held-out test set (matched)
☑ Performance tested across key user segments (new requirement)
☑ Edge case behavior documented (new requirement)
☑ Latency ≤ 200ms at p95 (traditional)
☑ Monitoring dashboards deployed (new requirement)

Business Value Milestones:
☑ Shadow deployment shows ≥80% accuracy on live traffic (new)
☑ Escalation rate ≤15% to human fallback (new)
☑ Cost per inference ≤ $0.02 (new)
☑ Model drift detection active (new requirement)
```

**Critical Insight:**
"Done" for AI means **ready to learn from production**, not "perfect and unchanging."

---

### Discussion Questions:
1. Walk through a recent AI feature using the 8-step framework. Did you choose the right lifecycle? What would you do differently?
2. Which successful AI products (ChatGPT, GitHub Copilot, Netflix, TikTok) use hybrid approaches? What combinations did they use?
3. For your current project: Are you treating it as Software, AI/ML, GenAI, or Agentic? Should it be a hybrid?

### Key Takeaways:
- **Different AI types require different product lifecycles** (AI/ML, GenAI, Agentic)
- **Successful products are often hybrids** that combine multiple approaches
- **The 8-step framework helps you choose the right approach** before committing to development
- **Traditional Agile assumes one lifecycle**; AI products often require orchestrating multiple
- **Velocity isn't meaningful** when story points can't capture research uncertainty across different AI types
- **Research spikes imply bounded discovery**; AI research is inherently unbounded
- **"Done" must account for probabilistic performance**, not binary pass/fail
- The goal isn't to abandon Agile—it's to **adapt it for non-deterministic, multi-lifecycle systems**

---

### Real-World Pattern: How Successful AI Products Adapted Agile

**Case Study: GitHub Copilot's Two-Track Approach**

**Discovery Track (OpenAI Partnership):**
- 18-month research cycle to develop Codex model
- Hundreds of experiments on code generation approaches
- Iterative improvements based on developer feedback
- Variable-length research cycles (not 2-week sprints)

**Delivery Track (GitHub Product Team):**
- 2-week sprints for IDE integration
- Fixed-length cycles for VS Code, JetBrains plugins
- Predictable engineering velocity
- Infrastructure work (authentication, telemetry, billing)

**The Handoff:**
Research validated code generation approach → Engineering integrated it into developer workflows

**Result:** 
- MVP launched in 18 months (research) + 6 months (product integration)
- Measurable ROI: 55% faster coding, reduced cognitive load
- Iterative rollout: Technical preview → Individuals → Teams → Enterprise

**What Made It Work:**
1. **Separated research uncertainty from delivery commitments**
2. **Engineering built infrastructure while research validated approach**
3. **Clear success metrics for both tracks** (model performance + user adoption)
4. **Phased rollout minimized risk** (tested with developers first)

**Case Study: TikTok's Continuous Experimentation Model**

TikTok doesn't do traditional sprints. They run **continuous experimentation at massive scale**:

**Their Agile Adaptation:**
- No fixed sprint commitments—prioritize by experiment velocity
- Thousands of A/B tests running simultaneously
- Models retrain daily based on production data
- Release planning = experiment prioritization

**Why Traditional Agile Would Fail Here:**
- Can't commit to "improve engagement by X%" in a 2-week sprint
- Velocity is meaningless when experiments have 10% success rate
- "Done" means "learned from production," not "shipped complete"

**What They Measure Instead:**
- Experiments per week (throughput)
- Time to validate hypothesis
- % of experiments that improve core metrics
- Speed of rolling out winning experiments

**The Pattern:** TikTok treats their entire product as an **experimentation pipeline**, not a feature roadmap. This is the extreme end of AI-adapted Agile.

---

## Lesson 2: Hybrid Agile-Research Workflows

### The Two-Track Model for AI Products

The solution to Lesson 1's tensions: **run research and engineering in parallel, not in sequence.**

#### Core Concept: Discovery Track + Delivery Track

**Discovery Track (Research Cycle)**
- **Focus**: Model experimentation, accuracy improvement, approach validation
- **Cadence**: Variable length (1-6 weeks depending on problem complexity)
- **Team**: ML researchers, data scientists, technical product manager
- **Output**: Validated approach, accuracy benchmarks, integration requirements
- **Success metric**: Learning velocity (hypotheses tested, approaches validated)

**Delivery Track (Engineering Sprint)**
- **Focus**: Infrastructure, APIs, integration, monitoring, user experience
- **Cadence**: Fixed 2-week sprints
- **Team**: Software engineers, MLOps, designers, product manager
- **Output**: Production-ready systems, deployment pipelines, user interfaces
- **Success metric**: Traditional velocity (features shipped, infrastructure completed)

**Why This Works:**
- Researchers aren't pressured to commit to unknowable timelines
- Engineers maintain predictable sprint rhythm
- Both tracks feed each other: research informs what to build, engineering feedback shapes what's feasible

#### Visual Model

```
DISCOVERY TRACK (Variable Cycles)
┌─────────────┐    ┌──────────────────┐    ┌─────────────┐
│ Experiment  │───▶│   Experiment     │───▶│  Validated  │
│  Cycle 1    │    │    Cycle 2       │    │  Approach   │
│  (2 weeks)  │    │   (4 weeks)      │    │             │
└─────────────┘    └──────────────────┘    └─────────────┘
       │                    │                       │
       ├────────────────────┼───────────────────────┤
       │         Learnings & Requirements           │
       ▼                    ▼                       ▼
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│  Sprint 1   │    │  Sprint 2   │    │  Sprint 3   │
│ (2 weeks)   │    │ (2 weeks)   │    │ (2 weeks)   │
└─────────────┘    └─────────────┘    └─────────────┘
DELIVERY TRACK (Fixed Sprints)
```

#### What Each Track Delivers

**Discovery Track Outputs:**
- **Week 1-2**: "GPT-4 achieves 78% accuracy with basic prompting; Claude Sonnet hits 81% with structured prompts"
- **Week 3-6**: "Fine-tuned Llama 3 reaches 87% accuracy but requires 2-second latency; GPT-4 with RAG hits 86% at 400ms"
- **Week 7-8**: "RAG approach validated: 86% accuracy, 380ms latency, $0.015/call—ready for production pilot"

**Delivery Track Outputs (Running in Parallel):**
- **Sprint 1-2**: Evaluation framework, data pipeline, baseline UI
- **Sprint 3-4**: API infrastructure, monitoring dashboards, A/B testing framework
- **Sprint 5-6**: Production deployment pipeline, human-in-the-loop fallback, user onboarding

**The Handoff:**
Week 8: Research validates RAG approach → Engineering begins integration sprint with known parameters

#### Sprint Planning with Experimentation Buffers

**Traditional Sprint Planning:**
```
Capacity: 40 story points
Committed: 38 story points (95% capacity utilization)
Buffer: 2 points for interruptions
```

**AI Sprint Planning:**
```
DISCOVERY TRACK:
Hypothesis: 3 approaches to test this cycle
Time box: 3 weeks
Experiments: 12 planned (4 per approach)
Buffer: 30% of cycle time for unexpected findings

DELIVERY TRACK:
Sprint capacity: 30 story points
AI feature work: 15 points (50% capacity)
Infrastructure work: 10 points (stable, predictable)
Buffer: 5 points (17% for research pivots)
```

**Why 50% AI Capacity:**
If research invalidates your approach mid-sprint, you haven't wasted 100% of engineering capacity. The infrastructure work (APIs, monitoring, data pipelines) remains valuable regardless of which model approach wins.

**Real Example: E-commerce Recommendation Engine**

**Discovery Track (Week 1-4):**
```
Cycle 1 Goal: Validate personalization approach
Experiments:
☑ Collaborative filtering baseline (Week 1) → 62% accuracy
☑ GPT-4 with user history (Week 2) → 71% accuracy
☐ Fine-tuned embedding model (Week 2-3) → postponed (dependency issue)
☑ Hybrid: CF + GPT-4 (Week 3) → 76% accuracy
☑ Add browsing session context (Week 4) → 79% accuracy ✓

Outcome: Hybrid approach validated, ready for production pilot
```

**Delivery Track (Sprints 1-2, running parallel):**
```
Sprint 1:
☑ User preference API (5 pts)
☑ Recommendation endpoint stub (3 pts)
☑ A/B testing framework (8 pts)
☑ Analytics dashboard (5 pts)
Total: 21 pts (30 pt capacity → 30% buffer preserved)

Sprint 2:
☑ Caching layer for embeddings (8 pts)
☑ Fallback to rule-based system (5 pts)
☑ Monitoring alerts for latency (3 pts)
☐ Model integration (postponed—waiting for research validation)
Total: 16 pts (14 pt buffer → research not ready yet)
```

**Notice:** Engineering didn't wait for research to complete. They built foundational infrastructure. When research validated the approach, integration happened in Sprint 3 with minimal risk.

#### Success Metrics Beyond Velocity

**Traditional Agile Metrics:**
- Velocity: Story points completed per sprint
- Sprint commitment reliability: % of committed stories completed
- Cycle time: Days from "To Do" to "Done"

**AI-Adapted Metrics:**

**Discovery Track:**
- **Research throughput**: Experiments per week (target: 3-5)
- **Hypothesis validation rate**: % of approaches tested (target: 80% of planned experiments completed)
- **Learning efficiency**: Time to invalidate dead-end approaches (target: <3 days)
- **Convergence rate**: Accuracy improvement per experiment cycle (target: +2-5% per cycle)

**Delivery Track:**
- **Infrastructure velocity**: Traditional story points for non-AI work (target: stable at team's baseline)
- **Integration readiness**: % of dependencies ready when research validates (target: >80%)
- **Deployment reliability**: Success rate of model deployments (target: >95%)

**Combined Metrics:**
- **Model performance gates**: % of releases meeting accuracy thresholds (target: 100%)
- **User value milestones**: Features in production improving KPIs (target: align with product OKRs)
- **Time-to-production**: Research validation → production deployment (target: <2 sprints)

**What Good Looks Like:**
```
Quarter 1 Metrics Dashboard:

DISCOVERY:
✓ 47 experiments completed (target: 40)
✓ 6 approaches validated, 11 invalidated (hit learning goals)
✓ Average convergence: +4.2% accuracy per cycle

DELIVERY:
✓ 23 story points/sprint average (stable)
✓ 88% infrastructure ready at research handoff
✓ 2 AI features deployed to production
✓ Both features meeting accuracy gates (91%, 87%)

COMBINED:
✓ Research→Production: 4.5 weeks average
✓ 0 production incidents from AI features
✓ User engagement +18% from personalization feature
```

---

### Implementation Checklist

**Week 1: Assess Current State**
- [ ] Map your current sprint process
- [ ] Identify which work is research vs. delivery
- [ ] Calculate % of sprint time spent on AI uncertainty

**Week 2-3: Design Two-Track System**
- [ ] Define discovery cycle lengths for your team
- [ ] Establish research throughput metrics
- [ ] Create experiment templates
- [ ] Design sprint planning that accounts for both tracks

**Week 4-6: Pilot with One Feature**
- [ ] Choose a new AI feature
- [ ] Run first discovery cycle
- [ ] Maintain parallel delivery sprints
- [ ] Document learnings

**Week 7-8: Refine and Scale**
- [ ] Retrospective on two-track process
- [ ] Adjust cycle lengths, buffer %
- [ ] Train stakeholders on new metrics
- [ ] Roll out to additional teams

---

## Lesson 3: Story Mapping for Agentic AI Features

### Writing User Stories for ML-Powered Features

Traditional user stories follow a simple formula:
```
As a [user type]
I want [action]
So that [benefit]
```

AI user stories require additional dimensions:

#### The AI-Enhanced Story Template

```
As a [user type]
I want [AI-assisted action]
So that [benefit]

AI Performance Requirements:
- Accuracy threshold: [X%] for [specific user segment]
- Latency: [Xms] at [percentile]
- Cost: ≤$[X] per [action]
- Fallback behavior: [what happens when AI fails]

Success Metrics:
- [User outcome metric]
- [AI performance metric]
- [Business impact metric]

Uncertainty Factors:
- [Known unknowns that might affect delivery]
```

#### Real Examples

**Example 1: Customer Support Chatbot**

**Traditional Story (Insufficient):**
```
As a customer
I want to get instant answers to product questions
So that I don't have to wait for a support agent
```

**AI-Enhanced Story:**
```
As a customer
I want to get instant answers to product questions from an AI assistant
So that I don't have to wait for a support agent

AI Performance Requirements:
- Accuracy: ≥85% answer quality (measured by user thumbs up/down)
- Latency: ≤2 seconds to first response
- Cost: ≤$0.05 per conversation
- Fallback: Escalate to human agent after 2 failed attempts or on user request

Success Metrics:
- 40% reduction in support ticket volume
- 85% user satisfaction with AI responses
- 70% of conversations fully resolved by AI (no human escalation)

Uncertainty Factors:
- Unknown: optimal escalation trigger (need to test in production)
- Unknown: performance on newly launched product categories
- Known: accuracy will degrade over time without retraining
```

**Why This Works:**
- Engineering knows when to escalate to humans (fallback strategy)
- Stakeholders understand the probabilistic nature (85% target, not 100%)
- Team can define "done" with clear metrics
- Product can prioritize based on cost constraints

**Example 2: Document Intelligence Extraction**

**Traditional Story (Insufficient):**
```
As a finance manager
I want invoice data automatically extracted
So that I can process payments faster
```

**AI-Enhanced Story:**
```
As a finance manager
I want invoice data automatically extracted from PDFs and scans
So that I can process payments 3x faster than manual entry

AI Performance Requirements:
- Extraction accuracy: ≥95% for standard fields (vendor, amount, date)
- Edge case handling: ≥80% for non-standard layouts
- Latency: ≤5 seconds per document
- Cost: ≤$0.10 per document
- Fallback: Flag low-confidence extractions for human review (<90% confidence score)

Success Metrics:
- 70% of invoices processed with zero human review
- 25% flagged for review (human validates in 30 seconds)
- 5% catastrophic failures (full manual entry required)
- Average processing time: 45 seconds (down from 4 minutes)

Uncertainty Factors:
- Unknown: performance on handwritten invoices (need production data to train)
- Unknown: whether confidence scores correlate with accuracy (need to validate)
- Known: new vendor formats will require retraining
- Known: multilingual invoices may need separate models
```

**The Critical Addition: Confidence-Based Workflows**
Notice the fallback strategy includes **confidence thresholds**. This allows the system to "know what it doesn't know"—a key pattern for AI user stories.

#### Acceptance Criteria That Account for Model Uncertainty

**Traditional Acceptance Criteria:**
```
Given [context]
When [action]
Then [exact outcome]
```

**AI Acceptance Criteria:**
```
Given [context]
When [action]
Then [probabilistic outcome with measurable thresholds]
And [fallback behavior when threshold not met]
```

#### Real Examples

**Example 1: Sentiment Analysis Feature**

**Traditional Criteria (Breaks for AI):**
```
✗ Given a customer review
  When the model analyzes sentiment
  Then it correctly identifies positive/negative/neutral sentiment

(What does "correctly" mean? 80%? 95%? Across which data?)
```

**AI-Adapted Criteria:**
```
✓ Given a representative test set of 1,000 customer reviews (300 positive, 500 neutral, 200 negative)
  When the model analyzes sentiment
  Then it achieves:
    - ≥90% accuracy on positive reviews
    - ≥85% accuracy on neutral reviews
    - ≥88% accuracy on negative reviews
    - ≥87% overall accuracy

✓ Given a review with mixed sentiment (both positive and negative mentions)
  When the model analyzes sentiment
  Then it flags the review as "mixed" for human review
  (Because we know current models struggle with nuanced sentiment)

✓ Given a review in production
  When the model confidence score is <75%
  Then the system routes the review to the human review queue
  And logs the review for future model training
```

**Why This Works:**
- Testable thresholds (90%, 85%, 88%)
- Acknowledges model limitations (mixed sentiment)
- Defines behavior for uncertainty (confidence-based routing)
- Creates data flywheel (low-confidence cases improve future models)

**Example 2: Predictive Maintenance Alert**

**Traditional Criteria (Breaks for AI):**
```
✗ Given sensor data from a machine
  When the model detects anomalies
  Then it sends a maintenance alert

(When should it alert? How many false positives are acceptable?)
```

**AI-Adapted Criteria:**
```
✓ Given historical sensor data with known failure events
  When the model is trained and evaluated
  Then it achieves:
    - ≥92% recall (catches 92% of actual failures)
    - ≥78% precision (78% of alerts are true failures)
    - Alerts 48-72 hours before failure (actionable lead time)

✓ Given real-time sensor data in production
  When the model predicts failure risk >85%
  Then it sends an immediate alert to maintenance team
  And logs prediction for post-failure validation

✓ Given real-time sensor data in production
  When the model predicts failure risk 60-85%
  Then it sends a "monitor closely" notification
  And increases sensor polling frequency

✓ Given a false positive alert
  When maintenance confirms no failure occurred
  Then the system logs the false positive
  And adds the data to the retraining queue
  (Building the dataset to improve precision over time)
```

**The Pattern:**
1. **Quantified performance thresholds** (92% recall, 78% precision)
2. **Risk-based actions** (different responses for different confidence levels)
3. **Feedback loops** (log false positives for retraining)
4. **Business trade-offs made explicit** (prefer false positives to missed failures)

#### Prioritization Frameworks: RICE for Agentic AI

Traditional RICE scoring:
- **R**each: How many users affected
- **I**mpact: How much benefit per user
- **C**onfidence: How certain are we about Reach/Impact
- **E**ffort: How long will it take to build

**AI-Adapted RICE:**

**R**each × **I**mpact × **C**onfidence / (**E**ffort × **T**echnical Feasibility)

**New Element: Technical Feasibility (0.1 - 1.0 score)**

| Score | Description | Example |
|-------|-------------|---------|
| 1.0 | Solved problem, proven approach | GPT-4 API for content generation |
| 0.8 | Known approach, needs customization | Fine-tune existing model for domain |
| 0.6 | Research required, likely solvable | Novel feature, but similar work exists |
| 0.4 | Significant research, uncertain | Pushing state-of-the-art boundaries |
| 0.2 | Speculative, may not be possible | No known solution, high uncertainty |

**Example Comparison:**

**Feature A: AI-Powered Product Recommendations**
- Reach: 100,000 users (3 points)
- Impact: Medium (2 points—some users will convert)
- Confidence: 90% (0.9)
- Effort: 4 person-months
- Technical Feasibility: 0.9 (proven approach, many existing solutions)
- **RICE Score: (3 × 2 × 0.9) / (4 × 0.9) = 5.4 / 3.6 = 1.5**

**Feature B: Predictive Inventory Optimization**
- Reach: 50,000 users (2 points)
- Impact: High (3 points—saves significant money)
- Confidence: 70% (0.7)
- Effort: 3 person-months
- Technical Feasibility: 0.5 (novel problem, uncertain if current models can handle)
- **RICE Score: (2 × 3 × 0.7) / (3 × 0.5) = 4.2 / 1.5 = 2.8**

Feature B scores higher despite longer research uncertainty because the business impact justifies the risk.

**When to Deprioritize AI Features:**
- Technical Feasibility <0.4 **AND** Effort >3 months → Research spike first, don't commit to delivery
- Impact score low **AND** Technical Feasibility <0.6 → Not worth the uncertainty
- Confidence <50% on Reach/Impact → Need more discovery before prioritizing

---

### Story Mapping Exercise

**Scenario: Build an AI-powered contract review assistant for legal teams**

**User Journey:**
1. Upload contract → 2. AI analyzes → 3. Highlights risks → 4. Suggests edits → 5. Lawyer reviews → 6. Approves or escalates

**Your Task: Write AI-enhanced user stories for Step 3 (Highlights risks)**

**Traditional Story:**
```
As a lawyer
I want the AI to highlight risky clauses
So that I can review contracts faster
```

**Your Enhanced Story (fill in):**
```
As a lawyer
I want [AI-assisted action]
So that [benefit]

AI Performance Requirements:
- Accuracy threshold: [?]
- Latency: [?]
- Fallback behavior: [?]

Success Metrics:
- [?]
- [?]

Uncertainty Factors:
- [?]
```

**Acceptance Criteria (write 3):**
1. Given [context], When [action], Then [probabilistic outcome + threshold]
2. [Confidence-based fallback]
3. [Feedback loop for improvement]

---

## Lesson 4: Release Planning with Model Iterations

### MVP Thresholds: What Accuracy is "Good Enough"?

The hardest question in AI product management: **When do we ship?**

#### The 70-80-90 Rule

**70% Accuracy: Research Prototype**
- Proves the approach is viable
- Not ready for production
- Good for internal demos and stakeholder alignment

**80% Accuracy: Minimum Viable AI**
- Good enough for **human-in-the-loop** deployment
- Users notice value but expect some errors
- Requires active human oversight and correction

**90% Accuracy: Production-Grade AI**
- Good enough for **augmented** deployment
- Users trust the system, review output selectively
- Human intervention for edge cases only

**95%+ Accuracy: Autonomous AI**
- Good enough for **automated** deployment
- Minimal human oversight
- Errors are rare and low-impact

**Critical Insight: Context Matters More Than Numbers**

**When 75% is Good Enough:**
- **Content recommendations**: Users can ignore bad suggestions
- **Search ranking**: Imperfect results still provide value
- **Draft generation**: Humans will edit anyway
- **Low-stakes decisions**: Errors don't cause harm

**When 95% Isn't Good Enough:**
- **Medical diagnosis**: False negatives cost lives
- **Financial transactions**: Errors lose money
- **Legal analysis**: Missed clauses create liability
- **Safety-critical systems**: Failures cause harm

#### Real Examples of MVP Threshold Decisions

**Example 1: Email Auto-Categorization (Shipped at 82%)**

**Context:**
- Feature: Automatically categorize incoming emails into folders
- Accuracy: 82% on test data
- User impact of error: Misplaced email (user can manually move it)
- Cost of error: 10 seconds of user time

**Decision: Ship it**
**Rationale:**
- 82% accuracy = 8/10 emails auto-sorted correctly
- Users save 2 minutes per 10 emails (20 seconds per email)
- Even with errors, net time saved = 1m20s per 10 emails
- Low stakes: Misplaced email doesn't cause harm

**Example 2: Loan Approval Assistant (Held at 91%)**

**Context:**
- Feature: AI recommends approve/deny for loan applications
- Accuracy: 91% on test data
- User impact of error: Wrongly approved loan defaults; wrongly denied loan loses customer
- Cost of error: $10K-50K per mistake

**Decision: Don't ship yet**
**Rationale:**
- 9% error rate = 9 wrong decisions per 100 applications
- At $25K average cost of error = $225K risk per 100 loans
- Human review process is only 30% slower than AI
- High stakes: Errors create financial/reputational damage

**Shipped at 96% with hybrid approach:**
- AI approves obvious "yes" (high confidence)
- AI denies obvious "no" (high confidence)
- Human reviews borderline cases (30% of applications)

#### The MVP Decision Matrix

| Accuracy | Deployment Model | Use Cases | Requirements |
|----------|------------------|-----------|-------------|
| 70-79% | Shadow Mode Only | - Collect production data<br>- Prove value internally | - Full human workflow in parallel<br>- No user-facing AI yet |
| 80-85% | Human-in-Loop | - Draft generation<br>- Recommendations<br>- Low-stakes suggestions | - Easy human override<br>- Clear AI confidence signals<br>- Seamless fallback |
| 86-92% | Augmented | - Customer support<br>- Content moderation<br>- Data extraction | - Confidence-based routing<br>- Human review queue<br>- Feedback loops |
| 93-95% | Mostly Automated | - Predictions<br>- Categorization<br>- Routine decisions | - Edge case detection<br>- Escalation workflows<br>- Audit trails |
| 96%+ | Fully Automated | - Real-time systems<br>- High-volume tasks | - Exception handling<br>- Monitoring/alerting<br>- Rollback capability |

### Phased Rollouts and Shadow Deployments

#### Phase 1: Shadow Deployment (Weeks 1-4)

**Goal:** Validate model performance on real production data without user impact

**How It Works:**
1. Production traffic goes to existing system (human workflow)
2. AI model processes same data in parallel (shadow mode)
3. AI predictions logged but not shown to users
4. Team compares AI predictions vs. human decisions

**Real Example: Fraud Detection**
```
Week 1-2: Shadow Deployment
- 10,000 transactions processed
- Existing rules flagged 120 as fraud (1.2%)
- AI flagged 98 as fraud (0.98%)
- Overlap: 76 transactions (both systems agreed)
- AI-only flags: 22 (need investigation)
- Rules-only flags: 44 (need investigation)


