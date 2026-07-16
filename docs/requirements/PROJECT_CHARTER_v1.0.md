# Warehouse Suite - Project Charter v1.0

## Document Control

- Status: APPROVED WITH ITEMS TO BE CONFIRMED
- Version: 1.0
- Approved date: 2026-07-16
- Scope owner: DucTrong Nguyen
- Project: Warehouse Suite
- Roadmap stage: Stage 0 - Project Charter and Source-of-Truth
- Related document: docs/requirements/MVP_SCOPE_v1.0.md

## 1. Project Objective

Warehouse Suite MVP will validate a complete Cycle Count operational vertical slice:

Login and authorization -> Master Data -> Data Import -> Cycle Count Online and Offline -> Recount and Approval -> Audit -> Dashboard -> Backup and Restore.

The MVP must demonstrate that the selected architecture can operate safely before additional warehouse modules are developed.

## 2. Deployment Location

Initial deployment location:

- HCM DC warehouse.

Pilot approach:

- Start with one selected zone or operational area.
- Do not deploy across the entire warehouse on the first day.
- Expand to other zones only after the pilot passes all required gates.

Item to be confirmed:

- Final pilot zone.

## 3. Target Users

Initial planning assumptions:

- 1 System Administrator.
- 2 to 3 Supervisors.
- Up to 20 Counter or Operator users working concurrently.
- 2 to 3 Approvers.
- 3 to 5 Viewers.

A user may hold more than one approved role.

Final user quantities and role assignments must be confirmed before the Permission Matrix is approved.

## 4. Preliminary Role Definitions

### System Administrator

- Configure the system.
- Manage users and roles.
- Manage approved settings.
- Perform or coordinate backup and restore.
- Review system health and technical logs.

### Supervisor

- Create Cycle Count plans and tasks.
- Assign tasks.
- Monitor progress.
- Review exceptions.
- Request recount where authorized.

### Counter or Operator

- View assigned tasks.
- Perform Cycle Count.
- Save results online or offline.
- Synchronize pending results.
- Respond to approved recount tasks.

### Approver

- Review variances.
- Request recount where authorized.
- Approve or reject results according to approved rules.
- Record the reason for controlled decisions.

### Viewer

- View authorized dashboards and reports.
- Must not create, update, approve, or delete controlled records.

## 5. Problems to Be Solved

The MVP must address the following problems:

1. Cycle Count planning and task assignment depend heavily on manual work.

2. Count results may be recorded using paper or Excel, resulting in:

   - Duplicate data entry.
   - Slow consolidation.
   - Weak version control.
   - Risk of missing or incorrect records.

3. Current processes make it difficult to track:

   - Tasks not started.
   - Tasks in progress.
   - Tasks completed.
   - Tasks waiting for recount.
   - Tasks waiting for approval.

4. Mobile devices may lose Wi-Fi connectivity inside the warehouse:

   - Pending results must be stored offline.
   - Closing and reopening the browser must not lose pending data.
   - Reconnection must not create duplicate records.

5. Variance, recount, and approval workflows must be standardized.

6. Controlled actions require a complete Audit Log containing:

   - User.
   - Action.
   - Timestamp.
   - Affected record.
   - Result.
   - Approved before-and-after values where applicable.
   - Related session or device information where available.

7. Consolidation and dashboard preparation currently require unnecessary manual effort.

8. Backup and Restore procedures for Cycle Count data have not yet been validated.

## 6. Technical Success Criteria

### Data Integrity

- Lost valid records: 0.
- Duplicate records caused by retry or reconnection: 0.
- Every operation must have a visible status.
- Failed operations must not be silently discarded.
- Dashboard totals must reconcile with approved source records.
- Unexplained reconciliation differences are not acceptable.

### Offline and Synchronization

- Pending offline data must survive browser close and reopen.
- Offline operations must be maintained in a controlled queue.
- Retry operations must be idempotent.
- Conflict scenarios must follow approved conflict-resolution rules.
- All mandatory offline and recovery scenarios must pass.

### Authorization

- Users must not perform actions outside approved permissions.
- Hiding a button is not considered authorization.
- PocketBase API rules must enforce authorization.
- All mandatory permission negative tests must pass.

### Audit

All controlled actions must record:

