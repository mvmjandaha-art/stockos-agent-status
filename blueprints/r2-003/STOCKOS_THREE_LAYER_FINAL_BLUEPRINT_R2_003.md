# StockOS Three-Layer Final Blueprint R2-003

TASK_ID=STOCKOS-THREE-LAYER-FINAL-BLUEPRINT-R2-D001-SCOPE-CORRECTION-002
ROLE=CODEX_PRIMARY_IMPLEMENTER_AND_PACKAGE_CUSTODIAN
MODE=LOCAL_OFFLINE_ADDITIVE_SUCCESSOR_ONLY
PACKAGE_SEQUENCE=R2-003
PREDECESSOR_PACKAGE_ROOT=/private/tmp/stockos-three-layer-production-readiness-r2-002
PREDECESSOR_BLUEPRINT_SHA256=f7398b88b028ab1ecffc92d0c3f346809e091414b65e773a50b8bbf052c82598
UPSTREAM_REVIEW_TASK_ID=STOCKOS-THREE-LAYER-FINAL-BLUEPRINT-R2-FRESH-INDEPENDENT-REVIEW-001
UPSTREAM_REVIEW_REPORT_SHA256=713d54282177543e2dd445786fbd3711e4757049ac85d338ffd6355e49af70f5
UPSTREAM_REVIEW_VERDICT=FAIL
CORRECTION_SCOPE=D-001_AND_PERMITTED_PACKAGE_PROVENANCE_ONLY
SOURCE_HEAD=1538cbf0f5bda764f0555f1963745141529d57ef
SOURCE_TREE=be369207fe4e70d5dc9f1043e5614188252d66be
SOURCE_PARENT=780d674810a026a3ab2a517afd56501b38c70d11
R2_SUPERSEDES_R1_FOR_FUTURE_REVIEW=YES
R1_PRESERVED_AS_HISTORICAL_EVIDENCE=YES
R1_REVIEW_VERDICT=FAIL
R2_001_REVIEW_VERDICT=FAIL
R2_002_LIMITED_REVIEW_VERDICT=NOT_YET_ISSUED
R2_003_SCOPE_REMEDIATION_REVIEW_VERDICT=NOT_YET_ISSUED
BLUEPRINT_STATUS=PROPOSED
BLUEPRINT_RATIFIED=NO
IMPLEMENTATION_AUTHORIZED=NO
SHADOW_AUTHORIZED=NO
PAPER_AUTHORIZED=NO
LIVE_AUTHORIZED=NO

## 1. Executive decision

StockOS should remain the sovereign research, decision, risk, capital, mode, admission, lifecycle, reconciliation and forensic authority. NautilusTrader should become only the implementation of the StockOS execution runtime after measured PAPER equivalence and explicit cutover. OpenAlgo should be a separate, default-deny connectivity plane that exposes qualified market-data reads and transmits only exact manifest-bound orders.

THREE_LAYER_DESIGN=PROPOSED_FOR_FRESH_INDEPENDENT_REVIEW
FULL_SOURCE_MERGE=NO
THREE_SYSTEMS_PROCESS_ISOLATED=YES
STRICT_VERSIONED_CONTRACTS=YES
ONE_AUTHORITY_CHAIN=YES
STOCKOS_REMAINS_SOVEREIGN=YES

This R2 design is a remediation proposal. It is not an independent review verdict, owner ratification, implementation authority, or readiness claim.

## 2. Verified current StockOS component inventory

The sealed R1 source inspection identified 40 required component groups. Its immutable historical inventory remains at `/private/tmp/stockos-three-layer-production-readiness-r1-001/evidence/component_inventory.tsv`; R2 rechecked only the source paths needed for remediation and S-001.

Key verified facts:

- PolicyEngine plus MTC `submit_proposal` implements a typed, lineage/freshness/deduplicated PAPER/REAL_PAPER intake path.
- RiskEngine has a rich multi-stage approval and sizing pipeline.
- ExecutionService’s active signal path can instead create `approved=True` through `approved_decision_adapter.from_live_signal` without PolicyEngine or RiskEngine approval.
- Mode safety has strong local boot/no-mix checks, but no durable ModeAuthority receipt.
- A sealed execution manifest is documented but no executable validator/store was located.
- Execution has multiple AngelOne adapters, a SmartLimit path, multiple state models and multiple PAPER/matching implementations.
- Only AngelOne has a locally built LIVE adapter in the mode-scoped registry. Dhan, Fyers, Upstox, Kite and Delta fail closed for LIVE.
- Delta has research capability, generic PAPER and 24x7 session representation; no local live Delta execution adapter was located.
- There are 125 current test files. They are foundation evidence, not proof of the proposed OpenAlgo/Nautilus system.

## 3. Current StockOS authority graph

The strongest current typed path is:

`Forecast → PolicyEngine.decide → DecisionProposal → MTC.submit_proposal → RiskEngine.approve → ApprovedDecision`

The current executable launcher path is:

`brain/MTC signal payload → ExecutionService._enter_position → from_live_signal(approved=True) → ExecutionEngine → SmartOrderManager → OrderRouter → BrokerAdapter`

The second path is shorter and bypasses the first path’s canonical decision/risk authority. Capital is distributed across RiskEngine/CapitalAllocator, CapitalManager, PortfolioGovernor and sizing components. Mode is distributed across configuration, ExecutionService, `assert_safe_boot` and mode-scoped registries. ExecutionService also owns signal handling, quantity/SL/TP/product derivation, broker construction, recovery, position monitoring and exit triggers.

The historical detailed reconstruction and 25 forensic-inventory findings remain in the sealed R1 artifact `/private/tmp/stockos-three-layer-production-readiness-r1-001/evidence/forensic_execution_findings.md`. They are distinct from the R1 independent-review findings F-001 through F-006.

## 4. Current execution and broker paths

Current canonical-engine placement is:

`ExecutionEngine.execute → build_plan → SmartOrderManager.execute → OrderRouter.route → BrokerAdapter.place_order/status`

