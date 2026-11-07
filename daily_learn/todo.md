# Repository Improvement Backlog

## 1. financial_tracker

### High Priority
- [ ] **Enforce organization-member consistency in financial events**
  - Ensure that a financial event cannot reference an organization and a member belonging to a different organization.
  - Consider composite foreign keys to enforce relational consistency.
  - Add positive and negative constraint tests.

- [ ] **Add database constraint and ETL reliability tests**
  - Test required fields, foreign keys, duplicate prevention, and financial event corrections.
  - Ensure ETL reruns do not create unintended duplicate records.
  - Document how to execute the tests.

### Medium Priority
- [ ] **Standardize date and timestamp semantics**
  - Define the distinction between business dates (`date`) and system timestamps (`timestamptz`).
  - Keep `event_date` as `date` if time-of-day is not required.
  - Align DDL and README documentation.
  - Fix the `creted_at` typo in `financial_platform`.

- [ ] **Define one-to-one cardinality for user profiles**
  - Confirm whether each authentication account should have exactly one profile.
  - If so, add a UNIQUE constraint to `user_profiles.user_auth_id`.
  - Add a test to prevent duplicate profiles.

---

## 2. website_pengelolaan_tugas_kuliah_bersama

### High Priority
- [ ] **Resolve database engine target and align role provisioning**
  - Confirm whether the project targets TiDB/MySQL or PostgreSQL.
  - Rewrite role provisioning scripts according to the selected database engine.
  - Remove empty or hard-coded credentials.
  - Implement least-privilege access control.
  - Test the scripts against the declared database engine.

- [ ] **Enforce relational consistency across academic and group data**
  - Ensure faculties belong to their referenced universities.
  - Ensure study programs belong to their referenced faculties.
  - Prevent duplicate group memberships.
  - Ensure task members belong to the task's group.
  - Validate course consistency between groups, tasks, and subtasks.
  - Add database constraints and validation tests.

- [ ] **Connect login form to backend authentication**
  - Define the authentication API contract.
  - Connect `Login.jsx` to the backend endpoint.
  - Implement input validation and loading states.
  - Handle successful login, invalid credentials, and network errors.
  - Ensure credentials and tokens are not exposed.

### Medium Priority
- [ ] **Define authentication lifecycle and audit-field behavior**
  - Implement password reset token expiration and single-use behavior.
  - Define secure password hashing and verification.
  - Automate `updated_at` updates.
  - Integrate environment variables or a secret manager.
  - Document implemented security mechanisms and remaining limitations.
