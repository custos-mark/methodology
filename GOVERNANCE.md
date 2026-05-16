# Governance

This document specifies how the Custos methodology is governed: who owns the standard, who can issue certificates, how the methodology changes, and how conflicts of interest are managed. It complements [CONTRIBUTING.md](CONTRIBUTING.md), which explains the day-to-day contribution flow.

The structure mirrors the ISO/IEC model where the standard-holder and the certifying body are different legal entities. Separation is a feature: an organization that both writes a standard and certifies against it has an inherent conflict that no policy can fully neutralize.

## Two-entity structure

### Standard-holding non-profit consortium

Owns:

- The methodology text and its versioning
- The Custos Mark brand and visual identity
- The public registry of certificates and the verification API
- The ethics and pedagogy council
- The conflict-of-interest register
- Auditor accreditation

Funded by:

- Membership fees from institutional members (universities, child-rights organizations, professional bodies)
- Methodology licensing to ministries of education for public-procurement frameworks
- Grants where the funder's interests are aligned with the consortium's mission and disclosed

**Jurisdiction:** Netherlands (vereniging) or Belgium. Both offer English-language administration, proximity to EU institutions, and a credible regulatory reputation. Final choice pending legal review.

The consortium does **not** sell audits or accept payment from audited vendors. Vendor revenue flows to the operating lab only.

### Operating audit laboratory

A commercial entity licensed by the consortium to perform audits against the methodology. Generates revenue from audit fees.

The lab is structurally separated from the consortium:

- Different legal entity, different ownership, different officers
- Lab leadership cannot also be voting members of the methodology standards council
- Lab cannot unilaterally interpret the methodology; ambiguities are escalated to the consortium
- All audit reports are reviewed by a second auditor independent of the lead auditor on the engagement

**Initial jurisdiction:** Serbia (d.o.o.) for cost reasons, with planned relocation or branching into an EU jurisdiction as the operation matures and as accreditation under ISO/IEC 17021-1 becomes relevant.

Later, additional licensed labs may be onboarded. The consortium's accreditation criteria for new labs are public.

## Founding council

The credibility of an education-focused mark depends on its council. The council ratifies methodology changes, hears appeals, and sets ethical direction.

**Target composition (~7 members):**

- 1–2 university faculties of education with European reputation
- 1 child-rights organization with EU presence (e.g., a Eurochild member organization)
- 1 EdTech industry-association representative, **in a minority position**, for legitimacy with vendors
- 1 data-protection expert with focus on children's data
- 1 child psychologist with peer-reviewed publications on child–technology interaction
- 1 former education regulator or senior civil servant from a ministry of education
- 1 AI-ethics academic with relevant publications

**Hard rules:**

- AI vendors MUST NOT dominate the board. The vendor representation is capped at one seat regardless of council size.
- Members MUST disclose all material relationships with audited or applicant vendors.
- Members serve fixed-term renewable mandates (typical: 3 years, one renewal).
- Founding members are credited as such permanently; subsequent members serve under standard terms.

The standards council operates on consensus where possible, supermajority (5/7 for a 7-member council) where consensus fails. Dissenting opinions are recorded publicly.

## Methodology amendment process

1. **Proposal** — via the [CONTRIBUTING.md](CONTRIBUTING.md) flow.
2. **Working-group review** — assigned by methodology layer. Working groups draft recommended text.
3. **Public consultation** — 30 days, comments public.
4. **Standards council decision** — ratifies, modifies, or rejects with reasons.
5. **Release** — version-tagged per the [versioning policy](README.md#versioning), changelog entry, contributor credit.

Emergency amendments (e.g., a newly-disclosed jailbreak class that defeats a Layer 1 requirement) may compress the consultation window to 7 days, but never skip it. Emergency amendments must be reviewed and either ratified or reversed by the next ordinary council session.

## Auditor accreditation

Only auditors licensed by the consortium may issue Custos Mark certificates.

**Requirements for individual auditors:**

- Demonstrated technical competence (technical auditors) or pedagogical/child-protection competence (Layer 4 auditors) — evidenced by qualifications, prior audit experience, and the lab's internal training programme
- Signed conflict-of-interest declaration covering current and recent vendor relationships
- Annual re-attestation
- Continuing education on methodology updates

**Requirements for audit organizations:**

- Quality management aligned with ISO/IEC 17021-1 principles, formal accreditation pursued as the consortium matures
- Documented audit procedures
- Independent second-auditor review on every certificate
- Liability insurance appropriate to certificate scope

The consortium MAY suspend or revoke an auditor's licence for material breach of methodology, undisclosed conflict of interest, or repeated quality failures. Revocation is published in the auditor registry.

## Conflict of interest

### Public register

Every auditor, council member, and methodology maintainer's material relationships with audited or applicant vendors are recorded in a public register. "Material" means: employment, board service, equity ownership above a de minimis threshold, paid consulting within the past 24 months, or close family member in such a position.

### Recusal

Where a relationship exists, the affected individual MUST recuse from:

- Audits of that vendor
- Council deliberations on that vendor's certificates or appeals
- Methodology decisions that disproportionately affect that vendor

Recusals are recorded.

### Cooling-off periods

- Lab auditors who leave to join an EdTech vendor: 12 months before they may interact with the consortium on behalf of that vendor.
- Vendor employees joining the lab or consortium: 12 months before they may participate in audits of their former employer or audits in the same product category at director level.
- Council members joining a vendor: must resign from the council before joining; may not return to the council for 24 months.

### Whistleblower protection

Anyone reporting a methodology breach, undisclosed conflict, or audit irregularity is protected: identity is shielded from the affected party, retaliation grounds for revocation of license/council seat, and a published whistleblower handling procedure governs follow-up.

## Appeals

Vendors may appeal:

- Refused certifications
- Findings within an audit
- Suspensions or revocations

Appeals are heard by a panel of council members not involved in the original decision. The vendor may submit written argument and, for Child-Safe Excellence cases, request an oral hearing. Decisions are written and published with the affected vendor's commercially-sensitive material redacted on request.

Where an appeal is upheld, the original auditor and decision are not punished for a good-faith judgment, but the methodology gap or interpretation issue that caused the disagreement is documented and may inform the next revision.

## Long-term path to formal status

Three-to-five-year horizon:

- **ISO/IEC 17021-1 accreditation** for the operating lab, granting recognition for management-system audits.
- **AI Act Notified Body status** for high-risk educational AI conformity assessment, allowing the lab to perform a portion of the formal regulatory conformity assessment alongside or in lieu of horizontal notified bodies.
- **Memoranda of understanding** with ministries of education for public-procurement use.
- **Cross-recognition agreements** with parallel initiatives in the UK, North America, or elsewhere, where mutual recognition is in the interest of vendors, regulators, and the public.

The two-entity structure is designed to accommodate this path without restructuring. The consortium remains the standard-holder; the lab grows into formal accreditation.

## Transparency

- **Annual transparency report** covering audits performed, certificates issued, suspended, or revoked, incident reports received, appeals heard, methodology changes ratified, financial summary.
- **Public registry** of every certificate including expired, suspended, and revoked, with reasons displayed.
- **Public methodology history** via the changelog and git log of this repository.
- **Public conflict-of-interest register.**
- **Public auditor registry.**

The transparency obligations are themselves part of the standard: they are how the consortium holds itself to account.

---

*Where this document and the consortium's eventual articles of association diverge, the articles of association govern. This document will be updated to reflect any material divergence and the divergence noted in the changelog.*
