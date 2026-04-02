# Personas

Evaluate from the perspective of each persona below. Not every persona will be relevant to every screen — skip personas that would not realistically encounter the artifact.

## 1. The Administrator
**Daily Operator.** Manages the product itself — configuration, infrastructure, policies, upgrades. CLI/IaC-native, uses the UI for monitoring and debugging.

- **Primary goal:** Confirm system health and take operational action without leaving the page.
- **Frustration trigger:** Having to navigate elsewhere to answer basic operational questions.
- **Interaction pattern:** Daily visits. Scans for anomalies, then drills into specifics. Wants a control room, not a spec sheet.
- **Assigned dimensions:** Model & Feedback, Risk Audit, Leverage & Autonomy, Spatial & Craft

## 2. The Secret Consumer
**Application Developer.** Needs credentials or data from the system. Doesn't care about internals — just wants reliable delivery. Explores via UI, automates via SDK/API.

- **Primary goal:** Get to the resource they need or configure their app to retrieve it. Infrastructure details are irrelevant.
- **Frustration trigger:** Landing on an infrastructure page when their job is "get a value." Being shown actions they can't perform.
- **Interaction pattern:** Occasional UI visits during setup. Once automated, never returns.
- **Assigned dimensions:** Model & Feedback, Reduction & Necessity, Leverage & Autonomy

## 3. The Governance & Compliance Owner
**Security / Policy Lead.** Enforces access control, audits access patterns, ensures policies are met. Needs to verify permissions, trace events, and produce compliance evidence.

- **Primary goal:** Assess security posture at a glance — who has access, what's exposed, is the audit trail intact.
- **Frustration trigger:** Risky configurations presented as neutral facts. High-privilege actions without governance context or audit visibility.
- **Interaction pattern:** Periodic reviews. Needs to quickly determine "is this configured securely?" and export evidence.
- **Assigned dimensions:** Risk Audit, Model & Feedback, Leverage & Autonomy

## 4. The CI/CD Integrator
**Platform / DevOps Engineer.** Wires the system into pipelines — dynamic credentials, automation, config injection at deploy time. Lives in automation, hits the UI when things break.

- **Primary goal:** Get connection details and auth method guidance needed to configure a pipeline.
- **Frustration trigger:** Being guided toward manual auth patterns when machine auth is the correct approach.
- **Interaction pattern:** One-time setup visit, then rare debugging visits. Needs the page to accelerate automation, not assume manual interaction.
- **Assigned dimensions:** Leverage & Autonomy, Risk Audit, Model & Feedback

## 5. The Newcomer
**First-Time User.** First encounter with the product. Needs to build a mental model without breaking anything. UI-dependent, documentation-dependent.

- **Primary goal:** Understand what this is, what they can do with it, and what to do first.
- **Frustration trigger:** Unexplained domain terms. High-consequence actions without educational guardrails.
- **Interaction pattern:** Exploratory. Reads everything. Afraid to click destructive-looking actions. Needs progressive disclosure and sequenced guidance.
- **Assigned dimensions:** Model & Feedback, Reduction & Necessity, Risk Audit, Spatial & Craft

## 6. The Infrequent Overseer
**Engineering Manager / Team Lead.** Checks in weekly or monthly — reviews patterns, approves changes, tracks adoption. Re-learns the interface every visit.

- **Primary goal:** Answer "is this healthy, secure, and being used correctly?" in under 30 seconds.
- **Frustration trigger:** No temporal context — no activity, no trends, no "what changed since last time."
- **Interaction pattern:** Infrequent, scan-heavy. Needs the page to surface what matters without requiring deep navigation.
- **Assigned dimensions:** Model & Feedback, Leverage & Autonomy, Reduction & Necessity

## Notes

- If a persona is not realistically relevant to the artifact, skip it.
- For each relevant persona, evaluate all assigned dimensions.
- Avoid repeating the same critique across personas unless the overlap itself is the finding.
