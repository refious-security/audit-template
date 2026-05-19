# Severity Classification — Refious Security

Refious Security classifies every finding on a five-level severity scale derived from the **impact × likelihood** matrix below. The classification is reproducible: any reviewer reading the finding should be able to verify the severity against the rubric.

---

## Severity Levels

| Level | Definition |
|---|---|
| **Critical** | Direct loss of user funds, permanent freezing of significant funds, full protocol compromise, or unauthorized control of the protocol with no recovery path. Realistically exploitable. |
| **High** | Theft or freezing of significant funds, severe smart contract logic failures, or major access-control breakdowns. May require specific market conditions or moderate attacker capability. |
| **Medium** | Theft or freezing of limited funds, temporary protocol disruption, manipulation of secondary mechanics, or exploit chains requiring multiple non-trivial preconditions. |
| **Low** | Minor protocol misbehavior, edge-case failures, non-fund-impacting logic issues, or findings with significant mitigating factors. |
| **Informational** | Best-practice violations, code quality issues, gas optimizations, documentation drift. No security impact. |

---

## Impact × Likelihood Matrix

|                  | **High Likelihood**       | **Medium Likelihood**    | **Low Likelihood**       |
|------------------|---------------------------|--------------------------|--------------------------|
| **High Impact**  | Critical                  | High                     | Medium                   |
| **Medium Impact**| High                      | Medium                   | Low                      |
| **Low Impact**   | Medium                    | Low                      | Informational            |

The matrix is a **starting point**, not a verdict. Final classification accounts for:

- Realism of attacker capability under live mainnet conditions.
- Cost-of-exploit vs reward.
- Recovery and rollback options.
- Whether the vulnerability is reachable from an external entry point.

---

## Impact — How Bad Is It If Exploited

**High**
- Loss or freezing of significant user or protocol funds.
- Permanent denial of core protocol functionality.
- Unauthorized control of admin / governance / upgrade paths.
- Cross-chain settlement breaks.

**Medium**
- Loss or freezing of limited funds (bounded by collateral, fees, or specific deposits).
- Temporary protocol disruption recoverable by governance.
- Manipulation of secondary mechanics (oracle skew within bounds, partial liquidity drain).
- Breakage of an invariant whose violation reduces system safety margins.

**Low**
- Misbehavior contained to a single user account with no propagation.
- Edge-case logic failures triggerable only under hostile self-action.
- Non-fund-impacting griefing.
- Failures recoverable via standard administrative paths.

---

## Likelihood — How Hard Is It To Trigger

**High**
- Exploitable directly by any externally owned account.
- No special market conditions, role, or capital required.
- Single transaction.

**Medium**
- Requires a specific role (other user, validator, keeper), specific market conditions (price gap, low liquidity, validator overlap), or a multi-step setup.
- Flash-loan-enabled flows with no other obstacles count as Medium-to-High depending on capital threshold and gas economics.

**Low**
- Requires a compromised privileged role.
- Requires improbable cross-protocol coordination.
- Requires specific block-position assumptions (chain reorganizations of unusual depth).

---

## Boundary Cases

**Findings that DO escalate to Critical:**
- Reachable infinite mint / unauthorized burn.
- Bypass of withdrawal limits or vesting schedules.
- Signature replay across chain or domain boundaries.
- Re-initialization of upgradeable contracts.

**Findings that do NOT typically escalate above Medium:**
- Reentrancy on functions with no fund movement.
- Front-running where the user has a stop-loss mechanism available.
- Issues requiring already-compromised governance keys.

**Findings that are Informational:**
- Missing event emissions on non-fund-moving paths.
- Typos in revert messages.
- Inefficient storage layouts that don't affect security.
- Code style deviations.

---

## Severity Inflation Is A Failure Mode

Severity inflation — labeling a Low as a High to make the report look impactful — is a credibility killer. Refious explicitly avoids it. A short report with three correctly-classified findings outweighs a long report with ten inflated ones.

The opposite is also true: undercalling severity to protect a relationship is a violation of the audit's purpose. We don't do that either.

---

> Severity is a claim about impact and likelihood. It must survive cross-examination by a competent reviewer reading nothing but the rubric and the finding.
