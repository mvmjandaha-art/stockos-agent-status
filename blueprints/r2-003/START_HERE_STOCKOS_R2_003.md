# START HERE — StockOS Three-Layer R2-003

DOCUMENT_CLASS=NON_NORMATIVE_NAVIGATION_AND_ROADMAP
AUTHORITATIVE_BLUEPRINT=STOCKOS_THREE_LAYER_FINAL_BLUEPRINT_R2_003
AUTHORITATIVE_BLUEPRINT_SHA256=e407d7a5a3753b1455372635cfd982efbd5a590f7c868a1e961daafb38431376
AUTHORITATIVE_BLUEPRINT_SIZE=39665
CORRECTION_CHAIN=D-001
DO_NOT_USE_AS_REPLACEMENT_BLUEPRINT=YES

This document is a navigation aid derived from the sealed R2-003 blueprint,
its D-001 scope-correction ledger, and the 38-row gap report incorporated by
the blueprint's §33 production-readiness analysis. It does not change,
ratify, summarize away, or replace the authoritative blueprint. If this
document conflicts with the exact R2-003 mirror, the exact R2-003 mirror wins.

## 1. What StockOS Is

StockOS is intended to be the sovereign system for trading research,
strategy artifacts, decisions, risk, capital, operating mode, final
admission, lifecycle policy, reconciliation, forensic evidence, and learning.
The target is an evidence-driven trading operating system for Indian markets,
with an independently bounded Delta 24x7 path retained for future
qualification. The blueprint covers intraday and other strategy research
capabilities, but it does not authorize a trading mode, instrument, broker,
account, or deployment merely because the architecture describes one.

The operating model is:

- StockOS owns research, immutable strategy proposals, PolicyEngine decisions,
  MTC proposal intake and final admission, RiskDecision, CapitalDecision,
  ModeAuthority, StartupGate, sealed manifests, AuthorizedExecutionEnvelope,
  lifecycle and protective-exit policy, reconciliation, forensic records, and
  immutable learning evidence.
- Nautilus is only the proposed implementation of the StockOS execution
  runtime. It may perform veto-only structural checks, OMS/order-state work,
  execution-engine work, and portfolio mirroring after exact ingress
  validation. It is not a parallel decision, risk, capital, mode, broker, or
  lifecycle authority.
- OpenAlgo is only the proposed connectivity plane. It may provide qualified
  market-data REST/WS, exact broker symbol mapping, exact
  place/modify/cancel transport, and normalized broker events. It may not
  select strategy, instrument, side, quantity, account, broker, mode,
  failover, or exposure.

The legal system is fail closed. Market-data gaps, stale snapshots, invalid
or expired authority, contract errors, unknown write results, sequence or
hash-chain breaks, cross-account provenance, incomplete reconciliation, and
unsafe stop conditions block admission or stop progression. Unknown broker
write state requires reconciliation and prohibits blind resubmission.

Research and learning consume normalized market data and reconciled immutable
execution evidence. They can generate, backtest, and score strategy proposals
but cannot approve themselves, allocate capital, choose PAPER/LIVE, open an
execution session, call a broker, read broker credentials, or mutate execution
state. Persistence and auditability require a durable manifest, receipts,
order/event provenance, reconciliation completion, a hash-correlated forensic
ledger, recovery evidence, and immutable learning records.

The target supports one authority chain, one matching engine per session, one
active writer per authority state, demand-driven services, bounded queues and
retries, measured resource limits, process custody, explicit rollback, and
Owner-controlled authorization. The Owner remains the final human authority
for blueprint ratification, implementation, SHADOW, real PAPER, and LIVE.

Source: authoritative blueprint §§1–5, 8–15, 20–25, 31–36.

## 2. Authoritative Document Chain

The byte-identical architecture authority is:

