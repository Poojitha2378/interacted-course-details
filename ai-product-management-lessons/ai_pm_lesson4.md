## Lesson 4: Release Planning with Model Iterations

### MVP vs. MEP: Different Product Approaches for Different AI Types

Before discussing accuracy thresholds, you need to understand that **AI products require a fundamentally different "minimum" than traditional products**.

#### Traditional MVP (Minimum Viable Product)

**Philosophy:** Ship the smallest feature set that delivers value
**Goal:** Learn from users quickly with minimal investment
**Success:** Users adopt the basic feature, provide feedback
**Example:** Launch a task management app with just "create task" and "mark complete"—no tags, no due dates, no collaboration yet

**Why MVP Fails for Agentic AI:**
An agentic AI that only "kind of works" doesn't deliver value—it creates frustration. Imagine a customer service agent that handles 60% of queries correctly. Users won't trust it. They'll bypass it entirely.

#### MEP (Minimum Experienceable Product) for Agentic AI

**Philosophy:** Ship the smallest scope where AI can demonstrate autonomous value
**Goal:** Prove the AI can complete end-to-end workflows reliably in a constrained domain
**Success:** Users trust the AI to handle specific tasks without constant supervision
**Example:** Launch a customer service agent that ONLY handles password resets—but does it perfectly (95%+ success rate)

**The Critical Difference:**

| Dimension | Traditional MVP | Agentic MEP |
|-----------|----------------|-------------|
| Scope | Broad features, basic functionality | Narrow scope, deep capability |
| Accuracy | "Good enough" (70-80%) | Must be reliable (90-95%+) |
| User Experience | "This is useful but incomplete" | "This actually works autonomously" |
| Trust Building | Improve features over time | Prove autonomous capability first |
| Release Strategy | Ship fast, iterate on features | Ship narrow, prove reliability, expand scope |

**Real-World Examples:**

**MEP Success: GitHub Copilot**
- **Narrow Scope**: Code completion and generation (not full app development)
- **Deep Capability**: 55% of code accepted without modification
- **Trust Building**: Developers experienced value immediately—the AI genuinely helped
- **Expansion**: Started with simple completions → function generation → multi-file context → now chat-based assistance

**MEP Failure Avoided: ChatGPT**
- **What they didn't do**: Launch as "AI that answers ANY question about EVERYTHING"
- **What they did**: Launched as "research preview" with clear limitations
- **Scope management**: Text-only initially (no images, no web browsing, no code execution)
- **Trust building**: Set expectations low ("may produce incorrect information"), then exceeded them
- **Expansion**: Text → images → web browsing → code execution → vision → voice

**Traditional MVP Failure: Early AI Assistants (Siri, Alexa in 2011-2014)**
- **Broad Scope**: Promised to "do anything" with voice commands
- **Low Accuracy**: 40-60% intent recognition, frequent misunderstandings
- **User Experience**: Frustration—easier to just type or tap
- **Trust Erosion**: Users stopped trying after repeated failures
- **Learning**: Broad scope + low accuracy = failed product

#### Applying MEP to Your Agentic AI Product

**Step 1: Identify the Narrowest Valuable Scope**

Instead of: "AI agent that handles all customer support"
Start with: "AI agent that handles 3 specific, high-frequency queries"

**Example Scope Definitions:**

**Too Broad (Traditional MVP thinking):**

Feature: Customer service chatbot
Handles: Product questions, billing, returns, complaints, troubleshooting
Target: 70% resolution rate
Result: 70% means 3 in 10 conversations fail → users lose trust → adoption fails

**Right-Sized MEP:**
Feature: AI agent for password reset + account recovery
Handles:

Password reset requests
Account unlock (after failed login attempts)
Two-factor authentication setup
Target: 95% automated resolution (5% escalate to human)

Result: Users trust the AI for these specific tasks → builds confidence → expand to more tasks

**Step 2: Set Reliability Thresholds, Not Feature Breadth**

For agentic AI, success = **reliability in narrow scope** > breadth of capabilities

**MEP Threshold Matrix:**

| AI Product Type | Minimum Accuracy for MEP | Scope Strategy |
|----------------|-------------------------|----------------|
| **Agentic AI** (autonomous actions) | 90-95%+ | Narrow scope, high reliability |
| **GenAI** (content creation) | 75-85% | Broader scope, human editing expected |
| **AI/ML** (predictions/recommendations) | 80-90% | Depends on error cost |
| **Software + AI hybrid** | Varies by component | High reliability on critical path |

**Why the High Bar for Agentic AI:**
- Users must trust the agent to act autonomously
- Low accuracy = constant human intervention = defeats the purpose
- Better to do 3 things perfectly than 20 things poorly

**Step 3: Design Expansion Roadmap**

**Traditional MVP Expansion (Feature-Based):**
V1: Basic features (ship fast)
V2: Add more features
V3: Add even more features

