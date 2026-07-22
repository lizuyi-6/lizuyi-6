# Repository Portfolio Map

> This file is the source of truth for deciding whether a repository is a flagship product, reusable package, experiment, mirror, or archive candidate.

## Operating rules

1. A new repository must have an independent user, release cycle, permission boundary, or deployment target.
2. When more than roughly one third of the required capability already exists elsewhere, add an app, package, plugin, or feature instead of creating a repository.
3. Shared infrastructure belongs in reusable packages: AI providers, authentication, storage, tracing, document ingestion, reporting, integrations, and UI primitives.
4. Experiments have an explicit graduation or archive condition.
5. Mirrors, recovered snapshots, datasets, vendor exports, and historical code must be labelled clearly and must not appear as current products.

## Flagship products

| Repository | Role | Decision |
|---|---|---|
| `zaochang` | Creator product community and incubation ecosystem | Keep as flagship |
| `ReactorOS` | Industrial edge supervisor and safety control system | Keep as flagship |
| `rust-norion` | Local inference control and memory research | Keep as flagship |
| `anion` | AI interview, analysis, memory, and career workspace | Keep as flagship |
| `newide` | Agentic IDE platform | Keep as flagship |
| `weagreeto` | Collaborative group decision and travel application | Keep as product |
| `hks` | AI intellectual-property coworker | Keep after security remediation |
| `Networksafe` | Internal security-hardware platform | Keep private and product-scoped |

## Product lines to consolidate

### Finance automation

Primary repository: `automoney`

- Migrate useful backend, schema, and mini-program work from `finauto`.
- Archive `finauto` after migration.
- Shared candidates: `accounting-domain`, `document-ingestion`, `audit-events`.

### Agent platform

Product applications:

- `aethermind`
- `daily-work-summary`
- `client-evaluator`

Reusable packages to extract:

- `claudemem` -> `agent-memory`
- `agent-tracer` -> `agent-observability`
- `apimiddle` -> `model-gateway` or shared API gateway
- common Feishu, GitHub, local activity, report, and document adapters

### Creator tools

Primary product: `content-ai`

- `trendmonitor` -> trend ingestion package
- `promo-video-generator` -> video output package
- `doc2md` -> document conversion package
- `pdftranslate` -> translation/document package
- `fontcrafter` -> lab or creator package after validation

### WeAgreeTo

Primary repository: `weagreeto`

- `qx` is a recovered build/snapshot, not a second active product.
- Move durable recovery documentation into `weagreeto/docs/recovery` or keep `qx` as an archived snapshot.

### AI development tools

- Keep `newide` as the IDE product.
- Keep `usager` as the subscription and usage monitor.
- Mark `claude-code-source`, `openclaw-backup`, and `manus` as mirrors, upstream experiments, or archive candidates.

## Hardware, edge, and security

These repositories have distinct deployment or permission boundaries and should not be merged only to reduce repository count:

- `Networksafe`
- `wbmid`
- `fluxguard-pcb`
- `aetherguard-security-dataset`
- `ReactorOS`
- `rust-norion`
- `ai-code-detector`

Extract stable interfaces only when at least two products consume them, for example:

- device protocols
- audit event schemas
- edge security primitives
- hardware acceptance contracts

## Labs and archive candidates

| Repository | Recommended action |
|---|---|
| `day0` | Archive; content already belongs in `code-journal` |
| `day1` | Archive; content already belongs in `code-journal` |
| `ls01` | Move to labs or archive until it has a concrete product boundary |
| `loger-clone` | Move to labs or archive unless it has unique maintained code |
| `image-hosting` | Remove if empty, or define it as an explicit asset repository |
| `personalab-demo` | Archive after demonstration use |
| `openclaw-backup` | Label as mirror/backup and archive |
| `claude-code-source` | Label as mirror and archive |
| `manus` | Convert to a proper fork or archive |
| `qx` | Archive as a WeAgreeTo recovery snapshot |
| `finauto` | Archive after migration into `automoney` |

`code-journal` remains the private historical archive. Do not split archived learning projects back into active repositories.

## Immediate security and privacy work

- Rotate the exposed provider credential previously committed in `hks`; removing it from the current file does not invalidate the leaked value.
- Remove all hard-coded credential fallbacks and purge them from Git history.
- Review public READMEs for personal phone numbers, exact addresses, customer links, internal identifiers, and stale pricing data.
- Enable secret scanning and push protection where available.

## Repository lifecycle

Every repository should carry one lifecycle label in its README:

- `ACTIVE_PRODUCT`
- `ACTIVE_PACKAGE`
- `LAB`
- `MIRROR`
- `RECOVERED_SNAPSHOT`
- `ARCHIVED`

Review this map whenever a product is created, merged, transferred, or archived.
