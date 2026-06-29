# Decision Record: Build vs. Buy an AI Capability

> Architecture Decision Record (ADR). Genericized example of how I frame and document a significant product decision.

**Status:** Accepted
**Decision owner:** Product Owner (me), with Engineering and Security
**Date:** Genericized

## Context
We needed an AI-powered capability (e.g., intelligent search / retrieval over a large content set). We could **build** it on a frontier model + our own retrieval stack, or **buy** a managed vendor product. The decision affected cost, time-to-value, control over data, and our ability to differentiate.

## Options considered

| Option | Pros | Cons |
|---|---|---|
| **Buy** (managed vendor) | Fast to ship; vendor owns relevance/infra; predictable SLA | Recurring cost; less control of data boundaries; harder to deeply customize; vendor lock-in |
| **Build** (frontier model + own retrieval) | Full control of data + UX; differentiation; flexible | Slower; we own quality, evals, and on-call; needs in-house depth |
| **Hybrid** (buy now, keep build option open via an orchestration layer) | Ship fast *and* preserve optionality | Slightly more upfront architecture work |

## Decision
Chose a **hybrid** approach: adopt a vendor to ship value quickly, but place an **orchestration layer** between our app and the AI provider so the model/vendor is swappable later. Security and data-boundary requirements were treated as gating criteria for any vendor.

## Rationale
- Time-to-value mattered; the vendor cleared the security bar and got us shipping.
- The orchestration layer means switching cost stays low — we can in-source later if differentiation or economics demand it.
- Keeps evaluation, guardrails, and tool use owned by us regardless of provider.

## Consequences
- **Positive:** Faster launch; preserved future optionality; centralized evals/guardrails.
- **Negative / watch:** Vendor cost scales with usage; we must monitor relevance quality and revisit build-in-house once volume crosses a threshold.
- **Revisit trigger:** Re-evaluate if annual vendor cost exceeds the cost of an in-house team, or if we need customization the vendor can't support.

## How I'd communicate this
One slide for leadership (the table above + the trigger), and this ADR in the repo so the *why* survives team changes.