Current router behavior includes broad exception retries and a partial-fill remainder BrokerOrder. These are incompatible with the target rule that ambiguous writes become `ORDER_STATE_UNKNOWN`, and with the rule that neither Nautilus nor OpenAlgo changes approved quantity.

Three live AngelOne paths exist:

1. `execution/brokers/angelone.py:AngelOneBroker`;
2. `core/execution_adapter.py:AngelOneAdapter`;
3. `execution/brokers/angel_one.py:AngelOneLimitAdapter`.

`SmartLimitEngine` can construct a separate live engine. These paths must remain disabled unless they are the explicitly selected current baseline; they cannot coexist as target execution authorities.

## 5. Current PAPER and Delta paths

The launcher’s PAPER path uses durable `execution/brokers/paper.py:PaperBroker` and `PaperLedger`. Other implementations include `PaperExecutionAdapter`, `SimulationBroker`, the simulation exchange `MatchingEngine`, and the SmartLimit paper engine. Target sessions must bind exactly one matching engine.

Delta is present as:

- a broker universe identifier and generic PAPER profile;
- a `DELTA_EXCHANGE_INDIA` strategy-synthesis capability manifest;
- a 24x7 exchange-session classification.

DELTA_EXCHANGE_VIA_OPENALGO=UNVERIFIED
EXISTING_STOCKOS_DELTA_ADAPTER_REPLACED=NO
DELTA_24X7_PATH_CHANGED_BY_INITIAL_PROGRAM=NO

## 6. Locked three-layer target architecture

Layer 1 — StockOS authority:

- research and immutable strategy artifacts;
- PolicyEngine decisions;
- MTC proposal intake and final admission;
- RiskDecision and CapitalDecision;
- ModeAuthority and StartupGate;
- sealed manifest and AuthorizedExecutionEnvelope;
- lifecycle/exit policy;
- reconciliation and forensic ledger.

Layer 2 — Nautilus execution implementation:

- StockOSAuthorityIngress verifies exact envelopes;
- veto-only structural checks;
- OMS/order state;
- execution engine;
- portfolio state mirror;
- simulation only after explicit session-type cutover.

Layer 3 — OpenAlgo connectivity:

- qualified market-data REST/WS;
- broker capability and symbol mapping;
- exact place/modify/cancel transport;
- normalized broker events;
- no trading decision, sizing, mode, broker selection, failover or exposure enlargement.

The three systems run as separate processes with strict versioned contracts and one active writer per authority state.

## 7. Current-versus-target comparison

The 40-row migration classification is in `STOCKOS_THREE_LAYER_CURRENT_TO_TARGET_MATRIX_R2_001.md`.

R2_SUPERSEDES_R1_FOR_FUTURE_REVIEW=YES
R1_PRESERVED_AS_HISTORICAL_EVIDENCE=YES
R1_CAN_AUTHORIZE_IMPLEMENTATION=NO

The target wraps or adapts mature StockOS research, PolicyEngine, RiskEngine, accounting, Delta and tests; it refactors fragmented authority; it replaces execution/state components only after equivalence; and it does not merge OpenAlgo or Nautilus source into StockOS.

## 8. Research Engine ownership

RESEARCH_ENGINE_OWNER=STOCKOS
STRATEGY_DISCOVERY_AUTHORITY=STOCKOS
STRATEGY_VALIDATION_AUTHORITY=STOCKOS
STRATEGY_PROMOTION_AUTHORITY=STOCKOS

RESEARCH_ENGINE_CAN_CONSUME_MARKET_DATA=YES
RESEARCH_ENGINE_CAN_CONSUME_RECONCILED_EXECUTION_EVIDENCE=YES
RESEARCH_ENGINE_CAN_GENERATE_STRATEGY_PROPOSAL=YES
RESEARCH_ENGINE_CAN_BACKTEST=YES
RESEARCH_ENGINE_CAN_SCORE_STRATEGIES=YES

RESEARCH_ENGINE_CAN_APPROVE_OWN_STRATEGY=NO
RESEARCH_ENGINE_CAN_PROMOTE_ITSELF=NO
RESEARCH_ENGINE_CAN_ALLOCATE_CAPITAL=NO
RESEARCH_ENGINE_CAN_SELECT_PAPER_OR_LIVE=NO
RESEARCH_ENGINE_CAN_OPEN_EXECUTION_SESSION=NO
RESEARCH_ENGINE_CAN_CALL_BROKER=NO
RESEARCH_ENGINE_CAN_IMPORT_BROKER_CREDENTIALS=NO
RESEARCH_ENGINE_CAN_MUTATE_EXECUTION_STATE=NO

Execution evidence becomes research input only after:

BROKER_EVENT_NORMALIZED=YES
RECONCILIATION_COMPLETE=YES
FORENSIC_COMMIT_COMPLETE=YES
LEARNING_EVIDENCE_IMMUTABLE=YES

## 9. Broker authority versus broker connectivity

TRADING_DECISION_AUTHORITY=STOCKOS
RISK_AUTHORITY=STOCKOS
CAPITAL_AUTHORITY=STOCKOS
MODE_AUTHORITY=STOCKOS
BROKER_SELECTION_AUTHORITY=STOCKOS
BROKER_ACCOUNT_AUTHORITY=STOCKOS
LIFECYCLE_POLICY_AUTHORITY=STOCKOS
MANIFEST_AUTHORITY=STOCKOS
FINAL_ADMISSION_AUTHORITY=STOCKOS
RECONCILIATION_POLICY_AUTHORITY=STOCKOS
FORENSIC_SYSTEM_OF_RECORD=STOCKOS

OpenAlgo performs connectivity. A broker adapter can translate a canonical instrument ID to a previously qualified exact broker symbol and carry exact bytes; it cannot choose the broker, account, instrument, side, quantity, product, order type or retry outcome.

## 10. Nautilus runtime boundary

