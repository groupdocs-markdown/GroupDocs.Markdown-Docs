---
id: quick-start-guide
url: markdown/net/quick-start-guide
title: Quick start guide
weight: 0
description: "Get started with GroupDocs.Markdown for .NET in minutes — convert documents to Markdown with a single line of code"
keywords: quick start, getting started, convert, example
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## Quick start guide

This guide shows you how to convert documents to Markdown with GroupDocs.Markdown for .NET. You'll have working code in under 2 minutes.

### How it works

{{< mermaid class="text-center" >}}
flowchart LR
    A["Input Document\n(DOCX, PDF, XLSX, EPUB, ...)"]
    B["MarkdownConverter"]
    C["Markdown Output\n(.md file or string)"]
    A --> B --> C
{{< /mermaid >}}

### Prerequisites

1. Install the NuGet package:

{{< tabs "qs-install">}}
{{< tab ".NET CLI" >}}
```bash
dotnet add package GroupDocs.Markdown
```
{{< /tab >}}
{{< tab "Package Manager" >}}
```powershell
Install-Package GroupDocs.Markdown
```
{{< /tab >}}
{{< /tabs >}}

2. Add the namespace:
```csharp
using GroupDocs.Markdown;
```

### Example 1: Convert Word to Markdown

The simplest conversion — one line of code:

{{< tabs "qs-word-to-md">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Convert a Word document to Markdown
string markdown = MarkdownConverter.ToMarkdown("business-plan.docx");
Console.WriteLine(markdown);

// Or save directly to a file
MarkdownConverter.ToFile("business-plan.docx", "business-plan.md");
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}

### Example 2: Convert PDF with image export

Save a PDF to Markdown with images extracted to a folder:

{{< tabs "qs-pdf-with-images">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    ImageExportStrategy = new ExportImagesToFileSystemStrategy("output/images")
    {
        ImagesRelativePath = "images"
    }
};

MarkdownConverter.ToFile("report.pdf", "output/report.md", options);
// Images saved to output/images/
// Markdown references: ![](images/img-001.png)
```
{{< /tab >}}
{{< tab "report.pdf" >}}
{{< tab-text >}}
`report.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/report.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}

### Example 3: Convert Excel with options

Convert a spreadsheet with column truncation and front matter:

{{< tabs "qs-excel-options">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    MaxColumns = 8,
    MaxRows = 50,
    IncludeFrontMatter = true,
    Flavor = MarkdownFlavor.GitHub
};

using var converter = new MarkdownConverter("budget.xlsx");

// Inspect before converting
DocumentInfo info = converter.GetDocumentInfo();
Console.WriteLine($"Worksheets: {info.PageCount}");

// Convert
ConvertResult result = converter.Convert(options);
Console.WriteLine(result.Content);

// Check warnings
foreach (string w in result.Warnings)
    Console.WriteLine($"Warning: {w}");
```
{{< /tab >}}
{{< tab "budget.xlsx" >}}
{{< tab-text >}}
`budget.xlsx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/budget.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< /tabs >}}

### What's next?

- [Supported document formats]({{< ref "markdown/net/getting-started/supported-document-formats.md" >}}) — full list of input formats
- [Image handling strategies]({{< ref "markdown/net/developer-guide/advanced-usage/strategy" >}}) — Base64, file system, skip, custom
- [Markdown flavor control]({{< ref "markdown/net/developer-guide/advanced-usage/markdown-flavor.md" >}}) — GitHub vs CommonMark
- [YAML front matter]({{< ref "markdown/net/developer-guide/advanced-usage/front-matter.md" >}}) — for static site generators
