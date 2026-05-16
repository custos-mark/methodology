# 6. Tiers, scope, and certificate lifecycle

This document defines how the five layers compose into the three certification tiers, how a certificate's scope is bound, and how certificates evolve over their lifetime.

## 6.1 The three tiers

### 6.1.1 Verified

- **What it signals:** the product has passed the minimum threshold for school admission. Quality, privacy, and AI Act prohibitions have been checked at a baseline level; deeper pedagogy, child-protection, and operational depth have not.
- **Who it is for:** small vendors entering the market, products in pilot phase, narrow-scope products (e.g., a single-purpose vocabulary tutor) where a full evaluation would be disproportionate.
- **What is evaluated:** Layer 1 (subset), Layer 2 (subset), Layer 3 (Article 5 screen + classification + spot-checked high-risk items), Layer 5 (basic availability + versioning + notification). Layer 4 is **not** evaluated; vendors at Verified MAY NOT market Layer 4 properties.
- **Important — Annex III §3 override.** If the classification determination in [03-layer3-ai-act-compliance.md §3.1.2](03-layer3-ai-act-compliance.md) places the system in AI Act Annex III §3 (high-risk educational use), the full high-risk requirements in §3.2 apply **even at Verified**. The Verified tier reduces the depth of voluntary evaluation; it does not exempt the vendor from the regulatory layer that schools are themselves exposed to. Vendors whose systems fall under Annex III §3 SHOULD apply for Education-Ready or higher; auditors MUST decline to issue a Verified certificate that elides high-risk obligations the vendor will face under EU law.
- **Duration:** 2–3 weeks
- **Indicative price:** €3K–€5K
- **Validity:** 12 months
- **Renewal:** annual re-audit required

### 6.1.2 Education-Ready

- **What it signals:** the product meets the bar to be sold to schools and education networks. Quality, privacy, AI Act conformity, and operational maturity have been audited in full. Layer 4 child-protection elements have been evaluated; the crisis-scenario handling has been verified.
- **Who it is for:** the default tier for any EdTech vendor selling to schools as a primary customer.
- **What is evaluated:** Layers 1, 2, 3, and 5 in full; Layer 4 in subset (§4.1, §4.3, §4.4, §4.7 required; §4.2, §4.5, §4.6 strongly recommended).
- **Duration:** 6–8 weeks
- **Indicative price:** €15K–€25K
- **Validity:** 12 months
- **Renewal:** annual re-audit required

### 6.1.3 Child-Safe Excellence

- **What it signals:** the product has passed the strictest available evaluation. Ethics-council review, on-site audit, full cross-lingual fairness coverage, and rigorous Layer 4 evaluation including pedagogical empirical validation.
- **Who it is for:** ministries, large tenders, vendors positioning at the premium end.
- **What is evaluated:** all five layers in full; ethics-council review of Layer 4; on-site audit elements for Layer 2 and Layer 5.
- **Duration:** 3–4 months
- **Indicative price:** €40K–€80K
- **Validity:** 12 months
- **Renewal:** annual re-audit required

### 6.1.4 Tier matrix

| Layer | Verified | Education-Ready | Child-Safe Excellence |
|---|---|---|---|
| L1 Technical measurement | Subset, automated | Full, automated | Full, automated + manual review |
| L2 Children's data protection | Subset (docs + PII canary + erasure + prohibited uses) | Full | Full + on-site |
| L3 AI Act and regulatory | Art. 5 + classification + spot-checked high-risk | Full checklist | Full + extended |
| L4 Child protection and pedagogy | **Not required** | Subset (§4.1, §4.3, §4.4, §4.7) | Full + ethics-council review |
| L5 Operational maturity | Subset (§5.1, §5.2 docs, §5.4.3) | Full | Full + on-site |

### 6.1.5 The +Inclusive modifier

A horizontal modifier `+Inclusive` is granted in addition to any tier when the product passes the extended inclusivity tests in [04-layer4-child-protection-pedagogy.md §4.6](04-layer4-child-protection-pedagogy.md). It is recorded on the certificate and the service card.

The +Inclusive modifier expires with the underlying certificate and is renewed (or not) at re-audit.

## 6.2 Scope binding

Every certificate is bound to a specific:

- **Product** — a named, marketable AI service distinct from sibling products by the same vendor
- **Version or version range** — the version range is permitted only when the vendor documents change-control sufficient to demonstrate behavioural stability across the range; otherwise a specific version
- **Use-cases** — declared in writing by the vendor, evaluated against, and printed on the certificate
- **Languages** — only languages that were tested in the certification appear; languages not tested MUST NOT be marketed as covered
- **Age range** — the specific age band the certificate covers; ages outside the band are not covered
- **Operating countries** — the specific national markets in which the certificate applies; outside these countries the vendor MAY operate but MUST NOT represent the mark as covering that market

**The scope is non-negotiable.** A vendor MUST NOT represent the certificate as covering anything beyond these six anchors. Marketing material referencing the certificate MUST link to the public service card, where the precise scope is visible.

**Why country is a scope anchor, not metadata.** The audit's substantive content varies by country. National implementations of GDPR Article 8 (age-of-consent) diverge across member states: DE 16, IT 14, PL 13, NL 16, ES 14, FR 15 (with parental authorisation for 13–15) — see [02-layer2-data-protection.md §2.1.3](02-layer2-data-protection.md). AI Act enforcement timelines diverge across member states. Curriculum-alignment probes (§1.1.3) reference specific national curricula. National child-protection regimes apply differently in each country. Language and country are not interchangeable: Spanish-in-Spain is not Spanish-in-Mexico, German-in-Germany is not German-in-Austria, French-in-France is not French-in-Belgium. A product certified for a language but not bound to a country could be misrepresented across markets where the audit's substantive content was never run.