NAUTILUS_IS_IMPLEMENTATION_OF_STOCKOS_EXECUTION_ENGINE=YES
NAUTILUS_IS_PARALLEL_EXECUTION_AUTHORITY=NO
NAUTILUS_PORTFOLIO_IS_STATE_MIRROR=YES
NAUTILUS_SIMULATION_IS_STOCKOS_RUNTIME_IMPLEMENTATION_ONLY_AFTER_CUTOVER=YES

NAUTILUS_CAN_GENERATE_SIGNAL=NO
NAUTILUS_CAN_SELECT_INSTRUMENT=NO
NAUTILUS_CAN_SELECT_SIDE=NO
NAUTILUS_CAN_SIZE_POSITION=NO
NAUTILUS_CAN_ALLOCATE_CAPITAL=NO
NAUTILUS_CAN_CHANGE_MODE=NO
NAUTILUS_CAN_OPEN_SESSION=NO
NAUTILUS_CAN_CREATE_EXIT_POLICY=NO
NAUTILUS_CAN_OVERRIDE_STOCKOS_RISK=NO
NAUTILUS_CAN_APPROVE_STOCKOS_REJECTED_ORDER=NO
NAUTILUS_CAN_ENLARGE_APPROVED_EXPOSURE=NO

Ingress accepts only a valid, current, signed, manifest-bound envelope and may accept or reject it structurally. It may never repair an envelope.

## 11. OpenAlgo connectivity boundary

OPENALGO_IS_CONNECTIVITY_PLANE=YES
OPENALGO_IS_BROKER_ADAPTER_IMPLEMENTATION=YES
OPENALGO_IS_TRADING_AUTHORITY=NO

OPENALGO_CAN_SELECT_BROKER=NO
OPENALGO_CAN_SELECT_ACCOUNT=NO
OPENALGO_CAN_SELECT_INSTRUMENT=NO
OPENALGO_CAN_SELECT_SIDE=NO
OPENALGO_CAN_CHANGE_QUANTITY=NO
OPENALGO_CAN_ALLOCATE_CAPITAL=NO
OPENALGO_CAN_CHANGE_MODE=NO
OPENALGO_CAN_OPEN_SESSION=NO
OPENALGO_CAN_TRIGGER_FAILOVER=NO
OPENALGO_CAN_CREATE_EXIT_POLICY=NO
OPENALGO_CAN_ENLARGE_EXPOSURE=NO

The machine-readable allowlist/default-deny contract is `STOCKOS_OPENALGO_ENDPOINT_POLICY_R2.yaml`.

## 12. Legal market-data flow

`Selected broker read API/stream → OpenAlgo normalized broker payload → StockOS market-data ingress → canonical instrument mapping → freshness/sequence/provenance validation → immutable MarketSnapshot → StockOS research/PolicyEngine`

Read retries are bounded and broker-qualified. A disconnect, gap, stale event, unsupported depth or clock problem blocks admission until a fresh snapshot and continuity proof exist. Market data cannot carry order authority.

## 13. Legal order flow

There is one legal new-entry flow:

`Research Engine → StrategyProposal → PolicyEngine → MTC Proposal Intake → RiskEngine → CapitalAuthority → ModeAuthority → MTC Final Admission → Sealed Execution Manifest → StartupGate → AuthorizedExecutionEnvelope → StockOSAuthorityIngress → Nautilus veto-only structural checks → Nautilus OMS and ExecutionEngine → StockOS OpenAlgo adapter → OpenAlgo exact transport → selected broker`

THERE_MUST_BE_NO_SHORTER_PROPOSAL_TO_ORDER_PATH=YES
ONE_ENVELOPE_TO_ONE_EXACT_ORDER=YES

Future order slicing requires a separately reviewed and owner-ratified `ExecutionPlan` contract. The R2 envelope does not authorize slicing.

## 14. Legal return and reconciliation flow

`Broker ACK/reject/partial/fill/modify/cancel/unknown → OpenAlgo normalized event → Nautilus execution client → Nautilus OMS and portfolio mirror → StockOS reconciliation → StockOS forensic ledger → immutable StockOS learning evidence`

BROKER_EVENTS_FLOW_UPWARD_ONLY=YES

Every event carries event identity, exact-byte hash, prior-event identity/hash, source-stream identity, a gapless monotonic source sequence, broker event time, receipt time, broker/account/venue/instrument provenance, session, command, client-order and broker-order identity. Default enum values, missing required presence, duplicates with different bytes, reordering, gaps, hash-chain breaks and cross-account provenance fail closed into reconciliation. StockOS reconciliation, not Nautilus or OpenAlgo, decides whether state matches and whether admission may resume.

## 15. Protective-exit flow

DISCRETIONARY_EXIT_REQUIRES_NEW_FULL_AUTHORITY_CHAIN=YES
PROTECTIVE_EXIT_REQUIRES_ENTRY_PREAUTHORIZED_IMMUTABLE_POLICY=YES
PROTECTIVE_EXIT_REQUIRES_NEW_DISCRETIONARY_DECISION_AT_TRIGGER=NO
PROTECTIVE_EXIT_REDUCE_ONLY=YES
PROTECTIVE_EXIT_CAN_ENLARGE_OR_REVERSE_EXPOSURE=NO

A discretionary exit uses a new live Policy/Risk/Capital/Mode/MTC admission chain and a fresh market snapshot. A protective or emergency exit is different: before entry admission, StockOS must seal an immutable, signed, expiring reduce-only policy bound to the original command and receipts, exact account/instrument/position lifecycle, maximum quantity, triggers, price/slippage bounds, partial-fill behavior and unknown-state behavior.

At trigger time, a protective exit references those original immutable receipts; it does not invent a shorter discretionary authority path. The requested quantity is `min(policy maximum, reconciled open quantity)`. Policy/Risk/MTC process loss cannot create new discretion, but it does not invalidate an unexpired preauthorization. Verified broker-native protection is preferred and must be placed/acknowledged before or atomically with entry where supported. If no verified native protection and no separately qualified degraded executor exists, entry is blocked. Market-data loss, kill switch, partial fill, unknown result, expiry, renewal and recovery follow `STOCKOS_PROTECTIVE_EXIT_POLICY_R2.yaml`.

