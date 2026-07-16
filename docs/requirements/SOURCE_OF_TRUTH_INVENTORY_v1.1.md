# Warehouse Suite - Source of Truth Inventory v1.0

## Document Control

- Status: ACTIVE
- Version: 1.1
- Created date: 2026-07-16
- Last updated: 2026-07-16
- Owner: DucTrong Nguyen
- Roadmap stage: Stage 0 - Project Charter and Source-of-Truth

## 1. Purpose

This document identifies the approved information sources for Warehouse Suite.

AI and developers must use the documents listed here before designing collections, workflows, permissions, calculations, interfaces, or tests.

If a required source is missing, incomplete, conflicting, or not approved, implementation must stop and report:

`INSUFFICIENT EVIDENCE TO IMPLEMENT`

AI must not replace missing evidence with assumptions.

## 2. Evidence Status Definitions

- APPROVED: The document is accepted as a controlling source.
- ACTIVE: The document is currently maintained and may control project work.
- DRAFT: The document is under development and must not control production behavior.
- TO BE PROVIDED: The evidence does not yet exist in the repository.
- TO BE CONFIRMED: Information exists partially but still requires owner confirmation.
- BLOCKER: Work depending on this evidence must not begin.
- REFERENCE ONLY: The document may provide context but does not override an approved source.

## 3. Approved Project-Control Documents

| ID | Document | Repository Path | Status | Controls |
|---|---|---|---|---|
| SOT-001 | MVP Scope v1.0 | docs/requirements/MVP_SCOPE_v1.0.md | APPROVED | MVP capabilities, exclusions, scope-control rules and success criteria |
| SOT-002 | Project Charter v1.0 | docs/requirements/PROJECT_CHARTER_v1.0.md | APPROVED WITH ITEMS TO BE CONFIRMED | Objective, users, preliminary roles, deployment model, KPIs, approval responsibilities and open items |
| SOT-003 | Source of Truth Inventory v1.0 | docs/requirements/SOURCE_OF_TRUTH_INVENTORY_v1.0.md | ACTIVE | Evidence register, evidence status and implementation blockers |

## 4. Required Business and Process Sources

| ID | Required Source | Planned Repository Path | Status | Required Before |
|---|---|---|---|---|
| SOT-010 | Cycle Count BRD and SRS | docs/requirements/cycle-count/Yeu_cau_App_Cycle_Count_BRDSRS_v2.9.docx | APPROVED - CONTROLLING SOURCE | Cycle Count schema, workflow, parser, business logic and regression tests |
| SOT-011 | Current Cycle Count SOP | docs/workflows/cycle-count-current-process.md | TO BE PROVIDED - BLOCKER | Target workflow design |
| SOT-012 | Target Cycle Count workflow | docs/workflows/cycle-count-target-process.md | TO BE CREATED - BLOCKER | Status model and module implementation |
| SOT-013 | Recount and Approval rules | docs/workflows/recount-approval-rules.md | TO BE PROVIDED - BLOCKER | Recount or Approval implementation |
| SOT-014 | Offline and synchronization rules | docs/workflows/offline-sync-rules.md | PARTIAL IN BRD/SRS v2.9 - BLOCKER | Full offline architecture, idempotency, retry and conflict implementation |
| SOT-015 | Backup and Restore requirements | docs/requirements/backup-restore-requirements.md | TO BE PROVIDED | Backup and Restore implementation |
| SOT-016 | Audit event requirements | docs/requirements/audit-event-catalogue.md | TO BE PROVIDED | Audit Log implementation |
| SOT-017 | Dashboard KPI definitions | docs/requirements/cycle-count-kpi-definitions.md | TO BE PROVIDED | Dashboard calculations |

## 5. Required Data Sources

Only sanitized data may be committed to this public repository.

