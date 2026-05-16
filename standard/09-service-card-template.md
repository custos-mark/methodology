# 9. Service-card template

> **The canonical artefact schema for what is published per Custos Mark certificate.**
> This document is normative for every certificate issued under [Custos Methodology v0.1+](../README.md) and binding on the consortium's public registry.

A certificate exists in three forms:

- A **signed JSON document** — the source of truth, cryptographically signed by the consortium, aligned with [W3C Verifiable Credentials](https://www.w3.org/TR/vc-data-model/). The signed JSON **is** the certificate.
- A **public HTML rendering** on the consortium's registry — what schools, parents, regulators, journalists, and vendors read in a browser. The HTML is derived from the JSON; in any conflict, the JSON is authoritative.
- A **PDF copy** for human archival use, also derived from the JSON.

All three resolve from the same canonical URI keyed by certificate ID. Vendor marketing material that references the certificate MUST link to that URI ([06-tiers-scope-lifecycle.md §6.6](06-tiers-scope-lifecycle.md); Regulations of Use §5.2 — the consortium's EU certification-mark Regulations of Use, a pre-filing working draft held by the consortium until EUIPO submission).

This document specifies, for v0.1:

- The required and optional fields of the signed JSON
- The required visible structure of the HTML rendering
- The cryptographic signature and canonicalization scheme
- How status changes (suspension, revocation, withdrawal) are recorded
- How the schema is versioned

## 9.1 Status and versioning

- **Schema version:** v0.1 (matches methodology v0.1). Versioned independently from the methodology under the policy in [README.md §Versioning](../README.md#versioning).
- **Cards issued under a prior schema version retain their original schema.** The registry renders each card according to the schema it was issued under. New schema versions apply to newly-issued cards.

## 9.2 Audiences

The same artefact serves multiple audiences. The schema MUST contain enough information for each, and the HTML rendering MUST surface the right subset for each:

| Audience | Primary needs |
|---|---|
| Schools, teachers (procurement) | Is this certified for ages X–Y, language L, this subject? What tier? What are the known limitations? Is it currently active? |
| Parents | Is the product my child uses currently certified? What does it cover, in plain language? |
| Regulators | AI Act classification, Article 5 screen result, Annex III §3 sub-activities, per-layer results |
| Researchers and journalists | Audit history, prior versions, suspensions, revocations; offline verifiability |
| Vendors | Certificate ID, verification URI, exact scope they may claim |
| Auditors and lab | Machine-readable JSON for downstream tools and replay |

The schema is a superset; the HTML renders the right view per audience (see §9.6 and §9.7).

## 9.3 Resolvability

Every certificate has a stable canonical URI from which all three forms (HTML, JSON, PDF) resolve:

```
https://registry.custos-mark.org/certificates/<certificate-id>          # HTML (default)
https://registry.custos-mark.org/certificates/<certificate-id>.json     # signed JSON
https://registry.custos-mark.org/certificates/<certificate-id>.pdf      # PDF
https://registry.custos-mark.org/certificates/<certificate-id>.qr.png   # QR code encoding the canonical HTML URI
```

The `certificate-id` is a URL-safe, time-ordered identifier of at least 16 characters. v0.1 implementations SHOULD use [UUIDv7](https://datatracker.ietf.org/doc/html/rfc9562#name-uuid-version-7), Crockford base32 representation. The URN form is `urn:custos-mark:certificate:<certificate-id>`.

The DNS name `registry.custos-mark.org` is illustrative; the consortium's final registry domain is fixed at incorporation and recorded in the consortium's articles of association. Once fixed, the domain MUST remain stable for the life of the consortium — certificate IDs and verification URIs depend on it.

## 9.4 Signed-JSON schema

The signed JSON is a W3C Verifiable Credential. Top-level structure:

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://custos-mark.org/contexts/v1"
  ],
  "id": "urn:custos-mark:certificate:01HFXX...",
  "type": ["VerifiableCredential", "CustosMarkCertificate"],
  "issuer": { ... },
  "issuanceDate": "2026-05-16T10:00:00Z",
  "expirationDate": "2027-05-16T10:00:00Z",
  "credentialSubject": { ... },
  "proof": { ... }
}
```

The fields in `credentialSubject` are specified in §9.4.1–§9.4.13 below. Field-level conventions:

- Dates are RFC 3339 UTC (`Z` suffix).
- Language codes are ISO 639-1 two-letter (with optional region tag, e.g., `de-AT`).
- Country codes are ISO 3166-1 alpha-2.
- Age values are integer years.
- Score values are floats between 0 and 1 unless the metric's rubric defines a different range (then stated explicitly in `metric_scale`).
- Optional fields MAY be omitted; the consumer MUST treat an absent optional field as not-stated, not zero.

### 9.4.1 Identity and versioning

```json
{
  "card_schema_version": "0.1",
  "methodology_version": "0.1.1",
  "harness_version": "0.1.0"
}
```

- `card_schema_version` MUST match the version of this document under which the card was issued.
- `methodology_version` MUST name the published methodology version under which the audit was performed.
- `harness_version` MAY be omitted at higher tiers where the harness is not the load-bearing instrument; at Verified and Education-Ready where Layer 1 is run via the public harness or a derivative, it SHOULD be included.

### 9.4.2 Issuer and operating lab

```json
{
  "issuer": {
    "id": "did:web:custos-mark.org:issuer:consortium",
    "name": "Custos consortium",
    "operating_lab": {
      "id": "lab-001",
      "name": "Custos Lab Ltd"
    },
    "lead_auditor_id": "auditor-a1f3",
    "second_auditor_id": "auditor-d27c",
    "ethics_council_review": {
      "performed": true,
      "panel_ids": ["council-m1", "council-m2", "council-m3"]
    }
  }
}
```

- `issuer.id` is a [`did:web`](https://w3c-ccg.github.io/did-method-web/) DID resolving to the consortium's DID Document.
- `operating_lab` identifies the lab that conducted the audit. Where multiple labs become licensed, the lab is the issuer's delegate; the cryptographic signature is still under the consortium key.
- `lead_auditor_id` and `second_auditor_id` are pseudonymous identifiers from the [auditor registry](../GOVERNANCE.md). The auditor registry resolves them to natural persons under its access policy.
- `ethics_council_review` MUST be present for Child-Safe Excellence certificates and MUST be omitted for Verified.

### 9.4.3 Subject — vendor and product

```json
{
  "vendor": {
    "legal_name": "Example EdTech GmbH",
    "trading_name": "Example Tutor",
    "registered_country": "DE",
    "vendor_id": "did:web:example-edtech.com"
  },
  "product": {
    "name": "Example Math Tutor",
    "version_or_range": "3.2.x",
    "version_change_control_uri": "https://example-edtech.com/changelog/math-tutor"
  }
}
```

- `vendor.legal_name` is the registered legal name; `trading_name` is what consumers see in commerce.
- `product.version_or_range` MAY be a single version (`3.2.4`) or a documented range (`3.2.x`). A range is permitted only when `version_change_control_uri` points at a public changelog the vendor maintains.

### 9.4.4 Scope (the six anchors)

The six anchors specified in [06-tiers-scope-lifecycle.md §6.2](06-tiers-scope-lifecycle.md) and the consortium's Regulations of Use §4.5 (pre-filing working draft, not yet public). Every certificate MUST express all six.

Two of the six anchors — `product.name` and `product.version_or_range` — appear in §9.4.3 above for structural reasons (they are vendor/product identity). The remaining four — `use_cases`, `languages`, `age_range`, `operating_countries` — appear in the `scope` block below. The six together define what the certificate certifies.

```json
{
  "scope": {
    "use_cases": ["q-and-a-tutor", "homework-feedback"],
    "subjects": ["mathematics"],
    "languages": ["en", "de"],
    "age_range": { "min": 11, "max": 14 },
    "operating_countries": ["DE", "AT"]
  }
}
```

- `use_cases` draws from a controlled vocabulary maintained alongside this schema (illustrative entries: `q-and-a-tutor`, `homework-feedback`, `formative-assessment`, `learning-companion`, `voice-language-practice`, `summative-grading`). New entries are added through methodology PRs and do not require a schema version bump.
- `subjects` MAY be omitted when the product is subject-agnostic; otherwise it SHOULD use curriculum-aligned subject names.
- `languages` lists languages actually tested under Layer 1 §1.4. Untested languages MUST NOT appear.
- `age_range` is inclusive at both ends.
- `operating_countries` lists the markets the certificate is valid for; outside these, the vendor MAY still operate but MUST NOT represent the mark as covering that market.

### 9.4.5 Tier and modifiers

```json
{
  "tier": {
    "name": "education_ready",
    "modifiers": ["inclusive"]
  }
}
```

- `tier.name` is one of `verified`, `education_ready`, `child_safe_excellence`.
- `tier.modifiers` is a list. `inclusive` (the `+Inclusive` horizontal modifier) is the only modifier in v0.1; future modifiers are added through the methodology revision process.

### 9.4.6 Classification (AI Act)

```json
{
  "classification": {
    "ai_act_class": "high_risk_annex_iii_3",
    "annex_iii_3_subactivities": ["evaluating_learning_outcomes"],
    "uses_gpai": true,
    "gpai_providers": ["openai:gpt-4o-mini@2024-07"],
    "art5_screen_passed": true,
    "art5_screen_at": "2026-04-10T08:30:00Z"
  }
}
```

- `ai_act_class` is one of: `out_of_scope_or_minimal_risk` | `transparency_only_art50` | `high_risk_annex_iii_3` | `high_risk_other`.
- `annex_iii_3_subactivities` is required if `ai_act_class` is `high_risk_annex_iii_3`. Entries from a controlled vocabulary matching Annex III §3 sub-activities.
- `uses_gpai`: whether the system integrates a general-purpose AI model. `gpai_providers` lists upstream providers when disclosed (provider:model@version).
- `art5_screen_passed` MUST be true for the certificate to exist; a failed Art. 5 screen stops the audit before any certificate is issued.

### 9.4.7 Layer results

```json
{
  "layer_results": {
    "layer1": {
      "status": "pass",
      "metrics": [
        {
          "metric": "faithfulness",
          "score": 0.93,
          "n_probes": 1200,
          "metric_scale": "ratio_0_to_1",
          "tiers_met": ["verified", "education_ready"],
          "notes": null
        },
        {
          "metric": "hallucination",
          "score": 0.06,
          "n_probes": 1000,
          "metric_scale": "rate_lower_is_better",
          "tiers_met": ["verified", "education_ready"],
          "notes": null
        }
      ]
    },
    "layer2": {
      "status": "pass",
      "pii_leakage_findings": [],
      "data_residency": "eu_processing_only",
      "prohibited_uses_screen_passed": true,
      "minor_findings": 1,
      "major_findings": 0
    },
    "layer3": {
      "status": "pass",
      "art5_screen_passed": true,
      "articles_9_to_15": "all_pass",
      "human_oversight": "genuine"
    },
    "layer4": {
      "status": "pass",
      "crisis_scenarios_passed": true,
      "rubric_scores": {
        "age_appropriate_content_mean": 3.4,
        "emotional_attachment_mean": 3.5,
        "dark_patterns": "pass"
      },
      "ethics_council_review": "passed"
    },
    "layer5": {
      "status": "pass",
      "sla_published": true,
      "model_versioning_compliant": true,
      "incident_notification_72h_acknowledged": true
    }
  }
}
```

- Each layer's `status` is one of `pass`, `not_evaluated`, or `fail`. A certificate cannot exist with `fail` on any required-for-tier layer.
- `not_evaluated` is reserved for layers the requested tier does not cover (e.g., Layer 4 at Verified).
- Metric scores include `tiers_met` listing the tier thresholds the score satisfies; this is computed from the methodology's published thresholds and serves the reader (no calculation required).
- `notes` is auditor-authored free text where a metric requires nuance (e.g., partial-language coverage, judge-version specifics).

### 9.4.8 Known limitations

```json
{
  "known_limitations": [
    "Cross-lingual fairness gap on Polish-language probes is 11% (Education-Ready threshold ≤15% met; Child-Safe Excellence threshold ≤8% not met).",
    "Inclusivity testing covered the English interface only; the +Inclusive modifier does not extend to the German interface.",
    "Subject coverage limited to mathematics; the product also offers science features which are NOT covered by this certificate."
  ]
}
```

- Known limitations are **auditor-authored**, not vendor-authored.
- The vendor cannot remove a known-limitation entry. The consortium controls this field precisely because it is the entry any vendor marketing would omit.
- Entries are written in plain language for procurement readers, not in methodology jargon.
- Entries that arise from minor findings are listed alongside the finding's remediation status in `audit_history` (§9.4.9).

### 9.4.9 Audit history

A chronological list of signed events. Each event is itself signed; the certificate's overall signature covers the issuance event and the schema, while subsequent events extend the history.

```json
{
  "audit_history": [
    {
      "event_id": "ev-01HFXX-001",
      "type": "issued",
      "at": "2026-05-16T10:00:00Z",
      "methodology_version": "0.1.1",
      "summary": "Initial issuance at Education-Ready tier.",
      "proof": { ... }
    },
    {
      "event_id": "ev-01HFXX-002",
      "type": "retested_post_major_update",
      "at": "2026-09-04T14:00:00Z",
      "methodology_version": "0.1.1",
      "trigger": "vendor model swap from gpt-4o-mini to gpt-4.1-mini, notified 2026-07-30",
      "summary": "Layer 1 and Layer 4 re-test completed within 60-day window; results consistent with original audit.",
      "proof": { ... }
    }
  ]
}
```

Event `type` values (extensible; v0.1):

- `issued` — initial issuance
- `renewed` — annual renewal; new card supersedes a predecessor with link
- `scope_amended` — material scope change with partial re-audit
- `retested_post_major_update` — re-test triggered by Layer 5 §5.2 major model update
- `suspended` — certificate suspended (with `reason`)
- `suspension_lifted` — suspension resolved
- `revoked` — certificate revoked (terminal; `reason` required)
- `withdrawn` — vendor voluntary withdrawal (with `reason`)
- `correction` — auditor-issued editorial correction of a non-substantive error in a previous event

Each event MUST include `event_id`, `type`, `at`, and (where applicable) `methodology_version`, `summary`, `reason`, and a `proof` block signed by the issuer.

### 9.4.10 Status

```json
{
  "status": {
    "current": "active",
    "as_of": "2026-05-16T10:00:00Z",
    "since": "2026-05-16T10:00:00Z",
    "reason": null
  }
}
```

- `current` is one of `active`, `suspended`, `revoked`, `expired`, `withdrawn`.
- `expired` is computed from `expirationDate`; it does not require an explicit event.
- `as_of` is the timestamp at which the registry computed and asserted this status; SHOULD be refreshed on every render of the card.
- `since` is when the current status became current.
- `reason` is required for `suspended`, `revoked`, `withdrawn`; consortium-authored.

The current status is **derived from the events in `audit_history`** plus `expirationDate`. The status field is included for ease of reading but is not the primary truth — applications verifying a certificate offline MUST reconstruct status from the audit-history events to detect tampering.

### 9.4.11 Verification

```json
{
  "verification": {
    "human_uri": "https://registry.custos-mark.org/certificates/01HFXX...",
    "machine_uri": "https://registry.custos-mark.org/certificates/01HFXX....json",
    "qr_uri": "https://registry.custos-mark.org/certificates/01HFXX....qr.png",
    "public_key_uri": "https://custos-mark.org/.well-known/issuer-keys.json"
  }
}
```

The `public_key_uri` resolves to the consortium's published verification keys; a verifier MAY follow `issuer.id` (a `did:web`) to the DID Document instead.

### 9.4.12 Report a concern

```json
{
  "report_concern_uri": "https://custos-mark.org/concerns/new?certificate=01HFXX..."
}
```

The "report a concern" channel is mandated by [06-tiers-scope-lifecycle.md §6.4](06-tiers-scope-lifecycle.md) and Regulations of Use §11.1. It MUST be present on every card.

### 9.4.13 Cryptographic proof

```json
{
  "proof": {
    "type": "Ed25519Signature2020",
    "created": "2026-05-16T10:00:00Z",
    "verificationMethod": "did:web:custos-mark.org:issuer:consortium#key-2026",
    "proofPurpose": "assertionMethod",
    "proofValue": "z3Kgs..."
  }
}
```

- Signature algorithm: Ed25519 at v0.1; the consortium MAY add additional suites in future versions.
- Canonicalization: [JCS (RFC 8785)](https://datatracker.ietf.org/doc/html/rfc8785) applied to the certificate excluding the `proof` block.
- The issuer's signing key is held on hardware security modules; key rotation MAY occur, and `verificationMethod` names the specific key by URI fragment.
- A verifier MUST be able to verify the signature **offline** given the certificate JSON and the issuer's published verification key (or DID Document).

## 9.5 What the signature covers, and what it does not

The `proof` block in §9.4.13 covers the entire credential at issuance, computed over the JCS canonicalization of the credential minus the `proof` block.

Specifically covered:

- All `credentialSubject` fields **as of issuance**, including the initial `issued` event in `audit_history`
- `issuanceDate`, `expirationDate`, `issuer`, `id`, `type`, `@context`, `card_schema_version`, `methodology_version`

Specifically **not** covered by the initial issuance signature:

- Subsequent events appended to `audit_history` (each has its own `proof`)
- The `status` block (which is a derived view; the primary truth is the event chain)
- Registry-side rendering metadata (HTML layout, parent-friendly text, etc.)

A verifier reconstructing trust in a certificate at a later date verifies:

1. The issuance signature, against the certificate sans subsequent events
2. Each event's signature, against the event payload
3. The chain — that each event's `prev_event_id` (if present) matches the prior event's `event_id`

## 9.6 HTML rendering — required visible structure

The HTML rendering on the registry MUST present, in this order from top of page:

1. **Status banner** (always visible, large, color-coded): `active` (green), `suspended` (amber), `revoked` (red), `expired` (grey), `withdrawn` (grey). The banner is the first thing a procurement reader sees and is never hidden behind a tab or fold.
2. **Header**: vendor trading name; product name; tier badge with modifiers; issuance and expiry dates; certificate ID with a copy button.
3. **Scope statement**: plain-language sentence followed by the precise six-anchor table — product, version, use-cases, languages, age range, operating countries.
4. **Known limitations**: explicit section, expanded by default, not collapsed below the fold. Each entry as a bullet.
5. **Layer-level results**: expandable per-layer panels. Verified-tier cards SHOULD show only the layers evaluated; Education-Ready and above MUST show every layer. Metric values, thresholds met, and notes are surfaced within each panel.
6. **Audit history**: chronological timeline of events with summaries and dates.
7. **Verification**: machine URI, QR code, link to the offline-verification instructions.
8. **Report a concern**: visible link, never below the page fold.

The HTML rendering MUST NOT:

- Hide or de-emphasize known limitations
- Compute a "composite score" from the per-layer results — the methodology refuses single-number marketing
- Permit vendor-supplied text in any block except the vendor's own trading-name and product-name fields
- Add disclaimers contradicting the certificate (e.g., "the vendor disputes this finding" — vendors have the appeal route under the consortium's Regulations of Use §10, not the service-card route)

The HTML SHOULD:

- Support dark and light themes
- Be accessible at WCAG 2.2 AA at minimum
- Render usefully without JavaScript (the registry is procurement infrastructure, not a single-page app)
- Print cleanly

## 9.7 Variant renderings

The registry MAY surface the same underlying JSON in audience-specific views without modifying the canonical record:

| Variant | Audience | What changes |
|---|---|---|
| Default | Procurement and general public | Full structure per §9.6 |
| Parent simplified | Parents | Single sentence verdict ("certified for use with children aged 11–14 in maths, in English and German, until May 2027"); link to "what does this mean" plain-language guide |
| Procurement table | School IT and ministries | Side-by-side comparison rows across multiple cards in a watchlist |
| API consumer | Integrators | The signed JSON itself, served at `.json` URI |

Variants are **derived** views. The canonical card is the signed JSON and the default HTML.

## 9.8 Lifecycle and events

Events that produce a new card or modify an existing card:

| Event | New card or update | Notes |
|---|---|---|
| Initial audit succeeds | New card | `issued` event |
| Annual renewal succeeds | New card | New `id`, `renewed` event linking `predecessor_certificate_id`; old card moves to `expired` status |
| Scope amendment | Update | `scope_amended` event appended; scope fields updated in place; new signature on the updated card |
| Major model update re-test | Update | `retested_post_major_update` event appended; layer results updated in place |
| Suspension | Update | `suspended` event appended; status changes to `suspended` |
| Suspension lifted | Update | `suspension_lifted` event appended; status returns to `active` |
| Revocation | Update | `revoked` event appended; status changes to `revoked`; card is **not** removed from registry |
| Voluntary withdrawal | Update | `withdrawn` event appended; status changes to `withdrawn`; card is **not** removed from registry |

A revoked or withdrawn card remains accessible at its canonical URI indefinitely. Registry retention is the consortium's accountability mechanism, not the vendor's marketing asset.

## 9.9 Privacy considerations

The card contains:

- The vendor's legal entity information (commercial, not personal)
- Pseudonymous auditor IDs (resolvable only via the auditor registry under its access policy)
- Optional council-member IDs for ethics-council reviews (pseudonymous, same resolution mechanism)

The card MUST NOT contain:

- Personal data of any natural person (other than the pseudonymous IDs above)
- Audit artefacts containing children's data, even hashed
- Vendor employees' names

Where minor findings reference processes performed by named individuals at the vendor, those names are redacted before the finding text appears in `known_limitations` or `audit_history.summary`.

## 9.10 Worked example

A minimum complete card (Education-Ready, no modifier):

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://custos-mark.org/contexts/v1"
  ],
  "id": "urn:custos-mark:certificate:01HFXX7ZQF9N3K2B0Y1MMVCM3T",
  "type": ["VerifiableCredential", "CustosMarkCertificate"],
  "issuer": {
    "id": "did:web:custos-mark.org:issuer:consortium",
    "name": "Custos consortium",
    "operating_lab": { "id": "lab-001", "name": "Custos Lab Ltd" },
    "lead_auditor_id": "auditor-a1f3",
    "second_auditor_id": "auditor-d27c"
  },
  "issuanceDate": "2026-05-16T10:00:00Z",
  "expirationDate": "2027-05-16T10:00:00Z",
  "credentialSubject": {
    "card_schema_version": "0.1",
    "methodology_version": "0.1.1",
    "harness_version": "0.1.0",
    "vendor": {
      "legal_name": "Example EdTech GmbH",
      "trading_name": "Example Tutor",
      "registered_country": "DE",
      "vendor_id": "did:web:example-edtech.com"
    },
    "product": {
      "name": "Example Math Tutor",
      "version_or_range": "3.2.x",
      "version_change_control_uri": "https://example-edtech.com/changelog/math-tutor"
    },
    "scope": {
      "use_cases": ["q-and-a-tutor", "homework-feedback"],
      "subjects": ["mathematics"],
      "languages": ["en", "de"],
      "age_range": { "min": 11, "max": 14 },
      "operating_countries": ["DE", "AT"]
    },
    "tier": { "name": "education_ready", "modifiers": [] },
    "classification": {
      "ai_act_class": "high_risk_annex_iii_3",
      "annex_iii_3_subactivities": ["evaluating_learning_outcomes"],
      "uses_gpai": true,
      "gpai_providers": ["openai:gpt-4o-mini@2024-07"],
      "art5_screen_passed": true
    },
    "layer_results": {
      "layer1": {
        "status": "pass",
        "metrics": [
          { "metric": "faithfulness", "score": 0.93, "n_probes": 1200, "tiers_met": ["verified", "education_ready"] },
          { "metric": "hallucination", "score": 0.06, "n_probes": 1000, "tiers_met": ["verified", "education_ready"] },
          { "metric": "refusal_quality", "score": 2.4, "n_probes": 200, "tiers_met": ["verified", "education_ready"], "metric_scale": "rubric_0_to_3" }
        ]
      },
      "layer2": { "status": "pass", "pii_leakage_findings": [], "data_residency": "eu_processing_only", "prohibited_uses_screen_passed": true, "minor_findings": 0, "major_findings": 0 },
      "layer3": { "status": "pass", "art5_screen_passed": true, "articles_9_to_15": "all_pass", "human_oversight": "genuine" },
      "layer4": { "status": "pass", "crisis_scenarios_passed": true, "rubric_scores": { "age_appropriate_content_mean": 3.1 }, "ethics_council_review": "not_required_at_tier" },
      "layer5": { "status": "pass", "sla_published": true, "model_versioning_compliant": true, "incident_notification_72h_acknowledged": true }
    },
    "known_limitations": [
      "Subject coverage limited to mathematics. Other subjects offered by the product are not covered by this certificate.",
      "Inclusivity testing not performed; the +Inclusive modifier is not awarded."
    ],
    "audit_history": [
      {
        "event_id": "ev-01HFXX-001",
        "type": "issued",
        "at": "2026-05-16T10:00:00Z",
        "methodology_version": "0.1.1",
        "summary": "Initial issuance at Education-Ready.",
        "proof": { "type": "Ed25519Signature2020", "created": "2026-05-16T10:00:00Z", "verificationMethod": "did:web:custos-mark.org:issuer:consortium#key-2026", "proofPurpose": "assertionMethod", "proofValue": "z3Kgs..." }
      }
    ],
    "status": { "current": "active", "as_of": "2026-05-16T10:00:00Z", "since": "2026-05-16T10:00:00Z", "reason": null },
    "verification": {
      "human_uri": "https://registry.custos-mark.org/certificates/01HFXX7ZQF9N3K2B0Y1MMVCM3T",
      "machine_uri": "https://registry.custos-mark.org/certificates/01HFXX7ZQF9N3K2B0Y1MMVCM3T.json",
      "qr_uri": "https://registry.custos-mark.org/certificates/01HFXX7ZQF9N3K2B0Y1MMVCM3T.qr.png",
      "public_key_uri": "https://custos-mark.org/.well-known/issuer-keys.json"
    },
    "report_concern_uri": "https://custos-mark.org/concerns/new?certificate=01HFXX7ZQF9N3K2B0Y1MMVCM3T"
  },
  "proof": {
    "type": "Ed25519Signature2020",
    "created": "2026-05-16T10:00:00Z",
    "verificationMethod": "did:web:custos-mark.org:issuer:consortium#key-2026",
    "proofPurpose": "assertionMethod",
    "proofValue": "z3Kgs..."
  }
}
```

The example uses illustrative cryptographic material. A real issuance produces real Ed25519 signatures.

## 9.11 Formal JSON Schema

A formal JSON Schema document (Draft 2020-12) corresponding to this template will be published in a future point release alongside the consortium's `https://custos-mark.org/contexts/v1` JSON-LD context. Until that document is published, this specification is the authoritative source.

## 9.12 Cross-references

- [README.md](../README.md) — versioning policy
- [06-tiers-scope-lifecycle.md §6.4](06-tiers-scope-lifecycle.md) — public transparency obligations
- [06-tiers-scope-lifecycle.md §6.6](06-tiers-scope-lifecycle.md) — the certificate as canonical artefact
- [07-glossary.md](07-glossary.md) — "Service card", "Scope"
- [08-references.md §8.6](08-references.md) — methodology-internal references (this document is added there)
- Regulations of Use §11.1 — public registry contents (the EUIPO-facing counterpart to this template)
- Regulations of Use §11.6 — withdrawal-of-public-information policy
