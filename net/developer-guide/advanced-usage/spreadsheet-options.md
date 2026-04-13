---
id: spreadsheet-options
url: markdown/net/spreadsheet-options
title: Spreadsheet conversion options
weight: 6
description: "Control column truncation, row limits, sheet separators, and hidden worksheets"
keywords: spreadsheet, Excel, CSV, columns, rows, truncation, worksheets
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

When converting spreadsheets, use these properties on `ConvertOptions` to control the Markdown table output.

### Column and row truncation

{{< tabs "spreadsheet-truncation">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    MaxColumns = 8,     // Only first 8 columns
    MaxRows = 50,       // Only first 50 data rows per sheet
};

MarkdownConverter.ToFile("cost-analysis.xlsx", "spreadsheet-truncation.md", options);

// Truncated columns/rows show "..." indicators.
// Warnings are reported in ConvertResult.Warnings.
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "spreadsheet-truncation.md" >}}  
```text
## Summary

| Category | FY2024 | FY2025 | FY2026 |
| --- | --- | --- | --- |
| Parts and materials | $1,325,000.00 | $1,480,000.00 | $1,620,000.00 |
| Manufacturing equipment | $900,500.00 | $980,000.00 | $1,050,000.00 |
| Warehousing | $420,000.00 | $510,000.00 | $590,000.00 |
| Shipping | $380,000.00 | $445,000.00 | $520,000.00 |
| Marketing | $250,000.00 | $340,000.00 | $480,000.00 |
| R&D | $180,000.00 | $230,000.00 | $310,000.00 |
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/spreadsheet-options/SpreadsheetTruncation/spreadsheet-truncation.md)
{{< /tab >}}
{{< /tabs >}}

### Sheet separator and hidden sheets

{{< tabs "spreadsheet-sheets">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    SheetSeparator = "\n---\n",    // Separator between worksheets
    IncludeHiddenSheets = false    // Skip hidden worksheets (default)
};

using var converter = new MarkdownConverter("cost-analysis.xlsx");
ConvertResult result = converter.Convert("spreadsheet-sheets.md", options);

foreach (string warning in result.Warnings)
    Console.WriteLine($"Warning: {warning}");
// e.g. "Worksheet 'Data' truncated at 50 rows."
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "spreadsheet-sheets.md" >}}  
```text
## Summary

| Category | FY2024 | FY2025 | FY2026 |
| --- | --- | --- | --- |
| Parts and materials | $1,325,000.00 | $1,480,000.00 | $1,620,000.00 |
| Manufacturing equipment | $900,500.00 | $980,000.00 | $1,050,000.00 |
| Warehousing | $420,000.00 | $510,000.00 | $590,000.00 |
| Shipping | $380,000.00 | $445,000.00 | $520,000.00 |
| Marketing | $250,000.00 | $340,000.00 | $480,000.00 |
| R&D | $180,000.00 | $230,000.00 | $310,000.00 |
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/spreadsheet-options/SpreadsheetSheets/spreadsheet-sheets.md)
{{< /tab >}}
{{< /tabs >}}

### Available options

| Property | Type | Default | Description |
|---|---|---|---|
| `MaxColumns` | `int` | `0` (unlimited) | Maximum columns per table |
| `MaxRows` | `int` | `0` (unlimited) | Maximum data rows per worksheet |
| `SheetSeparator` | `string` | `"\n---\n"` | Separator inserted between worksheets |
| `IncludeHiddenSheets` | `bool` | `false` | Whether to include hidden worksheets |
