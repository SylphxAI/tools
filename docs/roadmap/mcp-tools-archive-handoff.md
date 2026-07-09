# MCP Tools Archive Handoff Roadmap

This repository is retained for history, not for new MCP product development.
The SOTA path is to move useful capabilities into active product-owned Rust MCP
servers instead of reviving a broad TypeScript adapter monorepo.

## Archive Policy

- Keep existing source and package history readable.
- Do not publish new packages from this repository.
- Do not add new MCP servers or adapter abstractions here.
- Treat package READMEs as historical documentation.
- Reintroduce only selected capabilities through active product ADRs.

## Successor Mapping

| Historical capability | Successor owner |
| --- | --- |
| PDF extraction | `pdf-reader-mcp` |
| Filesystem operations | `filesystem-mcp` |
| RAG and code retrieval | `coderag` |
| Generic reader orchestration | `smart-reader-mcp` |
| Image evidence | `image-reader-mcp` |
| Video evidence | `video-reader-mcp` |
| Work-state and continuation | `mission-control` |
| Consultation and synthesis | `consultant-mcp` |
| Architecture understanding | `architecture-reader-mcp` |

Utility-only capabilities such as hashing, base64, XML, JSON, wait, and network
fetch should be revived only when an active product needs them as part of a
coherent workflow. They should not become standalone product surfaces unless a
new ADR proves demand, maintenance ownership, benchmarks, and release gates.

## Target Runtime Standard

Future MCP servers should use Rust for the server/runtime path. Rust owns:

- MCP protocol handling and transport selection;
- tool schema registration and validation;
- filesystem/network/process safety boundaries;
- deterministic error envelopes;
- request limits and backpressure;
- installable binary packaging;
- benchmarks and smoke proof.

TypeScript is acceptable for dashboards, generated clients, migration parity
tests, or temporary compatibility wrappers. It is not the target MCP server
runtime for this family.

## Roadmap

### Phase 0: Freeze

- Keep this repository archived.
- Keep package source unchanged.
- Make the archive state machine-readable through `PROJECT.md` and
  `.doctrine/project.json`.

### Phase 1: Map Demand

- For any requested legacy capability, first identify the active owner.
- File the implementation plan in that active repository, not here.
- Require a user job, package boundary, security model, benchmark target, and
  release gate before reviving the capability.

### Phase 2: Product-Owned Rebuild

- Rebuild selected capabilities in Rust inside the active product boundary.
- Use shared conformance fixtures only when they are generated from the owning
  product contract.
- Avoid a generic tools monorepo until repeated implementation proves a real
  shared primitive is needed.

### Phase 3: Portfolio Cleanup

- Keep this repository archived after handoff.
- Remove links from active docs that imply this repo is current.
- Use active product READMEs, ADRs, and manifests as the public entry points.

## Done State

The archive is done when future agents can tell, from the top-level docs and
manifest, that this repository is historical and that all active MCP product
work belongs in the Rust-native family repositories.
