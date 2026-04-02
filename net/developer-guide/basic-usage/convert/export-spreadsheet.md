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

## Convert Excel Spreadsheets to Markdown

Use GroupDocs.Markdown to convert XLSX and other spreadsheet files to Markdown tables. You can control how many columns and rows are included using spreadsheet-specific options.

### Using static method

The simplest way to convert a spreadsheet file:

{{< tabs "export-spreadsheet-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
License.Set("GroupDocs.Markdown.lic");

// Convert XLSX to Markdown string
string markdown = MarkdownConverter.ToMarkdown("financial-data.xlsx");

// Or save directly to a file
MarkdownConverter.ToFile("financial-data.xlsx", "financial-data.md");
```
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API. The `ConvertOptions` class provides spreadsheet-specific properties such as `MaxColumns` and `MaxRows` to limit the size of the exported tables:

{{< tabs "export-spreadsheet-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("financial-data.xlsx");
var options = new ConvertOptions
{
    MaxColumns = 10,
    MaxRows = 100,
    HeadingLevelOffset = 1
};

ConvertResult result = converter.Convert(options);
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/net/getting-started/supported-document-formats" >}}).
