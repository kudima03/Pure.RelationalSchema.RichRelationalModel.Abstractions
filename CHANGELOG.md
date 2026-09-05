# Changelog

All notable changes to Pure.RelationalSchema.RichRelationalModel.Abstractions are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

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
