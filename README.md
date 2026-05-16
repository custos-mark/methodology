# Custos — Methodology

> **Status: v0.1 — working draft. Public consultation is open.**
> This document defines what a third-party audit measures when a product applies for the Custos Mark — a vertical certification for AI services used in education and by minors.

The methodology is published openly so that vendors, schools, parents, regulators, researchers, and journalists can read, critique, and replicate it. Certificates may only be issued by auditors licensed by the Custos consortium, but the standard itself is free for anyone to read, fork, or build on.

---

## What this is

A precise, machine-verifiable, pedagogy-aware audit standard for AI products used in classrooms, by children at home, and inside EdTech platforms. It sits between three existing layers of governance:

- **ISO/IEC 42001** — organization-level AI management. Too abstract to inform school procurement.
- **EU AI Act conformity assessment** — mandatory and product-level, but limited to high-risk systems and accredited notified bodies.
- **Vendor self-declarations** — not independently verifiable.

Where these are silent, this methodology speaks: about a specific product, at a specific version, evaluated against published tests, by independent auditors operating under a non-profit consortium with pedagogical and child-safety expertise on its board.

## How to read it

Start with the [overview](standard/00-overview.md). It defines normative language (MUST / SHOULD / MAY), the five-layer structure, and how an audit applies the standard to a candidate product.

Then read the five layers:

1. [Layer 1 — Technical measurement](standard/01-layer1-technical-measurement.md) — automated probes against the vendor API: faithfulness, hallucination, age appropriateness, calibration, cross-lingual fairness, robustness.
2. [Layer 2 — Children's data protection](standard/02-layer2-data-protection.md) — GDPR + national child-data regimes, PII leakage testing, data minimization, right-to-erasure, prohibited uses.
3. [Layer 3 — AI Act and regulatory compliance](standard/03-layer3-ai-act-compliance.md) — Annex III classification, Articles 9–15 checklist, Article 5 prohibited practices, genuine human oversight.
4. [Layer 4 — Child protection and pedagogical ethics](standard/04-layer4-child-protection-pedagogy.md) — age-appropriate content handling, emotional-attachment guardrails, crisis-scenario handling, dark-patterns audit, bias, inclusivity, pedagogical justification.
5. [Layer 5 — Operational maturity](standard/05-layer5-operational-maturity.md) — availability, model versioning, school-facing documentation, complaints and incidents.

Then read how the layers compose into certificates: [Tiers, scope, lifecycle](standard/06-tiers-scope-lifecycle.md). Then how each certificate is published: [Service-card template](standard/09-service-card-template.md) — the canonical artefact schema that the public registry uses.

Reference material: [Glossary](standard/07-glossary.md) · [References](standard/08-references.md).

## Tiers at a glance

| Tier | Coverage | Audience |
|---|---|---|
| **Verified** | Layer 1 (subset) + Layer 2 (subset) | Minimum signal for school admission |
| **Education-Ready** | Layers 1, 2, 3, 5 — full | Default for selling to schools and networks |
| **Child-Safe Excellence** | All five layers, ethics-council review, on-site audit | Ministries, large tenders, premium positioning |

A horizontal modifier `+Inclusive` may be added when the product passes the extended inclusivity tests in Layer 4.

Every certificate is bound to a specific product, a specific version, a specific declared set of use-cases, languages, age range, and operating countries. A vendor cannot claim that "our entire product is certified" if only one feature was tested, and cannot represent the mark as covering a market the audit did not run for.

## Governance and license

- Methodology changes go through public consultation. See [GOVERNANCE.md](GOVERNANCE.md).
- Annual revision cycle, point releases as needed for new threats (e.g., new jailbreak classes).
- Public changelog with rationale for each change: [CHANGELOG.md](CHANGELOG.md).
- License: **Creative Commons Attribution 4.0 International (CC BY 4.0)**. See [LICENSE](LICENSE). Anyone may fork, replicate, or build on this work with attribution.

Only auditors licensed by the consortium may issue Custos Mark certificates. The license to read and reuse the methodology is separate from the licence to certify.

## How to contribute

The methodology is developed in the open. To propose a change, file an issue describing the problem you're solving, the evidence behind it, and the change you propose. Substantive contributions are credited in the changelog. See [CONTRIBUTING.md](CONTRIBUTING.md) for the consultation process, review cadence, and conflict-of-interest expectations.

## Versioning

This is **v0.1 — working draft**. It exists to be read, criticized, and improved before v1.0. Vendors should not yet apply for certification against it; pilot audits may be undertaken under explicit working-draft terms with the consortium. v1.0 will be released after the first cohort of pilot audits and public consultation.

Version compatibility:

- **Major versions** (1.0, 2.0) — methodology changes that may change a previously-passing product's outcome. Re-audit required at next renewal.
- **Minor versions** (1.1, 1.2) — clarifications, new optional probes, expanded language coverage. No re-audit triggered.
- **Patch versions** (1.0.1) — editorial corrections only. No substantive change.

A certificate names the methodology version it was issued under. Older certificates remain valid under their issuance version until expiry.

## Where this lives

This is the **public** repository (`custos-mark/methodology`). It is the canonical source for the methodology text, governance documents, public seed examples of scenarios and corpora, and the public judge specification. It is intended for public mirror to GitHub once the consortium and founding council are formally constituted. Until then, treat it as a pre-launch working draft maintained by the founding team.

A paired **private** repository (`custos-mark/custos-mark-private`) holds the operational artefacts that cannot be public without compromising the audits this methodology governs — the ≥50% rotating private portion of the crisis-scenario library required by [Layer 4 §4.3.2](standard/04-layer4-child-protection-pedagogy.md), the private jailbreak scenarios required by [Layer 1 §1.5](standard/01-layer1-technical-measurement.md), the working corpus of child prompts beyond the public seed samples, the auditor handbook, pinned judge configurations with their validation evidence, and lab-internal harness extensions. Access to the private repository is restricted to licensed auditors, council members and methodology maintainers, operating-lab staff, and authorised researchers under embargo; access is logged, and the policy is published in the private repo's ACCESS document.

The split is structural, not editorial: the public repo defines *what* is measured and *how*, the private repo holds the materials needed to *actually run* an audit without making the audit gameable. Reproducibility is preserved through the lab's immutable audit-artefact store — every probe used in every audit can be replayed, even though the underlying scenarios are not public.

---

*Custos is a working name pending EUIPO clearance and consortium incorporation. The consortium, operating lab, brand, and founding council are in formation; this document precedes them by design — the standard is meant to be readable and criticizable before institutional capture becomes possible.*
