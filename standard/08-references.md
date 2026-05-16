# 8. References

This document maps the methodology's normative content to the external instruments it references. Items marked **[N]** are normative — failure to conform breaks the methodology. Items marked **[I]** are informative — useful context but not directly checked.

References are versioned where applicable. Where an instrument is amended after this methodology version is published, the current methodology version remains tied to the version of the instrument cited; the next methodology release reflects the amendment.

---

## 8.1 EU instruments

### [N] EU AI Act — Regulation (EU) 2024/1689 of 13 June 2024

The principal regulatory anchor for [Layer 3](03-layer3-ai-act-compliance.md).

| Article / Annex | Methodology mapping |
|---|---|
| Art. 3 (Definitions) | Used throughout to identify what counts as an AI system and the operator roles |
| **Art. 5** (Prohibited practices) | §3.3 — categorical disqualifiers including emotion recognition in educational settings, exploitation of age-related vulnerabilities |
| **Art. 9** (Risk management) | §3.2.1 |
| **Art. 10** (Data and data governance) | §3.2.2 |
| **Art. 11** (Technical documentation) | §3.2.3 |
| **Art. 12** (Record-keeping) | §3.2.4 |
| **Art. 13** (Transparency to deployers / users) | §3.2.5 |
| **Art. 14** (Human oversight) | §3.2.6 and §3.4 |
| **Art. 15** (Accuracy, robustness, cybersecurity) | §3.2.7 |
| Art. 50 (Transparency for certain AI systems) | §3.1.1 — interaction-with-natural-persons transparency |
| Chapter V (GPAI) | §3.6 |
| **Annex III §3** (Education and vocational training high-risk classification) | §3.1.2 — gate for high-risk evaluation |
| Annex IV (Technical documentation requirements) | §3.2.3 detail |

Available at: https://eur-lex.europa.eu/eli/reg/2024/1689

### [N] GDPR — Regulation (EU) 2016/679

The principal regulatory anchor for [Layer 2](02-layer2-data-protection.md).