**MEP Expansion (Capability-Based):**
V1: Narrow scope, 95% reliability (prove it works)
V2: Expand to adjacent workflows (maintain reliability)
V3: Increase complexity (harder tasks, still reliable)

**Real Example: Customer Service Agent Expansion**

**Phase 1 MEP (Month 1-3):**
Scope:
✓ Password resets
✓ Account unlock
✓ 2FA setup
Reliability: 96% success rate
User Experience: "It actually works!"
Volume: 2,000 queries/month automated

**Phase 2 Expansion (Month 4-6):**
Add:
✓ Subscription status checks
✓ Invoice requests
✓ Basic product information
Reliability: 94% success rate (still high)
User Experience: "It handles more stuff now"
Volume: 5,000 queries/month automated

**Phase 3 Scaling (Month 7-12):**
Add:
✓ Troubleshooting common issues
✓ Order modifications
✓ Returns/refunds (simple cases)
Reliability: 91% success rate (maintain threshold)
User Experience: "Handles most of my needs"
Volume: 12,000 queries/month automated

**Notice:** Scope expands, but reliability stays above 90% threshold. This maintains trust while increasing value.

---

### MVP Thresholds: What Accuracy is "Good Enough"?

The hardest question in AI product management: **When do we ship?**

The answer depends on whether you're building traditional AI features or agentic systems.

#### The 70-80-90-95 Rule (Revised for MEP)

**70% Accuracy: Research Prototype**
- Proves the approach is viable
- Not ready for production (traditional OR agentic)
- Good for internal demos and stakeholder alignment
- **Decision: Continue research, don't ship**

**80% Accuracy: Minimum Viable AI (Traditional AI/ML, GenAI)**
- Good enough for **human-in-the-loop** deployment
- Users notice value but expect some errors
- Requires active human oversight and correction
- **Applies to: Content generation, recommendations, predictions with human review**
- **NOT for agentic AI** (too unreliable for autonomous action)

**90% Accuracy: Production-Grade AI**
- Good enough for **augmented** deployment
- Users trust the system, review output selectively
- Human intervention for edge cases only
- **Minimum for agentic AI** (MEP threshold for autonomous actions)
- **Applies to: Most GenAI, high-stakes AI/ML, entry-level agentic systems**

**95%+ Accuracy: Autonomous AI**
- Good enough for **fully automated** deployment
- Minimal human oversight
- Errors are rare and low-impact
- **Target for mature agentic AI** (after MEP proves concept)
- **Applies to: Critical agentic workflows, safety-sensitive systems**

**Critical Insight: Context Matters More Than Numbers**

**When 75% is Good Enough (Traditional MVP):**
- **Content recommendations**: Users can ignore bad suggestions
- **Search ranking**: Imperfect results still provide value
- **Draft generation**: Humans will edit anyway
- **Low-stakes decisions**: Errors don't cause harm
- **Product type: GenAI, AI/ML recommendations**

**When 90% is the Minimum (MEP for Agentic):**
- **Autonomous customer service**: Bad responses damage brand
- **Workflow automation**: Errors break processes
- **Decision-making agents**: Wrong actions have consequences
- **Product type: Agentic AI**

**When 95% Isn't Good Enough:**
- **Medical diagnosis**: False negatives cost lives
- **Financial transactions**: Errors lose money
- **Legal analysis**: Missed clauses create liability
- **Safety-critical systems**: Failures cause harm
- **Product type: High-stakes agentic AI**

#### Real Examples of MVP vs MEP Threshold Decisions

**Example 1: Email Auto-Categorization (Traditional MVP at 82%)**

**Context:**
- Feature: Automatically categorize incoming emails into folders
- Accuracy: 82% on test data
- User impact of error: Misplaced email (user can manually move it)
- Cost of error: 10 seconds of user time
- **Product type: AI/ML classification**

**Decision: Ship as MVP**
**Rationale:**
- 82% accuracy = 8/10 emails auto-sorted correctly
- Users save 2 minutes per 10 emails (20 seconds per email)
- Even with errors, net time saved = 1m20s per 10 emails
- Low stakes: Misplaced email doesn't cause harm
- **Fits traditional MVP model** (imperfect but useful)

**Example 2: AI Agent for Invoice Processing (MEP at 94%)**

**Context:**
- Feature: AI agent autonomously processes invoices end-to-end
- Accuracy: 94% on test data
- User impact of error: Incorrect payment, vendor relationship damage
- Cost of error: $500-$5,000 per mistake
- **Product type: Agentic AI**

**Decision: Ship as MEP (narrow scope)**
**Approach:**
- **Scope limitation**: Only process invoices from top 20 vendors (predictable formats)
- **Reliability**: 94% accuracy on these specific vendors (95%+ on top 10)
- **Human handoff**: Flag unusual invoices for review (6% of total)
- **Expansion plan**: Add vendors incrementally as accuracy improves

**Why MEP worked:**
- Narrow scope = higher accuracy on specific subset
- Proved autonomous processing works reliably
- Built trust before expanding to all vendors

