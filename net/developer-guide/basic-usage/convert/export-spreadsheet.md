---
id: export-spreadsheet
url: markdown/net/convert/export-spreadsheet
title: Xlsx to Md
weight: 3
description: "This article demonstrates how to convert Spreadsheet to Markdown with GroupDocs.Markdown for .NET."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

Use GroupDocs.Markdown to convert XLSX and other spreadsheet files to Markdown tables. You can control how many columns and rows are included using spreadsheet-specific options.

### Using static method

The simplest way to convert a spreadsheet file:

{{< tabs "export-spreadsheet-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

// Convert XLSX to Markdown string
string markdown = MarkdownConverter.ToMarkdown("cost-analysis.xlsx");

// Or save directly to a file
MarkdownConverter.ToFile("cost-analysis.xlsx", "export-spreadsheet-static.md");
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-spreadsheet-static.md" >}}  
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
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-spreadsheet/ExportSpreadsheetStatic/export-spreadsheet-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API. The `ConvertOptions` class provides spreadsheet-specific properties such as `MaxColumns` and `MaxRows` to limit the size of the exported tables:

{{< tabs "export-spreadsheet-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("cost-analysis.xlsx");
var options = new ConvertOptions
{
    MaxColumns = 10,
    MaxRows = 100,
    HeadingLevelOffset = 1
};

converter.Convert("export-spreadsheet-instance.md", options);
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-spreadsheet-instance.md" >}}  
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
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-spreadsheet/ExportSpreadsheetInstance/export-spreadsheet-instance.md)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/net/getting-started/supported-document-formats" >}}).
