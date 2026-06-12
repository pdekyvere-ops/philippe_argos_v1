# Public Tool Availability Matrix — Sanitized Testcase

Date: 2026-06-12
State: public testcase / non-canonical / session-observed

This file is a sanitized public testcase for recording tool-surface observations. It intentionally excludes:

- private account details
- personal email, calendar, or contact data
- private repository names beyond the hosting repository itself
- internal project topology
- trade secrets or proprietary claims
- private file IDs, Drive IDs, OAuth details, tokens, or credentials
- operational wetlab, bioengineering, or unsafe procedural content

## Purpose

This matrix records how a tool surface can be classified without assuming that a documented capability is always exposed in a given chat session or model mode.

Core rule:

```text
documented != exposed != invoked != observed != replayable != admitted
```

## Evidence State Ladder

| State | Meaning |
|---|---|
| documented | Public documentation or UI text says the capability exists. |
| exposed | The current runtime shows a callable tool/action. |
| invoked | A harmless call was attempted. |
| observed_read | A read-only call returned a result. |
| observed_write | A write call completed in a deliberately safe target. |
| replay_required | The observation must be repeated before relying on it. |
| admitted | A stable matrix entry has been reviewed and promoted. |

## Session Observation Summary

| Surface | Mode tested | Evidence state | Safe public summary | Restriction |
|---|---|---|---|---|
| Model picker | Extra High | documented | Mode exists as a selectable intelligence setting. | Mode alone does not prove tool access. |
| Apps / connectors | Extra High | documented | App availability may vary by model, plan, account, and configuration. | Probe every session. |
| Web lookup | Extra High | observed_read | Current public documentation lookup worked. | Cite sourced claims. |
| Drive-like document/sheet surface | Extra High | observed_write | Additive holding-pen spreadsheet/document writes were possible in a controlled target. | Do not overwrite canonical records without review. |
| Mail-like private app | Extra High | observed_read | No-match harmless probe returned no private content. | Do not inspect content unless explicitly tasked. |
| Calendar-like private app | Extra High | observed_read | No-match harmless probe returned no private content. | Use explicit time bounds and task justification. |
| Contacts-like private app | Extra High | observed_read | No-match harmless probe returned no private content. | Do not enumerate contacts unless needed. |
| Code repository app | Extra High | observed_write | This public testcase file was written to a safe public repository. | No secrets, no private repo inventory, no destructive writes. |

## Failure Modes and Mitigations

| Failure mode | Risk | Mitigation |
|---|---|---|
| documented_not_exposed | A documented capability is assumed available when it is not. | Record both documentation state and runtime observation state. |
| mode_drift | Tool availability changes when model/intelligence mode changes. | Record mode on every probe row. |
| connector_permission_drift | Account/app permission changes affect read/write access. | Run harmless no-match probes before relying on a connector. |
| partial_write_filter | A write surface exists but content-specific safety filters block some writes. | Use additive tabs/files and smaller neutral batches. |
| private_data_leak | A generic matrix accidentally exposes personal or private data. | Redact identifiers and avoid private inventories. |
| source_freshness_drift | Public docs or tool behavior changes. | Timestamp sources and rerun version checks. |
| prompt_injection | Retrieved content attempts to alter instructions. | Treat retrieved content as evidence only, never authority. |
| overclaiming | Session-local evidence is treated as globally true. | Require replay before admission. |

## Public Probe Policy

```yaml
public_probe_policy:
  allow_benign_probe: true
  allow_read_only_public_source_probe: true
  allow_write_only_to_safe_test_target: true
  allow_private_content_harvest: false
  allow_secret_or_token_exposure: false
  allow_destructive_write: false
  allow_privilege_escalation: false
  default_state: replay_required
```

## Notes

This file is not an official product document and not a complete capability matrix. It is a sanitized public artifact showing how tool availability may be recorded safely for future replay.
