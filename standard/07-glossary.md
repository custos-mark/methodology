# 7. Glossary

Terms used in this methodology, defined for the avoidance of ambiguity. Terms in **bold** within a definition are themselves defined elsewhere in this glossary.

---

**Annex III §3.** The section of the EU AI Act listing high-risk AI systems in the education and vocational-training domain. See [03-layer3-ai-act-compliance.md §3.1.2](03-layer3-ai-act-compliance.md).

**Audit.** A structured evaluation of a specific **product version** against a specific **methodology version**, performed by a **licensed auditor** working under a **lab**, resulting in a written report and (if successful) a **certificate**.

**Auditor.** An individual qualified and licensed by the **consortium** to perform audits against this methodology.

**Calibration curve.** A statistical mapping between a system's expressed confidence and the empirical correctness of its answers. See [01-layer1-technical-measurement.md §1.3.1](01-layer1-technical-measurement.md).

**Canary token.** A globally-unique synthetic value seeded into test accounts to trace whether personal data leaks outside its intended boundaries. See [02-layer2-data-protection.md §2.2.1](02-layer2-data-protection.md).

**Certificate.** A signed, public attestation that a specific **product version** passed a specific **audit** at a specific **tier** under a specific **methodology version**, valid for a defined period and bound to the **scope** (q.v.) declared by the vendor and confirmed by the audit.

**Child-Safe Excellence.** The highest **tier** of certification. See [06-tiers-scope-lifecycle.md §6.1.3](06-tiers-scope-lifecycle.md).

**Classification determination.** The lead auditor's written determination of how the AI Act classifies the system being audited (prohibited / high-risk / GPAI / transparency-only / out-of-scope). See [03-layer3-ai-act-compliance.md §3.1](03-layer3-ai-act-compliance.md).

**Consortium.** The non-profit standard-holder that owns this methodology, the brand, and the public registry. Distinct from the **lab**. See [../GOVERNANCE.md](../GOVERNANCE.md).

**Crisis scenarios.** A library of test scenarios in which a synthetic child signals suicidal ideation, self-harm, abuse, eating disorders, or other safety-critical states. Failure to handle any scenario correctly fails the entire audit. See [04-layer4-child-protection-pedagogy.md §4.3](04-layer4-child-protection-pedagogy.md).

**Cross-lingual fairness.** The requirement that quality metrics hold up across the languages the product is tested in, within a bounded language gap. See [01-layer1-technical-measurement.md §1.4](01-layer1-technical-measurement.md).

**DPIA.** Data Protection Impact Assessment per GDPR Art. 35.

**Dark patterns.** User-interface or interaction designs that manipulate users into actions against their interests. See [04-layer4-child-protection-pedagogy.md §4.4](04-layer4-child-protection-pedagogy.md).

**Defense success rate.** Proportion of prompt-injection scenarios in which the system maintained its constraints. See [01-layer1-technical-measurement.md §1.5.2](01-layer1-technical-measurement.md).

**EDPB.** European Data Protection Board.

**Education-Ready.** The default **tier** of certification for vendors selling to schools. See [06-tiers-scope-lifecycle.md §6.1.2](06-tiers-scope-lifecycle.md).

**Ethics and pedagogy council.** A standing body within the **consortium** that reviews Layer 4 findings at the Child-Safe Excellence tier and ratifies substantive methodology changes. See [../GOVERNANCE.md](../GOVERNANCE.md).

**Faithfulness.** The fraction of atomic claims in a model response that are supported by retrieved context or by the curriculum-aligned knowledge base. See [01-layer1-technical-measurement.md §1.1.1](01-layer1-technical-measurement.md).

**GDPR.** General Data Protection Regulation, EU Regulation 2016/679.

**GPAI.** General-Purpose AI Model, as defined in the EU AI Act.

**Hallucination rate.** Proportion of out-of-domain prompts where the system invents a plausible answer rather than declining or flagging uncertainty. See [01-layer1-technical-measurement.md §1.1.2](01-layer1-technical-measurement.md).

**High-risk.** An AI Act classification triggering Articles 9–15 conformity requirements. Many educational AI uses are high-risk under Annex III §3. See [03-layer3-ai-act-compliance.md](03-layer3-ai-act-compliance.md).

**Inclusivity modifier (+Inclusive).** A horizontal modifier added to a **tier** when the product passes the extended inclusivity tests for children with disabilities. See [04-layer4-child-protection-pedagogy.md §4.6](04-layer4-child-protection-pedagogy.md).

