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