| ID | Required Source | Planned Repository Path | Status | Required Before |
|---|---|---|---|---|
| SOT-020 | SKU source file | samples/source/sku/ | RECEIVED IN REVIEW SESSION - GITHUB UPLOAD PENDING | SKU schema, import and tests |
| SOT-021 | Location source file | samples/source/location/ | RECEIVED IN REVIEW SESSION - GITHUB UPLOAD PENDING | Location schema, parser, import and tests |
| SOT-022 | Inventory Golden Sample root | tests/fixtures/cycle-count/golden/20260715182904Nguyen Duc Trong_Location Inventory_VN Ho Chi Minh DC.xls | APPROVED - CONTROLLING ROOT | Inventory parser, snapshot, reconciliation and regression tests |
| SOT-023 | Cycle Count task sample | samples/sanitized/cycle-count/tasks/ | TO BE PROVIDED | Task design and tests |
| SOT-024 | Cycle Count result sample | samples/sanitized/cycle-count/results/ | TO BE PROVIDED | Result and variance design |
| SOT-025 | Golden Sample profile and expected validation | docs/requirements/cycle-count/Yeu_cau_App_Cycle_Count_BRDSRS_v2.9.docx | APPROVED PROFILE - AUTOMATED EXPECTED OUTPUT STILL REQUIRED | Regression test implementation |
| SOT-026 | Invalid and exception samples | tests/fixtures/cycle-count/negative/ | TO BE PROVIDED | Negative and exception tests |

## 6. Required Data-Design Sources

| ID | Required Source | Planned Repository Path | Status | Required Before |
|---|---|---|---|---|
| SOT-030 | SKU Data Dictionary | docs/data-dictionary/sku-data-dictionary.md | TO BE CREATED - BLOCKER | SKU collection migration |
| SOT-031 | Location Data Dictionary | docs/data-dictionary/location-data-dictionary.md | TO BE CREATED - BLOCKER | Location collection migration |
| SOT-032 | Inventory Data Dictionary | docs/data-dictionary/inventory-data-dictionary.md | TO BE CREATED - BLOCKER | Inventory collection migration |
| SOT-033 | Cycle Count Data Dictionary | docs/data-dictionary/cycle-count-data-dictionary.md | TO BE CREATED - BLOCKER | Cycle Count collection migration |
| SOT-034 | Entity Relationship Model | docs/architecture/entity-relationship-model.md | TO BE CREATED - BLOCKER | Database design approval |
| SOT-035 | Inventory source-of-truth decision | docs/architecture/inventory-source-of-truth-decision.md | TO BE CONFIRMED - BLOCKER | Inventory balance, movement or posting design |
| SOT-036 | Status and transition model | docs/workflows/cycle-count-status-model.md | TO BE CREATED - BLOCKER | Cycle Count workflow implementation |

## 7. Required Security Sources

| ID | Required Source | Planned Repository Path | Status | Required Before |
|---|---|---|---|---|
| SOT-040 | User and Role Matrix | docs/requirements/user-role-matrix.md | TO BE CONFIRMED - BLOCKER | Authentication and authorization implementation |
| SOT-041 | Role and Action Permission Matrix | docs/requirements/permission-matrix.md | TO BE CREATED - BLOCKER | PocketBase API rules |
| SOT-042 | Data-access rules | docs/requirements/data-access-rules.md | TO BE CREATED | Collection API rules |
| SOT-043 | Session and authentication policy | docs/requirements/authentication-policy.md | TO BE CONFIRMED | Login implementation |
| SOT-044 | Public repository security rules | .gitignore | ACTIVE | All repository work |

## 8. Required Technical and Operational Sources

| ID | Required Source | Planned Repository Path | Status | Required Before |
|---|---|---|---|---|
| SOT-050 | Architecture Decision Record | docs/architecture/ADR-001-platform-architecture.md | TO BE CREATED | Stage 1 completion |
| SOT-051 | Supported device and browser matrix | docs/requirements/device-browser-matrix.md | TO BE CONFIRMED | Mobile and offline testing |
| SOT-052 | Network and server design | docs/architecture/network-server-design.md | TO BE CONFIRMED | Pilot deployment |
| SOT-053 | Backup retention and recovery targets | docs/requirements/recovery-targets.md | TO BE CONFIRMED | Backup design |
| SOT-054 | Test Strategy | docs/requirements/test-strategy.md | TO BE CREATED - BLOCKER | Feature Release Gate |
| SOT-055 | Deployment and rollback runbook | docs/requirements/deployment-runbook.md | TO BE CREATED | Pilot and Production Release |
| SOT-056 | Performance benchmark plan | docs/requirements/performance-benchmark-plan.md | TO BE CREATED | Load-test approval |

## 9. Evidence Priority

### P0 - Must Be Supplied Before Stage 1 Can Close

1. Cycle Count BRD and SRS.
2. Current and target Cycle Count workflow.
3. Recount and Approval rules.
4. Offline and synchronization rules.
5. Sanitized SKU sample.
6. Sanitized Location sample.
7. Sanitized Inventory sample.
8. Golden Sample and expected output.
9. User and Role Matrix.
10. Inventory source-of-truth decision.