**Judge.** An LLM configured to label model outputs (e.g., classify hallucinations, decompose claims for faithfulness) under the methodology's judge specification. Validated against human auditor labels on a sampled subset.

**Lab.** The operating audit laboratory licensed by the **consortium** to perform audits. Structurally separated from the consortium. See [../GOVERNANCE.md](../GOVERNANCE.md).

**Language gap.** The maximum minus minimum of a metric across tested languages, expressed as a percentage. See [01-layer1-technical-measurement.md §1.4.1](01-layer1-technical-measurement.md).

**Layer.** One of the five top-level methodology divisions: Technical measurement (L1), Children's data protection (L2), AI Act and regulatory compliance (L3), Child protection and pedagogical ethics (L4), Operational maturity (L5).

**Major finding.** An audit finding that materially affects certification. Rectifiable within 30 days for a conditional pass at most tiers. See [02-layer2-data-protection.md §2.1.2](02-layer2-data-protection.md) for the example application.

**Methodology version.** The version of this document under which an audit was performed and a certificate issued. See [../README.md §Versioning](../README.md#versioning).

**Minor finding.** An audit finding noted for next-audit correction, not blocking current certification.

**Notified Body.** Under the AI Act, an accredited body designated to perform formal conformity assessments of high-risk AI systems. A long-term aspiration of the consortium's **lab**.

**Overconfidence rate.** Proportion of high-confidence answers from the system that are wrong. See [01-layer1-technical-measurement.md §1.3.1](01-layer1-technical-measurement.md).

**Product version.** The specific version of an AI product to which a **certificate** is bound.

**Prohibited practice.** A practice under AI Act Article 5 that is categorically forbidden. The methodology adds a small number of additional categorical disqualifiers specific to children. See [03-layer3-ai-act-compliance.md §3.3](03-layer3-ai-act-compliance.md) and [02-layer2-data-protection.md §2.3](02-layer2-data-protection.md).

**Refusal quality.** The auditor-rated quality of the system's response when it correctly declines an out-of-scope prompt. See [01-layer1-technical-measurement.md §1.3.2](01-layer1-technical-measurement.md).

**Revocation.** Permanent removal of a **certificate** with public registry entry. See [06-tiers-scope-lifecycle.md §6.3.5](06-tiers-scope-lifecycle.md).

**Robustness.** A product's resilience to non-clean inputs, including child-style prompts, prompt injection, and adversarial inputs. See [01-layer1-technical-measurement.md §1.5](01-layer1-technical-measurement.md).

**Scope.** The six anchors that bind a **certificate**: product, version, use-cases, languages, age range, operating countries. Country is a first-class anchor because the audit's substantive content varies by country (GDPR Art. 8 age-of-consent, AI Act enforcement, national curricula, national child-protection regimes); language alone does not capture this. See [06-tiers-scope-lifecycle.md §6.2](06-tiers-scope-lifecycle.md).

**Service card.** The public canonical artefact for a **certificate** on the registry. Exists in three forms (signed JSON, HTML rendering, PDF) that all resolve from the same canonical URI; the signed JSON is authoritative. Contains scope, tier, AI Act classification, per-layer results with metric scores, known limitations, audit history, status, and cryptographic verification handle. Schema specified in [09-service-card-template.md](09-service-card-template.md); transparency obligations in [06-tiers-scope-lifecycle.md §6.4 and §6.6](06-tiers-scope-lifecycle.md).

**Standards council.** The consortium body that ratifies methodology changes. Operates on consensus where possible, supermajority where not. See [../GOVERNANCE.md](../GOVERNANCE.md).

**Suspension.** A temporary pause on a **certificate** pending resolution of a defined cause. See [06-tiers-scope-lifecycle.md §6.3.4](06-tiers-scope-lifecycle.md).

**Tier.** One of three certification levels: Verified, Education-Ready, Child-Safe Excellence. See [06-tiers-scope-lifecycle.md §6.1](06-tiers-scope-lifecycle.md).

**Verified.** The entry **tier** of certification. See [06-tiers-scope-lifecycle.md §6.1.1](06-tiers-scope-lifecycle.md).

**Working draft.** A pre-1.0 version of the methodology, suitable for review and pilot use under explicit working-draft terms but not for production certification.
