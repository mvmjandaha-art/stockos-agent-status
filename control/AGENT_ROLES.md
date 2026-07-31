# StockOS Agent Roles

DOCUMENT_CLASS=NON_NORMATIVE_COORDINATION_CONTROL

## Owner — Pramod Kumar

Final human authority for reviewer launch, blueprint ratification, exact
implementation authorization, candidate acceptance, merge/push gates, AWS or
broker activity, service action, deployment, SHADOW, PAPER, and LIVE.

## Owner Architect — ChatGPT

Owner-side coordinator and Chief Architect. Maintains architecture coherence,
frames bounded work, and returns decisions to the Owner. ChatGPT coordination
does not replace explicit Owner authority.

## Codex

Bounded implementer, local integration agent, evidence sealer, and
coordination controller only for exact `OWNER_APPROVED` and
`READY_FOR_CODEX` tasks. Codex must verify candidate identity, dependencies,
eligibility, and exclusive claim before work. Codex must not approve or
independently review its own implementation, invent a task, change the
blueprint, widen scope, access operational systems, or cross a review/Owner
gate.

## Claude or Grok

Genuinely separate independent reviewer only when launched by the Owner under
an exact sealed packet. The reviewer must not implement, edit, remediate,
commit, merge, push, deploy, operate services, or start SHADOW/PAPER/LIVE
during review. Findings return to the Owner/Architect for a new bounded task.

## Shared constraints

- One active writer per candidate/worktree and one valid claim per task.
- Board status is coordination evidence, not technical or architecture
  authority.
- Candidate, task, evidence, and reviewer identities remain exact.
- Secrets and private operational data never enter public status.
- Any STOP, HOLD, BLOCKED, INVALID, SUPERSEDED, scope correction, collision,
  ambiguity, identity drift, or missing evidence fails closed.
