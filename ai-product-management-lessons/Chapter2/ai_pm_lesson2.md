
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

### Sprint Planning with Experimentation Buffers

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

### Success Metrics Beyond Velocity

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
