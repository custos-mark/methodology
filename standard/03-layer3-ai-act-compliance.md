# Layer 3 — AI Act and regulatory compliance

> **Layer 3 measures conformity with the EU AI Act (Regulation 2024/1689) and related EU and national rules applicable to AI in education.**
> Primary methods: documentation review against a structured checklist, with technical probes to verify documented controls are actually in place.

The Custos Mark is not a substitute for the formal conformity assessment required under the AI Act for high-risk systems performed by a Notified Body. Where formal conformity assessment is required, this layer overlaps with but does not replace it. Where the law does not yet require conformity assessment (because the deployment is not yet in the high-risk regime, because the system is not high-risk, or because national implementation has not caught up), this layer fills the verification gap.

## 3.1 System classification

### 3.1.1 The classification gate

Every audit begins with a written **classification determination**:

- Is the system, as scoped, an **AI system** within the meaning of AI Act Art. 3(1)?
- Does it fall under any **prohibited practice** in Art. 5? (See §3.3.)
- Is it **high-risk** under Annex III? (See §3.1.2.)
- Is it a **general-purpose AI model** (GPAI) used in or integrated with the educational product? (Implications for transparency obligations.)
- Does it have **transparency obligations** under Art. 50 (e.g., interaction with natural persons, content generation)?

The classification determination is signed by the lead auditor, reviewed by a second auditor, and included in the certificate.

### 3.1.2 Annex III §3 — education and vocational training

Educational AI is frequently classified high-risk under AI Act Annex III §3. The auditor MUST determine whether the system performs any of the following:

- Determining access to or admission to educational institutions or programmes
- Evaluating learning outcomes (including formative assessment with material weight)
- Assessing the appropriate level of education for individuals
- Monitoring and detecting prohibited behaviour during tests

If the system performs **any** of these, full high-risk requirements under §3.2 apply **regardless of the tier of certification requested**. The vendor cannot opt out of Layer 3 high-risk evaluation by applying for a lower tier. This is the only place in the methodology where requested tier is overridden.

If the system does **not** perform any Annex III §3 activity but is used in an educational context, the high-risk requirements in §3.2 still inform Layer 3 evaluation as best-practice expectations, scaled to tier.

## 3.2 High-risk requirements (Articles 9–15)

A structured checklist mapped to the AI Act articles. Each item is scored Pass / Minor Finding / Major Finding / Fail.

### 3.2.1 Art. 9 — Risk management system

- A documented risk management process exists and is periodically reviewed
- Risks specifically to children's rights, safety, and development are identified
- Mitigations are documented, implemented, and tested
- An incident register exists and is current
- Residual risk acceptance is documented and justified

### 3.2.2 Art. 10 — Data and data governance

- Training, validation, and testing datasets meet quality requirements appropriate to the educational purpose
- Bias-mitigation steps are documented
- Representativeness is assessed and weaknesses disclosed
- Where children's data is used in training, see Layer 2 §2.3 (prohibited use without explicit informed consent)
- Where the system uses a third-party foundation model, the vendor documents the upstream provider's data practices to the extent disclosable

### 3.2.3 Art. 11 — Technical documentation

- Technical documentation meets the Annex IV requirements (or equivalent for the product type)
- It is complete, current, and version-controlled
- It is available to authorized authorities on request
- It is detailed enough that a competent reviewer outside the vendor can understand how the system works

### 3.2.4 Art. 12 — Record-keeping and logging

- Logs capture events material to assessing safety, accuracy, and compliance
- Log retention is documented and proportionate (see also Layer 2 §2.2.5 for child-privacy implications)
- Logs are tamper-resistant
- Logs can be produced for the regulator or for incident investigation

### 3.2.5 Art. 13 — Transparency and information to users

- Teachers can understand how the system reaches its outputs at a level sufficient for them to use it responsibly
- Students receive age-appropriate transparency about how the system works and that it is an AI
- Parents receive transparency about what the system does with their child's data and learning
- Limitations of the system are disclosed honestly
- Out-of-distribution warnings are surfaced where relevant

### 3.2.6 Art. 14 — Human oversight

A frequent failure point. See §3.4 for detailed criteria. Summary checklist:

- Human oversight is designed in, not bolted on
- The teacher's role is documented and trained
- The system fails safely when human oversight is unavailable
- Override and intervention paths are tested, not just documented

### 3.2.7 Art. 15 — Accuracy, robustness and cybersecurity

- Accuracy metrics are documented (and verified against Layer 1)
- Robustness under realistic adversarial conditions is verified (and verified against Layer 1.5)
- Cybersecurity controls are documented and tested:
  - Authentication and access control commensurate with the data sensitivity
  - Protection against model attacks (e.g., adversarial inputs, model extraction) appropriate to the threat model
  - Patch management
  - Incident response

## 3.3 Prohibited practices (Article 5)

