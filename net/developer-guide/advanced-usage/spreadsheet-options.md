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

## Spreadsheet conversion options

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

string md = MarkdownConverter.ToMarkdown("large-data.xlsx", options);

// Truncated columns/rows show "..." indicators.
// Warnings are reported in ConvertResult.Warnings.
```
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

using var converter = new MarkdownConverter("workbook.xlsx");
ConvertResult result = converter.Convert(options);

foreach (string warning in result.Warnings)
    Console.WriteLine($"Warning: {warning}");
// e.g. "Worksheet 'Data' truncated at 50 rows."
```
{{< /tab >}}
{{< /tabs >}}

### Available options

| Property | Type | Default | Description |
|---|---|---|---|
| `MaxColumns` | `int` | `0` (unlimited) | Maximum columns per table |
| `MaxRows` | `int` | `0` (unlimited) | Maximum data rows per worksheet |
| `SheetSeparator` | `string` | `"\n---\n"` | Separator inserted between worksheets |
| `IncludeHiddenSheets` | `bool` | `false` | Whether to include hidden worksheets |
