# Pure.RelationalSchema.RichRelationalModel.Abstractions

Unified schema + relational-model interfaces for the **Pure** ecosystem — each interface merges a structural schema definition with its relational model counterpart into a single composable contract.

[![.NET build & test](https://github.com/kudima03/Pure.RelationalSchema.RichRelationalModel.Abstractions/actions/workflows/build-and-test.yml/badge.svg?branch=main)](https://github.com/kudima03/Pure.RelationalSchema.RichRelationalModel.Abstractions/actions/workflows/build-and-test.yml)
[![Build and Deploy](https://github.com/kudima03/Pure.RelationalSchema.RichRelationalModel.Abstractions/actions/workflows/publish-nuget.yml/badge.svg?branch=main)](https://github.com/kudima03/Pure.RelationalSchema.RichRelationalModel.Abstractions/actions/workflows/publish-nuget.yml)
[![NuGet](https://img.shields.io/nuget/v/Pure.RelationalSchema.RichRelationalModel.Abstractions)](https://www.nuget.org/packages/Pure.RelationalSchema.RichRelationalModel.Abstractions)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

## Overview

`Pure.RelationalSchema.RichRelationalModel.Abstractions` provides a thin layer of composite interfaces that simultaneously satisfy the structural schema contracts from `Pure.RelationalSchema.Abstractions` and the relational model contracts from `Pure.RelationalSchema.RelationalModel.Abstractions`. A type implementing `ITableRichRelationalModel`, for example, is usable wherever either `ITable` or `ITableRelationalModel` is expected — no adapter needed.

## Interfaces

| Interface | Extends | Description |
|-----------|---------|-------------|
| `ISchemaRichRelationalModel` | `ISchema`, `ISchemaRelationalModel` | A database schema that satisfies both the structural schema and relational model contracts |
| `ITableRichRelationalModel` | `ITable`, `ITableRelationalModel` | A table within a schema, carrying both structural and relational model identity |
| `IColumnRichRelationalModel` | `IColumn`, `IColumnRelationalModel` | A column satisfying both structural and relational model contracts |
| `IColumnTypeRichRelationalModel` | `IColumnType`, `IColumnTypeRelationalModel` | A column type (e.g. `integer`, `varchar`) satisfying both contract families |
| `IIndexRichRelationalModel` | `IIndex`, `IIndexRelationalModel` | An index satisfying both structural and relational model contracts |
| `IForeignKeyRichRelationalModel` | `IForeignKey`, `IForeignKeyRelationalModel` | A foreign key constraint satisfying both contract families |

All interfaces are in the `Pure.RelationalSchema.RichRelationalModel.Abstractions` namespace.

## Design Principles

- **Composable** — each interface is a single-line composition; no new members are added on top of the two parent contracts.
- **Immutable** — inherited from both contract families; all properties are read-only.
- **AOT-compatible** — the library is fully compatible with Native AOT compilation.

## Dependencies

- [`Pure.RelationalSchema.Abstractions`](https://github.com/kudima03/Pure.RelationalSchema.Abstractions/tree/1.2.0) — structural schema interfaces (`ISchema`, `ITable`, `IColumn`, `IColumnType`, `IIndex`, `IForeignKey`)
- [`Pure.RelationalSchema.RelationalModel.Abstractions`](https://github.com/kudima03/Pure.RelationalSchema.RelationalModel.Abstractions/tree/0.1.0-preview.1.0.0) — relational model interfaces that add identity and relational metadata to schema entities (`ISchemaRelationalModel`, `ITableRelationalModel`, etc.)

## Target Frameworks

- .NET 7
- .NET 8
- .NET 9
- .NET 10

## Installation

```shell
dotnet add package Pure.RelationalSchema.RichRelationalModel.Abstractions
```

## Usage

Implement the rich interfaces to get types that are accepted by both schema-layer and relational-model-layer APIs without casting or adapters:

```csharp
using Pure.RelationalSchema.RichRelationalModel.Abstractions;
using Pure.Primitives.Abstractions.Guid;
using Pure.Primitives.Abstractions.String;

public sealed class Schema : ISchemaRichRelationalModel
{
    public Schema(IGuid id, IString name)
    {
        Id = id;
        Name = name;
    }

    public IGuid Id { get; }
    public IString Name { get; }
}
```
