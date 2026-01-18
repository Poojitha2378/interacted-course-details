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



