# Scope-First Asset Ledger

**Offline-first evidence correlation for authorized security reviews.**

Scope-First Asset Ledger is a Go command-line project that normalizes **locally supplied** JSONL or CSV observations, evaluates them against a declared scope policy, preserves source provenance, and generates Markdown, JSON, or Graphviz DOT reports.

> **Authorization boundary:** the project does not enumerate domains, probe hosts, crawl URLs, authenticate, contact APIs, or make network requests. It only processes files an operator provides locally.

## Why it exists

Asset-discovery and HTTP-probing tools already perform collection. The difficult handoff is converting mixed outputs into a reviewable inventory that explains what is in scope, what needs review, and where each record came from. This project focuses on that handoff rather than duplicating a scanner.

## Validated capabilities

| Capability | v0.1 behavior |
|---|---|
| Local imports | Reads documented JSONL, NDJSON, and CSV evidence formats. |
| Scope policy | Evaluates declared root domains, exact hosts, and CIDRs. |
| Review states | Labels every entity `in-scope`, `review`, or `out-of-scope` with a reason. |
| Provenance | Retains source and local file/line references after deduplication. |
| Reports | Produces deterministic Markdown, JSON, and DOT outputs. |
| Validation | Includes unit tests, static vetting, safe fixtures, and CI configuration. |

## Local validation record

The initial implementation was formatted, tested, and vetted locally using documentation-reserved domains and IP ranges. The CLI was exercised with JSONL and CSV examples, plus Markdown and DOT report output. It is an **inventory/evidence-correlation utility**, not a vulnerability scanner or risk-scoring engine.

## Source archive

The complete structured Go source, tests, safe fixtures, documentation, CI workflow, license, and security policy are available in [`scope-first-asset-ledger-source.zip`](./scope-first-asset-ledger-source.zip). The archive preserves the repository layout while direct Git publishing is being restored.

```text
scope policy + local JSONL/CSV
              │
              ▼
     parse + normalize + validate
              │
              ▼
    scope decision + provenance ledger
              │
        ┌─────┼─────┐
        ▼     ▼     ▼
     Markdown JSON  DOT
```

## Intended evolution

The next steps are fixture-backed import adapters, a human review-decision file, and signed report manifests. New capabilities will remain offline-first unless an explicit authorization-aware network design is reviewed first.

## Project status

This is an early, documented portfolio project. Feedback on input normalization, scope-decision semantics, deterministic reporting, and safe evidence handoff is welcome.

## License and security

The source archive includes an MIT license, `SECURITY.md`, and contribution guidance. Please do not submit real targets, credentials, customer data, or exploit chains in issues or examples.