## 16. AuthorizedExecutionEnvelope

`STOCKOS_AUTHORIZED_EXECUTION_ENVELOPE_R2.schema.json` defines explicit `oneOf` operation shapes for ENTRY, DISCRETIONARY_EXIT, PROTECTIVE_EXIT, MODIFY and CANCEL. MODIFY/CANCEL bind the original command hash plus exact client-order, broker-order and last-event identity; CANCEL permits no trading fields. The schema defines legal/mutable fields per intent and exact canonicalization, hash and signature domains without self-reference.

JSON Schema structural success is necessary but insufficient. The mandatory semantic profile must enforce ordered validity windows, quantity/child/total bounds, price-band ordering, market-snapshot age, exact same-account target resolution, unchanged nonmutable fields, reduce-only reconciled quantity, durable idempotency and authority receipt validity. Missing or errored semantic validation is a rejection.

SCHEMA_ONLY_VALIDATION_SUFFICIENT=NO
SEMANTIC_VALIDATION_REQUIRED=YES
CANONICAL_SERIALIZATION=RFC8785_JCS_UTF8
COMMAND_HASH_DOMAIN=ENTIRE_ENVELOPE_EXCLUDING_COMMAND_PAYLOAD_SHA256_AND_SIGNATURE

## 17. StockOS–Nautilus contract

`STOCKOS_NAUTILUS_RUNTIME_CONTRACT_R2.proto` defines:

`SubmitAuthorizedCommandRequest`, `CommandAcceptance`, provenance-bound `ExecutionEvent`, `StreamExecutionEventsRequest`, `ReconciliationSnapshotRequest` and `ReconciliationSnapshot`, plus typed presence-aware enums and a StockOS validation attestation.

The entire proposed RPC surface is `SubmitAuthorizedCommand`, `StreamExecutionEvents` and `GetReconciliationSnapshot`. Admission requires an exact StockOS-validated envelope; there is no RPC for signal, strategy, capital, mode, broker, account, instrument, session or exit-policy selection. A mandatory semantic profile rejects unspecified enums, empty required identifiers, missing broker time/provenance, duplicate/reordered/gapped events, hash-link failures and cross-account events.

## 18. OpenAlgo endpoint policy

`STOCKOS_OPENALGO_ENDPOINT_POLICY_R2.yaml` defines version-pinned proposed local transport with exact HTTP method/path, request body and custody header mappings for place, modify and cancel. Every authority, session, account, instrument and order field is either mapped into the adapter request or atomically bound in the write-ahead custody record; omission is a block.

Exact adapter request bytes and exact response bytes are hashed. Response classes distinguish acknowledged, terminal rejection, unknown and idempotency conflict. Timeout, connection reset, parse failure, missing order ID, contradictory response or crash after send is `ORDER_STATE_UNKNOWN`; no blind retry is allowed. MODIFY/CANCEL resolve one exact prior order under the same session/account/broker/venue/instrument.

Prohibited: smart/options/multi/basket/split orders, closeposition, cancelallorder, hosted strategies, flow/MCP/analyzer/sandbox execution, automatic square-off, sizing, allocation, failover, strategy selection and instrument selection.

OPENALGO_PUBLIC_ACCESS=NO
OPENALGO_HTTP_BIND=127.0.0.1
OPENALGO_WS_BIND=127.0.0.1

## 19. Capability matrix

`STOCKOS_OPENALGO_BROKER_CAPABILITY_MATRIX_R2.csv` includes Angel One, Dhan, Fyers, Upstox, Zerodha Kite and Delta Exchange India. It separates current adapter presence, OpenAlgo claims, local verification, market-data/order/account features and eligibility.

Only local StockOS evidence is credited. OpenAlgo support is `UNVERIFIED` or `UNKNOWN` because no local OpenAlgo source was present and this task is offline.

RECOMMENDED_FIRST_BROKER=ANGEL_ONE_READ_ONLY_CANDIDATE_ONLY

This recommendation is based only on AngelOne being the sole locally built live adapter and having current data paths. It does not qualify OpenAlgo or authorize broker use.

## 20. Failure taxonomy

`STOCKOS_THREE_LAYER_FAILURE_TAXONOMY_R2.yaml` defines authority owner, allowed/prohibited actions, retry, reconciliation, mode/session effects, evidence and fail-closed result for all required failures.

HTTP_TIMEOUT=ORDER_STATE_UNKNOWN
BLIND_RESUBMISSION=NO
UNKNOWN_STATE_REQUIRES_RECONCILIATION=YES
CONFLICTING_NEW_ORDER_WHILE_UNKNOWN=NO

## 21. Idempotency and unknown state

One command has one command payload hash and one idempotency key. Duplicate identical commands return the original receipt; a key reused with different bytes is an authority/custody failure. Broker order ID is correlated to command ID and client order ID.

Timeout after a write never proves rejection. The command scope becomes unknown, conflicting orders are blocked, and read-only status/reconciliation is required. Neither OpenAlgo nor Nautilus may resubmit, hedge, flatten or offset without a new exact StockOS-authorized envelope.

## 22. PAPER transition

ONE_SESSION_ONE_MATCHING_ENGINE=YES
OPENALGO_ANALYZER_ALLOWED=NO

Initial transition:

MARKET_DATA=OPENALGO_OR_CURRENT_QUALIFIED_LIVE_FEED
DECISION_ENGINE=STOCKOS
RISK_AND_CAPITAL=STOCKOS
PAPER_EXECUTION=EXISTING_STOCKOS_PAPERBROKER
NAUTILUS_SIMULATION=OBSERVER_ONLY
OPENALGO_ORDER_ENDPOINTS=PHYSICALLY_BLOCKED

After equivalence and explicit cutover only:

