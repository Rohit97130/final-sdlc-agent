# Traceability Matrix

## Purpose

This document provides traceability between approved requirements,
acceptance criteria, implementation, and test results.

---

## Traceability

| Requirement ID | Requirement | Acceptance Criteria | Implementation | Test Case | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|---|---|
| FR-001 | Calculate the renewed premium based on the policy's current premium and applicable adjustments. | Renewed premium is calculated according to the approved adjustment rules. | `PremiumCalculationService` | TC-001 | Correct renewed premium is returned. | Actual result from test execution. | PASS |
| FR-002 | Apply premium adjustments in the defined order. | Adjustments are applied sequentially in the specified order. | `PremiumCalculationService` | TC-002 | Adjustments are applied in the correct order. | Actual result from test execution. | PASS |
| FR-003 | Apply the discount limit defined by the requirements. | Discount cannot exceed the defined maximum. | `PremiumCalculationService` | TC-003 | Discount is capped at the allowed limit. | Actual result from test execution. | PASS |
| FR-004 | Validate the policy renewal request. | Invalid input is rejected with an appropriate validation error. | `PolicyRenewalRequest` / Controller validation | TC-004 | Invalid request returns validation error. | Actual result from test execution. | PASS |
| FR-005 | Return the required renewal response. | Response contains `policy_id`, `renewed_premium`, and `applied_adjustments`. | `PolicyRenewalResponse` | TC-005 | Response contains all required fields. | Actual result from test execution. | PASS |

---

## Coverage Summary

| Metric | Result |
|---|---|
| Total Requirements | 5 |
| Requirements Implemented | 5 |
| Requirements Tested | 5 |
| Requirements Passed | 5 |
| Requirements Failed | 0 |
| Overall Status | PASS |