| Article | Methodology mapping |
|---|---|
| Art. 5 (Principles) | §2.2.2 (data minimization), §2.2.5 (storage limitation, integrity) |
| Art. 6 (Lawfulness) | §2.1.1 (legal-basis register) |
| Art. 7 (Conditions for consent) | §2.1.3 (consent quality, withdrawal) |
| **Art. 8** (Child's consent in information-society services) | §2.1.3 (age-of-consent table, national variation) |
| Art. 9 (Special categories) | §2.1.1 where special categories are processed |
| Art. 12 (Transparency to data subjects) | §2.1.1 (age-appropriate privacy notices) |
| Art. 13–14 (Information to be provided) | §2.1.1 |
| Art. 15 (Right of access) | §2.2.4 |
| Art. 17 (Right to erasure) | §2.2.3 |
| Art. 20 (Portability) | §2.2.4 |
| Art. 22 (Automated decision-making and profiling) | Cross-references Layer 3 §3.4 (human oversight) and §2.3 (profiling prohibition) |
| Art. 28 (Processor) | §2.1.3 (school-as-controller relationship) |
| Art. 32 (Security of processing) | §2.2.5 |
| **Art. 35** (DPIA) | §2.1.1 (DPIA requirement) |
| Art. 44–49 (Transfers) | §2.4 (cross-border handling) |

Available at: https://eur-lex.europa.eu/eli/reg/2016/679

### [N] EDPB Guidelines on consent and on children's data

Including:

- **EDPB Guidelines 05/2020 on consent** under GDPR
- **EDPB Guidelines on connected vehicles** (referenced for child-centred consent principles by analogy)
- **EDPB Article 29 Working Party Opinion 02/2009** on protection of children's personal data (Article 29 WP, since superseded by EDPB but still cited)
- **EDPB statements** on dark patterns and on age-verification

The methodology references EDPB guidance where it operationalizes GDPR requirements specifically for children.

### [I] EU AI Liability Directive / Product Liability Directive revision

Referenced for context where vendor liability for harms attributable to AI failures may interact with the methodology's findings.

### [I] Digital Services Act — Regulation (EU) 2022/2065

Referenced where the product falls within the DSA scope (intermediary services, very-large online platforms). Layer 4 §4.4 dark-patterns audit borrows from DSA Art. 25.

### [I] Digital Markets Act — Regulation (EU) 2022/1925

Referenced where the product is integrated with a designated gatekeeper.

---

## 8.2 ISO/IEC and related international standards

### [I] ISO/IEC 42001:2023 — Artificial Intelligence Management System

Organization-level management system requirements for AI. The methodology references 42001 controls in [Layer 5](05-layer5-operational-maturity.md) and parts of [Layer 3 §3.2.1](03-layer3-ai-act-compliance.md). 42001 alone is **insufficient** for the Custos Mark because it is organization-level; this methodology is product-level.

### [I] ISO/IEC 23894:2023 — Guidance on AI risk management

Referenced where risk management practices feed audit evidence for Layer 3 §3.2.1.

### [I] ISO/IEC 23053:2022 — Framework for AI systems using machine learning

Referenced for terminology.

### [I] ISO/IEC TR 24028 — Trustworthiness of AI

Referenced for trustworthiness terminology.

### [I] ISO/IEC 17021-1:2015 — Conformity assessment — Requirements for bodies providing audit and certification

The methodology's [GOVERNANCE.md](../GOVERNANCE.md) anticipates ISO/IEC 17021-1 accreditation for the operating lab. Not yet a normative requirement of the methodology itself, but a long-term operational target.

### [I] ISO/IEC 25010 / 25023 — Software product quality model and measurement

Referenced for terminology around quality attributes (functional suitability, reliability, usability, security, etc.).

---

## 8.3 Child-protection and education instruments

### [N] UN Convention on the Rights of the Child (UNCRC)

The methodology's [Layer 4](04-layer4-child-protection-pedagogy.md) is anchored in the UNCRC, especially:

- Art. 3 — best interests of the child
- Art. 12 — child's right to be heard
- Art. 13 — freedom of expression
- Art. 16 — protection of privacy
- Art. 17 — access to information
- Art. 19 — protection from violence
- Art. 28–29 — education

### [N] UN Committee on the Rights of the Child — General Comment No. 25 (2021) on children's rights in relation to the digital environment

The single most operative international guidance for the methodology's child-protection layer. Cited extensively in Layer 4 design.

Available at: https://www.ohchr.org/en/documents/general-comments-and-recommendations/general-comment-no-25-2021-childrens-rights-relation

### [I] Council of Europe Convention 108+ (modernized Convention for the protection of individuals with regard to the processing of personal data)

Referenced where the methodology operates beyond EU jurisdictions.

### [I] UNESCO Recommendation on the Ethics of Artificial Intelligence (2021)

Informative, particularly for cross-cultural perspectives on AI in education and the principle of human oversight.

### [I] UNESCO Guidance for generative AI in education and research (2023, updated 2024)

Informative for pedagogical principles in [Layer 4 §4.7](04-layer4-child-protection-pedagogy.md).

### [I] UK Children's Code (Age-Appropriate Design Code)

Informs Layer 2 and Layer 4 expectations for products operating in or marketed to UK users. Particularly its 15 standards including data minimisation, default privacy settings, profiling, nudge techniques, connected toys, and DPIAs.

### [I] California Age-Appropriate Design Code (AB 2273)

Informative reference for products operating in California or with California-resident users.

---

## 8.4 Pedagogical and child-development references

### [I] OECD reviews and frameworks on digital learning and AI in education

Used as informative context for Layer 4 §4.7 pedagogical justification, particularly OECD's work on AI literacy and on the use of AI in formative assessment.

### [I] European Reference Framework of Key Competences for Lifelong Learning (2018/C 189/01)

Informative reference for what constitutes a competence-aligned educational product.

### [I] DigComp framework

European Digital Competence Framework, referenced where AI literacy is relevant to product evaluation.

---

## 8.5 Accessibility instruments

### [N] EN 301 549 — Accessibility requirements for ICT products and services

The accessibility reference for the [+Inclusive modifier](04-layer4-child-protection-pedagogy.md#46-inclusivity-for-children-with-disabilities-inclusive-modifier) §4.6.1. Conformance with EN 301 549 at a level appropriate to the product type is required for the modifier.

### [N] WCAG 2.2 — Web Content Accessibility Guidelines

Referenced via EN 301 549; WCAG 2.2 AA is the practical floor for web-based educational products seeking +Inclusive.

### [I] EU Web Accessibility Directive — Directive (EU) 2016/2102

Informative for public-sector deployment context.

### [I] European Accessibility Act — Directive (EU) 2019/882

Informative for consumer-product accessibility implications.

---

## 8.6 Methodology-internal references

The following are this methodology's own internal references. They are normative for any audit performed under this methodology version.

- [README.md](../README.md) — overview and versioning policy
- [GOVERNANCE.md](../GOVERNANCE.md) — governance, conflicts of interest, auditor accreditation
- [CONTRIBUTING.md](../CONTRIBUTING.md) — methodology change process
- [CHANGELOG.md](../CHANGELOG.md) — version history
- [00-overview.md](00-overview.md) — normative language, scope, layer composition, audit shape
- [01-layer1-technical-measurement.md](01-layer1-technical-measurement.md) — Layer 1
- [02-layer2-data-protection.md](02-layer2-data-protection.md) — Layer 2
- [03-layer3-ai-act-compliance.md](03-layer3-ai-act-compliance.md) — Layer 3
- [04-layer4-child-protection-pedagogy.md](04-layer4-child-protection-pedagogy.md) — Layer 4
- [05-layer5-operational-maturity.md](05-layer5-operational-maturity.md) — Layer 5
- [06-tiers-scope-lifecycle.md](06-tiers-scope-lifecycle.md) — tier composition, scope binding, lifecycle
- [09-service-card-template.md](09-service-card-template.md) — canonical artefact schema for each certificate (signed JSON + HTML rendering); used by the public registry
- [07-glossary.md](07-glossary.md) — defined terms

---

## 8.7 Pending references

References to be added in future versions. Several of the items below have **operational homes** in the paired private repository (`custos-mark/custos-mark-private`), where they support the running of audits but are not publicly published for gameability reasons. A future point release of this public methodology will document the specification of each — what it is, how it is built, how it is validated — without publishing the underlying materials. The private-repo location is noted on each item where applicable.

- The methodology's **judge specification** — pinned LLM judge configuration, system prompts, and validation set — pending publication in a future point release. Operational home: `custos-mark-private/judges/`.
- The methodology's **scenario libraries** — Layer 4 §4.3 crisis scenarios, Layer 1 §1.5.2 jailbreak scenarios — partly public, partly held privately for gameability reasons; specifications for the public portions pending. Operational homes: `custos-mark-private/scenarios/crisis/` and `custos-mark-private/scenarios/jailbreak/`.
- The methodology's **child-prompt corpus** beyond the public seed examples — Layer 4 §4.1 working corpus required at Education-Ready and above (1000+ prompts) and Child-Safe Excellence (2000+) — pending publication of the public seed sample and construction methodology. Operational home: `custos-mark-private/corpus/child-prompts/`.
- The methodology's **curriculum reference set** — pending consolidation under [01-layer1-technical-measurement.md §1.1.3](01-layer1-technical-measurement.md).
- **National implementations of GDPR Art. 8** — the table in [02-layer2-data-protection.md §2.1.3](02-layer2-data-protection.md) is illustrative at v0.1; a comprehensive per-country table is pending.
- **National implementations of AI Act** as Member State implementing legislation is enacted.
- **Clinical citations for §4.3.3 harmful-technique prohibitions.** The methodology's prohibition of substitution-style self-harm suggestions (ice-cube tricks, rubber-band snapping) and method-mentions in suicide contexts has empirical grounding in clinical suicidology and self-harm research; specific citations to peer-reviewed sources are pending. Until they are pinned, the auditor's manual review under §4.3 relies on the council's clinical members' professional judgement.
