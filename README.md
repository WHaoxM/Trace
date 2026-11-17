# Trace Runtime

Trace Runtime is the local-first execution and state foundation for Trace. It contains runtime and domain packages, data protocols and storage, Agent/MCP/Codex host adapters, integrations, SDKs, templates, and the local Runtime host. Product interaction design and web experiences are maintained separately; this repository's package map is an engineering boundary, not a product-module definition. Source presence or a successful build does not prove every product flow or experience is complete.

## Repository scope

This repository owns the runtime services and domain packages, data protocols and storage, Agent/MCP/Codex host adapters, integrations, SDKs, templates, and local Runtime host. The public TraceWeb client, landing page, and marketing site are maintained separately and are not copied here. The local HTTP host under `apps/desktop` is a Runtime adapter, not the TraceWeb repository.

User project databases, private profiles, credentials, local logs, generated builds, and dependency caches are not source inputs. The Runtime may read or create project state only through the documented, explicit project/profile boundaries.

## Implementation package groups

The seven groups in [packages/README](packages/README.md) describe implementation ownership and code organization. They are not the user-facing product modules, nor a prescribed sequence of product activities; those boundaries are maintained separately from this Runtime-only repository.

1. Core
2. Collaboration
3. Evolution
4. Product application
5. Host / integration
6. Template / bundle
7. SDK

The **Product application** group contains two distinct code packages, `product/workspace` and `product/application`; they retain separate state owners and transactions. `apps/*` and `native/` are executable or distribution boundaries, not additional domain modules.

## Start here

- [Architecture and ownership](docs/architecture.md)
- [First-time setup](docs/getting-started.md)
- [Local Runtime operations](docs/local-runtime.md)
- [Documentation index](docs/README.md)
- [Codex Plugin boundary](docs/codex-plugin.md)
- [Versioning and release policy](governance/version-policy.json)

The workspace requires Node.js `>=22.13.0` and pnpm `>=10.34.5` (see `package.json`). Install from the lockfile and build the current source before local use. A build is not a substitute for the required end-to-end validation of affected user flows.

## Imported baseline

The initial Runtime snapshot in this repository comes from `Tracehackthon/trace_backend` commit `26ea0f77876f840a5f173a19a6a924b8122422c0` (`trace-runtime` package version `0.8.0`). This migration preserves the existing `WHaoxM/Trace` history by adding the snapshot on top of its original `main`; it does not import the source repository's Git history. Runtime behavior, installation, and browser E2E are separate verification gates and are not implied by the import.
