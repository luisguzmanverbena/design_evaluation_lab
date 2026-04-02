# Design Principles Evaluation

Score the design against all 7 principles. Every principle must receive a score — none may be skipped. Use the level descriptions to calibrate; they define what each score means concretely.

## Scale

- **0 - Missing:** The principle is entirely absent and unacceptably so.
- **1 - Partial:** The principle is present in a minimal way. There is room for improvement.
- **2 - Effective:** The principle is well-implemented and contributes positively to the user experience.

## Principles

### End to end. In and out of our products. (E2E. In-N-Out.)
| 0 - Missing | 1 - Partial | 2 - Effective |
|---|---|---|
| The solution does not instruct or assist the user on next steps if they are outside of the scope of the solution. | The solution somewhat assists the user on next steps. The user will need to take additional unguided steps to complete their JTBD. | The solution is able to provide a smooth handoff to the next step of the experience, inside or outside of our products. |

### Unified and consistent (consistency within the given product/space)
| 0 - Missing | 1 - Partial | 2 - Effective |
|---|---|---|
| Most important components of the experience are not from the design system(s) and/or do not follow conventional patterns. | Most important components and workflows adhere to known standards. Some elements may not be standard. | The full experience uses known patterns and components. Any custom components have been thoroughly vetted. |

### Content is clear and technically accurate
| 0 - Missing | 1 - Partial | 2 - Effective |
|---|---|---|
| The content does not describe the purpose of the experience. CTAs are generic and non-descriptive. | The content or CTAs partially describe their intended message. | Content describes the workflow and CTAs adequately describe the outcomes. |

### The right interface for the right JTBD
| 0 - Missing | 1 - Partial | 2 - Effective |
|---|---|---|
| The interface is a generic way to interact with the product. It is a reproduction of another interface and does not add substantial value. The experience does not fully leverage the interface (API/CLI/UI). | The interface is adequate for some JTBDs. The user will need help in completing their JTBD. | The experience balances speed, control and convenience for all given JTBDs and personas. |

### We are trusted partners / Guide and recommend
| 0 - Missing | 1 - Partial | 2 - Effective |
|---|---|---|
| The experience provides multiple options to accomplish a JTBD, but does not give a recommendation on best practices. | The experience provides some guidance on best practices. The user might struggle to find the right options for their JTBD. | The experience takes into account a user's preferences and needs. It recommends an approved and efficient pattern and clearly articulates the value. |

### Design for the right scale
| 0 - Missing | 1 - Partial | 2 - Effective |
|---|---|---|
| The solution does not work for average use or edge cases. | The solution accommodates average use, but not edge cases, or vice versa. | The design is flexible and can accommodate all common and edge cases. The solution is reasonably future-proofed. |

### Design for automation and low interaction
| 0 - Missing | 1 - Partial | 2 - Effective |
|---|---|---|
| The experience assumes manual interaction for tasks that should be automated. No config export, API references, or automation support. | The experience supports some automation patterns but still requires manual steps for common workflows. | The experience minimizes manual interaction. Automation paths (config export, API references, IaC snippets) are first-class. Alerts, notifications, and repetitive tasks are handled systematically. |

## Output format

For each principle, provide:
- **Score** (0, 1, or 2)
- **Rationale** — one-line justification required for all scores

All 7 principles must be scored. No principle may be skipped or marked as not applicable.