**Example 3: Customer Service Agent (Rejected at 91%, Shipped as MEP at 96%)**

**Initial Attempt (Failed):**
Scope: Handle all customer queries
Accuracy: 91% overall
Result: 9% error rate = 90 frustrated customers per 1,000 queries
Decision: Don't ship (too unreliable for autonomous agent)

**MEP Approach (Success):**
Phase 1 Scope:

Password resets only
Account unlock only

Accuracy: 96% on these specific tasks
Result: 4% error rate = 40 issues per 1,000 (manageable)
Decision: Ship MEP, prove reliability, then expand
Phase 2 Scope:

Add subscription questions
Add invoice requests

Maintain: 94% accuracy (above threshold)
Expand incrementally while maintaining trust

**The Pattern:** 
- Traditional MVP = ship broad, accept lower accuracy
- Agentic MEP = ship narrow, demand high accuracy
- GenAI = somewhere in between (depends on user editing capability)

#### The MVP vs MEP Decision Matrix

Use this framework to decide which approach fits your AI product:

| Question | Traditional MVP | Agentic MEP |
|----------|----------------|-------------|
| **Does the AI act autonomously?** | No (human reviews/edits) | Yes (takes actions independently) |
| **Can users easily correct errors?** | Yes (edit, ignore, override) | No (damage already done) |
| **What's the cost of an error?** | Low ($0-$10) | Medium-High ($100-$10K+) |
| **Is accuracy the differentiator?** | No (features/UX matter more) | Yes (reliability is the value prop) |
| **Can you ship broad scope?** | Yes (many features, basic quality) | No (narrow scope, high quality) |
| **Minimum accuracy for launch** | 75-85% | 90-95% |
| **Expansion strategy** | Add features → improve accuracy | Prove reliability → expand scope |

**Decision Rules:**

**Choose Traditional MVP when:**
- ✅ Human is in the loop (reviews, edits, approves)
- ✅ Errors are easily fixable by users
- ✅ Value comes from breadth of features
- ✅ Product type: GenAI with human editing, AI/ML recommendations

**Choose Agentic MEP when:**
- ✅ AI acts autonomously without human review
- ✅ Errors are costly or damage trust
- ✅ Value comes from reliability, not feature count
- ✅ Product type: Agentic AI, autonomous workflows

**Hybrid Approach (Most Common):**
Many products combine both strategies:
- **Core autonomous features** → MEP approach (narrow, reliable)
- **Assisted features** → MVP approach (broad, human-reviewed)

**Example: Customer Support Platform (Hybrid)**
MEP Component (Agentic):

Password resets (96% accuracy, fully autonomous)
Account unlocks (95% accuracy, fully autonomous)

MVP Component (Assisted):

Draft responses for complex queries (80% accuracy, agent edits)
Suggested knowledge base articles (75% accuracy, agent picks)


This hybrid approach lets you ship agentic features where reliability is proven, while providing AI assistance for tasks where human judgment is still needed.

| Accuracy | Deployment Model | Use Cases | Requirements | MVP or MEP? |
|----------|------------------|-----------|-------------|-------------|
| 70-79% | Shadow Mode Only | - Collect production data<br>- Prove value internally | - Full human workflow in parallel<br>- No user-facing AI yet | Neither (research) |
| 80-85% | Human-in-Loop | - Draft generation<br>- Recommendations<br>- Low-stakes suggestions | - Easy human override<br>- Clear AI confidence signals<br>- Seamless fallback | **Traditional MVP** |
| 86-92% | Augmented | - Customer support (assisted)<br>- Content moderation<br>- Data extraction | - Confidence-based routing<br>- Human review queue<br>- Feedback loops | **MVP or MEP** (depends on autonomy) |
| 93-95% | Mostly Automated | - Predictions<br>- Categorization<br>- Routine decisions | - Edge case detection<br>- Escalation workflows<br>- Audit trails | **Agentic MEP** (narrow scope) |
| 96%+ | Fully Automated | - Real-time systems<br>- High-volume tasks | - Exception handling<br>- Monitoring/alerting<br>- Rollback capability | **Agentic MEP** (proven scope) |

### Phased Rollouts and Shadow Deployments

#### Phase 1: Shadow Deployment (Weeks 1-4)

**Goal:** Validate model performance on real production data without user impact

**How It Works:**
1. Production traffic goes to existing system (human workflow)
2. AI model processes same data in parallel (shadow mode)
3. AI predictions logged but not shown to users
4. Team compares AI predictions vs. human decisions

**Real Example: Fraud Detection**
Week 1-2: Shadow Deployment

10,000 transactions processed
Existing rules flagged 120 as fraud (1.2%)
AI flagged 98 as fraud (0.98%)
Overlap: 76 transactions (both systems agreed)
AI-only flags: 22 (need investigation)
Rules-only flags: 44 (need investigation)

Week 3-