Examples of acceptable scope statements:

- "AI-powered math tutor for English-language users aged 11–14, operating in the UK and Ireland, covering the Cambridge Lower Secondary mathematics curriculum, on product versions 3.2.x"
- "Voice-enabled language learning companion for users aged 8–12, French and Spanish interfaces, foundational learning activities only, scoring excluded, operating in France, Belgium, and Spain"

Examples of unacceptable scope statements:

- "Our entire AI suite" (too broad; no specific product or version)
- "All ages" (specific age range required)
- "Multiple European languages" (specific languages required)
- "EU-wide" (specific operating countries required; "EU" is not a scope anchor — member-state law differs)

## 6.3 Lifecycle

### 6.3.1 Issuance

A certificate is issued when:

- All required layers for the requested tier pass
- The second-auditor review is complete
- The ethics-council review (Child-Safe Excellence) is complete with no unresolved concerns
- Audit fees are paid
- The vendor has executed the certification agreement, including the obligation to notify the consortium of incidents per [05-layer5-operational-maturity.md §5.4.3](05-layer5-operational-maturity.md)

The certificate is:

- A signed JSON document (specification aligned with W3C Verifiable Credentials)
- A corresponding PDF for human-readable use
- A public service-card entry in the registry
- An entry in the cryptographic registry's append-only log

### 6.3.2 Renewal

- **Validity period:** 12 months from issuance
- **Renewal trigger:** the vendor applies for renewal at least 60 days before expiry. The consortium does not automatically renew.
- **Renewal scope:** the methodology version used for renewal is the current published version, which may differ from the issuance version. Vendors may need to address new requirements.
- **Renewal audit:** typically lighter than initial audit (focused on changes since last audit and on currently-rotating private test sets) but never trivial.

### 6.3.3 Mandatory re-test

Independent of the annual renewal cycle, re-test is required when:

- The vendor performs a **major model update** (see Layer 5 §5.2.1). Re-test of Layers 1 and 4 within 60 days of deployment.
- The vendor performs a **material scope change** (new features, languages, age range, or removal of features). Scope-amendment audit before the change can be marketed under the certificate.
- The consortium issues a **methodology version bump** with a major version increment. Re-test at the next renewal; major-version certificates remain valid until expiry under the prior version, but the registry notes the version they were issued under.

### 6.3.4 Suspension

Suspension is a temporary state in which the certificate's claims are paused without revocation. Suspension is triggered by:

- An unresolved child-safety incident in production
- Failure to complete a required re-test within the stated window
- Material misrepresentation of scope in vendor marketing
- Non-payment of consortium fees
- Disclosure of an undisclosed conflict of interest in the vendor's auditor selection

Suspension is published on the service card with reason. The vendor has a defined window (typically 60 days) to address the suspension cause; failure to resolve becomes a revocation.

### 6.3.5 Revocation

Revocation removes the certificate permanently. The vendor MUST cease all use of the trust mark and the Custos Mark brand immediately. Triggers:

- Fraud (e.g., the vendor presented a test environment that did not match production)
- A fundamental child-safety failure
- Repeated major findings
- Failure to resolve a suspension within the cure period
- A material breach of the certification agreement

Revocation is public and permanent on the registry. The vendor may apply for a new certificate after a cooling-off period (typically 12 months) and a remediation review.

### 6.3.6 Voluntary withdrawal

A vendor may withdraw a certificate voluntarily, e.g., when discontinuing a product. The registry reflects "withdrawn" with the reason. Withdrawal does not retroactively erase prior public service-card history.

## 6.4 Public transparency obligations

Every certificate carries publicly:

- **Scope statement** — precise, machine-parseable
- **Layer-level results** — not a single composite score. Schools and parents read the layer detail; the consortium does not let vendors hide weak layers behind strong ones.
- **Known limitations** — explicit, drafted by the auditor, not removable by the vendor. A section that any vendor marketing would omit; that is why the consortium controls it.
- **Audit history** — initial certification, renewals, re-tests, scope amendments, suspensions, revocations
- **Cryptographic verification handle** — certificate ID, signature, public-key reference for offline verification
- **"Report a concern" channel** routed to the consortium

The transparency obligations are part of the certification agreement: by accepting certification, the vendor consents to this level of public disclosure.

## 6.5 Migration between tiers

A vendor MAY apply to **upgrade** a certificate to a higher tier mid-validity. The upgrade audit covers the additional layers and depths required at the new tier; existing layers in scope of the prior tier are not re-audited unless the methodology version has changed in the interim.

A vendor MAY **downgrade** a certificate mid-validity, e.g., for cost reasons. Downgrade is administrative; the registry records the change with date and reason.

A vendor MAY NOT claim a higher tier than currently certified at, regardless of past or pending certifications.

## 6.6 The certificate as canonical artefact

The public service card on the registry is the canonical artefact, not the PDF, not the badge, not the vendor's marketing copy. All vendor representations of the certificate MUST link to the service card. The certificate ID resolves to a single canonical URL that is durable across consortium infrastructure changes.

This is intentional: the certificate is **infrastructure**, not a marketing asset. Schools, parents, regulators, and journalists all read the same artefact when they verify a claim.