- [STOCKOS_THREE_LAYER_FINAL_BLUEPRINT_R2_003.md](https://github.com/mvmjandaha-art/stockos-agent-status/blob/main/blueprints/r2-003/STOCKOS_THREE_LAYER_FINAL_BLUEPRINT_R2_003.md)
  — 39,665 bytes, SHA-256
  `e407d7a5a3753b1455372635cfd982efbd5a590f7c868a1e961daafb38431376`.
- [STOCKOS_THREE_LAYER_R2_D001_SCOPE_CORRECTION_LEDGER.md](https://github.com/mvmjandaha-art/stockos-agent-status/blob/main/blueprints/r2-003/STOCKOS_THREE_LAYER_R2_D001_SCOPE_CORRECTION_LEDGER.md)
  — SHA-256
  `92c91d45dbfb975ef028b917d0ed1f49dc613ff1dc53a4526f5d472c070eecc1`.

D-001 first corrected the blueprint's stale summary counts to 12 P1 PAPER
blockers and 2 P4 future optimizations while retaining 38 total gaps. R2-003
then corrected the scope declaration from the misleading shorthand
`D-001_ONLY` to
`D-001_AND_PERMITTED_PACKAGE_PROVENANCE_ONLY`. The ledger proves that
successor identity, seal-chain provenance, exact-copy evidence, and routing
identities also changed while D-001 substance, gap classifications,
architecture invariants, phase authorizations, and model-role boundaries did
not.

This START_HERE file is not byte-identical authority. It is an index and
roadmap that points back to the exact mirror above.

Source: blueprint header and §§33–36; correction-ledger BP-001–BP-003,
COPY-001–COPY-004, NEW-001–NEW-009, and Locked substantive results.

## 3. Three-Layer Architecture Map

### Layer 1 — StockOS authority

- **Purpose:** remain the sovereign research, decision, risk, capital, mode,
  admission, lifecycle, reconciliation, and forensic authority.
- **Owned responsibilities:** Research Engine and immutable strategy
  artifacts; PolicyEngine; MTC proposal intake and final admission;
  RiskDecision; CapitalDecision; ModeAuthority; StartupGate; sealed execution
  manifest; AuthorizedExecutionEnvelope; lifecycle and protective-exit
  policies; broker/account selection authority; reconciliation; forensic
  ledger; immutable learning evidence.
- **Inputs:** normalized fresh sequenced market data; strategy proposals;
  current market snapshots; reconciled broker and execution events; Owner
  authority and session configuration.
- **Outputs:** approved or rejected decisions; signed receipts; sealed
  manifest; exact AuthorizedExecutionEnvelope; reconciliation decisions;
  immutable forensic and learning evidence.
- **Prohibited responsibilities:** it may not bypass Policy→MTC→Risk→Capital
  →Mode→MTC-final admission; the research subsystem may not self-promote,
  allocate capital, choose PAPER/LIVE, call a broker, or mutate execution
  state; the authority process may not read broker credentials.
- **Dependencies:** valid authority receipts, current market snapshot,
  canonical instrument mapping, manifest store, StartupGate, reconciliation
  and forensic availability, and a qualified runtime/connectivity path when a
  session is separately authorized.
- **Authority boundary:** StockOS alone owns trading decision, risk, capital,
  mode, broker/account selection, lifecycle, final admission, reconciliation
  policy, and forensic truth.
- **Failure behavior:** reject invalid or expired authority, stale/gapped
  data, missing evidence, unsafe modes, unresolved unknown orders, or
  incomplete reconciliation; never synthesize missing authority.

### Layer 2 — Nautilus execution implementation

- **Purpose:** implement the StockOS execution runtime after exact envelope
  validation and, for simulation, only after explicit equivalence and cutover.
- **Owned responsibilities:** StockOSAuthorityIngress verification,
  veto-only structural checks, OMS/order state, execution-engine mechanics,
  execution event streaming, reconciliation snapshots, and portfolio-state
  mirroring.
- **Inputs:** exact valid current signed manifest-bound
  AuthorizedExecutionEnvelope values and normalized broker events.
- **Outputs:** command acceptance or rejection, exact execution commands,
  provenance-bound execution events, OMS/portfolio mirror state, and
  reconciliation snapshots.
- **Prohibited responsibilities:** no signal generation, instrument/side
  selection, sizing, capital allocation, mode/session opening, broker/account
  selection, lifecycle creation, risk override, rejected-order approval,
  envelope repair, or exposure enlargement.
- **Dependencies:** StockOS authority ingress and attestation; versioned
  contract; bounded transport; one matching engine; exact OpenAlgo adapter;
  reconciliation and process/session custody.
- **Authority boundary:** Nautilus can veto structurally but cannot create or
  expand StockOS authority. Its portfolio is a mirror, not the system of
  record.
- **Failure behavior:** reject malformed, stale, unspecified, reordered,
  gapped, hash-broken, or cross-account inputs; unknown write results remain
  unknown and require StockOS reconciliation; no blind retry.

### Layer 3 — OpenAlgo connectivity

- **Purpose:** isolate qualified market-data and broker connectivity from
  trading authority.
- **Owned responsibilities:** broker-qualified read APIs and streams;
  canonical-to-qualified broker symbol transport mapping; exact
  place/modify/cancel HTTP transport; exact request/response-byte custody;
  normalized broker events.
- **Inputs:** qualified broker data or an exact already-authorized adapter
  request whose authority fields are mapped or atomically custody-bound.
- **Outputs:** normalized market-data payloads, exact transport responses, and
  normalized ACK/reject/partial/fill/modify/cancel/unknown events.
- **Prohibited responsibilities:** no trading decision, broker/account/
  instrument/side selection, quantity change, allocation, mode/session
  change, failover, lifecycle policy, smart/options/multi/basket/split orders,
  hosted strategy execution, automatic square-off, or exposure enlargement.
- **Dependencies:** pinned and legally reviewed dependency custody; one
  qualified broker capability; loopback-only default-deny endpoint policy;
  broker-scoped credentials isolated to this process; bounded reads and
  reconciliation.
- **Authority boundary:** OpenAlgo carries exact bytes; it never grants
  authority and never returns credentials upstream.
- **Failure behavior:** ambiguous write results become
  `ORDER_STATE_UNKNOWN`; block conflicting orders and require read-only status
  and reconciliation; never blindly resubmit, hedge, flatten, or fail over.

Source: blueprint §§6, 8–21, 23, and 25.

## 4. End-to-End StockOS Data and Decision Flow

The legal data and order path is:

1. **Market/broker data intake:** selected qualified broker read API/stream
   → OpenAlgo normalized payload (or the current qualified live feed during
   the initial transition).
2. **Normalization and validation:** StockOS market-data ingress → canonical
   instrument mapping → freshness, sequence, provenance, clock, and
   continuity validation → immutable `MarketSnapshot`.
3. **Feature and strategy processing:** StockOS research and strategy
   components consume immutable snapshots and produce immutable
   `StrategyProposal` artifacts.
4. **Decision authority:** `PolicyEngine` decides → `DecisionProposal` →
   MTC proposal intake. There is no legal shorter signal-to-order path.
5. **Risk and capital authority:** `RiskEngine` issues the risk decision and
   the single capital authority issues the capital receipt.
6. **Mode and final admission:** ModeAuthority validates the mode; MTC performs
   final admission; StockOS seals the manifest; StartupGate must pass.
7. **Execution authority:** StockOS creates one exact signed
   `AuthorizedExecutionEnvelope` → StockOSAuthorityIngress → Nautilus
   veto-only structural checks → Nautilus OMS and ExecutionEngine.
8. **Transport or simulated order:** for a separately authorized live path,
   the StockOS OpenAlgo adapter sends exact bytes to OpenAlgo and the selected
   broker. During the initial real-PAPER transition, the existing StockOS
   `PaperBroker` remains the one matching authority and OpenAlgo write
   endpoints remain physically blocked. Nautilus simulation is observer-only
   until explicit equivalence and cutover.
9. **Return flow:** broker or simulated ACK/reject/partial/fill/modify/cancel/
   unknown → normalized event → Nautilus OMS and portfolio mirror → StockOS
   reconciliation.
10. **Persistence:** reconciliation completion → durable StockOS forensic
    ledger → immutable hash-correlated execution and recovery evidence.
11. **Learning:** only normalized, reconciled, forensic-committed evidence
    becomes immutable StockOS learning input.
12. **Reporting and audit:** stage latency, queue/resource metrics, receipts,
    event provenance, PnL/cost accounting, reconciliation, forensic hashes,
    and session/rollback custody form the evidence record.

Protective exits are not a shortcut. They require an immutable signed
preauthorized reduce-only policy bound before entry to the original command,
receipts, position lifecycle, maximum quantity, triggers, validity, and
unknown-state behavior. Discretionary exits require a fresh full authority
chain.

Source: blueprint §§12–18, 21–23, 28–31.

## 5. Current Readiness State

```text
TOTAL_CLASSIFIED_GAP_ROWS=38
P0_SECURITY_OR_AUTHORITY_BLOCKER_COUNT=11
P1_PAPER_BLOCKER_COUNT=12
P2_LIVE_BLOCKER_COUNT=9
P3_SCALE_OR_PERFORMANCE_COUNT=4
P4_FUTURE_OPTIMIZATION_COUNT=2
GAP_032_CLASSIFICATION=P1_PAPER_BLOCKER
GAP_034_CLASSIFICATION=P1_PAPER_BLOCKER
```

| Readiness dimension | Exact current state |
|---|---|
| Architecture specified | YES — proposed R2-003 documentation/architecture remediation |
| Blueprint independently reviewed | NO — `R2_003_SCOPE_REMEDIATION_REVIEW_VERDICT=NOT_YET_ISSUED` |
| Blueprint ratified | NO |
| Implementation complete | NO |
| Implementation authorized | NO |
| Application tests for this blueprint executed | NO |
| Integration/packaging qualified | NO |
| SHADOW authorized | NO |
| PAPER authorized | NO |
| LIVE authorized | NO |
| Production ready | NO |
| AWS readiness | UNKNOWN |
| OpenAlgo/Nautilus dependency and license custody | UNVERIFIED / NOT AUTHORIZED |

The blueprint is complete as a proposal pending a genuinely fresh independent
review. A valid review PASS creates eligibility for a separate Owner
ratification decision only. It does not authorize implementation, SHADOW,
PAPER, LIVE, deployment, credentials, brokers, services, merge, or push.

Source: blueprint header and §§26, 28, 33–36.

## 6. Gap Register Summary

This table transcribes and organizes the 38 rows from the sealed
`STOCKOS_THREE_LAYER_PRODUCTION_READINESS_GAP_REPORT_R2_001.md` incorporated
by blueprint §33. “Required evidence” is the row's focused-test requirement;
the exact gap report remains supporting evidence, while the R2-003 blueprint
remains architecture authority.

| Gap | Title | Classification | Affected layer/component | Reason/current state | Dependency | Required evidence | Must close | Blocks PAPER | Blocks LIVE |
|---|---|---|---|---|---|---|---|---|---|
| GAP-001 | Canonical approval path | P0_SECURITY_OR_AUTHORITY_BLOCKER | StockOS authority; approved adapter/launcher | ExecutionService can synthesize approved entry | A/C | No-shorter-path and noncanonical-approval rejection | Before PAPER | YES | YES |
| GAP-002 | Executable sealed manifest | P0_SECURITY_OR_AUTHORITY_BLOCKER | StockOS manifest authority | Manifest is documented only | A | Missing/tampered/expired/hash-mismatch tests | Before PAPER | YES | YES |
| GAP-003 | Durable mode and startup gate | P0_SECURITY_OR_AUTHORITY_BLOCKER | ModeAuthority, boot, connectivity | No durable mode receipt; connectivity precedes target gate | A | Mode mismatch, startup order, leader fencing | Before PAPER | YES | YES |
| GAP-004 | Unknown-state and quantity immutability | P0_SECURITY_OR_AUTHORITY_BLOCKER | Order router; StockOS/Nautilus/OpenAlgo write path | Broad retry and partial-remainder resubmission | A/C | Timeout, partial-fill, and no-mutation tests | Before PAPER | YES | YES |
| GAP-005 | Single transport authority | P0_SECURITY_OR_AUTHORITY_BLOCKER | AngelOne, SmartLimit, routers/adapters | Multiple live placement paths | A–C | Static reachability and one-placement-path proof | Before PAPER | YES | YES |
| GAP-006 | Single capital authority | P0_SECURITY_OR_AUTHORITY_BLOCKER | Allocator/manager/governor | Capital authority is fragmented | A | One-owner and quantity-chain-hash proof | Before PAPER | YES | YES |
| GAP-007 | Forensic system of record | P0_SECURITY_OR_AUTHORITY_BLOCKER | Journals/stores/reconciliation | No single durable forensic authority | A/C | Write-failure, hash-chain, storage-identity tests | Before PAPER | YES | YES |
| GAP-008 | Durable kill/revocation evidence | P0_SECURITY_OR_AUTHORITY_BLOCKER | Safety rails/session authority | Switch is process-local only | A/C | Restart persistence and exit-allowed proof | Before PAPER | YES | YES |
| GAP-009 | One normalized market-data ingress | P1_PAPER_BLOCKER | Feed/provider paths; Layer 3→1 | Multiple REST/WS authorities | B | Mapping, reconnect, gap, stale, backpressure | Before real PAPER | YES | YES |
| GAP-010 | Canonical instrument mapping | P1_PAPER_BLOCKER | Instrument master/registry/adapter | Multiple instrument/symbol authorities | A/B | Lot, tick, freeze, token, symbol corpus | Before real PAPER | YES | YES |
| GAP-011 | One matching engine per session | P1_PAPER_BLOCKER | PAPER engines and Layer 2 runtime | Multiple PAPER engines exist | C | One-engine reachability and duplicate-fill prevention | Before real PAPER | YES | YES |
| GAP-012 | Accounting equivalence | P1_PAPER_BLOCKER | Costs, ledger, PnL | Accounting is not cross-engine proven | C | Exact rounded fill/charge/tax/margin/PnL corpus | Before real PAPER | YES | YES |
| GAP-013 | Exit-policy recovery | P1_PAPER_BLOCKER | Restart journal and lifecycle | Missing journal can regenerate SL/TP | C | Crash with open/partial/unknown order | Before real PAPER | YES | YES |
| GAP-014 | Manifest-bound exit authority | P1_PAPER_BLOCKER | Exit trigger/admission | Exit lacks target policy/risk/manifest chain | A/C | No-shorter-exit, stale snapshot, reduce-only tests | Before real PAPER | YES | YES |
| GAP-015 | Repeatable reconciliation receipt | P1_PAPER_BLOCKER | Reconciliation paths | Multiple incomplete reconciliation surfaces | A/C | Order/trade/position mismatch and replay | Before real PAPER | YES | YES |
| GAP-016 | Canonical state mapping | P1_PAPER_BLOCKER | Order/position models | Multiple order/position models | C | Transition corpus and mirror-divergence tests | Before real PAPER | YES | YES |
| GAP-017 | Qualified OpenAlgo capability | P2_LIVE_BLOCKER | Layer 3 broker endpoints | Local support is unverified | B/D | Broker read/write contract corpus | Before LIVE | NO | YES |
| GAP-018 | Credential/token lifecycle | P2_LIVE_BLOCKER | OpenAlgo secrets boundary | Rotation, expiry, isolation are unverified | B/D | Expiry, rotation, redaction tests | Before LIVE | NO | YES |
| GAP-019 | Broker rate/reconnect policy | P2_LIVE_BLOCKER | OpenAlgo/broker transport | Rate-limit/reconnect behavior is unverified | B/D | 429, backoff, reconnect, sequence-gap tests | Before LIVE | NO | YES |
| GAP-020 | Process isolation | P2_LIVE_BLOCKER | Nine-service target topology | Target isolation is not implemented | A/C | Graph, identity, fault, queue-isolation tests | Before LIVE | NO | YES |
| GAP-021 | AWS runtime evidence | P2_LIVE_BLOCKER | AWS/IAM/network/systemd/IaC | Runtime evidence is UNKNOWN | D | Offline IaC then separately authorized AWS qualification | Before LIVE | NO | YES |
| GAP-022 | Backup and restore | P2_LIVE_BLOCKER | Forensic/config persistence | Backup/restore state is UNKNOWN | D | Hashed restore drill | Before LIVE | NO | YES |
| GAP-023 | Disaster recovery | P2_LIVE_BLOCKER | Process/host/broker recovery | Failover and owner-run recovery are unqualified | D | Process/host-loss recovery and reconciliation | Before LIVE | NO | YES |
| GAP-024 | Operator runbooks | P2_LIVE_BLOCKER | Target topology operations | Arm/revoke/reconcile/rollback runbooks incomplete | A–D | Tabletop and deterministic offline steps | Before LIVE | NO | YES |
| GAP-025 | Latency measurement | P3_SCALE_OR_PERFORMANCE | End-to-end stages | No target latency distribution | B–D | Deterministic load/replay benchmark | Before target-setting/scale | NO | NO until target set |
| GAP-026 | Queue/backpressure/resource proof | P3_SCALE_OR_PERFORMANCE | Feed/controller/runtime | Bounds are unproven | B/C | Burst, backpressure, memory-growth tests | Before qualified scale | NO | YES at scale |
| GAP-027 | Cross-process correlation | P3_SCALE_OR_PERFORMANCE | Logs/flight recorder | Correlation is incomplete | A–C | Correlation completeness and replay | Before PAPER | YES | YES |
| GAP-028 | Dependency license/legal custody | P1_PAPER_BLOCKER | OpenAlgo/Nautilus dependencies | Exact legal status and notices not verified | Dependency custody before B | Exact license/hash/notice/legal-decision check | Before Work Unit B/real PAPER | YES before B | YES |
| GAP-029 | Exact dependency pins and SBOM | P1_PAPER_BLOCKER | OpenAlgo/Nautilus dependencies | Tags, commits, locks, hashes, SBOM absent | Dependency custody before B | Lock/SBOM reproducibility | Before Work Unit B/real PAPER | YES before B | YES |
| GAP-030 | Native Nautilus broker adapter | P4_FUTURE_OPTIMIZATION | Layer 2/3 hot path | No evidence OpenAlgo is the bottleneck | Stage 8/future | Benchmark equivalence | Only if measurement justifies | NO | NO |
| GAP-031 | Multi-broker rollout | P4_FUTURE_OPTIMIZATION | Broker capability scope | Only AngelOne has a local LIVE implementation | Future separate qualification | Per-broker capability suites | Before each added broker | NO | YES for added broker |
| GAP-032 | Demand-driven services | P1_PAPER_BLOCKER | Supervisor and heavy services | Consumers do not own reference-counted demand start | A/C | Dependency-start, no-consumer-stop, research-batch-stop tests | Before real PAPER | YES | YES |
| GAP-033 | Atomic SafeStopGate | P0_SECURITY_OR_AUTHORITY_BLOCKER | Service lifecycle/counters | Stop does not prove zero dependencies | A/C/D | Every counter, race, stale publisher, expiry, PID/residue tests | Before PAPER | YES | YES |
| GAP-034 | Versioned service dependency graph | P1_PAPER_BLOCKER | Exact nine-node topology | No graph/consumer-lease contract | A–C | Nine nodes, one counter owner, fenced transitive leases | Before real PAPER | YES | YES |
| GAP-035 | Per-service resource limits | P3_SCALE_OR_PERFORMANCE | CPU/RAM/queue/retry/log/process custody | Budgets incomplete or UNKNOWN | A–D | Budget, backpressure, rotation, orphan tests | Before qualified scale | NO | YES at scale |
| GAP-036 | Safe crash/restart | P0_SECURITY_OR_AUTHORITY_BLOCKER | Authority/runtime/service restart | Restart can meet stale authority or ambiguous state | A/C/D | Expired manifest, unknown order, duplicate, identity tests | Before PAPER | YES | YES |
| GAP-037 | Orphan-process prevention | P2_LIVE_BLOCKER | Target service process custody | Child/background custody is unproven | A–D | Crash, timeout, reap, residue tests | Before PAPER/LIVE | YES | YES |
| GAP-038 | Duplicate runtime prevention | P0_SECURITY_OR_AUTHORITY_BLOCKER | Runtime, WS, router, matcher reachability | Duplicate authorities remain reachable | A–C | Duplicate runtime/WS/order/matcher reachability | Before PAPER | YES | YES |

Counts: P0=11, P1=12, P2=9, P3=4, P4=2, total=38.

Source: blueprint §33 and the sealed 38-row gap report identified there.

## 7. P1 PAPER Blockers

The 12 P1 blockers below must close before evidence can support real PAPER.
Real PAPER uses live qualified market data and the real StockOS
strategy/decision/risk/capital/mode/admission path; only the final broker order
is simulated. Fake data or fake signals are not acceptable real-PAPER
evidence.

1. **GAP-009 — one normalized market-data ingress.** Implement one fresh,
   sequenced, provenance-bound ingress. Test mapping, reconnect, gaps,
   staleness, and backpressure. Independent evidence must prove one qualified
   read authority and continuity recovery. Closure gate: Work Unit B plus the
   integration gate. Shortcut prohibited: multiple REST/WS authorities or
   fake-market feeds.
2. **GAP-010 — canonical instrument mapping.** Implement one canonical
   instrument ID and exact broker mapping. Test lot, tick, freeze, token, and
   symbol behavior. Independent evidence must bind mapping identity and
   qualification. Closure gate: A/B. Shortcut prohibited: strategy- or
   broker-specific symbol selection outside authority.
3. **GAP-011 — one matching engine per session.** Make all duplicate PAPER
   matchers unreachable and bind a session to exactly one engine. Test static
   reachability and duplicate-fill prevention. Independent evidence must prove
   one active engine. Closure gate: C equivalence/cutover. Shortcut prohibited:
   comparing multiple simultaneously authoritative engines.
4. **GAP-012 — accounting equivalence.** Implement and verify exact fill,
   brokerage, tax, margin, PnL, slippage, and rounding equivalence. Use a
   deterministic corpus and independent result comparison. Closure gate: C.
   Shortcut prohibited: headline PnL comparison without event-level custody.
5. **GAP-013 — immutable exit-policy recovery.** Persist the original
   entry-bound lifecycle policy so restart cannot regenerate discretionary
   SL/TP. Test open, partial, unknown, and crash states. Independent evidence
   must prove byte/receipt continuity. Closure gate: C. Shortcut prohibited:
   rebuilding exits from defaults after restart.
6. **GAP-014 — manifest-bound reduce-only exit envelope.** Implement the
   exact protective/discretionary exit authority rules. Test stale snapshots,
   no-shorter-exit paths, target resolution, and reduce-only quantities.
   Independent evidence must bind the exit to original receipts. Closure gate:
   A/C. Shortcut prohibited: ad hoc emergency discretion or exposure reversal.
7. **GAP-015 — repeatable reconciliation completion receipt.** Consolidate
   order, trade, position, and ledger reconciliation. Test mismatch and replay.
   Independent evidence must show deterministic completion and fail-closed
   admission. Closure gate: A/C. Shortcut prohibited: treating a broker ACK or
   one store as reconciliation.
8. **GAP-016 — deterministic canonical state mapping.** Map all order and
   position transitions into one canonical model. Test a full transition
   corpus and deliberate mirror divergence. Independent evidence must show
   consistent StockOS truth and Nautilus mirror behavior. Closure gate: C.
   Shortcut prohibited: parallel state authorities.
9. **GAP-028 — dependency license/legal custody.** Before Work Unit B,
   capture exact license texts, hashes, notices, pins, and the required legal
   decision. Independently verify the custody packet. Closure gate: dependency
   custody. Shortcut prohibited: relying on a package name, memory, or
   unpinned online claim.
10. **GAP-029 — exact pins, locks, artifact hashes, and SBOM.** Build a
    reproducible dependency-custody packet for OpenAlgo and Nautilus.
    Independently reproduce locks and artifact identities. Closure gate:
    before B. Shortcut prohibited: floating versions or adding dependencies
    before authorization.
11. **GAP-032 — demand-driven services.** Implement the lightweight
    supervisor, declared consumer leases, default-stopped heavy services, and
    research lifecycle. Test dependency start, no-consumer stop, protective
    leases, and batch completion. Independent evidence must show correct
    counters and no unnecessary service. Closure gate: A/C. Shortcut
    prohibited: always-on heavy services or schedule-as-authority.
12. **GAP-034 — versioned nine-node dependency graph.** Implement the exact
    supervisor/authority/research/data/Nautilus/OpenAlgo/PAPER/LIVE/Delta
    graph, one counter owner, and fenced transitive lease/release behavior.
    Independently verify graph identity and lifecycle traces. Closure gate:
    A–C. Shortcut prohibited: implicit dependencies or two owners for one
    counter.

Source: blueprint §§22–23, 26–28, 33 and the sealed gap report rows GAP-009
through GAP-016, GAP-028, GAP-029, GAP-032, and GAP-034.

## 8. Work Breakdown to Completion

Every package below is an inert planning decomposition. No package is
authorized by this publication. Before implementation, the Owner must allocate
one exact base commit, exact owned paths, one active coding agent, acceptance
evidence, and a stop point. Codex is the bounded implementer/local integration
agent; a genuinely independent Claude or Grok reviewer receives a separate
read-only packet and must not share implementation authority.

| Work package | Objective and blueprint source | Owned components | Prohibited components/scope | Dependencies | Acceptance, focused/adversarial/integration requirements | Completion artifact and independent review | Next eligible package |
|---|---|---|---|---|---|---|---|
| WP-0 Blueprint gate | Fresh R2-003 review and Owner ratification; header, §§32–36 | Sealed review evidence only | Source edits, remediation, implementation, services, trading | Valid handoff and fresh claim | Identity, scope, 38-gap, ledger, manifest/receipt and semantic-invariance review | Sealed independent report; separate Owner decision | WP-A only after explicit authorization |
| WP-A StockOS authority and lifecycle contracts | Work Unit A; §§13–18, 20–23, 27–28 | Policy/MTC/Risk/capital/mode/manifest/envelope validators; exact target resolver; event/provenance validator; nine-service graph; SafeStopGate; protective-exit policy; one-matcher and rollback lifecycle tests | Broker/dependency ingestion, LIVE writes, AWS, unrelated strategies, OpenAlgo/Nautilus internals | Ratified blueprint and exact Owner packet | No-shorter-path, semantic/canonical vectors, stale/invalid authority, counter races, split brain, unknown state, PID/residue, matcher reachability; focused + adversarial + full-suite/integration impact | Sealed WP-A receipt and test evidence; independent implementation review | Dependency custody / WP-B eligibility |
| WP-DEP Dependency custody | §26 and GAP-028/029 | Exact tags/commits, artifacts, locks, SBOM, notices, license texts and legal decision evidence | Dependency use, source copying, broker writes, architecture changes | Reviewed WP-A scope; separate network/legal authorization | Reproducible downloads/hashes/locks and complete notice/legal evidence | Sealed custody packet; independent custody review | WP-B eligibility |
| WP-B One-broker read-only data | Work Unit B; §§12, 19, 22, 27 | One broker capability, canonical mapping, qualified read-only market-data path, physically blocked write endpoints, SHADOW payload generation only when separately authorized | Delta migration, order writes, multiple brokers, credentials outside OpenAlgo boundary | WP-A + WP-DEP PASS and explicit Owner authorization | Mapping/reconnect/gap/stale/backpressure, rate-limit and redaction tests; integration with immutable MarketSnapshot; no write reachability | Sealed WP-B evidence; independent implementation/security review | WP-C eligibility |
| WP-C Observer, PAPER equivalence and cutover gate | Work Unit C; §§14, 17, 22, 27–31 | StockOSAuthorityIngress, Nautilus observer, state comparison, portfolio mirror, existing PaperBroker authority, one-matcher proof, reconciliation, accounting equivalence and rollback | Early Nautilus authority, dual matchers, live transport, implicit cutover | WP-A/B PASS and exact authorized session type | Transition corpus, fills/partials/slippage/cost/tax/margin/PnL, exits, recovery, unknown state, revocation, replay, divergence, full suite and integration qualification | Sealed WP-C equivalence/cutover packet; independent review | WP-D or operational qualification eligibility |
| WP-D Bounded live-connectivity implementation | Work Unit D; §§18–21, 23–31 | One broker/account/instrument family, owner-bounded capital, exact write transport, credential lifecycle, rate limits, reconciliation, recovery, runbooks, AWS artifacts only under separate authority | Multi-broker, failover, blind retry, unbounded capital, Delta migration, automatic LIVE | WP-A–C PASS, dependency custody, reviewed broker/AWS packet and explicit Owner authorization | Exact request/response bytes, timeout/unknown, idempotency conflict, modify/cancel target, credential rotation, 429/reconnect, recovery, firewall/IAM/systemd/IaC, backup/restore, rollback; full qualification | Sealed WP-D and operational-readiness evidence; independent review | SHADOW readiness assessment |
| WP-Q Integration and packaging qualification | §§28–31 and gap closure | Exact combined candidate, packaging, contracts, migrations, test/evidence harnesses | Feature additions, architecture drift, operational launch | Reviewed A–D candidate as applicable | Focused, adversarial, full-suite, clean package, origin, process-residue, performance and recovery evidence | Immutable qualification packet; fresh independent review | Operational readiness |
| WP-O Operational readiness | §§23, 25–31 | Runbooks, observability, resource budgets, backup/restore, disaster recovery, rollback, IAM/network/service definitions as separately authorized | Starting services, AWS writes, broker activity without exact packet | Qualified integration candidate | Tabletop/drills, reconciliation, kill/revoke, restore, process custody, measured limits and audit completeness | Sealed operational-readiness report; independent review | SHADOW decision |
| WP-S SHADOW qualification | Migration §30 stage `OPENALGO_SHADOW` | Read-only qualified data and physically blocked payload observation for exact candidate | Broker writes, simulated authority shortcuts, PAPER/LIVE | Owner-authorized SHADOW packet after operational readiness | Live-data freshness/sequence, exact would-send bytes, no-write proof, stability/performance and reconciliation evidence | Sealed SHADOW evidence; independent review | Real-PAPER readiness review |
| WP-P Real PAPER qualification and observation | §§22, 30–31 | Real live data + real StockOS strategy/risk path + one simulated final broker order; bounded observation and reconciliation | Fake data/signals as evidence, multiple matchers, any real broker order | Owner-authorized real-PAPER session after fresh readiness PASS | Deterministic session manifest, one engine, accounting/recovery/exit/reconciliation, bounded live-data observations, rollback and audit evidence | Sealed PAPER observation/evidence packet; independent review | LIVE-readiness assessment |
| WP-L LIVE readiness and controlled rollout | §§23, 30–36 | One separately approved broker/account/instrument family, bounded capital/session, exact runbook and rollback | Implicit authorization, multi-broker, failover, blind retry, unbounded rollout | PAPER evidence PASS, all applicable blockers closed, fresh LIVE-readiness review, Owner-only LIVE authorization | StartupGate, broker/AWS/credential/reconciliation/kill/protective-exit/recovery/observability evidence; bounded canary and rollback | Sealed LIVE-readiness and rollout evidence; independent post-stage review | Expand only by new Owner packet |

No package has a currently authorized successor. “Next eligible package” means
only that the Owner/Architect may consider a new exact task after the prior
gate; it is not automatic continuation.

## 9. Controlled Agent Division

- **ChatGPT:** Owner-side coordinator and Chief Architect. It maintains
  architecture coherence, prepares bounded task packets, and advises the
  Owner; it does not substitute for Owner launch authority.
- **Codex:** bounded implementer and local integration agent. It may act only
  within one exact task, candidate, base identity, owned-path set, and network/
  operational boundary. Codex must not approve or independently review its
  own implementation.
- **Claude or Grok:** genuinely separate independent reviewer when required.
  The reviewer reads the exact frozen candidate and evidence, records PASS/
  FAIL/invalidity, and must not implement, edit, remediate, commit, push,
  deploy, or operate during review.
- **Owner Pramod Kumar:** final human launch authority for review, ratification,
  implementation, SHADOW, PAPER, LIVE, and any operational action.

Reviewer findings return to the Owner/Architect. Any remediation needs a new
bounded task, a new candidate identity, new tests, and a new independent
review. Reviewer identity and context must remain independent. The shared
board is coordination evidence only; it is not technical authority and does
not replace sealed artifacts, candidate identities, task packets, or Owner
authorization.

Source: blueprint §32 and §§35–36; correction-ledger role and scope locks.

## 10. Path from Blueprint to Implementation

Every stage is a gate. No stage is currently authorized merely because it is
listed.

| Stage | Entry gate | Required evidence | Responsible role | PASS condition | STOP condition | Next stage |
|---:|---|---|---|---|---|---|
| 1. Blueprint handoff verification | Exact sealed R2-003 packet and free review paths | Hash/size/mode/inventory, provenance, D-001, ledger and reserved-path evidence | Codex read-only custodian | Exact packet and scope reconcile | Any collision, drift, mismatch, write, or uncertainty | Fresh review |
| 2. Fresh independent blueprint review | Valid handoff; Owner launch; fresh claim/session | Independent full packet review and sealed report | Fresh Claude or Grok | Valid review PASS | FAIL, invalid freshness/custody, or unresolved finding | Owner ratification decision |
| 3. Owner/Architect ratification | Valid fresh PASS | Exact reviewed identity, findings disposition, Owner record | Owner with ChatGPT architect support | Explicit blueprint ratification | No explicit ratification or unresolved finding | Exact WP-A authorization |
| 4. Bounded implementation packages | Ratification + separate exact packet/base/paths | Code, design, focused tests, completion receipt | Codex | Package acceptance criteria pass | Scope drift, failing gate, mixed identity, or missing authority | Package review |
| 5. Focused and adversarial testing | Frozen package candidate | Contract, failure, race, recovery, negative-path evidence | Codex test executor | All scoped tests pass with exact candidate custody | Any failure, hang, residue, exclusion ambiguity | Independent implementation review |
| 6. Independent implementation reviews | Frozen candidate and test packet; fresh reviewer | Code/contract/test/evidence review | Fresh Claude or Grok | Valid PASS on exact candidate | Finding, invalid freshness, or candidate drift | Next bounded package/integration |
| 7. Integration and packaging qualification | All required reviewed packages | Full-suite/integration, package origin, clean identity, process residue, migration and rollback | Codex integrator; independent reviewer | Combined candidate and package evidence pass | Test, origin, identity, packaging, or residue failure | Operational readiness |
| 8. Operational readiness evidence | Qualified package | Runbooks, IAM/network/service design, observability, backups, DR, resource limits, recovery and audit | Codex/local ops evidence under exact authority; Owner | All required evidence independently passes | UNKNOWN/missing operational evidence or unauthorized external action | SHADOW decision |
| 9. SHADOW qualification | Explicit Owner SHADOW authorization | Live read-only data, would-send payload, write-block proof, stability/reconciliation | Codex operator within packet; independent reviewer | Exact SHADOW gates pass with no write | Any write reachability, data/custody failure, or instability | Real-PAPER readiness review |
| 10. Real-PAPER readiness review | SHADOW PASS and all PAPER blockers closed | One-engine, real-data, strategy/risk, accounting, recovery, exit and reconciliation readiness | Fresh reviewer; Owner decision | Readiness PASS on exact candidate | Any open P0/P1 or unproven real-data path | Owner real-PAPER authorization |
| 11. Owner-authorized real PAPER | Explicit bounded Owner packet | Session manifest, limits, broker-write block, rollback/runbook | Owner launches; Codex operates within packet | StartupGate and preflight pass | Missing authority, stale manifest, unsafe state | Bounded observation |
| 12. Bounded live-data PAPER observation | Valid real-PAPER session | Live data + real decision/risk path + simulated final order; raw metrics and ledger | Codex operator | Bounded session completes and reconciles | Data gap, unknown state, mismatch, unsafe exit/stop | PAPER evidence review |
| 13. PAPER evidence review | Sealed observation packet | Accounting, lifecycle, recovery, performance, reconciliation, audit and rollback evidence | Fresh Claude or Grok | Valid PASS | Finding, invalid custody, or insufficient sample/evidence | LIVE-readiness assessment |
| 14. LIVE-readiness assessment | PAPER PASS; LIVE blockers closed | Broker, credentials, AWS, IAM, networking, runbooks, DR, kill/exit, bounded capital | Fresh reviewer; Owner/Architect | Exact readiness PASS | Any open blocker, UNKNOWN critical state, or unauthorized drift | Owner-only LIVE decision |
| 15. Owner-only LIVE authorization | Valid LIVE-readiness PASS | Exact broker/account/instrument/capital/session/candidate/runbook authorization | Owner only | Explicit bounded LIVE authorization | No explicit authorization or changed identity | Controlled LIVE rollout |
| 16. Controlled LIVE rollout | Valid LIVE authority and StartupGate | Canary/bounded session, live reconciliation, observability, protective exits, rollback readiness | Owner launch; Codex bounded operation | Stage completes within limits and reconciles | Unknown order, limit breach, drift, kill/reconcile/exit failure | Post-launch governance |
| 17. Rollback, reconciliation, audit and governance | Any stage completion/failure or Owner stop | Session revocation, exact state equality or Owner-resolved reconciliation, PID/socket custody, forensic commit | Codex within runbook; Owner adjudicates | State is reconciled, evidence sealed, next authority explicit | Unknown broker state, unsafe flatten assumption, residue, incomplete evidence | New Owner decision only |

Current sealed state: blueprint proposal complete, fresh independent R2-003
review not yet issued, ratification NO, and every implementation or operational
authorization NO.

Source: blueprint §§27–36 and the Owner-prescribed publication roadmap.

## 11. SHADOW, PAPER, and LIVE Boundaries

| Mode/evidence class | Meaning | Authorization boundary |
|---|---|---|
| Offline tests | Deterministic unit, contract, property, adversarial, replay, race, recovery, packaging and integration tests without broker/AWS operation | A test PASS is evidence only; it grants no SHADOW/PAPER/LIVE authority |
| Simulation | A controlled simulated market or matching environment used for exact mechanics/equivalence | Must use one matching engine and an explicit session type; not real-PAPER evidence when data/signals are fake |
| SHADOW | Qualified live read-only market data drives the candidate's real would-send path while all order-write endpoints are physically blocked | Requires separate Owner SHADOW authorization after readiness gates; no broker write |
| Real PAPER | Qualified live market data and the real StockOS feature/strategy/Policy/MTC/Risk/Capital/Mode/final-admission path run; only the final broker order is simulated by the one qualified PAPER engine | Requires all P0/P1 PAPER blockers closed, fresh readiness review, and explicit Owner PAPER authorization |
| LIVE | Exact authorized orders may reach one qualified broker/account/instrument family under bounded capital/session/runbook controls | Requires PAPER evidence, LIVE-blocker closure, fresh LIVE-readiness review, and Owner-only explicit LIVE authorization |

During the initial PAPER transition:

```text
MARKET_DATA=OPENALGO_OR_CURRENT_QUALIFIED_LIVE_FEED
DECISION_ENGINE=STOCKOS
RISK_AND_CAPITAL=STOCKOS
PAPER_EXECUTION=EXISTING_STOCKOS_PAPERBROKER
NAUTILUS_SIMULATION=OBSERVER_ONLY
OPENALGO_ORDER_ENDPOINTS=PHYSICALLY_BLOCKED
```

Only after equivalence and explicit cutover may Nautilus simulation implement
StockOS PAPER execution for the qualified session type and the old PaperBroker
be retired for that type. A schedule may wake a readiness check; it cannot
authorize PAPER/LIVE or open a session. Rollback is session revocation plus
reconciliation, never an implicit mode change or automatic flatten.

Source: blueprint §§22–23, 30–31, and §§35–36.

## 12. Owner Dashboard

| Item | Current state |
|---|---|
| Current phase | `DOCUMENTATION_AND_ARCHITECTURE_REMEDIATION_ONLY` |
| Authoritative candidate | `STOCKOS_THREE_LAYER_FINAL_BLUEPRINT_R2_003.md` / 39,665 bytes / `e407d7a5...31376` |
| Current blocker/gap count | 38 total: 11 P0, 12 P1 PAPER, 9 P2 LIVE, 4 P3, 2 P4 |
| Current task represented here | Publish exact coordination mirrors and non-normative navigation only |
| Current reviewer state | R2-003 scope-remediation review verdict `NOT_YET_ISSUED` |
| Last blueprint review state in R2-003 | Upstream R2-001 review `FAIL`; D-001 corrected; R2-003 still pending fresh review |
| Next required decision | Owner launch of one genuinely fresh independent R2-003 review, then separate ratification decision if PASS |
| Implementation state | Not authorized; not performed by the blueprint |
| SHADOW state | NOT AUTHORIZED |
| PAPER state | NOT AUTHORIZED |
| LIVE state | NOT AUTHORIZED |
| Production readiness | NO |
| AWS readiness | UNKNOWN |

Source: blueprint header and §§33–36; correction ledger Locked substantive
results.

## 13. How Agents Must Use This Repository

When network access is authorized, Codex and coordination agents must:

1. Read [issue #1](https://github.com/mvmjandaha-art/stockos-agent-status/issues/1)
   and every latest comment.
2. Read this START_HERE navigation file.
3. Open the exact authoritative blueprint mirror and verify 39,665 bytes and
   SHA-256
   `e407d7a5a3753b1455372635cfd982efbd5a590f7c868a1e961daafb38431376`.
4. Read and obey the exact current task packet.
5. Stay inside the assigned role, candidate, paths, repositories, network
   domains, actions, and stopping point.
6. Publish only sanitized completion status and permitted public artifacts.
7. Stop at an Owner/Architect decision, fresh independent-review gate,
   remediation gate, or authority boundary.

Strict offline Claude/Grok reviewers must follow their sealed launch packet
and must not access GitHub during review. Board status is coordination
evidence, never candidate or technical authority.

## 14. Security and Publication Boundary

This publication is classified:

```text
PUBLICATION_CLASS=PUBLIC_SAFE_EXACT_MIRROR
```

The public coordination copies were eligible for exact publication because a
targeted credential/token/key/account/private-endpoint scan and Gitleaks scan
found no secret value in the exact blueprint or correction ledger. Generic
architecture terms, hashes, task IDs, component names, loopback addresses, and
generic `/private/tmp` provenance paths are not credentials.

Public coordination copies:

- exact R2-003 blueprint mirror;
- exact D-001 scope-correction ledger mirror;
- this non-normative navigation/roadmap.

Private exact mirrors:

- [Private exact blueprint](https://github.com/mvmjandaha-art/stockos-coordination-private/blob/main/authoritative/r2-003/STOCKOS_THREE_LAYER_FINAL_BLUEPRINT_R2_003.md)
- [Private exact correction ledger](https://github.com/mvmjandaha-art/stockos-coordination-private/blob/main/authoritative/r2-003/STOCKOS_THREE_LAYER_R2_D001_SCOPE_CORRECTION_LEDGER.md)

The sealed local R2-003 package remains unchanged and is the custody source
for the exact mirrors. This public repository must never contain passwords,
API keys, tokens, cookies, client secrets, private keys, environment-file
contents, account-identifying data, AWS credentials/account exposure, private
endpoints, authentication headers, or secret-bearing logs.

## 15. Final Definition of Done

StockOS is not done when coding finishes. Final completion requires all of the
following on one exact candidate and authority chain:

- architecture conformity to the reviewed and Owner-ratified R2 authority;
- closure of all applicable security/authority, PAPER, LIVE, operational, and
  scale blockers;
- one legal decision/risk/capital/mode/final-admission chain and no shorter
  entry or discretionary-exit path;
- exact envelope, transport, idempotency, provenance, reconciliation,
  protective-exit, service-graph, SafeStop, crash/restart, and process-custody
  implementation;
- focused, property/contract, adversarial, concurrency, recovery, performance,
  integration, packaging, and full-suite evidence;
- deterministic market-data and canonical-instrument correctness;
- one matching engine and exact accounting/lifecycle equivalence;
- broker-write safety, no blind retry, unknown-state reconciliation, durable
  kill/revocation, and bounded capital/exposure;
- durable persistence, backup/restore, disaster recovery, forensic hashes,
  immutable learning evidence, and repeatable reconciliation;
- observability for stage latency, clocks, drops, queue depth, memory, CPU,
  retry, process identity, child custody, and audit correlation;
- genuinely independent reviews of each required frozen candidate and
  evidence packet, with remediation separated into new tasks;
- qualified operational runbooks, IAM/network/service topology, rollback,
  reconciliation, and residue proof;
- explicit Owner-authorized SHADOW with no-write evidence;
- explicit Owner-authorized real PAPER using live qualified data and the real
  StockOS decision/risk path, followed by bounded observation and independent
  evidence review;
- fresh LIVE-readiness PASS, Owner-only bounded LIVE authorization, controlled
  rollout, protective/kill/rollback readiness, and post-launch governance;
- an immediate fail-closed stop whenever identity, authority, data, state,
  safety, evidence, or operational custody becomes unknown.

Until those gates are met:

```text
BLUEPRINT_RATIFIED=NO
IMPLEMENTATION_AUTHORIZED=NO
SHADOW_AUTHORIZED=NO
PAPER_AUTHORIZED=NO
LIVE_AUTHORIZED=NO
PRODUCTION_READY=NO
```

Source: authoritative blueprint §§13–36.
