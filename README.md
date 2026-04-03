# aura-stl

Aura standard library as an independent Aura project.

## Phase 2.1 Scope

This package defines a minimal, coherent STL surface in Aura itself:

- Algebraic core: `Option[T]`, `Result[T, E]`, `Ordering`
- Functional sequence: `Seq[T]` as persistent list
- Core helpers: small pure utility functions

The design goal is to keep this layer runtime-agnostic and mostly pure Aura.

## Phase 2.2 Runtime Boundary

The runtime boundary is intentionally tiny and centralized in `src/runtime.aura`.

- Syscall surface (current):
  - `write(fd, bytes)`
  - `write_stdout(bytes)`
  - `write_stderr(bytes)`
- Core memory helper placeholders:
  - `retain(value)`
  - `release(value)`

Higher-level behavior stays in Aura STL modules and must not bind kernel symbols directly.

## Layout

- `build.aura` - package manifest
- `src/*.aura` - library modules
- `src/*.test.aura` - unit-test modules
