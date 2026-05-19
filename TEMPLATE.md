# Audit Report — `<Protocol Name>`

**Audit ID:** R-YYYYMM-NN
**Conducted by:** Refious Security
**Engagement period:** YYYY-MM-DD — YYYY-MM-DD
**Report date:** YYYY-MM-DD
**Report version:** 1.0

---

## 1. Engagement Summary

### 1.1 Scope

- **Repository:** `<owner/repo>`
- **Commit (initial review):** `<commit hash>`
- **Commit (remediation review):** `<commit hash>`
- **Files in scope:**
  - `<path/to/Contract1.sol>`
  - `<path/to/Contract2.sol>`
  - ...
- **Explicitly out of scope:**
  - `<path/to/ExcludedFile.sol>` — reason
  - External dependencies — reviewed only for trust assumptions, not implementation

### 1.2 Threat Model

<Describe the protocol's intended threat model. Who can do what, to whom, under which assumptions. Privileged roles. External trust dependencies. Composability exposure. This anchors every finding's relevance.>

### 1.3 Methodology

This engagement followed [`METHODOLOGY.md`](https://github.com/refious-security/audit-template/blob/main/METHODOLOGY.md):

1. Scoping and threat-modeling.
2. Architecture review.
3. Manual code review.
4. Adversarial analysis.
5. Finding validation (reproduction + classification).
6. Reporting.
7. Remediation review.

Severity is classified per [`SEVERITY.md`](https://github.com/refious-security/audit-template/blob/main/SEVERITY.md).

### 1.4 Team

<Anonymous contributor count or named reviewers per client preference.>

---

## 2. Findings Summary

| ID | Severity | Title | Status |
|---|---|---|---|
| R-001 | Critical | <title> | Fixed |
| R-002 | High | <title> | Fixed |
| R-003 | High | <title> | Acknowledged |
| R-004 | Medium | <title> | Fixed |
| R-005 | Medium | <title> | Won't Fix |
| R-006 | Low | <title> | Mitigated |
| R-007 | Informational | <title> | Acknowledged |

**Totals:** Critical: N · High: N · Medium: N · Low: N · Informational: N

---

## 3. Findings (Detail)

### R-001 — `<Finding Title>`

**Severity:** Critical
**Status:** Fixed (commit `<hash>`)
**Location:** `path/to/Contract.sol`, function `<name>`, lines `<L1–L2>`
**Impact:** High
**Likelihood:** High

#### Description

<What the issue is. Plain prose. One or two paragraphs.>

#### Root Cause

<Why the issue exists. Reference the specific code construct. Quote the relevant lines.>

```solidity
// path/to/Contract.sol:LXX
<offending code>
```

#### Impact

<What can an attacker actually do. Quantified where possible (funds at risk, time to exploit, attacker capability required).>

#### Reproduction

<Step-by-step exploit walkthrough OR foundry test reference OR transaction trace. Every Critical / High finding has a reproducible path.>

```solidity
// reproduction snippet or PoC reference
```

#### Recommendation

<Concrete fix. Code-level where appropriate. Architectural where required.>

#### Fix Verification

<What the fix commit changed and why it addresses the root cause, not just the surface symptom. Reference the remediation commit hash.>

---

### R-002 — `<Finding Title>`

[Same structure as R-001.]

---

<...repeat for each finding...>

---

## 4. Out-of-Scope Acknowledgements

The following were reviewed for trust-assumption purposes but not audited at the implementation level:

- `<dependency>` — reason and assumption being relied upon.

---

## 5. Architecture Notes

<Optional. High-level architecture summary, control-flow diagrams, invariant catalogue. Use when the system is complex enough that a reviewer of the report benefits from the orientation.>

---

## 6. Tools and Techniques

- Manual code review (primary).
- Foundry / Hardhat-based test harnesses for finding reproduction.
- Static analysis as a supplementary signal, not a finding source.
- Adversarial threat modeling.

---

## 7. Disclaimer

This report describes the security posture of the audited code at the specific commit hashes listed in §1.1. Code changes outside that scope, deployment-time configuration, off-chain operational practices, and third-party dependencies not under audit are not covered.

A clean audit is not a guarantee of safety. It is a high-confidence statement that, within the scope and time bounds of the engagement, the reviewers found no further issues.

---

**Signed:**
Refious Security
`<contact handle>`
