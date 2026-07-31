# StockOS R2-003 Visual Blueprint

DOCUMENT_CLASS=NON_NORMATIVE_MERMAID_VISUAL_NAVIGATION
AUTHORITATIVE_BLUEPRINT=STOCKOS_THREE_LAYER_FINAL_BLUEPRINT_R2_003.md
AUTHORITATIVE_BLUEPRINT_SHA256=e407d7a5a3753b1455372635cfd982efbd5a590f7c868a1e961daafb38431376
AUTHORITATIVE_BLUEPRINT_SIZE=39665
CORRECTION_SCOPE=D-001_AND_PERMITTED_PACKAGE_PROVENANCE_ONLY
DO_NOT_USE_AS_REPLACEMENT_BLUEPRINT=YES

BLUEPRINT_RATIFIED=NO
IMPLEMENTATION_AUTHORIZED=NO
SHADOW_AUTHORIZED=NO
PAPER_AUTHORIZED=NO
LIVE_AUTHORIZED=NO

This visual is a non-normative navigation aid derived only from the exact
sealed R2-003 blueprint and its D-001 scope-correction chain. It adds no
architecture, requirement, readiness claim, or authorization. If any diagram
or explanation conflicts with the exact blueprint, the exact blueprint wins.

- [Exact authoritative blueprint](https://github.com/mvmjandaha-art/stockos-agent-status/blob/main/blueprints/r2-003/STOCKOS_THREE_LAYER_FINAL_BLUEPRINT_R2_003.md)
- [D-001 scope-correction ledger](https://github.com/mvmjandaha-art/stockos-agent-status/blob/main/blueprints/r2-003/STOCKOS_THREE_LAYER_R2_D001_SCOPE_CORRECTION_LEDGER.md)
- [Detailed navigation and gap register](https://github.com/mvmjandaha-art/stockos-agent-status/blob/main/blueprints/r2-003/START_HERE_STOCKOS_R2_003.md)

## 1. Owner, Architect, and Agent Authority

```mermaid
flowchart TB
    O["Owner — Pramod Kumar<br/>Final launch and authorization authority"]
    A["ChatGPT — Owner-side coordinator<br/>and Chief Architect"]
    C["Codex — bounded implementer,<br/>local integrator, evidence custodian"]
    R["Fresh Claude or Grok —<br/>independent reviewer only"]
    B["Issue #1 status board<br/>coordination evidence only"]
    BP["Sealed R2-003 blueprint + D-001 chain<br/>architecture authority"]

    O -->|"Owner direction"| A
    A -->|"Exact bounded task packet"| C
    O -->|"Owner-launched sealed review packet"| R
    C -->|"Sealed implementation/evidence; no self-approval"| O
    R -->|"PASS, findings, or invalid review; no remediation"| O
    BP -->|"Governs architecture and boundaries"| A
    BP -->|"Constrains task scope"| C
    BP -->|"Exact frozen review target"| R
    C -.->|"Sanitized append-only status"| B
    R -.->|"Sanitized outbox via authorized synchronization"| B
    B -.->|"Never replaces authority or evidence"| BP
```

Authority rules:

- Owner authorization is required for fresh review launch, blueprint
  ratification, implementation, SHADOW, PAPER, and LIVE.
- ChatGPT coordinates architecture on the Owner side but does not replace the
  Owner's final authority.
- Codex must not approve or independently review its own implementation.
- A fresh Claude/Grok reviewer must not implement, edit, remediate, commit,
  merge, push, deploy, or operate during review.
- Board comments coordinate work; they do not replace the blueprint, exact
  task packet, candidate identity, sealed evidence, or Owner decision.

Source: blueprint §§32, 35, and 36.

## 2. Exact Three-Layer Architecture

```mermaid
flowchart LR
    MD["Selected qualified broker<br/>read API / stream"]
    BR["Selected broker"]

    subgraph L3["Layer 3 — OpenAlgo connectivity"]
        OAData["Qualified market-data REST/WS<br/>normalized broker payload"]
        OAMap["Broker capability +<br/>canonical symbol mapping"]
        OATransport["Exact place / modify / cancel transport<br/>exact request and response byte custody"]
        OAEvents["Normalized broker events"]
    end

    subgraph L1["Layer 1 — StockOS authority"]
        Ingress["Market-data ingress<br/>freshness + sequence + provenance"]
        Snapshot["Immutable MarketSnapshot"]
        Research["Research + immutable<br/>strategy artifacts"]
        Policy["PolicyEngine"]
        MTC1["MTC proposal intake"]
        Risk["RiskDecision"]
        Capital["CapitalDecision"]
        Mode["ModeAuthority"]
        MTC2["MTC final admission"]
        Manifest["Sealed execution manifest<br/>+ StartupGate"]
        Envelope["AuthorizedExecutionEnvelope"]
        Reconcile["StockOS reconciliation"]
        Forensic["StockOS forensic ledger"]
        Learning["Immutable StockOS<br/>learning evidence"]
    end

    subgraph L2["Layer 2 — Nautilus execution implementation"]
        NIngress["StockOSAuthorityIngress<br/>exact envelope verification"]
        Veto["Veto-only structural checks"]
        OMS["Nautilus OMS + order state"]
        Exec["Nautilus ExecutionEngine"]
        Mirror["Portfolio state mirror"]
    end

    MD --> OAData --> Ingress --> Snapshot --> Research --> Policy
    Policy --> MTC1 --> Risk --> Capital --> Mode --> MTC2 --> Manifest --> Envelope
    Envelope --> NIngress --> Veto --> OMS --> Exec --> OAMap --> OATransport --> BR
    BR --> OAEvents --> OMS
    OMS --> Mirror --> Reconcile --> Forensic --> Learning
    Learning -.->|"Reconciled and immutable evidence only"| Research
```

### Authority boundaries

```mermaid
flowchart TB
    S["StockOS alone owns<br/>research, decision, risk, capital, mode,<br/>broker/account selection, admission,<br/>lifecycle, reconciliation, forensic truth"]
    N["Nautilus implements execution mechanics<br/>and mirrors state; structural veto only"]
    O["OpenAlgo carries qualified data<br/>and exact transport bytes only"]

    S -->|"Exact signed manifest-bound envelope"| N
    N -->|"Exact already-authorized request"| O
    O -->|"Normalized provenance-bound events"| N
    N -->|"Execution state and reconciliation snapshot"| S

    N -.->|"Cannot generate signal, size, allocate,<br/>change mode, open session, override risk,<br/>repair envelope, or enlarge exposure"| X1["PROHIBITED"]
    O -.->|"Cannot select broker/account/instrument/side,<br/>change quantity, allocate, fail over,<br/>create exit policy, or enlarge exposure"| X2["PROHIBITED"]
```

The three systems are separate processes with strict versioned contracts and
one active writer per authority state.

Source: blueprint §§1, 6, and 8–21.

## 3. Complete Market-to-Decision-to-Risk-to-Execution Flow

```mermaid
flowchart TD
    A1["Qualified market/broker data"]
    A2["OpenAlgo normalized read payload"]
    A3["StockOS canonical instrument mapping"]
    A4["Freshness + sequence + provenance validation"]
    A5["Immutable MarketSnapshot"]
    A6["Research Engine"]
    A7["Immutable StrategyProposal"]
    A8["PolicyEngine decision"]
    A9["MTC proposal intake"]
    A10["RiskEngine approval"]
    A11["CapitalAuthority receipt"]
    A12["ModeAuthority receipt"]
    A13["MTC final admission"]
    A14["Sealed execution manifest"]
    A15["StartupGate PASS"]
    A16["Signed AuthorizedExecutionEnvelope"]
    A17["StockOSAuthorityIngress"]
    A18["Nautilus veto-only checks"]
    A19["Nautilus OMS + ExecutionEngine"]
    A20["StockOS OpenAlgo adapter"]
    A21["OpenAlgo exact transport"]
    A22{"Separately authorized<br/>session type?"}
    A23["One simulated PAPER order<br/>through the qualified matching engine"]
    A24["One exact broker order<br/>to the selected broker"]
    A25["ACK / reject / partial / fill /<br/>modify / cancel / unknown"]
    A26["OpenAlgo normalized event"]
    A27["Nautilus OMS + portfolio mirror"]
    A28["StockOS reconciliation"]
    A29["StockOS forensic commit"]
    A30["Immutable learning + audit evidence"]
    F["FAIL CLOSED<br/>block admission; reconcile unknown state;<br/>never blind-resubmit"]

    A1 --> A2 --> A3 --> A4 --> A5 --> A6 --> A7 --> A8 --> A9 --> A10
    A10 --> A11 --> A12 --> A13 --> A14 --> A15 --> A16 --> A17 --> A18 --> A19 --> A20 --> A21 --> A22
    A22 -->|"Owner-authorized real PAPER"| A23
    A22 -->|"Owner-authorized bounded LIVE"| A24
    A23 --> A25
    A24 --> A25
    A25 --> A26 --> A27 --> A28 --> A29 --> A30
    A30 -.->|"Only after normalization,<br/>reconciliation, forensic commit,<br/>and immutable custody"| A6

    A4 -.->|"Gap, stale data, unsupported depth,<br/>clock or provenance failure"| F
    A15 -.->|"Invalid authority, manifest,<br/>mode, session, or dependency"| F
    A18 -.->|"Schema or semantic rejection"| F
    A21 -.->|"Timeout, reset, parse failure,<br/>missing ID, contradiction, crash after send"| F
    A25 -.->|"ORDER_STATE_UNKNOWN"| F
    F -.-> A28
```

There must be no shorter proposal-to-order path. One valid envelope maps to
one exact order. Neither Nautilus nor OpenAlgo may change approved quantity.
Unknown write state blocks conflicting orders and requires reconciliation.

Source: blueprint §§12–21.

## 4. Real PAPER Definition and Learning Loop

```mermaid
flowchart LR
    LiveData["Qualified live market data"]
    RealFeatures["Real StockOS feature<br/>and strategy processing"]
    RealAuthority["Real Policy → MTC intake → Risk → Capital →<br/>Mode → MTC final admission"]
    ExactRuntime["Exact manifest, StartupGate,<br/>envelope, runtime, lifecycle"]
    SimOrder["Only the final broker order is simulated<br/>by exactly one qualified PAPER engine"]
    Recon["Real reconciliation, accounting,<br/>recovery, exits, and forensic evidence"]
    Learn["Immutable reconciled learning evidence"]

    LiveData --> RealFeatures --> RealAuthority --> ExactRuntime --> SimOrder --> Recon --> Learn
    Learn -.-> RealFeatures

    Fake["Fake data or fake signals"]
    Fake -.->|"Not acceptable real-PAPER evidence"| Stop["STOP"]
```

Initial transition locked by the blueprint:

```text
MARKET_DATA=OPENALGO_OR_CURRENT_QUALIFIED_LIVE_FEED
DECISION_ENGINE=STOCKOS
RISK_AND_CAPITAL=STOCKOS
PAPER_EXECUTION=EXISTING_STOCKOS_PAPERBROKER
NAUTILUS_SIMULATION=OBSERVER_ONLY
OPENALGO_ORDER_ENDPOINTS=PHYSICALLY_BLOCKED
ONE_SESSION_ONE_MATCHING_ENGINE=YES
```

Nautilus simulation becomes the StockOS PAPER execution implementation only
after measured equivalence and explicit cutover for an exact session type.

Source: blueprint §§8, 14, and 22.

## 5. Blueprint-to-SHADOW-to-PAPER-to-LIVE Gated Path

```mermaid
flowchart LR
    P0["R2-003 handoff verification"]
    P1["Fresh independent<br/>blueprint review"]
    P2["Owner / Architect<br/>ratification decision"]
    P3["Exact Owner-authorized<br/>bounded implementation packages"]
    P4["Focused + adversarial +<br/>full/integration tests"]
    P5["Fresh independent<br/>implementation reviews"]
    P6["Integration + packaging +<br/>operational qualification"]
    P7["Owner-authorized SHADOW<br/>live read-only data; writes blocked"]
    P8["Fresh real-PAPER<br/>readiness review"]
    P9["Owner-authorized real PAPER"]
    P10["Bounded live-data PAPER<br/>observation + evidence"]
    P11["Fresh PAPER evidence review<br/>+ LIVE-readiness assessment"]
    P12["Owner-only bounded<br/>LIVE authorization"]
    P13["Controlled LIVE rollout"]
    P14["Rollback + reconciliation +<br/>audit + post-launch governance"]

    P0 -->|"PASS only"| P1
    P1 -->|"Valid fresh PASS only"| P2
    P2 -->|"Explicit ratification + separate task"| P3
    P3 --> P4 --> P5 --> P6
    P6 -->|"Explicit Owner SHADOW authorization"| P7
    P7 --> P8
    P8 -->|"Readiness PASS + Owner authorization"| P9
    P9 --> P10 --> P11
    P11 -->|"All applicable blockers closed<br/>+ explicit Owner LIVE authorization"| P12
    P12 --> P13 --> P14
```

Every gate stops on identity drift, missing evidence, open required blockers,
unknown critical state, invalid reviewer custody, scope ambiguity, or absent
Owner authority. A documentation PASS never authorizes implementation or an
operational phase.

The blueprint's nine-stage migration path remains:

```mermaid
flowchart LR
    M0["CURRENT_STOCKOS"]
    M1["OPENALGO_READ_ONLY"]
    M2["OPENALGO_SHADOW"]
    M3["STOCKOS_PAPER_WITH_OPENALGO_DATA"]
    M4["NAUTILUS_OBSERVER"]
    M5["NAUTILUS_PAPER_EQUIVALENCE"]
    M6["NAUTILUS_RUNTIME_CUTOVER"]
    M7["BOUNDED_LIVE"]
    M8["NATIVE_HOT_PATH_ADAPTERS_IF_JUSTIFIED"]
    M0 --> M1 --> M2 --> M3 --> M4 --> M5 --> M6 --> M7 --> M8
```

Source: blueprint §§27–36.

## 6. Codex and Independent Reviewer Separation

```mermaid
sequenceDiagram
    participant Owner as Owner / Architect
    participant Codex as Codex implementer
    participant Evidence as Sealed candidate + evidence
    participant Reviewer as Fresh Claude or Grok

    Owner->>Codex: Exact authorized task, base, paths, criteria
    Codex->>Codex: Implement only bounded scope
    Codex->>Evidence: Seal candidate identity, tests, completion artifact
    Codex-->>Owner: Stop at independent-review gate
    Owner->>Reviewer: Launch fresh exact read-only review packet
    Reviewer->>Evidence: Verify frozen identity and evidence
    alt PASS
        Reviewer-->>Owner: Sealed PASS; no remediation
    else bounded findings
        Reviewer-->>Owner: Exact findings; no remediation
        Owner-->>Codex: New task only if OWNER_APPROVED and READY_FOR_CODEX
    else invalid or blocked
        Reviewer-->>Owner: Preserve candidate and BLOCK
    end
```

Source: blueprint §32 and the D-001 ledger's locked model-role boundary.

## 7. Automatic Continuation Boundary

```mermaid
flowchart TD
    Q["Task reaches terminal result"]
    Pass{"CURRENT_VERDICT=PASS?"}
    Named{"Exact successor explicitly named<br/>and already authorized?"}
    Ready{"OWNER_APPROVED + READY_FOR_CODEX<br/>+ CODEX eligible + dependencies PASS?"}
    Clear{"No STOP / HOLD / BLOCKED / INVALID /<br/>SUPERSEDED / scope correction / collision?"}
    Gate{"Fresh review, Owner decision,<br/>merge/push, AWS/broker, service,<br/>deployment, SHADOW, PAPER, or LIVE gate?"}
    Continue["May claim only the exact successor"]
    Wait["WAITING_FOR_ELIGIBLE_TASK<br/>read-only board watch"]
    Stop["STOP and publish fail-closed status"]

    Q --> Pass
    Pass -->|"NO"| Stop
    Pass -->|"YES"| Named
    Named -->|"NO"| Wait
    Named -->|"YES"| Ready
    Ready -->|"NO"| Wait
    Ready -->|"YES"| Clear
    Clear -->|"NO"| Stop
    Clear -->|"YES"| Gate
    Gate -->|"YES"| Wait
    Gate -->|"NO"| Continue
```

A PASS can activate only its explicit successor. A failure can activate only
an already pre-approved bounded remediation task. Codex never invents
continuation authority.

## 8. Current Readiness and Authorization State

```mermaid
flowchart TB
    State["CURRENT_STATUS<br/>BLUEPRINT_COMPLETE_PENDING_INDEPENDENT_REVIEW"]
    Review["R2_003_SCOPE_REMEDIATION_REVIEW_VERDICT<br/>NOT_YET_ISSUED"]
    Gaps["38 classified gaps<br/>P0=11 · P1 PAPER=12 · P2 LIVE=9<br/>P3=4 · P4=2"]
    D1["D-001 locked results<br/>GAP-032=P1 PAPER blocker<br/>GAP-034=P1 PAPER blocker<br/>unauthorized semantic change count=0"]
    Auth["BLUEPRINT_RATIFIED=NO<br/>IMPLEMENTATION_AUTHORIZED=NO<br/>SHADOW_AUTHORIZED=NO<br/>PAPER_AUTHORIZED=NO<br/>LIVE_AUTHORIZED=NO"]
    Next["NEXT VALID ACTION<br/>Owner launches genuinely fresh,<br/>isolated, packet-only R2-003 review"]

    State --> Review
    State --> Gaps
    Gaps --> D1
    Review --> Auth
    D1 --> Auth
    Auth --> Next
```

```text
PRODUCTION_READY=NO
PROGRAM_STATUS=DOCUMENTATION_AND_ARCHITECTURE_REMEDIATION_ONLY
NEXT_IMPLEMENTATION_PATH=NONE_UNTIL_FRESH_REVIEW_AND_SEPARATE_OWNER_DECISION
```

A valid fresh review PASS can only make R2-003 eligible for a separate Owner
ratification decision. It authorizes no implementation, dependency use,
service, AWS, broker, SHADOW, PAPER, LIVE, merge, push, or deployment action.

Source: blueprint §§33–36 and D-001 correction-ledger Locked substantive
results.
