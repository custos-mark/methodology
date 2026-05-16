# 0. Overview

> **Custos Methodology, v0.1 — working draft.**
> Status: pre-release. Not yet for production certification.

This is the overview of the standard. It defines what the methodology covers, the language it uses, how the five layers compose, and how an audit applies them to a candidate product.

## 0.1 Purpose

The methodology specifies what a third-party audit measures when an AI product applies for the Custos Mark. Its purpose is to give:

- **Schools and teachers** a procurement-grade signal of fitness for use with students of stated ages.
- **Parents** a verifiable safety guarantee for tools their child uses.
- **Vendors** a clear, public, predictable bar to meet — with no moving goalposts and no hidden criteria.
- **Regulators** evidence of due diligence that complements formal AI Act conformity assessment.
- **Researchers and journalists** a public record they can audit, criticise, and hold the consortium accountable against.

## 0.2 Scope

The methodology applies to AI services used by minors in educational contexts, including but not limited to:

- AI tutors, homework helpers, learning companions
- AI features inside Learning Management Systems and Student Information Systems
- AI-assisted assessment, grading, and feedback systems
- AI tools used by teachers that produce content delivered to students
- AI tools used by parents to support their child's learning
- AI services targeted at children in informal-learning settings (libraries, museums, summer programmes) where educational intent is part of the product positioning

Out of scope at v0.1 (may be added in later versions):

- Pure infrastructure (model APIs without an educational product wrapper)
- Adult education and corporate training without minors in scope
- AI features inside school administrative software that does not interact with students
- Hardware-only products

A vendor applying for certification declares the scope. The audit binds the certificate to that declared scope and tests against it. Out-of-scope features remain uncertified and MUST NOT be marketed as covered.

## 0.3 Normative language

