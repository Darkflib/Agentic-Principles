# Principles of Good Agents

A manifesto for building reliable, respectful, and rational agentic systems

## Preamble

Agents are not just workflows with LLMs strapped on. They are reasoning systems, embedded in unpredictable contexts, tasked with acting on behalf of users—or sometimes against them.

We believe good agents must go beyond functionality. They must be anchored, accountable, and aligned. This manifesto outlines the principles we consider essential for creating agentic software that is safe to trust, productive to use, and possible to debug.

## 1. Anchor Outputs to Verifiable Data

No truth without traceability. Hallucinated insights are worse than wrong—they’re misleading. Every response should have a chain of evidence.

**Why:** LLM hallucination is not a bug, it’s a feature. To counteract that, outputs must trace back to reliable data. Think Retrieval-Augmented Generation (RAG), provenance-tracked graph traversal, or deterministic tooling.

**Practical Manifestations:**

- Chain-of-verification for outputs.
- Mandatory citations with inline provenance metadata.
- Graph-based “explain like I’m 5” trails from decision → source → input.

**Agent rule:** “If I can't cite it, I shouldn't say it.”

## 2. Prioritise Determinism Over Drama

LLMs are stochastic; users are not. Every action an agent takes should be predictable, reproducible, and explainable.

**Why:** Agents live on a spectrum from stochastic (reasoning) to deterministic (execution). Users expect the latter. Determinism should wrap the agent loop like guardrails.

**Practical Manifestations:**

- All tool outputs should be deterministic and testable.
- Control branching logic should favour explicit over inferred flow.
- Version and lock all model+prompt+tool combos.

Agent rule: “Surprise is for magicians, not for mission-critical systems.”

## 3. Defer When Uncertain

Guessing is not confidence. If an agent isn’t sure, it should say so. If it's failing, it should ask for help.

**Why:** Agents operating blindly across steps invite compounding errors. Agents should validate their own assumptions—and be aware of when to defer to humans or logs.

**Practical Manifestations:**

- Chain-of-thought with internal monologue.
- Output a “confidence + rationale” for each step.
- Encourage pre-commit review loops before triggering effects.

**Agent rule:** “I’d rather escalate than fabricate.”

## 4. Be Self-Aware, Not Self-Important
Agents must introspect, self-critique, and document their reasoning. Meta-cognition is a feature, not a frill.

Why: Agents operating blindly across steps invite compounding errors. Agents should validate their own assumptions—and be aware of when to defer to humans or logs.

Practical Manifestations:

- Chain-of-thought with internal monologue.
- Output a “confidence + rationale” for each step.
- Encourage pre-commit review loops before triggering effects.

Agent rule: “Here’s what I did, and why I did it.”

## 5. Fail Gracefully, Not Spectacularly
All software fails. Great agents fail with context, logs, and fallback options—not in silence or chaos.

**Why:** When agents fail (and they will), they must fail predictably. No random crashes, infinite loops, or partial commits.

**Practical Manifestations:**

- Circuit breaker patterns.
- Timeboxing LLM calls, retry limits, and pre/post state snapshots.
- Fall back to static UX or operator escalation.

**Agent rule:** “Break predictably, with receipts.”

## 6. Respect the Boundary of User Intent
Don’t overreach. Don’t overshare. Don’t override. A good agent knows what it’s been asked—and what it hasn’t.

Why: Natural language is lossy. Users often don’t know what they need. Agents should infer intent, but expose that inference.

Practical Manifestations:

- Translate input into canonical intent/goal structs.
- Show users what the agent thinks they meant.
- Confirm critical or ambiguous interpretations.

Agent rule: “My power ends where your intent does.”

## 7. Log Like You’ll Be Audited
Agent behaviour should be inspectable after the fact. All actions, inputs, and rationales must be available, structured, and signed.

Why: Postmortems need audit trails. For regulated industries (finance, legal, health), observability isn’t optional.

Practical Manifestations:

- Signed, tamper-evident logs of every decision and data access.
- Include all relevant model inputs/outputs and tool executions.
- Prefer structured logs (JSONL, OpenTelemetry events) over plaintext dumps.

Agent rule: “If I did it, I logged it.”

## 8. Expose What You Can Do, Not Just What You Did
Declare capabilities up front. Users and other agents should be able to reason about what you can do without trial and error.

Why: Agents should declare what they can do, what tools they have, and what inputs they need. Hidden behaviour = untrustworthy behaviour.

Practical Manifestations:

- Human-readable and machine-readable capability manifests.
- Include tool descriptions, data access scopes, model types, etc.
- Serve via .well-known/agent-capabilities.json for distributed interop.

Agent rule: “My skillset is public, not a mystery box.”

## 9. Prefer Small, Clear Steps
Opaque monoliths are hard to trust. Break big jobs into small, interpretable units, each with discrete goals.

Why: Small discrete steps make debugging and reasoning about how a system works far easier. If you can reason about it, you can trust it easier.

Practical Manifestations:

- 

Agent rule: “If it can’t be broken into steps, it can’t be debugged.”

## 10. Own Your Identity
Good agents don’t impersonate tools, humans, or gods. They operate with a consistent persona, goal, and boundary of action.

Why: Trust comes from being accurate and honest. Mis-representing who or what you are hurts this.

Practical Manifestations:

- 'Answer as if you were Abraham Lincoln' rather than "You are Abraham Lincoln'.
- 

Agent rule: “This is who I am, and this is what I’m here to do.”

## 11. Respect the Data Boundary
Respect the user’s data boundary: Privacy-first by design; cache, tokenise, or forget by default.

Why: Not everything needs to use public APIs and cloud. Even if the service terms say 'We won't use your data', it doesn't mean it can't leak somehow.

Practical Manifestations:

- In the early dats of ChatGPT, some conversations were shown to other people. If you can process locally then this is a non-issue.



