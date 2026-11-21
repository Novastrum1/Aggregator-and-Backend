# Readiness remediation — 2026-11-21

This is an evidence report, not a production or funding-readiness approval.
All network requests in this review were read-only. No key was accessed,
transaction signed/submitted, pool funded or liquidity claimed.

| Requested area | Verified progress | Remaining requirement |
| --- | --- | --- |
| Original functionality | Original TypeScript routing/discovery/API work is attributed separately from preserved Soroswap Rust. The synthetic benchmark reproduces 2000 flat pool checks versus 1000 index-build visits plus 4 edge checks, with 2 routes returned. Public Soroswap reference math matches in 3/3 same-ledger trials. | This is operation-count evidence and compatibility, not a new AMM invention, throughput result or split-route improvement. Extend benchmarks against representative workloads before broader performance claims. |
| Licensing | Conflicts and affected components are inventoried in LICENSE_REVIEW.md and Contract's LICENSING_REVIEW.md. | Obtain written rights-holder clarification/legal review, or replace affected implementations with independently developed compatible code. Editing a license declaration cannot grant missing rights. No clearance is asserted. |
| Testnet deployment | Legacy Factory and Router code hashes and uploaded Pair hash match recorded artifacts. Router points to Factory. Seven historical receipts match successful status, hash, ledger, fee and source through Horizon. | Current Contract main is not deployed. The old build requires the preserved source bundle. Fresh checks do not independently decode historical operation-to-contract XDR binding. Pair code TTL reports zero and no Pair instance exists; investigate lifetime/restoration before funding. |
| Liquidity pools | Factory getter confirms zero pools. | Resolve licensing and Pair code lifetime, then simulate and execute an approved Testnet pool/funding plan using a controlled signer. Do not substitute Soroswap-operated liquidity. |
| Live token swap | Backend correctly reports NO_POOLS and AGGREGATOR_NOT_DEPLOYED and refuses execution. | Deploy/verify the aggregator after licensing resolution, fund a real route, and demonstrate wallet review, user signing, independent simulation, submission, finality and balance changes. No live swap is claimed. |
| Ecosystem participation | Public code/tests/docs can support an authentic contribution record once reviewed and merged. | No third-party contribution, acceptance, community activity or future maintenance is fabricated. Record real upstream contributions and responses when they happen. |
| GitHub issues | Frontend proxy regression coverage and README corrections are prepared; Contract deployment documents now distinguish legacy records from current main. | Review/merge companion changes before closing the matching issues. Pool, live-wallet and legal issues stay open until independently evidenced. |

## Reproduce and inspect

- [Read-only chain report](evidence/testnet-verification-2026-11-21.json): generated with `npm run evidence:testnet -- --trials 3 --output docs/evidence/testnet-verification-2026-11-21.json` under Node 22. The output flag refuses overwriting an existing report; use a new dated path for a future check.
- [Horizon receipt checks](evidence/horizon-receipts-2026-11-21.json): GET each recorded transaction URL, compare public response fields to `contracts-testnet-completion-2026-11-02.json`. RPC NOT_FOUND reflects retention here; it is not a failed transaction result.
- [Routing counts](evidence/routing-benchmark-2026-11-21.json): `npm run benchmark:routing`, synthetic offline workload. Index construction cost is included separately.
- [Original contribution boundaries](ORIGINAL_CONTRIBUTIONS.md), [licensing review](LICENSE_REVIEW.md), [historical deployment reconciliation](DEPLOYMENT_RECONCILIATION.md), [write plan and prerequisites](TESTNET_LIVE_PLAN.md).

The reference report's 851 pools belong to public Soroswap, not VELTRIXAE.
Its 3/3 quote attempts (median 1057 ms, maximum 2323 ms) describe this client,
sample and period only. They are neither a VELTRIXAE trade nor a service SLA.

## Decisions needed before live execution

The maintainer needs a licensing resolution and a controlled Testnet signing
identity, plus a concrete reviewed deployment/funding plan. Never send secret
keys in chat or commit them. The project remains an incomplete Testnet demo;
this evidence does not establish hackathon/grant eligibility or production safety.