### P1 - Required Before Related Module Implementation

1. Audit event requirements.
2. Dashboard KPI definitions.
3. Backup and Restore requirements.
4. Invalid and exception samples.
5. Device and browser matrix.
6. Network and server design.
7. Recovery targets.
8. Test Strategy.

### P2 - Required Before Pilot or Production

1. Deployment and rollback runbook.
2. Performance benchmark plan.
3. Training material.
4. Support and defect-escalation process.
5. Named approvers for Data, Warehouse Management and IT.

## 10. Public Repository Data Rules

The repository is public.

The following must never be committed:

- Production pb_data.
- Database files.
- Passwords.
- Tokens.
- API keys.
- Environment secrets.
- Employee personal information.
- Customer-confidential information.
- Supplier-confidential information.
- Real financial data.
- Confidential SOP documents.
- Unsanitized warehouse files.

Files placed under samples/sanitized must be reviewed before commit.

Replacing a name with another realistic name is not sufficient anonymization if the remaining data can identify a real person, customer, supplier, SKU, order or transaction.

## 11. Conflict Resolution

When two sources conflict:

1. Stop implementation.
2. Record the conflict.
3. Identify the controlling source and document version.
4. Request a decision from the Scope Owner.
5. Update the affected document through a new version.
6. Preserve the old version and decision history.
7. Resume only after written approval.

AI must not silently select the rule it considers more reasonable.

## 12. Stage 0 Blocking Verdict

Current verdict:

`STAGE 0 IN PROGRESS - SOURCE EVIDENCE INCOMPLETE`

The following work is permitted:

- Repository setup.
- Documentation inventory.
- Evidence collection.
- Sanitization planning.
- Requirement clarification.
- Non-functional platform planning.

The following work is not yet permitted:

- Final collection design.
- Final PocketBase migrations.
- Cycle Count business logic.
- Offline synchronization implementation.
- Recount and Approval implementation.
- Production permission rules.
- Production Release claim.


## 12.1 Controlling Golden Sample Decision

Effective from BRD/SRS v2.9, the sole controlling Golden Sample root is:

`tests/fixtures/cycle-count/golden/20260715182904Nguyen Duc Trong_Location Inventory_VN Ho Chi Minh DC.xls`

Locked technical profile:

- Actual format: Excel 2003 XML Spreadsheet with `.xls` extension.
- Worksheet: Table1.
- Data rows: 3926.
- Source columns: 21.
- Unique locations: 1966.
- Unique Goods ID: 643.
- Total Qty: 98804.0.
- File size: 5308206 bytes.
- MD5: `0d0edde76378720ba2eb9bc5f086fba7`.
- SHA-256: `1f2f117b22c17d15455d03d4c07908690490dda2eebbe28f4174cc7c6fb5b8f3`.

The former file:

`20260610114449Nguyen Duc Trong_Location Inventory_VN Ho Chi Minh DC.xls`

is historical reference only.

It must not be used to determine PASS or FAIL for:

- Golden Sample Regression.
- Inventory parser acceptance.
- Location Parser acceptance.
- Stock Snapshot reconciliation.
- Application Release Gate.

Replacing or renaming another file to the controlling filename is not acceptable. The SHA-256 checksum must match the locked value.

## 12.2 Current Evidence Verdict

The following evidence is verified:

- BRD/SRS v2.9 exists in the repository working tree.
- The controlling Golden Sample exists in the repository working tree.
- The Golden Sample SHA-256 checksum matches BRD/SRS v2.9.
- SKU and Location source files were received and technically reviewed outside GitHub.
- SKU and Location source files have not yet been uploaded to the repository.
- Application regression against the new Golden Sample has not yet been run.
- Full offline and synchronization requirements remain incomplete.

Current verdict:

`STAGE 0 IN PROGRESS - CONTROLLING SOURCES IDENTIFIED, EVIDENCE UPLOAD AND REGRESSION INCOMPLETE`


## 13. Change History

| Version | Date | Change | Approved By |
|---|---|---|---|
| 1.0 | 2026-07-16 | Initial Source-of-Truth Inventory created | DucTrong Nguyen |
| 1.1 | 2026-07-16 | Registered BRD/SRS v2.9 and the 20260715182904 inventory file as the controlling Golden Sample root; recorded source-file evidence status and retained offline/sync blocker | DucTrong Nguyen |
