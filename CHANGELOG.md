# Changelog

All notable changes to Pure.RelationalSchema.RichRelationalModel.Abstractions are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [0.1.0-preview.0.2.0] — 2026-11-11

### Added

- Target framework **net11.0** alongside net7.0, net8.0, net9.0 and net10.0.

### Changed

- Updated `Pure.RelationalSchema.Abstractions` to 1.3.0 and
  `Pure.RelationalSchema.RelationalModel.Abstractions` to 0.1.0-preview.1.1.0.
- The NuGet package now includes `README.md`.

---

## [0.1.0-preview.0.1.0] — 2026-04-30

### Added

- **`ISchemaRichRelationalModel`** — composite interface merging `ISchema` and
  `ISchemaRelationalModel` into a single contract for a database schema.
- **`ITableRichRelationalModel`** — composite interface merging `ITable` and
  `ITableRelationalModel`.
- **`IColumnRichRelationalModel`** — composite interface merging `IColumn` and
  `IColumnRelationalModel`.
- **`IColumnTypeRichRelationalModel`** — composite interface merging
  `IColumnType` and `IColumnTypeRelationalModel`.
- **`IIndexRichRelationalModel`** — composite interface merging `IIndex` and
  `IIndexRelationalModel`.
- **`IForeignKeyRichRelationalModel`** — composite interface merging
  `IForeignKey` and `IForeignKeyRelationalModel`.