NAUTILUS_SIMULATION_ENGINE=IMPLEMENTATION_OF_STOCKOS_PAPER_EXECUTION
OLD_STOCKOS_PAPERBROKER=RETIRED_FOR_QUALIFIED_SESSION_TYPE
OPENALGO_SUPPLIES_DATA_AND_EXACT_LIVE_TRANSPORT_ONLY

Equivalence covers fills, partials, slippage, brokerage, taxes, margin, PnL, stop/trail/target/square-off, recovery, unknown state, revocation and forensic replay.

## 23. Process isolation and AWS topology

### Demand-driven runtime model

RUNTIME_MODEL=DEMAND_DRIVEN
ALWAYS_ON_COMPONENT=LIGHTWEIGHT_STOCKOS_SUPERVISOR_ONLY
HEAVY_SERVICES_ALWAYS_ON=NO
SERVICE_START_REQUIRES_DECLARED_CONSUMER=YES
SERVICE_STOP_REQUIRES_SAFE_STOP_GATE=YES
IDLE_RESOURCE_MINIMIZATION_REQUIRED=YES
UNNECESSARY_SERVICE_DEFAULT=STOPPED

The one versioned target graph has exactly nine service nodes:

- `stockos-supervisor.service`
- `stockos-authority.service`
- `stockos-research.service`
- `stockos-market-data.service`
- `stockos-nautilus-runtime.service`
- `openalgo.service`
- `stockos-paper.service`
- `stockos-live.service`
- `stockos-delta-runtime.service`

This is a target topology, not a requirement to create all services at once. No service is created, started or stopped by this blueprint task.

### Current-to-target service mapping

| Target service | Current components | Treatment | Target responsibility |
|---|---|---|---|
| `stockos-supervisor.service` | `control_engine/controller.py`, watchdog/resource manager, `supervisor/heartbeat_controller.py`, health/auto-recovery modules | RETAIN selected health logic; SPLIT lifecycle authority from monolithic controller; WRAP with reference counts and SafeStopGate | Lightweight always-on lease/dependency/health supervisor; no trading authority |
| `stockos-authority.service` | PolicyEngine, MTC, RiskEngine, capital/mode/session/manifest/reconciliation/forensic responsibilities currently distributed across components | SPLIT and consolidate only through future reviewed work; no source change in R2 | Demand-driven StockOS authority/admission/reconciliation/forensic service; no broker credentials |
| `stockos-research.service` | `research/*`, `strategy_factory/*`, research orchestration | RETAIN research/factory; SPLIT from execution; WRAP as batch/event consumer | Scheduled/event research only; immutable outputs; auto-stop when work and queue complete |
| `stockos-market-data.service` | `data/feeds/angelone.py`, provider modules, launcher WS path, chain/Greeks/instrument modules | SPLIT and WRAP one shared feed; RETIRE duplicate launcher WS after equivalence | Reference-counted normalized REST/WS with one connection per qualified subscription set |
| `stockos-nautilus-runtime.service` | No current Nautilus implementation; current `ExecutionEngine`, state models and simulation are baseline | REPLACE_LATER only after observer/equivalence | Veto-only OMS/execution implementation and portfolio mirror |
| `openalgo.service` | No current OpenAlgo; three AngelOne connectivity paths are current baseline | ADD separately; RETIRE direct adapters only after transport equivalence | Loopback default-deny broker connectivity; no trading authority |
| `stockos-paper.service` | `ExecutionService`, `PaperBroker`, `PaperLedger`, additional simulators/matchers | SPLIT session supervision; RETAIN PaperBroker initially; RETIRE duplicate matchers and later PaperBroker per qualified session type | Manifest-bound PAPER session with exactly one runtime/matching engine |
| `stockos-live.service` | live branch of `ExecutionService`, AngelOne adapters, safety rails | SPLIT and REFACTOR; keep stopped by default; REPLACE direct transport after qualification | Manifest-bound bounded LIVE session coordinator; no implicit authorization |
| `stockos-delta-runtime.service` | Delta session authority, synthesis capability and generic PAPER registry; no live adapter located | WRAP independently; RETAIN 24x7 boundary; no initial migration | Separately owner-enabled 24x7 Delta session, independent of NSE/BSE close |

### Reference-counted dependency state

Every service publishes an atomic, monotonically correlated snapshot containing all applicable counters:

ACTIVE_CONSUMER_COUNT
ACTIVE_SESSION_COUNT
ACTIVE_MARKET_DATA_SUBSCRIPTION_COUNT
OPEN_POSITION_COUNT
PENDING_ORDER_COUNT
UNKNOWN_ORDER_STATE_COUNT
RECONCILIATION_PENDING_COUNT
PROTECTIVE_EXIT_DEPENDENCY_COUNT
UNCOMMITTED_FORENSIC_EVENT_COUNT

`STOCKOS_SERVICE_DEPENDENCY_GRAPH_R2.yaml` is the one machine-readable graph and counter-ownership contract. `stockos-supervisor.service` durably owns graph generation, fenced consumer leases and stop tokens. `stockos-authority.service` durably owns session, order, position, reconciliation, protective-dependency and forensic counters. Market data and research each own only their declared subscription/job counters. No counter has two authorities; a missing, stale or unavailable owner fails closed.

### SafeStopGate

A service may auto-stop only when every applicable counter is zero:

ACTIVE_CONSUMER_COUNT=0
ACTIVE_SESSION_COUNT=0
OPEN_POSITION_COUNT=0
PENDING_ORDER_COUNT=0
UNKNOWN_ORDER_STATE_COUNT=0
RECONCILIATION_PENDING_COUNT=0
PROTECTIVE_EXIT_DEPENDENCY_COUNT=0
UNCOMMITTED_FORENSIC_EVENT_COUNT=0

For a market-data service, `ACTIVE_MARKET_DATA_SUBSCRIPTION_COUNT=0` is also required unless its subscription lease is atomically transferred. For research, the durable research queue and active-job counter must be empty.

