# Refious Security — Audit Methodology & Report Template

Standardized audit deliverable structure and severity classification used internally by Refious Security.

This repository is the **public-facing contract**: it tells protocols, partners, and reviewers exactly what an audit report from Refious will look like, how findings are classified, and what methodology underpins the engagement.

The actual internal tooling, scanners, and detection logic are **not** in this repository and never will be.

---

## Contents

| File | Purpose |
|---|---|
| `TEMPLATE.md` | Canonical audit-report template. Copy-paste skeleton for every engagement. |
| `SEVERITY.md` | Severity classification rubric — impact × likelihood matrix. Aligned with Immunefi conventions. |
| `METHODOLOGY.md` | High-level engagement methodology — phases, deliverables, communication cadence. |

---

## How Refious Audits Are Structured

Every engagement produces:

1. **Scope agreement** — commit hash(es), file list, out-of-scope boundary, threat model assumptions, timeline.
2. **Audit report** — built from `TEMPLATE.md` with all findings classified per `SEVERITY.md`.
3. **Remediation review** — verification that each fix actually addresses the finding's root cause. Status (`Fixed` / `Acknowledged` / `Won't Fix` / `Mitigated`) is published in the final report.
4. **Disclosure** — public publication in [`refious-security/audits`](https://github.com/refious-security/audits) once the mitigation window closes.

---

## Quality Bar

- **Every finding has a reproducible impact.** No "this *could* be exploited under speculative conditions" findings ship as High or Critical.
- **Every recommendation is implementable.** No abstract advice; concrete code-level or architecture-level guidance only.
- **Every severity is justified in the report.** Impact and likelihood are stated explicitly per the rubric — no opaque rating.
- **No false-positive padding.** Refious does not inflate Informational counts to make a report look thorough.

---

## Adopting These Templates

These documents are public so protocols and partners know what to expect. Other firms are welcome to fork and adapt for their own engagements; attribution is appreciated but not required.

For private engagements with Refious Security, contact the operations desk listed on the [organization profile](https://github.com/refious-security).

---

> A good audit report is one the protocol team can hand to their next investor and have them understand the risk surface in twenty minutes.
