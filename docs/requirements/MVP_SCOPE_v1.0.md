# Warehouse Suite — MVP Scope v1.0

## Document Control

- Status: APPROVED
- Version: 1.0
- Approved date: 2026-07-16
- Scope owner: DucTrong Nguyen
- Project: Warehouse Suite
- Roadmap stage: Stage 0 — Project Charter & Source-of-Truth

## 1. MVP Objective

The first Warehouse Suite MVP will validate one complete operational vertical slice:

Login and authorization → Master Data → Data Import → Cycle Count Online/Offline → Recount and Approval → Audit → Dashboard → Backup and Restore.

The MVP must prove that the selected architecture can operate safely before additional warehouse modules are developed.

## 2. Approved MVP Scope

The following capabilities are included in MVP v1.0:

1. Login and role-based authorization.
2. SKU Master.
3. Location Master.
4. SKU, Location, and Inventory import.
5. Cycle Count online.
6. Cycle Count offline and synchronization.
7. Recount and approval.
8. Audit Log.
9. Basic Cycle Count Dashboard.
10. Backup and Restore.

## 3. Out of Scope for MVP v1.0

The following capabilities remain in the Warehouse Suite roadmap but must not be implemented during MVP v1.0:

1. Inbound.
2. Outbound.
3. Inventory Transfer.
4. Inventory Adjustment.
5. Workforce Planner.
6. Productivity Management.
7. Overtime Management.
8. PnL Analysis.
9. Replenishment.
10. Location Utilization.
11. Inbound Space Planning.
12. SOP Management.
13. Local AI Chat.
14. Additional modules not explicitly approved in this document.

## 4. Scope Control Rules

- AI must not add a module to MVP without written approval from the scope owner.
- AI must not design database collections for out-of-scope modules unless required for an approved architectural dependency.
- AI must not implement speculative future requirements.
- Missing business rules must be reported as:

  `INSUFFICIENT EVIDENCE TO IMPLEMENT`

- New requirements must be recorded through a new version of this document.
- Previous version history must not be deleted or overwritten.
- Changes must be append-only and traceable.

## 5. MVP Success Criteria

MVP v1.0 is successful only when:

- All approved MVP modules are implemented.
- PocketBase permissions are enforced and tested.
- Cycle Count works online.
- Cycle Count offline operations survive browser close and network interruption.
- Synchronization does not lose or duplicate count records.
- Recount and approval rules work according to approved specifications.
- Audit records identify who performed each controlled action and when.
- Backup and Restore are tested successfully.
- Automated smoke tests pass.
- Scenario logic tests pass.
- Negative and exception tests pass.
- Test evidence is recorded.
- User Acceptance Testing is signed off.
- No unresolved critical defect remains.

## 6. Release Restriction

Until every MVP Release Gate has passed, the project must be labelled:

`CANDIDATE — RELEASE GATE NOT PASSED`

The application must not be presented as production-ready based only on completed UI pages or static checks.

## 7. Change History

| Version | Date | Change | Approved By |
|---|---|---|---|
| 1.0 | 2026-07-16 | Initial MVP scope approved with 10 capabilities | DucTrong Nguyen