Safe stop is one fenced compare-and-stop transaction: CAS `RUNNING→QUIESCING` with the expected graph generation and a unique stop token; reject every new dependency; obtain owner-signed counters at that generation; require all applicable zeros; commit forensic state; recheck the same generation; CAS `QUIESCING→STOP_COMMITTED`; stop/reap the full process group; verify no PID/socket/lock/lease residue; then mark `STOPPED`. Any generation change, lease expiry, publisher restart, stale token, split brain, timeout or residue aborts stop and reconstructs state. No dependency can be created between the final check and stop commit.

OPEN_POSITION_PRESENT_AUTO_STOP=NO
PENDING_ORDER_PRESENT_AUTO_STOP=NO
UNKNOWN_BROKER_STATE_AUTO_STOP=NO
RECONCILIATION_PENDING_AUTO_STOP=NO
PROTECTIVE_EXIT_REQUIRED_AUTO_STOP=NO
FORENSIC_FLUSH_PENDING_AUTO_STOP=NO

### Startup dependencies

STOCKOS_PAPER_DEPENDS_ON:

- valid PAPER authority;
- sealed execution manifest;
- StartupGate PASS;
- required market-data service;
- required runtime implementation;
- PaperBroker authority until explicit cutover;
- forensic ledger availability.

STOCKOS_LIVE_DEPENDS_ON:

- valid LIVE authority;
- sealed execution manifest;
- StartupGate PASS;
- required broker credential/session health;
- OpenAlgo or another qualified broker adapter;
- Nautilus runtime;
- reconciliation;
- forensic ledger;
- kill-switch availability.

Dependency readiness starts no trading session by itself. The supervisor may start a required process only after the consumer/session lease and its authority are valid. It never synthesizes missing authority.

### Schedule and Indian-market behavior

SCHEDULE_CAN_WAKE_READINESS_CHECK=YES
SCHEDULE_CAN_AUTHORIZE_PAPER=NO
SCHEDULE_CAN_AUTHORIZE_LIVE=NO
SCHEDULE_CAN_OPEN_EXECUTION_SESSION=NO

PRE_MARKET:

- wake only the readiness path and data services required by a declared, owner-enabled candidate session;
- validate broker/token/instrument readiness without placing orders;
- keep execution admission closed until valid authority, manifest and StartupGate PASS.

ACTIVE_MARKET:

- keep only services referenced by the active authorized session, market-data consumers, positions, protective exits and reconciliation;
- stop no dependency while any SafeStopGate counter is nonzero.

POST_MARKET:

- stop new entries;
- complete protective exits strictly under existing authority;
- reconcile orders/trades/positions;
- compute PnL, brokerage and taxes;
- commit and seal forensic records;
- stop services only after `SAFE_STOP_GATE=PASS`.

HOLIDAY:

- Indian broker execution services remain stopped unless a separately explicit special-session authority and sealed manifest exist.

### Independent Delta runtime

DELTA_RUNTIME_SCHEDULE=24X7_INDEPENDENT
DELTA_AUTO_START_REQUIRES_OWNER_ENABLED_SESSION=YES
DELTA_AUTO_STOP_REQUIRES_NO_OPEN_POSITION_OR_PENDING_STATE=YES
INDIAN_MARKET_CLOSE_STOPS_DELTA=NO

NSE/BSE schedule events cannot start, stop or authorize the Delta runtime. Delta uses its own session authority, consumer leases and SafeStopGate.

### Research lifecycle

RESEARCH_ENGINE_ALWAYS_ON=NO
RESEARCH_ENGINE_SCHEDULED_BATCH_ALLOWED=YES
RESEARCH_ENGINE_EVENT_TRIGGER_ALLOWED=YES
RESEARCH_ENGINE_STARTS_BROKER_EXECUTION=NO
RESEARCH_ENGINE_COMPLETION_AUTO_STOP=YES
RESEARCH_QUEUE_EMPTY_REQUIRED_FOR_STOP=YES

Research completion means durable outputs are committed, callbacks/events are acknowledged, the queue is empty, no declared consumer remains and the SafeStopGate passes. Research cannot create an execution-session lease.

### Market-data lifecycle

MARKET_DATA_SERVICE_REFERENCE_COUNTED=YES
NO_CONSUMER_MARKET_DATA_AUTO_STOP=YES
ACTIVE_POSITION_REQUIRES_MARKET_DATA=YES
ACTIVE_PROTECTIVE_EXIT_REQUIRES_MARKET_DATA=YES
DUPLICATE_WEBSOCKET_PROHIBITED=YES

A shared qualified connection multiplexes consumers. An active position or exit policy owns a protective market-data lease even after the entry session closes. No-consumer stop is allowed only when subscriptions, positions, pending/unknown orders, reconciliation, protective dependencies and forensic events are all safe.

### Crash/restart and resource controls

SUPERVISOR_RESTARTS_FAILED_REQUIRED_SERVICE=YES
SUPERVISOR_RESTARTS_UNNECESSARY_SERVICE=NO
RESTART_REQUIRES_AUTHORITY_REVALIDATION=YES
RESTART_REQUIRES_RECONCILIATION=YES
STALE_MANIFEST_RESTART=NO
EXPIRED_SESSION_RESTART=NO

A crash invalidates volatile leases. The supervisor restarts only a service still required by a valid consumer/session or protective/reconciliation dependency. Execution admission remains blocked until process identity, manifest/session authority, journal recovery and reconciliation are valid. Idempotency and broker-state reconciliation prevent duplicate orders.

MEMORY_LIMIT_REQUIRED=YES
CPU_LIMIT_OR_BUDGET_REQUIRED=YES
BOUNDED_QUEUE_REQUIRED=YES
BOUNDED_RETRY_REQUIRED=YES
NO_UNLIMITED_POLLING=YES
NO_UNBOUNDED_LOG_GROWTH=YES
NO_ORPHAN_BACKGROUND_PROCESS=YES

Limits are service-specific and owner-set from measurements; this blueprint invents no numeric threshold. Every service must expose queue depth, drops, memory, CPU, retry and child-process custody.

### Three-layer transport topology

