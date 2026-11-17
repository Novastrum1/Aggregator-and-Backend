# Production readiness gates

This is an executable decision record for maintainers. It does not authorize a Mainnet deployment, transaction submission, or liquidity provision.

## Current decision

**Do not launch Mainnet.** The project has no independent audit, unresolved upstream licensing questions, no approved launch jurisdiction, no approved multisig governance record, and no verified live VELTRIXAE liquidity path.

## Required evidence before launch

| Gate | Evidence required | Owner |
| --- | --- | --- |
| Legal/compliance | Written scope for intended jurisdictions, entity and compliance contact, product disclosures | Authorized project representative and counsel |
| Licensing | Written determination or permissions resolving upstream license questions | Rights holders and counsel |
| Smart-contract security | Independent audit report for exact commit and WASM hashes; remediation record | Independent auditor and maintainers |
| Governance | Organization-controlled 3-of-5 admin/treasury multisig and separate 2-of-3 pause guardians | Authorized signers |
| Reproducibility | Source, dependencies, compiler/optimizer, bindings and deployed WASM hashes verified independently | Release engineer and reviewer |
| Testnet rehearsal | Verified deployment, initialization, pause, incident response, monitoring and recovery exercise | Engineering and operations |
| Liquidity and market controls | Approved assets, limits, routing policy, monitoring and user risk disclosures | Product, risk and compliance |
| Mainnet deployment | Explicit 3-of-5 approval, funded organization-controlled account, public manifest and verification report | Authorized signers |

## Non-custodial boundary

The API may quote and prepare unsigned transactions but must never sign, submit, retain a user's secret, accept recovery phrases, or have custody of user funds. Deployment and treasury signers are separate from user wallets and from CI.

## Release procedure

1. Complete every gate above with links to immutable evidence.
2. Create a release candidate and run CI, property, integration, differential, dependency, and secret-scanning checks.
3. Rehearse the exact deployment and incident runbooks on Testnet with fresh artifacts; record the results and time-bounded rollback/containment plan.
4. Obtain the required multisig approval after the evidence review.
5. Submit Mainnet operations manually from the controlled multisig process; CI can prepare artifacts but has no signing authority.
6. Publish contract IDs, source/WASM hashes, audit scope, known risks, monitoring status, and user-facing disclosures. Verify them on-chain before enabling interface actions.

Any failed or missing gate blocks release. Do not replace missing evidence with documentation assertions.
