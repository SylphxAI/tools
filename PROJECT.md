# MCP Tools Archive Project

This repository is a historical TypeScript MCP tools monorepo. It is archived
and no longer the canonical home for Sylphx MCP product development.

## Lifecycle

- State: `archived`
- Layer: `historical-tooling`
- Machine manifest: [`.doctrine/project.json`](./.doctrine/project.json)

## Current Purpose

- Preserve historical package source, release history, and migration context.
- Keep already published npm packages available for existing consumers.
- Point future work to the active Sylphx MCP family instead of extending this
  monorepo.

## Non-Goals

- Do not add new MCP servers here.
- Do not migrate this monorepo to Rust in place.
- Do not use `tools-adaptor-mcp` as the target adapter for new products.
- Do not treat package READMEs in this repo as current product strategy.

## Successor Direction

Active MCP products own their own Rust-native runtime and roadmap:

- Reader tools own file/media evidence extraction.
- Repository and code tools own project architecture and code retrieval.
- Filesystem tools own guarded local project operations.
- Mission Control owns work-state, continuation, and proof-chain coordination.

Capabilities from this archive may be reintroduced only by a new decision in the
owning active product repository. The target implementation pattern is a Rust
MCP server using the official Rust MCP SDK, with TypeScript limited to UI,
generated clients, migration tests, or explicitly time-boxed compatibility.