The methodology uses normative keywords in the sense of [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) and [RFC 8174](https://www.rfc-editor.org/rfc/rfc8174):

- **MUST**, **MUST NOT**, **REQUIRED** — absolute requirements. A product failing a MUST requirement at a given tier cannot receive that tier.
- **SHOULD**, **SHOULD NOT**, **RECOMMENDED** — strong expectations. Deviation requires the vendor to provide a written justification, which becomes part of the certificate's "known limitations" section.
- **MAY**, **OPTIONAL** — discretionary. Choices a vendor or auditor may make without affecting outcome.

When these keywords are not capitalized, they carry their ordinary English meaning.

## 0.4 Five-layer structure

Audits evaluate five layers. Each layer carries its own pass criteria per tier. A certificate is issued only when every required layer passes at the requested tier.

| Layer | Subject | Primary methods |
|---|---|---|
| 1. Technical measurement | Whether the system gives correct, age-appropriate, honest, robust answers | Automated probes against the vendor API |
| 2. Children's data protection | GDPR-grade handling of student, teacher, and parent data | Documentation review + technical probes |
| 3. AI Act and regulatory compliance | Conformity with EU AI Act and national child-protection rules | Documentation review + checklist |
| 4. Child protection and pedagogical ethics | Behaviour in safety-critical and developmentally-sensitive situations | Manual review + ethics-council oversight |
| 5. Operational maturity | School-ready operations: availability, versioning, documentation, complaints | Documentation review + interviews |

The layers are not interchangeable. A product cannot compensate for failing Layer 4 by excelling at Layer 1.

## 0.5 Tier model in one paragraph

Three tiers exist: **Verified** (minimum signal for school admission), **Education-Ready** (default for selling to schools and networks), and **Child-Safe Excellence** (ministry, large-tender, premium positioning). The tiers differ in which layers are evaluated, in test-set sizes, in threshold strictness, and in whether ethics-council and on-site review are required. The full tier matrix is in [06-tiers-scope-lifecycle.md](06-tiers-scope-lifecycle.md).

A horizontal modifier `+Inclusive` may be added when the product passes the extended inclusivity tests in [04-layer4-child-protection-pedagogy.md §4.6](04-layer4-child-protection-pedagogy.md).

## 0.6 Scope binding

Every certificate binds to:

- A specific **product** (a named, marketable AI service)
- A specific **version** or version range (with documented change-control)
- A specific declared **set of use-cases** (e.g., "Q&A tutor for biology, grades 7–9")
- A specific tested set of **languages**
- A specific claimed **age range**
- A specific set of **operating countries**

These six anchors define what the certificate certifies. A vendor MUST NOT represent the certificate as covering anything beyond them. Country is a scope anchor in its own right because the audit's substantive content varies by country: national implementations of GDPR Article 8 (age-of-consent) differ across member states, AI Act enforcement timelines differ across member states, and curriculum alignment is country-specific. Language and country are not interchangeable — Spanish in Spain is not Spanish in Mexico; German in Germany is not German in Austria.

## 0.7 How an audit applies this document

Every audit follows the same shape, regardless of tier:

1. **Intake.** Vendor submits the application with scope declaration, technical documentation, DPIA, pedagogical methodology document, and API access for the test environment.
2. **Classification gate.** The audit determines AI Act risk category (Annex III §3 or not). Some classifications trigger Layer 3 elements regardless of requested tier — see [03-layer3-ai-act-compliance.md](03-layer3-ai-act-compliance.md).
3. **Prohibited-practice screen.** The audit checks for AI Act Article 5 prohibited practices (see [03-layer3-ai-act-compliance.md §3.3](03-layer3-ai-act-compliance.md)) and the consortium's own categorical disqualifiers in [02-layer2-data-protection.md §2.3](02-layer2-data-protection.md) — e.g., training foundation models on children's data without explicit informed consent; profiling of minors for advertising. Failure at this gate stops the audit before any layer evaluation is performed; no certificate at any tier may be issued.
4. **Layer evaluation.** The required layers for the requested tier are evaluated in parallel where the team allows. Each layer produces a per-metric result and a layer-level pass/fail.
5. **Second-auditor review.** A second auditor independent of the lead reviews findings before report finalization.
6. **Ethics-council review** (Child-Safe Excellence only) reviews Layer 4 findings and any cross-layer judgements.
7. **Report and decision.** A written audit report is delivered to the vendor. If certified, a signed certificate is issued and published in the registry. If not, a written explanation of which findings blocked certification is delivered, with reapplication terms.
8. **Public registry entry.** The certificate, scope, layer-level results, known limitations, and audit history are published.

The audit MUST be reproducible. Any test run that produced a result can be replayed; inputs and outputs are stored as immutable artefacts; the methodology version used is named on the certificate.

## 0.8 Relationship to other standards

The methodology is designed to **compose with**, not replace, the following:

- **GDPR (EU Reg. 2016/679)** — Layer 2 incorporates GDPR's child-specific provisions (Art. 8) and the EDPB guidance on children's data. Conformity with GDPR is a prerequisite, not sufficient.
- **EU AI Act (Reg. 2024/1689)** — Layer 3 incorporates the high-risk classification and Articles 5, 9–15 explicitly. For products that fall under Annex III §3, the methodology's evaluation overlaps with but does not constitute the formal conformity assessment performed by a Notified Body.
- **ISO/IEC 42001:2023 (AI management system)** — Layer 5 and parts of Layer 3 reference 42001 controls. 42001 alone is insufficient for the Custos Mark because it is organization-level; this methodology is product-level.
- **ISO/IEC 23894 (AI risk management)** — referenced where risk management practices feed audit evidence.
- **UK Age-Appropriate Design Code (Children's Code)** — informs Layer 2 and Layer 4 expectations for products operating in or marketed to UK users.
- **Council of Europe Convention on the Rights of the Child** and its AI-related interpretive guidance — informs Layer 4.

The full mapping is in [08-references.md](08-references.md).

## 0.9 Threats this methodology takes seriously

The methodology is designed against the following threats. Where a threat is not addressed, that is documented openly.

- **Hallucinated facts taught as truth.** Addressed in Layer 1.1.
- **Children using systems outside their declared age range.** Addressed in Layer 1.2 and Layer 4.1.
- **PII leakage and training-data contamination from children's data.** Addressed in Layer 2.
- **Unhealthy emotional attachment to AI companions, including following the Character.AI incident pattern.** Addressed in Layer 4.2.
- **Crisis-signal mishandling** (suicide, self-harm, abuse, eating disorders). Addressed in Layer 4.3 as a zero-tolerance block.
- **Dark patterns targeting minors.** Addressed in Layer 4.4.
- **Cross-lingual fairness gaps** where non-English-speaking children receive markedly worse service. Addressed in Layer 1.4.
- **Prompt-injection in school settings**, including child-driven jailbreaks. Addressed in Layer 1.5.
- **Pedagogically empty products marketed with education claims.** Addressed in Layer 4.7.
- **Silent product changes**, especially model swaps that change behaviour overnight. Addressed in Layer 5.2.
- **Methodology gameability.** Addressed by rotating test sets, partially private benchmarks, and faster version updates than vendors can adapt to.

The methodology does **not** currently address (planned for future versions):

- Multimodal evaluation depth equal to text (image/audio/video probes are partial in v0.1)
- Group dynamics in classroom AI deployments (multi-user behaviour in a class context)
- **Cross-session retention dynamics.** The methodology's Layer 4 §4.2 emotional-attachment tests run within sessions of 10–30 turns. A child returning to the same system across days or weeks may experience a different attachment trajectory if the system retains memory of prior exchanges, re-engages with prior emotional content on next login, or builds a long-running model of the child. v0.1 does not evaluate these multi-session dynamics. v1.0 work is planned in collaboration with developmental psychologists.
- Long-horizon learning-outcome studies (would require methodology that runs over months, not weeks)
- Energy and environmental footprint of educational AI

## 0.10 What this document is not

- **Not a compliance tick-box.** A product passing this methodology has been examined against thresholds and rubrics, not against a self-attestation.
- **Not a replacement for the AI Act conformity assessment.** Where formal conformity assessment by a Notified Body is required by law, the Custos Mark complements but does not replace it.
- **Not static.** This methodology will change. Vendors building for an outdated draft will need to re-audit against the version current at renewal.
- **Not infallible.** The consortium will get things wrong. The public changelog, revocation history, and appeals process exist so that mistakes are visible and correctable.