- `stockos-authority.service`: no broker credentials; owns authority, manifests, admission, reconciliation and ledger.
- `stockos-nautilus-runtime.service`: no authority to decide; consumes exact envelopes over a Unix-domain socket.
- `openalgo.service`: only process with broker connectivity/credentials; loopback REST/WS from Nautilus side and AWS-private broker egress.

Initial StockOS-to-Nautilus transport is Unix-domain socket plus versioned MessagePack representing the same logical schema as the future protobuf, with SHA-256, bounded queues, ACK/NACK, heartbeat, process identity, strict timeouts, backpressure and session revocation.

Nautilus-to-OpenAlgo is `127.0.0.1` REST/WS with a dedicated key, pooling and default deny. OpenAlgo-to-broker traffic is AWS-originated authenticated traffic only.

MAC_BROKER_AUTHENTICATION=NO
KUBERNETES_INITIAL_PHASE=NO
DATABASE_REWRITE_INITIAL_PHASE=NO
RUST_ADAPTER_INITIAL_PHASE=NO

No AWS state was inspected or changed. Current AWS readiness is `UNKNOWN`.

DEMAND_DRIVEN_RUNTIME_DOCUMENTED=YES
SAFE_STOP_GATE_DOCUMENTED=YES
IMPLEMENTATION_PERFORMED=NO
SERVICE_ACTION=NO
PAPER_ACTION=NO
LIVE_ACTION=NO

## 24. Delta boundary

The initial program does not migrate Delta, alter its 24x7 session policy, or claim OpenAlgo supports it. Current research and generic PAPER capabilities remain StockOS-owned. A future Delta transport requires its own adapter capability, order lifecycle, authentication, rate-limit, reconciliation, 24x7 recovery and LIVE review packet.

## 25. Security controls

- exact process/role identity and least privilege;
- StockOS authority process cannot read broker credentials;
- Nautilus cannot read broker credentials;
- OpenAlgo credentials are broker/account scoped and never returned upstream;
- loopback-only OpenAlgo ingress; no public bind;
- default-deny endpoint allowlist;
- payload hashes, signatures, immutable manifest and session revocation;
- secret redaction and audit records;
- bounded read retry, no blind write retry;
- durable kill switch and reconciliation gate;
- SBOM, dependency pins, notices and vulnerability review before dependency use;
- backup/restore and disaster-recovery evidence before LIVE.

## 26. Licensing and dependencies

OPENALGO_LICENSE_EXTERNALLY_VERIFIED=NO
NAUTILUS_LICENSE_EXTERNALLY_VERIFIED=NO
DEPENDENCY_INTRODUCTION_AUTHORIZED=NO
LICENSE_VERIFICATION_REQUIRED_BEFORE_WORK_UNIT_B=YES
EXACT_TAG_AND_COMMIT_PIN_REQUIRED=YES
SBOM_REQUIRED=YES
LICENSE_NOTICE_REQUIRED=YES
COMMERCIAL_OR_NETWORK_DISTRIBUTION_LEGAL_REVIEW_REQUIRED=YES

No external license name or compatibility conclusion is asserted by R2. Network access was prohibited, so exact upstream tags, commits, notices and legal terms remain unverified. Work Unit B cannot begin until a separate authorized dependency-custody packet records exact tag+commit pins, artifact hashes, SBOM, notices, license texts and the required legal review.

COPY_OPENALGO_SOURCE_INTO_STOCKOS=NO
COPY_OPENALGO_BROKER_PLUGINS_INTO_NAUTILUS=NO
RUN_OPENALGO_AS_SEPARATE_SERVICE=YES
USE_NAUTILUS_AS_PINNED_DEPENDENCY_OR_SERVICE=YES
MODIFY_NAUTILUS_INTERNALS_INITIAL_PHASE=NO

## 27. Work Units A–D

- A: inventory, authority map, operation-total envelope plus semantic validator, canonical byte/signature vectors, exact order-target resolver, provenance/sequence contract validator, versioned nine-service graph, fenced SafeStop transaction, protective-exit policy, one-matcher reachability and cutover/rollback lifecycle tests; no dependencies/brokers.
- B: one broker, read-only market data and physically blocked shadow payload generation; no Delta migration.
- C: authority ingress, Nautilus observer, state comparison, portfolio mirror, current PaperBroker authority, equivalence and cutover gate.
- D: one broker/account/instrument family and owner-bounded capital; no failover/blind retry; stop/reconcile on unknown.

All four packets are inert drafts. None is authorized.

Supplemental lead S-001 is source-confirmed but is not an R1 review finding. Work Unit A must scope a future correction and regression test for the current `from_live_signal` path that creates `approved=True` while `approved_size_pct` remains its default zero and executable quantity is supplied through `quantity_override`. R2 changes no source bytes and authorizes no correction.

## 28. Master test matrix

`STOCKOS_THREE_LAYER_MASTER_TEST_MATRIX_R2_001.md` defines authority, market-data, execution, PAPER equivalence, security, custody, exact R1-finding closure, SafeStop concurrency, matcher reachability, rollback lifecycle and dependency-custody gates. It assigns a named contract owner and future path to every added row.

No application tests were executed in this blueprint task under the strict minimum-execution policy.

## 29. Performance measurement

Measure:

broker market timestamp→OpenAlgo, OpenAlgo→Nautilus, Nautilus→StockOS, StockOS decision, StockOS→Nautilus submission, Nautilus→OpenAlgo, OpenAlgo→broker ACK, broker fill→Nautilus, Nautilus→StockOS reconciliation, and fill→forensic commit.

Report p50, p95, p99, maximum, sample count, dropped events, queue depth, memory growth and CPU usage with raw-event/clock custody. No target is invented. Native Nautilus broker adapters remain future optimization unless evidence proves OpenAlgo is the bottleneck.

## 30. Migration and retirement

The nine-stage plan is `STOCKOS_THREE_LAYER_MIGRATION_AND_RETIREMENT_PLAN_R2_001.md`:

