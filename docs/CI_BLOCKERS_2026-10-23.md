# CI/security acceptance blockers — 2026-10-23

Canonical component: QMOOSA-0650; approved family: Payment Reality Gate & Finality Verification.

The former workflow referenced invalid `actions/checkout@4` and `github/codeql-action/*@3` action tags, selected JavaScript/TypeScript CodeQL for a Python-only test repository, and echoed `100/100 VERIFIED` without running tests.

The two existing test files have the same malformed source blob (`c41122bd4eb66a7a13ee20b21a9194f1b1cacf88`) and fail Python compilation. This review branch intentionally runs syntax validation and pytest **fail-closed** and uses CodeQL Python. Do not remove test execution to obtain a green status.

Acceptance requirements:
1. Replace malformed tests with valid implementation-coupled tests, including adversarial authorization, replay/idempotency and boundary cases appropriate to the approved protocol.
2. Provide actual implementation evidence, not README/architecture scaffolding or mocks.
3. Obtain successful current-HEAD tests and CodeQL, review dependency/security findings, and require independent security acceptance before merge or release.

This draft does not claim FIPS validation, production readiness, security approval, deployment or a passing test suite.
