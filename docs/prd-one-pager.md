# Sample PRD (One-Pager): Internal AI Assistant

> Genericized example of how I scope a product. Kept to one page on purpose — a PRD should fit in a reader's head.

**Author:** Product Owner (me) · **Status:** Draft → Reviewed · **Stage:** MVP

## Problem
A team loses meaningful time each week on repetitive lookup and content-assembly tasks. The work is high-volume, low-judgment, and error-prone — a strong fit for an LLM assistant, *if* it's accurate enough to trust.

## Users & jobs-to-be-done
- **Primary:** Individual contributors who do the repetitive task today.
- **Secondary:** Their manager, who needs consistency and auditability.
- **JTBD:** "When I need X, help me get a correct draft in seconds instead of assembling it manually."

## Goals
- Cut task time by a meaningful margin (target set with the team before build).
- Reach an accuracy bar on a **golden set** that the team agrees makes output trustworthy.
- Ship an MVP that proves the workflow before heavier investment.

## Non-goals
- Full automation with no human in the loop (v1 keeps a review step).
- Replacing the system of record.
- Supporting every edge case at launch.

## Solution (MVP)
A scoped assistant that retrieves the right context and drafts the output, with a human review step. Guardrails and logging from day one so we can measure quality.

## Success metrics
- **Primary:** time-per-task (before vs. after).
- **Quality:** accuracy on the golden set; thumbs-up rate; correction rate.
- **Adoption:** weekly active users among the target team.
- **Guardrail:** rate of unsafe/incorrect outputs reaching the user (must trend to ~0).

## Risks & mitigations
- *Model is sometimes wrong* → human-in-the-loop, confidence thresholds, golden-set evals before ship.
- *Low adoption* → co-design with the team; ship where they already work.
- *Scope creep* → strict non-goals; ship MVP, then iterate on evidence.

## Milestones
1. Golden set + accuracy bar agreed with the team.
2. MVP with guardrails + logging.
3. Pilot with the target team; measure against success metrics.
4. Decide: harden & scale, or stop.

## Open questions
- What's the minimum accuracy that makes this trustworthy for this team?
- Which surface (existing tool vs. standalone) drives the most adoption?
