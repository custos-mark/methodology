# Layer 5 — Operational maturity

> **Layer 5 measures whether the product is operationally ready for school use: available, predictable across versions, properly documented, and accountable when things go wrong.**
> Primary methods: documentation review, interviews with vendor operations staff, and verification against published commitments.

Layer 5 is deliberately narrower than general operational-maturity frameworks (ISO/IEC 42001, SOC 2, etc.). It focuses on what matters in schools, where unreliable services disrupt teaching and silent product changes are politically and pedagogically unacceptable.

## 5.1 Availability and continuity

### 5.1.1 Published SLA

The vendor MUST publish a Service Level Agreement covering at minimum:

- Uptime target (e.g., 99.5% monthly)
- Maintenance-window policy with school-friendly timing (no maintenance during school-day hours in the operating market)
- Incident-classification scheme (Sev-1 / Sev-2 / Sev-3) with defined response and resolution times
- Communication channels and frequency during incidents

The SLA must be **realistic**, not aspirational. Audited uptime over the prior 12 months MUST meet the stated SLA, or a credible remediation plan MUST be in place.

### 5.1.2 Behaviour under failure

The audit verifies that the system fails gracefully:

- **Degraded mode versus full unavailability.** Where possible, the product offers reduced functionality during incidents rather than complete outage.
- **Honest error messages.** Children receive age-appropriate, non-alarming error messages. Teachers receive enough information to manage the class.
- **No data loss.** In-flight student work is preserved across failures.
- **Recovery procedures** are documented and tested.

### 5.1.3 Support availability

- Support is offered in the operating language(s), not English only.
- Support hours align with school-day reality in the operating market (not US Pacific time for a German school).
- Documented incident-response time meets the SLA.
- A school-facing escalation path is published; teachers do not have to navigate a consumer-grade help desk to reach engineering when student safety is at stake.

## 5.2 Model versioning

**Critical for schools.** Schools cannot accept "a different product tomorrow without notice". This section is rigorous.

### 5.2.1 Change classification

The vendor MUST classify changes as:

| Class | Definition | Notice required | Re-test trigger |
|---|---|---|---|
| **Patch** | Bug fix or non-behavioural change | None required | None |
| **Minor model update** | Tuning or version bump where behaviour change is bounded | 30 days | Spot-check Layer 1 at next renewal |
| **Major model update** | Model family change, training-data refresh, or any change that materially alters output distribution | **90 days** | Mandatory re-test of Layer 1 and Layer 4 within 60 days of deployment |
| **Material scope change** | New features, new languages, new age range, removal of certified features | **90 days** | Scope amendment with partial re-audit |

### 5.2.2 Vendor obligations

- 90-day advance notice for major changes, delivered to certified-customer schools via a documented channel
- A grace period during which schools MAY remain on the previous version
- A documented model-deprecation policy (how long the previous version remains available)
- Mandatory re-test of certification on major model updates (binding condition of the certificate, not optional)
- Notice to the consortium concurrent with notice to customer schools

### 5.2.3 Failure modes

- Silent model swap without notice = Suspension of the certificate
- Failure to re-test within 60 days of a major change = Suspension
- Repeated silent changes = Revocation

## 5.3 Documentation for schools

The vendor MUST provide:

### 5.3.1 Implementation guide for school IT administrators

- Deployment options
- Authentication integration (SAML, OIDC, school SSO providers)
- LMS/SIS integration
- Data-processing-agreement template
- Privacy configuration options
- Logging and audit configuration
- Decommissioning procedure

### 5.3.2 Real-world use-case guide for teachers

- Concrete classroom uses with examples
- Lesson-plan integration suggestions
- How to handle common student misuses
- How to handle disagreement with AI output
- Pedagogical limitations to be aware of
- Not marketing material — written for actual teaching

### 5.3.3 Parent-facing materials

- Available in the parent's language
- Plain language, no jargon
- What the product does, what data it processes, how to opt the child out where lawful
- Contact channel for parental questions
- Reference to the Custos Mark service card

### 5.3.4 DPIA helper for schools

- Template school-side DPIA covering the vendor's data flows
- Acknowledges that the school typically has controller obligations in the deployment
- Identifies the controller/processor split clearly
- Provides the school with what it needs to discharge its own DPIA obligations without commissioning external counsel

### 5.3.5 Accessibility documentation

- WCAG/EN 301 549 conformance statement
- Known accessibility limitations
- Procedure for accessibility issue reporting

## 5.4 Complaints and incidents

### 5.4.1 Complaint channels

- **Open channel for teachers** to report concerns about AI behaviour
- **Open channel for parents** to report concerns about their child's use
- **Open channel for students** age-appropriate to report concerns
- Acknowledged within published response times
- Routed to staff competent to handle child-safety reports, not only Tier-1 support

### 5.4.2 Incident log

- Public **aggregated** incident log (no PII, no per-child reporting)
- Categorized by type (safety, privacy, accuracy, availability)
- Updated at least quarterly
- Includes resolution status and remediation taken

### 5.4.3 Obligation to notify the consortium

The vendor MUST notify the consortium within **72 hours** of becoming aware of any **child-safety incident**, including:

- A failure of the crisis-scenario handling in Layer 4 §4.3 in production
- A PII leakage involving a child
- A suspected unauthorized use of a child's data
- A material model behaviour change that may affect prior Layer 1 or Layer 4 results
- Any law-enforcement contact regarding the product's interaction with a child

Notification triggers:

- Investigation by the consortium
- Possible audit re-opening
- Possible suspension pending investigation
- Possible methodology update to address the underlying issue

Failure to notify within the 72-hour window is itself a Major Finding at minimum; failure to notify a child-safety incident at all is grounds for revocation.

### 5.4.4 Incident transparency on the service card

- Confirmed incidents are summarized on the service card
- Vendors do not control the summary text; the consortium drafts it
- Vendors may submit a written response of bounded length, published alongside

## 5.5 Composition: Layer 5 pass criteria

A product passes Layer 5 at a given tier when:

- SLA is published and met (or remediation plan accepted)
- Model-versioning policy meets §5.2 requirements
- All documentation under §5.3 is present and adequate for its audience
- Complaint and incident processes per §5.4 are in place and tested

Verified-tier audits cover only §5.1 (basic availability), §5.2 (versioning policy documented), and §5.4.3 (consortium-notification obligation). Education-Ready and above audit the full layer.