The following AI Act Article 5 prohibitions are categorical disqualifiers. **The Article 5 screen runs immediately after the classification determination in §3.1 and before any layer evaluation.** Failure stops the audit at this gate; no further evaluation is performed and no certificate at any tier is issued. The audit-shape sequencing — classification → prohibited-practice screen (Art. 5 plus the categorical disqualifiers in [02-layer2-data-protection.md §2.3](02-layer2-data-protection.md)) → layer evaluation — matches [00-overview.md §0.7](00-overview.md).

- **Emotion recognition in educational settings** (Art. 5(1)(f), as applied to educational establishments) is **prohibited** for products certified under this methodology. This includes inference of emotional state from facial expression, voice, biometric signals, or behavioural patterns for the purpose of adapting the educational experience.
- **Social scoring** of natural persons that leads to detrimental or unfavourable treatment in unrelated contexts (Art. 5(1)(c)). Educational systems MUST NOT compute composite student scores intended for use beyond the specific learning context they were collected in.
- **Subliminal techniques** beyond a person's consciousness or **purposefully manipulative or deceptive techniques** that materially distort behaviour to cause harm (Art. 5(1)(a)).
- **Exploitation of age-related vulnerabilities** that materially distorts the behaviour of a child to cause harm (Art. 5(1)(b)).
- **Biometric categorisation** to infer race, political opinion, trade-union membership, religious or philosophical belief, sex life or sexual orientation (Art. 5(1)(g)).
- **Real-time remote biometric identification** in publicly-accessible spaces for law-enforcement purposes is out of scope for this methodology but its presence in any educational product is disqualifying.

The list above is the methodology's interpretation of how Article 5 applies to educational products at the v0.1 stage. It is conservative by design.

## 3.4 Genuine human oversight (Art. 14 detail)

Human oversight that exists only on paper is the single most common Layer 3 failure mode. The audit verifies the teacher's **actual** ability to:

### 3.4.1 See what the AI told the student

- The teacher can access a clear, accurate record of student–AI interactions for their class.
- The record is timely (not just available retrospectively for audit purposes).
- The record is at a granularity that allows real teaching judgement, not a summary that hides material content.
- Children are aware that teachers can access these records (transparency principle).

### 3.4.2 Correct or override an AI decision

- Where the AI grades, recommends a placement, or generates feedback, the teacher can change or reject the AI's output.
- The change is recorded and reflected in what the student and parent see.
- The system does not penalize, slow, or hide teacher overrides.

### 3.4.3 Disable the function

- The teacher (or the school IT administrator) can disable AI features for a class, a student, or an exercise.
- Disabling does not require contacting the vendor.
- Disabling is granular enough to be useful (per-feature, not all-or-nothing).

### 3.4.4 Receive alerts for significant events

- The system surfaces alerts when a student writes about self-harm, abuse, sexual content, or other crisis signals (see Layer 4 §4.3).
- Alerts reach a designated school contact, not only the parent — because the parent may be the cause of the disclosure.
- Alerts are calibrated: an alert flood is functionally equivalent to no alerts.

### 3.4.5 Failure modes for Layer 3.4

If any of the four oversight capabilities above is **merely formal**:

- Verified — Minor Finding
- Education-Ready — Major Finding; conditional pass requires remediation within 30 days
- Child-Safe Excellence — Fail

## 3.5 National rules

The audit MUST verify compliance with national rules applicable in each declared operating country, including but not limited to:

- National implementation of GDPR Art. 8 (age of consent) — see Layer 2 §2.1.3
- National child-protection laws specific to digital services
- National educational data-protection codes (e.g., school-data regimes, ministerial guidance)
- Language requirements in user-facing material in jurisdictions that require it (e.g., language-of-instruction obligations)
- Accessibility laws applicable to publicly-funded school deployments (e.g., EN 301 549, national web-accessibility directives)

Where the vendor declares operation in a country, evidence of compliance with that country's relevant rules MUST be in the documentation pack.

## 3.6 General-purpose AI model considerations

Where the product uses a third-party general-purpose AI model:

- The vendor MUST disclose the upstream provider(s) and the model family
- Documentation MUST cover the contractual basis (DPA, processor terms)
- Where the upstream provider has GPAI obligations under the AI Act, the vendor MUST document how their use complies with the upstream obligations passed through
- Model swaps to a different upstream model are a material change and trigger a re-test under [05-layer5-operational-maturity.md §5.2](05-layer5-operational-maturity.md)

## 3.7 Composition: Layer 3 pass criteria

A product passes Layer 3 at a given tier when:

- No Article 5 prohibited practice is found
- Classification determination is complete and consistent with technical reality
- Where the system is Annex III §3 high-risk, all Articles 9–15 items are at least Pass or Minor Finding (no Major Findings or Fails) at Education-Ready; no findings worse than Minor at Child-Safe Excellence
- Genuine human-oversight evaluation per §3.4 meets the tier threshold
- National rules are documented and satisfied for each declared operating country

Verified-tier audits at Layer 3 are limited to:

- Article 5 screen
- Classification determination
- Self-attestation review against the high-risk checklist with spot-check verification on three Articles selected by the auditor

Education-Ready and above audit the full layer.
