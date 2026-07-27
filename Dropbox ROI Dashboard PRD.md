# PRD: Vantage — AI Utilization & ROI Dashboard (Dropbox)

## 1. Problem Statement
Dropbox has ~2,000 employees across 15 departments, with access to ~300 AI-capable applications (out of 800 total software apps). Leadership cannot currently answer: **is our AI investment producing measurable business value, and where should we invest next?** There's no unified view connecting *who has AI access*, *who actually uses it*, *how much*, and *what it returns* — so spend decisions are made on anecdote rather than evidence.

## 2. Approach
Build an executive dashboard that connects four layers of data per employee/department/application:
1. **Demographics & org data** (department, seniority, tenure, location, employment type, age/gender)
2. **AI access & usage data** (which apps, how much, how consistently)
3. **Cost data** (license, infra, setup, training, support, risk/rework)
4. **Outcome data** (department-specific business KPIs — deals closed, ticket resolution time, deployment frequency, etc.)

These are joined so usage and demographic cuts can be traced all the way through to dollar ROI, not just activity counts.

## 3. Segmentation Stages (brief)
Five sequential measurement stages, funnel-style, plus two parallel layers:

| Stage | Question it answers |
|---|---|
| **1. Availability** | Who *could* use AI? (licenses granted, entitlement gaps, "shelf-ware") |
| **2. Adoption** | Who *actually started* using it? (DAU/WAU/MAU, first-use lag, churn) |
| **3. Utilization** | How *much and how well* is it used? (prompts, sessions, acceptance rate) |
| **4. Efficiency** | Did it *save time*, net of rework? (time saved, approval rate) |
| **5. Business Outcomes** | Did it move a *real KPI*? (revenue, cycle time, quality — not activity counts) |
| **Cost (parallel)** | What did it cost, all-in? (license, infra, setup, training, support, risk) |
| **ROI & Value (synthesis)** | Net Value, ROI %, Payback Period — combining Outcomes against Cost, isolated via a control-group comparison so we're not just reading a raw correlation |

All five stages and the cost layer can be sliced by the same segmentation filters (department, seniority, tenure, location, employment type, age band, gender), so leadership can ask "is this pattern true for everyone, or just one group?"

## 4. Dashboard Views

**Page 1 — Executive Overview**
The landing page. Company-wide headline numbers (adoption, spend, hours saved, ROI %), a leaderboard of top/bottom-performing departments and applications by ROI, and global filter chips. Answers "are we winning overall, and where do I drill in?"

**Page 2 — Employee Details**
Breaks adoption and ROI down by every segment (seniority, tenure, location, employment type, and governance-gated age/gender) plus an activation-lag view (how fast new hires start using AI after being granted access). Answers "which employee groups are actually getting value, and which are being left behind?"

**Page 3 — Department Deep-Dive**
The detail view behind Page 1's department leaderboard. Shows one department's full funnel (Availability → ROI) benchmarked against the company average, its trend over time, its outcome KPIs (true business metrics, not activity counts), and which apps it relies on. Answers "why is this department's ROI what it is, and what's the bottleneck?"

**Page 4 — Application Portfolio**
The detail view behind Page 1's app leaderboard. Every AI-capable app plotted by adoption vs. ROI (sized by cost, colored by tier), plus a sortable register with license cost, utilization, and status (healthy / underutilized / shelf-ware / shadow AI). Answers "which of our 300 AI tools are earning their license fee, and which should we cut?"

**Page 5 — ROI & Business Outcomes Detail**
The "show your work" page behind the headline ROI number. Full cost breakdown (license, infra, setup, training, support, risk/rework), payback period, and — critically — a counterfactual chart comparing a high-adoption cohort against a matched control group, so the ROI claim isn't just correlation. Closes with a methodology/assumptions footnote (hourly rate used, how "hours saved" was calibrated, how double-counting was avoided). Answers "can I trust this number, and how was it built?"

## 5. Assumptions & Restrictions
This is an academic/case-study exercise, not a production system. Key limitations to flag to any reader:

- **Data is hypothetical**, not connected to real Dropbox systems, usage logs, or HRIS. All figures are illustrative.
- **Causal claims are simulated**, not proven — the counterfactual/control-group comparison demonstrates the *method* required for a valid ROI claim, not a validated real-world result.
- **"Hours saved" requires real calibration** (task-time benchmarks + survey instruments) that doesn't exist here — the dashboard shows where that number would plug in.
- **Age and gender cuts are governance-gated by design** (aggregate-only, suppressed below n=5, equity-analysis purpose only) — this is a policy stance embedded in the design, not a technical limitation, and would need real Legal/HR sign-off before deployment.
- **Individual-level scoring is deliberately excluded** — all usage data is shown at cohort/department/role level to avoid performance-review misuse and Goodhart's-law gaming.
- **Shadow AI (unsanctioned tools) is self-reported**, not system-logged, so it's flagged for security review but excluded from the ROI calculation until real instrumentation exists.
- **Single point-in-time snapshot** — no live data pipeline, refresh, or trend beyond the illustrative 6-month series on Pages 3 and 5.

## 6. Future Scope
- Connect to real usage-log and HRIS data sources to replace hypothetical figures.
- Build out Page 6 (Adoption & Utilization Trends — cohort curves, stickiness over time) and Page 7 (Risk & Governance — compliance flags, shadow AI, error rates), scoped out of this assignment as optional/stretch.
- Automate the causal-inference pipeline (staggered rollout tracking) so the counterfactual comparison runs on real cohorts, not illustrative ones.
- Extend cost model to actual per-department chargeback/showback for budget planning.
- Add alerting for shelf-ware (licensed-but-unused apps) and lapsed-user cohorts.
- Formal governance review (Legal/People Analytics) before any deployment involving demographic cuts.
