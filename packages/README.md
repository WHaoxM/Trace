# Trace Runtime packages

`packages/` is the reusable runtime and product-domain foundation. The seven groups below are maintainer boundaries, not seven separate user-facing apps, product modules, or a list users configure one by one. They do not prescribe a product workflow. Internal packages stay independently owned where their data, lifecycle, or API requires it.

## Seven package groups

| Group | Representative packages | Responsibility | Boundary |
|---|---|---|---|
| **Core** | `core/protocol`, `core/data`, `core/storage`, `core/runtime`, `core/change-set`, `core/migration`, `core/operations`, `core/instance`, `core/observability`, `core/source` | Protocol identity, data lineage, versioned storage, lifecycle, migration, and runtime services | Does not depend on Codex, UI, or a specific integration |
| **Collaboration** | `core/continuity`, `core/collaboration-context`, `core/retrieval-evidence` | Work continuity, collaboration model, source map, and evidence of host access | Does not claim that a supplied pointer was read or used |
| **Evolution** | `core/case-capture`, `core/precedent`, `core/capability-candidate`, `core/capability` | Explicit case capture, precedents, capability candidates, validation, publication, and rollback | Does not automatically adopt a candidate or publish a capability |
| **Product application** | `product/workspace`, `product/application` | Shared-workspace commands and state, plus project initialization, profile lock, version checks, and project collaboration flows | These remain distinct package owners: Product Workspace owns `web.sqlite`; project collaboration uses the project's `.trace/` state and `trace.sqlite` |
| **Host / integration** | `host/*`, `integration/*`, `plugin/contract` | Codex/other host adapters and external-source connectors | Adapters do not own the core state machine or product data |
| **Template / bundle** | `template/*`, `bundle/*`, `templates/`, `profiles/`, `patches/` | Cold-start defaults and reproducible runtime combinations | Updating a template or profile does not silently replace a project instance |
| **SDK** | `sdk/*`, `python/sdk` | Explicit cross-process protocol clients and server boundary | SDKs do not implement a second runtime or write storage directly |

`apps/*` are executable entry points and composition hosts; `native/` is an installation/distribution boundary. Neither is an additional domain group. The current codebase also keeps Product Workspace and Project Collaboration Runtime as separate packages under the single **Product application** group; this logical grouping does not merge their storage owners or transactions.

## Repository boundary

- Trace Runtime contains runtime services, product-domain packages, Agent/MCP/Codex entry points, integrations, SDKs, templates, and local host adapters.
- TraceWeb's public site, landing page, and client repository remain separate. `apps/desktop` here is the Runtime's local HTTP host/adapter, not a copy of the TraceWeb repository.
- User project databases, local profiles, credentials, generated builds, and dependency caches are not source-controlled runtime inputs.

Start at the root [README](../README.md), then use the [architecture](../docs/architecture.md), [local runtime guide](../docs/local-runtime.md), and [documentation index](../docs/README.md).
