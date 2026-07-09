# ADR-24: Archive Handoff For Legacy MCP Tools

- Status: accepted
- Date: 2026-07-09
- Owner: SylphxAI/tools

## Context

This repository contains a historical TypeScript monorepo of MCP tool packages,
core utilities, and adapter packages. It was archived on 2025-11-11 and marked
as no longer maintained.

The current Sylphx MCP strategy has moved to product-owned repositories with
stronger boundaries, evidence-first behavior, and Rust-native MCP runtimes. The
legacy monorepo should not become a parallel source of product direction or a
place to continue TypeScript adapter development.

## Decision

Keep this repository archived as historical source and migration context. Do not
resurrect it as an active MCP monorepo and do not migrate it to Rust in place.

When a capability from this archive is still commercially or technically useful,
the owning active product repository must make the decision and implement it
there. The target runtime pattern is Rust MCP server code using the official
Rust MCP SDK, with TypeScript limited to UI, generated clients, migration tests,
or explicitly time-boxed compatibility.

The repository-level documentation must point agents toward the active MCP
family and make clear that package-level READMEs are historical.

## Consequences

- The MCP family avoids two competing architecture tracks.
- Historical package source remains available for reference and migration.
- New work lands in active products with their own ADRs, roadmaps, CI, release
  gates, benchmarks, and production proof.
- Existing npm packages remain frozen; no new security or feature claims are
  made from this archive.

## Migration

1. Add a current-state project manifest for the archive.
2. Add an archive handoff roadmap that maps capability classes to active product
   owners.
3. Keep package code unchanged.
4. Re-archive the repository after the documentation PR lands.

## Verification

- JSON project manifest parses.
- Markdown diff is whitespace-clean.
- PR confirms this archive is not used as the target MCP runtime strategy.
