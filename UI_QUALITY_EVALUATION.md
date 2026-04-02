## The 5 Quality Dimensions

Evaluate the artifact across all 5 dimensions. If a dimension has insufficient observable evidence, say so — do not fabricate observations.

---

### 1. Mental Model Integrity

**Focus:**
- Affordances — do controls signal their behavior?
- Visibility of system state — does the user know what's happening?
- Mapping between controls and outcomes
- Error prevention and recovery
- Mental model coherence — does the interface reinforce a consistent internal logic?

---

### 2. Reduction & Necessity

**Focus:**
- Feature necessity — does every element earn its place?
- Elimination opportunities — what could be removed without loss?
- Signal-to-noise ratio
- Structural simplicity
- Long-term maintainability

Evaluate this dimension before Workflow Power & Autonomy. Remove first, then assess what compounds.

---

### 3. Heuristic Risk Radar

**Focus:**
- Consistency — does the interface follow its own rules?
- Feedback clarity — does the user know when actions succeed or fail?
- Error prevention — are destructive actions guarded?
- Undo mechanisms — what's reversible, what isn't?
- Naming clarity — are labels unambiguous for the context?
- Edge-case friction — what breaks at scale or in non-happy-path scenarios?

Focused exclusively on what can go wrong — not general model quality.

---

### 4. Spatial & Interaction Harmony

**Focus:**
- Hierarchy — is the most important content most prominent?
- Information density — is data load appropriate for the context?
- Motion meaning — does any animation or transition communicate something, or is it decorative?
- Visual rhythm — is there consistent spacing, sizing, alignment?
- Layout coherence — does the layout hold together across states?
- Craftsmanship — evidence of deliberate decisions vs. defaults

---

### 5. Workflow Power & Autonomy

**Focus:**
- Can the user complete the full task without leaving the interface or requiring external help?
- User independence — does the interface increase capability over time?
- Reduction of coordination overhead — fewer handoffs, approvals, context-switches
- Efficiency gain for repeat or high-frequency use

Evaluate on the surviving surface after Reduction & Necessity, not on the page as-is.

---

## Required Output Structure

For **each** of the 5 dimensions:

```
### [Dimension Name]

**Strengths**
- [Specific, non-generic. Tied to an observed element or behavior.]
- [Minimum 2, maximum 3.]

**Weaknesses**
- [Specific, non-repetitive. If a weakness spans multiple dimensions, place it under the most diagnostic one.]
- [Minimum 2, maximum 3.]

**UX Score**: [1–10]

**Highest-Leverage Improvement**: [One change. Specific. Actionable.]
```

### Scoring Calibration

| Score | Meaning |
|-------|---------|
| 1–2 | Broken |
| 3–4 | Weak |
| 5–6 | Acceptable but flawed |
| 7–8 | Strong |
| 9 | Exceptional |
| 10 | World-class and rare |

Do not inflate scores.

---

## After the Dimension Reviews

Provide all four of the following:

### 1. Disagreement Map
Where quality dimensions conflict with each other. List each conflict as a bullet with the implication for design direction.

### 2. Structural Flaw
The single highest-confidence systemic weakness across all dimensions. One finding.

### 3. 20% Simplification
One change that improves clarity or power by approximately 20%. Specific. No hedging.

### 4. Strategic Recommendation
Choose exactly one:
- **Ship as-is**
- **Iterate**
- **Simplify**
- **Re-architect**
- **Kill feature**

Based only on observed evidence. One-line rationale.