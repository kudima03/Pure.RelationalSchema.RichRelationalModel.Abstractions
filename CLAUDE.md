# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

All `dotnet` commands must be run from the `./src` directory.

```bash
dotnet restore
dotnet build --no-restore -warnaserror
dotnet format --verify-no-changes        # check code style (CI enforces this)
csharpier check .                        # check code style (CI enforces this)
dotnet format && csharpier format .      # auto-fix code style
dotnet pack --configuration Release -p:PackageVersion=<version> --output .
```

There are no test projects in this repository — the CI pipeline only builds and checks formatting.

## Architecture

This is an **interfaces-only NuGet library** — no implementations, no tests, no logic. Every file defines exactly one interface.

Each interface is a single-line composition that merges a structural schema contract from `Pure.RelationalSchema.Abstractions` with its relational model counterpart from `Pure.RelationalSchema.RelationalModel.Abstractions`:

```
ISchemaRichRelationalModel      : ISchema,      ISchemaRelationalModel
ITableRichRelationalModel       : ITable,        ITableRelationalModel
IColumnRichRelationalModel      : IColumn,       IColumnRelationalModel
IColumnTypeRichRelationalModel  : IColumnType,   IColumnTypeRelationalModel
IIndexRichRelationalModel       : IIndex,        IIndexRelationalModel
IForeignKeyRichRelationalModel  : IForeignKey,   IForeignKeyRelationalModel
```

The purpose is to allow a single concrete type to satisfy both contract families without adapters or casts.

**Multi-targeting:** net7.0, net8.0, net9.0, net10.0. All interfaces must remain AOT-compatible (`IsAotCompatible = true`).

**Package validation:** `EnablePackageValidation = true` with `PackageValidationBaselineVersion = 0.1.0-preview.0.1.0`. Breaking changes fail the build.

**Publishing:** triggered by pushing a semver tag (pattern `*.*.*`). The tag becomes the `PackageVersion`. The package is published to both GitHub Packages and NuGet.org.

## Code Style

Enforced via `.editorconfig`, `dotnet format --verify-no-changes`, and `csharpier check .` in CI:

- No `var` — always use explicit types
- File-scoped namespace declarations (`namespace Foo;` not `namespace Foo { }`)
- `using` directives must be placed outside the namespace
- All accessibility modifiers must be explicit
- No expression-bodied methods or constructors; expression-bodied properties are required
- Braces required for all code blocks
- Max line length: 90 characters
- Private fields: `_camelCase`; no non-private instance fields allowed
- Interfaces prefixed with `I`; generic type parameters prefixed with `T`

## Commit Messages

Do not mention Claude or AI assistance in commit messages.