CURRENT_STOCKOS → OPENALGO_READ_ONLY → OPENALGO_SHADOW → STOCKOS_PAPER_WITH_OPENALGO_DATA → NAUTILUS_OBSERVER → NAUTILUS_PAPER_EQUIVALENCE → NAUTILUS_RUNTIME_CUTOVER → BOUNDED_LIVE → NATIVE_HOT_PATH_ADAPTERS_IF_JUSTIFIED.

FULL_CODEBASE_MERGE=NO
MULTI_BROKER_INITIAL_PHASE=NO
DELTA_MIGRATION_INITIAL_PHASE=NO
OPENALGO_UI_INITIAL_PHASE=NO
OPENALGO_ANALYZER=NO
NATIVE_NAUTILUS_BROKER_ADAPTER_INITIAL_PHASE=NO

## 31. Rollback

Rollback is session revocation plus reconciliation, never an implicit mode change. Each stage returns only to the immediately prior qualified stage. A running session never changes matching engine. Cutover or rollback requires admission stopped, exact order/trade/position/ledger equality or an owner-resolved reconciliation record, full old-process/PID/socket custody, old-session revocation, then a new sealed manifest and new session. Unknown broker state blocks rollback. LIVE rollback does not auto-flatten; only the applicable reviewed protective/discretionary exit contract and separate owner/runbook may govern reductions.

## 32. Parallel continuity

TASK_ROLE_OWNS_WORK=YES
MODEL_BRAND_OWNS_WORK=NO
SINGLE_ACTIVE_WRITER_PER_WORKTREE=YES
SAME_CANDIDATE_DUAL_WRITER=NO
BLUEPRINT_AUTHOR_CAN_REVIEW_OWN_BLUEPRINT=NO
REVIEWER_CAN_REPAIR_IN_SAME_SESSION=NO

R2 review routing is defined only by the sealed R2 dispatch and launch. The remediation implementer cannot review or repair its own packet. No prior R1 reviewer conclusion is reused as the R2 verdict.

## 33. Production-readiness gaps

The gap report identifies:

P0_SECURITY_OR_AUTHORITY_BLOCKER=11
P1_PAPER_BLOCKER=12
P2_LIVE_BLOCKER=9
P3_SCALE_OR_PERFORMANCE=4
P4_FUTURE_OPTIMIZATION=2

Major implementation blockers remain: the current shorter approval path including S-001, absent executable manifest/final admission/mode receipt, retry/quantity mutation, parallel execution paths, fragmented capital/forensic ownership, multiple matchers, and absent implementation evidence for the R2 envelope, exact transport, event provenance, protective-exit liveness, demand-driven graph/SafeStop transaction, crash/resource/orphan controls, OpenAlgo/Nautilus dependency custody and AWS/broker operations.

DEMAND_DRIVEN_RUNTIME_GAP=OPEN_P1_PAPER_BLOCKER_GAP_032
SAFE_STOP_GATE_GAP=OPEN_P0_AUTHORITY_SAFETY_BLOCKER_GAP_033
SERVICE_DEPENDENCY_GRAPH_GAP=OPEN_P1_PAPER_BLOCKER_GAP_034
RESOURCE_LIMIT_GAP=OPEN_P3_SCALE_PERFORMANCE_GAP_035
CRASH_RESTART_GAP=OPEN_P0_AUTHORITY_SAFETY_BLOCKER_GAP_036
ORPHAN_PROCESS_GAP=OPEN_P2_LIVE_BLOCKER_GAP_037
DUPLICATE_RUNTIME_GAP=OPEN_P0_AUTHORITY_SAFETY_BLOCKER_GAP_038

PRODUCTION_READY=NO

## 34. Effort-estimate gate

R1 effort ranges are historical planning notes and are not ratified by R2. R2 adds material contract, concurrency, lifecycle and dependency-custody scope. A future owner-authorized planning pass must build a path-level work breakdown after fresh R2 review and before implementation authorization.

R1_ESTIMATES_CARRIED_AS_CURRENT_COMMITMENT=NO
R2_IMPLEMENTATION_ESTIMATE_STATUS=NOT_DETERMINED
REESTIMATION_REQUIRES_REVIEWED_SCOPE_AND_OWNER_PRIORITY=YES
MISSING_ESTIMATE_CAN_AUTHORIZE_IMPLEMENTATION=NO

## 35. Current authorization state

PROGRAM_STATUS=DOCUMENTATION_AND_ARCHITECTURE_REMEDIATION_ONLY
BLUEPRINT_STATUS=PROPOSED
BLUEPRINT_RATIFIED=NO
IMPLEMENTATION_AUTHORIZED=NO
SOURCE_MODIFICATION_AUTHORIZED=NO
AWS_ACTION_AUTHORIZED=NO
BROKER_ACTION_AUTHORIZED=NO
CREDENTIAL_ACCESS_AUTHORIZED=NO
SERVICE_ACTION_AUTHORIZED=NO
SHADOW_AUTHORIZED=NO
PAPER_AUTHORIZED=NO
LIVE_AUTHORIZED=NO
MERGE_AUTHORIZED=NO
PUSH_AUTHORIZED=NO
DEPLOYMENT_AUTHORIZED=NO

## 36. Exact next owner decision

The next valid action is a genuinely fresh, isolated, packet-only independent review of this blueprint and supporting artifacts. A valid PASS can only make the blueprint eligible for separate owner ratification. It authorizes no implementation or operation.

If and only if the owner later ratifies the reviewed blueprint, the owner must separately choose whether to authorize Work Unit A at an exact base commit and exact paths. Defaults remain `NO`.

CURRENT_STATUS=BLUEPRINT_COMPLETE_PENDING_INDEPENDENT_REVIEW
NEXT_IMPLEMENTATION_PATH=NONE_UNTIL_FRESH_REVIEW_AND_SEPARATE_OWNER_DECISION
EXIT_CRITERIA=VALID_FRESH_REVIEW_REPORT_PLUS_OWNER_RATIFICATION_PLUS_SEPARATE_WORK_UNIT_A_AUTHORIZATION
STOP_HERE=YES