- User.
- Timestamp.
- Action.
- Record reference.
- Result.
- Reason where required.

Historical audit records must not be overwritten or deleted through normal module operations.

### Backup and Restore

- A backup must be created successfully.
- Restore must be executed successfully in a test environment.
- Restored data must pass reconciliation tests.
- Backup existence alone is not evidence that Restore works.

## 7. Initial Performance Targets

The following targets are provisional and must be validated on the real server and network:

- Create 200 Cycle Count tasks in under 2 minutes.
- Open a mobile task list in under 3 seconds under normal LAN conditions.
- Save an online count result in under 2 seconds.
- Synchronize one device's pending queue within 5 minutes after connectivity returns.
- Support 20 mobile users performing Cycle Count concurrently without lost or duplicated records.
- Load the basic Cycle Count Dashboard in under 5 seconds.

Performance targets may be revised only with documented test evidence and approval.

## 8. Operational KPI Baseline

The following operational KPIs require baseline measurement during the pilot:

- Task completion rate.
- Average task completion time.
- Recount rate.
- Time from variance detection to approval.
- Time required to prepare Cycle Count reports.
- Reduction in manual consolidation effort.

Initial task completion target:

- At least 98 percent, subject to baseline review.

Unknown values must remain marked as:

TO BE CONFIRMED THROUGH PILOT

AI must not invent baseline values.

## 9. Approval Responsibilities

### Business Requirements Approval

- Scope Owner: DucTrong Nguyen.
- Warehouse Manager where required by internal policy.

### Data Structure Approval

- Scope Owner.
- Inventory Control or Data Owner.
- Final named approver: TO BE CONFIRMED.

### User Acceptance Testing Approval

- Scope Owner.
- Supervisor representative.
- Cycle Count user representative.
- Warehouse Manager where applicable.

### Production Release Approval

- Scope Owner.
- Warehouse Manager.
- IT or infrastructure owner where company resources are used.

AI has no authority to approve business requirements, User Acceptance Testing, or Production Release.

Completion of source code does not constitute Release approval.

## 10. Initial Deployment Model

Approved initial model:

- One designated Windows machine operates as the internal server.
- User computers and mobile devices connect through warehouse LAN or Wi-Fi.
- Normal operation must not depend on Internet access.
- PocketBase provides the internal API, authentication, data storage, and static hosting.

Technical conditions:

- The server must have a fixed internal IP address.
- Frontend libraries must be stored locally and pinned to approved versions.
- Runtime must not depend on CDN resources.
- Active pb_data must remain on the designated server.
- Active database files must not run from OneDrive, Google Drive, or a network share.
- Backups must be stored separately from the active database.
- External remote access is outside MVP scope.
- Local AI must not run on the MVP server unless a separate resource test is approved.

## 11. Scope and Change Control

- MVP scope is controlled by MVP_SCOPE_v1.0.md.
- AI must not add modules without written approval.
- AI must not invent missing business rules.
- Missing evidence must be reported as:

  INSUFFICIENT EVIDENCE TO IMPLEMENT

- Scope changes require a new document version.
- Version history is append-only.
- Previous approvals and test evidence must not be deleted.

## 12. Release Restriction

Until all required gates pass, the product must be labelled:

CANDIDATE - RELEASE GATE NOT PASSED

Completed user-interface pages, static checks, or successful login do not prove production readiness.

## 13. Items to Be Confirmed

The following information remains open:

1. Final pilot zone.
2. Final number of users by role.
3. Named Inventory Control or Data Owner.
4. Named Warehouse Manager approver.
5. Named IT or infrastructure approver.
6. Current operational KPI baselines.
7. Final device and browser test matrix.
8. Final backup retention and recovery targets.

These open items do not authorize AI to make assumptions.

## 14. Stage 0 Exit Conditions

Stage 0 cannot be closed until:

- MVP scope is approved.
- Project Charter is approved.
- Available source-of-truth documents are inventoried.
- Missing evidence is listed.
- All P0 information is supplied or formally accepted as an open blocker.
- Scope Owner approves Stage 0 completion.

## 15. Change History

| Version | Date | Change | Approved By |
|---|---|---|---|
| 1.0 | 2026-07-16 | Initial Project Charter approved with identified items to be confirmed | DucTrong Nguyen |
