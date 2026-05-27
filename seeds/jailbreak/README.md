# Public seed — jailbreak scenarios

> **Public reference sample of jailbreak / prompt-injection scenarios used to evaluate Layer 1 §1.5 robustness.**
> Companion to [`../../standard/01-layer1-technical-measurement.md`](../../standard/01-layer1-technical-measurement.md).

## Purpose

Layer 1 §1.5.2 requires that "≥ 50%" of each audit's jailbreak scenarios be private to the Custos operating lab, and that a "representative seed sample" be publicly disclosed so that:

1. **Vendors** preparing for audit understand the *kind* of attack their product is tested against.
2. **Regulators** and **researchers** can assess the design of the test suite and critique it.
3. **Auditors** outside the lab can validate the format against the binding scenario schema before reviewing audit artefacts.

This directory holds that public seed sample. The remaining (≥ 50%) jailbreak scenarios used in any audit are drawn from the private library at [`custos-mark-private/scenarios/jailbreak/`](https://github.com/custos-mark/custos-mark-private), under the access controls described in that repository's ACCESS.md.

## Layout

```
seeds/jailbreak/
├── README.md                                    (this file)
├── jbr-direct-instruction-501.yaml
├── jbr-direct-instruction-502.yaml
├── jbr-role-confusion-501.yaml
├── ...
```

Public-seed IDs use the 500-series number range to make them visually distinguishable from private-library IDs (which use the 001-series and onward). Files conform to the binding scenario schema described in the auditor handbook ([`scenario-schema.md`](https://github.com/custos-mark/custos-mark-private/blob/main/auditor-handbook/scenario-schema.md)) and validate against the same loader.

## Coverage

The seed sample includes at least one scenario from each of the seven attack classes defined in Layer 1 §1.5.2:

| Attack class | Seed scenarios |
|---|---|
| `direct_instruction` | jbr-direct-instruction-501, jbr-direct-instruction-502 |
| `role_confusion` | jbr-role-confusion-501, jbr-role-confusion-502 |
| `authority_impersonation` | jbr-authority-impersonation-501, jbr-authority-impersonation-502 |
| `multi_turn_escalation` | jbr-multi-turn-escalation-501 |
| `indirect_injection` | jbr-indirect-injection-501 |
| `encoded_payload` | jbr-encoded-payload-501 |
| `social_engineering` | jbr-social-engineering-501 |

## Versioning

This seed sample is versioned with the methodology. Patch-level changes (additions, retirements, clarifications) are listed in the methodology [CHANGELOG.md](../../CHANGELOG.md).

## What does NOT live here

- The full audit library (≥ 300 scenarios per production audit per §1.5.2). That is in the private repo.
- Crisis scenarios (Layer 4 §4.3). Those have their own public seed location alongside this one as it grows.
- Child-prompt corpus (Layer 4 §4.1). Likewise.

## License

This directory inherits the methodology repository's CC BY 4.0 licence (see [LICENSE](../../LICENSE)). The seed scenarios are reference material; the goal of publishing them is to enable preparation, scrutiny, and replication of the methodology - not to enable vendors to over-train against the public sample.
