# Contributing to the Custos Methodology

The methodology is developed in the open. We want it read, criticized, and improved by people we will never meet — teachers, parents, child psychologists, privacy lawyers, AI researchers, EdTech engineers, regulators. This document explains how to contribute and how proposals are reviewed.

## Who this is for

- **Pedagogues, child psychologists, and child-protection specialists** — substantive input on Layer 4 and on age-appropriate thresholds across all layers.
- **Privacy and AI-governance lawyers** — Layer 2 and Layer 3 accuracy against GDPR, AI Act, national child-data regimes.
- **AI engineers and researchers** — Layer 1 test design, gameability analysis, new probe categories.
- **Teachers, school IT, and parents** — real-world usefulness of the metrics, language clarity, what the service card should actually show.
- **EdTech vendors** — feasibility of the requirements, edge cases. Vendor input is welcome but is not given automatic weight; see "Conflicts of interest" below.

## How to propose a change

Open an issue. State, in this order:

1. **The problem.** What gap, error, or weakness in the current methodology are you addressing? Cite the section.
2. **The evidence.** Research, incidents, regulatory text, audit experience, or empirical data that supports the change. "I think it would be better" is not evidence.
3. **The proposed change.** Specific text or, for thresholds, a specific number. If you are not sure of the exact wording, a clear sketch is enough.
4. **The impact on existing or pilot certificates** (if applicable). Would products that previously passed now fail? Why is that acceptable?

For small, uncontroversial fixes (typos, broken cross-references, dead links), a PR without a prior issue is fine.

For substantive changes (new metrics, threshold adjustments, new layers, new prohibitions), open the issue first and wait for triage before drafting a PR. This prevents wasted writing.

## Review process

Every substantive proposal passes through:

1. **Triage** — within ~10 working days, a maintainer assigns the proposal to one of: `accepted-for-review`, `needs-more-evidence`, `out-of-scope`, `duplicate`, `rejected-with-reasoning`. Rejection always carries a written reason.
2. **Working-group review** — proposals tagged for the relevant layer are discussed by the appropriate working group (pedagogy, privacy, technical, child-protection). Working groups may invite the proposer to a session.
3. **Public consultation** — for changes the working group recommends, a 30-day public comment window opens. Comments are public and recorded.
4. **Council decision** — substantive methodology changes are ratified by the consortium's standards council. Minor editorial changes do not need ratification.
5. **Release** — accepted changes ship in the next point or major release per the [versioning policy](README.md#versioning), with an entry in [CHANGELOG.md](CHANGELOG.md) crediting the contributor.

The full cycle for a substantive change is typically **6–12 weeks**. Emergency changes — for example, a newly-disclosed jailbreak class that lets vendors trivially defeat Layer 1.5 — may be expedited; the public consultation period in that case is shortened, never skipped.

## Revision cadence

- **Annual revision cycle.** Every January, a comprehensive review collects accepted changes from the prior year and ships a major or minor release.
- **Point releases as needed.** Between annual cycles, point releases ship when accumulated changes merit it or when an urgent issue surfaces.
- **No silent changes.** Every change is in the changelog with rationale.

## Conflicts of interest

The credibility of this methodology depends on visible independence from the products it certifies.

- **Disclose** affiliations relevant to your contribution. "I work for an EdTech vendor that would be affected by this threshold" is required disclosure, not a disqualifier — it is context the reviewers need.
- **Vendor-originated proposals** are treated transparently and reviewed for vendor self-interest, but are not dismissed reflexively. EdTech engineers often see real implementation issues earlier than anyone else.
- **Council and maintainer recusals.** Reviewers with a material interest in the outcome of a proposal must recuse from the decision.
- **No undisclosed dual roles.** Anyone in a position of methodology authority must declare relationships with audited or applicant vendors. The public conflict-of-interest register applies to contributors who become maintainers.

Read [GOVERNANCE.md](GOVERNANCE.md) for the conflict-of-interest policy in full.

## Style and language

- **Normative keywords** (MUST, SHOULD, MAY, MUST NOT) follow RFC 2119 / RFC 8174 and are used deliberately. Do not introduce normative requirements with soft language.
- **Test design must be reproducible.** A new metric proposal must include a description specific enough that a competent auditor could implement it without consulting the proposer.
- **Avoid jargon when plain language works.** This document is read by teachers and parents, not only by engineers and lawyers.
- **Be precise about scope.** "Schools" is too broad; specify primary, secondary, vocational, university where relevant. "Children" is too broad; specify age bands.
- **Cite sources.** When invoking GDPR articles, AI Act articles, ISO standards, or research papers, cite specifically.

## What we will not accept

- Changes that lower child-safety thresholds without a strong evidentiary case and a public consultation period.
- Removal of the cross-lingual fairness layer or the crisis-scenario block. These are structurally non-negotiable.
- Vendor-specific carve-outs ("but for products like ours, this rule should not apply"). The methodology applies to product *categories*, not vendors.
- Marketing language. This is a standard, not a brand asset.

## Credit

Substantive contributors are credited in the changelog and on the methodology's contributor list. Organizations that contribute working-group time are acknowledged in the annual transparency report.

## Code of conduct

Contributors are expected to engage in good faith and with respect for fellow contributors. Disagreement about methodology — including strong disagreement — is welcome; personal hostility, harassment, or attempts to game the review process by overwhelming with noise are not. The maintainers reserve the right to mute, block, or ban contributors who repeatedly violate this expectation.

---

If you are unsure whether your contribution fits, open the issue anyway. Triage is cheap, and silent self-censorship costs the standard more than a rejection ever will.
