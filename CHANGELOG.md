# Changelog

All notable changes to the Custos Methodology are recorded here.
Format adapted from [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Versioning follows the policy in [README.md](README.md#versioning).

Each entry MUST state the change, the rationale, and — for major changes — whether existing certificates are affected.

---

## [Unreleased]

### Added
- `seeds/jailbreak/` — public reference sample of jailbreak / prompt-injection scenarios, with at least one scenario per attack class defined in §1.5.2: direct-instruction, role-confusion, authority-impersonation, multi-turn-escalation, indirect-injection, encoded-payload, and social-engineering. Ten scenarios total in the initial seed.
- §1.5.2 updated to enumerate the seven attack classes explicitly, to reference the public seed directory, and to reference (without exposing) the binding scenario schema in the private repo's auditor handbook.

### Changed
- §1.5.2 now explains the ≥ 30% private-scenario floor in relation to the ≥ 50% private floor for crisis scenarios in §4.3.2. The differential is intentional: rated jailbreak scoring bounds the gain from gaming the public sample, whereas a categorical crisis failure fails the entire audit (§4.3.4). The jailbreak attack landscape also evolves faster, so a smaller stable-private floor with more frequent refresh is operationally appropriate. Adding the rationale closes a drift point a reader could otherwise read as inconsistency between the two layers.

### Notes
- Public-seed scenario files conform to the scenario YAML schema maintained in the private repository at `auditor-handbook/scenario-schema.md`. The reference in §1.5.2 to that document is intentional even though the link 404s for unauthenticated readers — the methodology text frames the schema as restricted-access material, not as a missing resource.
- The seed exists so vendors and researchers can prepare and critique without needing access to the private library; per §1.5.2 the ≥ 30% private rotation continues to defend against gameability.
- No effect on tiers, thresholds, or pass criteria. Patch-level addition.

---

## [0.1.2] — 2026-05-16

### Changed
- **Scope binding promoted from five anchors to six.** Operating countries promoted to a first-class scope anchor alongside product, version, use-cases, languages, and age range. The v0.1.1 framing treated country implicitly through language coverage and operating-context metadata, but the audit's substantive content already varies by country: national implementations of GDPR Article 8 (age-of-consent) diverge across member states (DE 16, IT 14, PL 13, NL 16, ES 14, FR 15 with parental authorisation for 13–15), AI Act enforcement timelines diverge per member state, and curriculum-alignment probes (§1.1.3) reference specific national curricula. Language and country are not interchangeable — Spanish-in-Spain is not Spanish-in-Mexico, German-in-Germany is not German-in-Austria, French-in-France is not French-in-Belgium. The five-anchor framing also created an asymmetric marketing risk: a vendor with a language-only certificate could plausibly imply coverage across all markets sharing that language unless the certificate explicitly bound the country. Promoting `operating_countries` makes the binding explicit and aligns the methodology's rhetorical framing with the country-specific work the audit already performs.
- Files touched by the promotion inside this repository: [00-overview.md §0.6](standard/00-overview.md), [06-tiers-scope-lifecycle.md §6.2](standard/06-tiers-scope-lifecycle.md), [07-glossary.md "Scope"](standard/07-glossary.md), [09-service-card-template.md §9.4.4 and §9.6](standard/09-service-card-template.md), [README.md](README.md) scope summary. Companion changes were applied in the consortium's pre-filing Regulations of Use (§4.5 + §5.2/§5.3 + Annex A glossary) and in the founding-team's project spec, both held outside this public repository.

### Notes
- This is a substantive scope-model change that would normally warrant a v0.2.0 (minor) or v1.x (major) bump under the methodology's [versioning policy](README.md#versioning). A patch version is appropriate here because (a) the methodology is still v0.1 working draft, not v1.0 production; (b) no certificates have been issued under the prior scope model, so no auditor or vendor migration is required; (c) the service-card JSON shape was already country-aware in v0.1.1 — `operating_countries` was present in the schema, the change is the rhetorical promotion across documents.
- From v1.0 onward, an equivalent change to the scope-anchor set will be a major-version bump.

---

## [0.1.1] — 2026-05-16

### Changed
- **Project rebrand from "EduAI Trust Mark" (working title) to "Custos" (consortium) and "Custos Mark" (certificate brand).** Working-title clearance research identified a brand-name conflict with EduAI Foundation, an existing European non-profit operating in the same AI-in-education space, that makes the EduAI working title unsuitable for EUIPO registration in Classes 41/42. Other shortlisted candidates (Paideia, Aletheia, Eunomia, Veritas, Tutela) are heavily encumbered in the same namespace by EU-funded projects and existing AI/education organizations. Custos was retained as the working name pending formal EUIPO clearance because (a) the existing Custos-named entities sit in distinguishable goods/services (AI agent spend governance, blockchain anti-piracy, watches, faith-based foundations) rather than vertical AI-in-education certification, and (b) "Custos" as a Latin generic has bounded distinctiveness that supports coexistence in distinct service classes. No certificates have been issued; no auditor or vendor migration required.
- Methodology document name: "EduAI Trust Mark Methodology" → "Custos Methodology".
- Certificate brand: "EduAI Trust Mark" → "Custos Mark".
- Consortium reference: "EduAI Trust Mark consortium" → "Custos consortium" (or "Custos").
- Repository URL in LICENSE attribution updated: `github.com/edu-ai-trust-mark/methodology` → `github.com/custos-mark/methodology`.
- **Two-repository layout adopted.** The public methodology repository (`custos-mark/methodology`) is paired with a private repository (`custos-mark/custos-mark-private`) that holds the rotating private portion of the crisis-scenario library (§4.3.2), the private jailbreak scenarios (§1.5), the working corpus of child prompts beyond public seed examples (§4.1), the auditor handbook, pinned judge configurations and validation sets, and lab-internal harness extensions. The split is enforced at the repository boundary rather than via in-repo access control (`.gitignore` or branch protection) because the gameability rules in §4.3.2 and §1.5 require a stronger guarantee than a single misconfigured push could compromise. Reproducibility is preserved via the lab's immutable artefact store rather than public publication of the materials. README updated to describe the layout.

### Notes
- Custos remains a **working name** pending formal EUIPO clearance search and consortium incorporation. The README's working-title disclaimer is updated to reflect this.
- The functional space (vertical product certification for AI in education with pedagogical and child-safety expertise) remains uncontested; the rebrand resolves a brand-name clearance issue, not a competitive positioning issue.
- The private repository is initialized in v0.1.1 with structural scaffolding only — directory tree, top-level governance documents (README, LICENSE, ACCESS, CONTRIBUTING, CHANGELOG), and per-subdirectory READMEs defining scope. Actual content (scenarios, prompts, handbook chapters, judge configurations) lands in subsequent point releases as Phase 0 deliverables are produced.

---

## [0.1.0] — 2026-05-16

### Added
- Initial public working draft. Establishes the five-layer structure (technical measurement, children's data protection, AI Act compliance, child protection and pedagogical ethics, operational maturity), the three-tier certification model (Verified, Education-Ready, Child-Safe Excellence), and the scope-binding model (product + version + use-cases + languages + age range).
- Initial threshold values for Layer 1 metrics (faithfulness, hallucination, calibration, cross-lingual gap, child-style robustness, prompt injection resistance).
- Initial test design for Layer 2 PII leakage with canary-token methodology.
- Initial library of crisis-scenario categories for Layer 4 with zero-tolerance failure rule.
- Governance, contribution, and licensing documents.

### Notes
- This is a working draft. Thresholds, test set sizes, and rubric scales are open to revision based on pilot-audit evidence.
- v1.0 will be released after the first cohort of pilot audits and a public consultation period.
- No certificates have been issued yet; no migration concerns.

---

## Change-entry template

```
## [X.Y.Z] — YYYY-MM-DD

### Added
- {what was added, why, who proposed it (issue/PR reference)}

### Changed
- {what changed, why, impact on existing certificates}

### Deprecated
- {what is on a path to removal, replacement, removal target version}

### Removed
- {what was removed, why, where the replacement lives}

### Fixed
- {editorial fixes, broken cross-references, threshold typos}

### Security
- {changes that close gameability vectors or address newly-discovered jailbreak classes}

### Migration
- {if MAJOR: instructions for re-auditing}
```
