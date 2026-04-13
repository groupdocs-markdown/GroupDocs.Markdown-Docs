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

```bash
dotnet add package GroupDocs.Markdown
```

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

// Or save directly to a file
MarkdownConverter.ToFile("business-plan.docx", "qs-word-to-md.md");
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "qs-word-to-md.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/getting-started/quick-start-guide/QsWordToMd/qs-word-to-md.md)
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

MarkdownConverter.ToFile("business-plan.pdf", "output/report.md", options);
// Images saved to output/images/
// Markdown references: ![](images/img-001.png)
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "qs-pdf-with-images.zip" >}}  
```text
output/images/img-001.png (3 KB)
output/images/img-002.jpg (73 KB)
output/images/img-003.jpg (76 KB)
output/report.md (7 KB)
```
[Download full output](/markdown/net/_output_files/getting-started/quick-start-guide/QsPdfWithImages/qs-pdf-with-images.zip)
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

using var converter = new MarkdownConverter("cost-analysis.xlsx");

// Inspect before converting
DocumentInfo info = converter.GetDocumentInfo();
Console.WriteLine($"Worksheets: {info.PageCount}");

// Convert
ConvertResult result = converter.Convert("qs-excel-options.md", options);

// Check warnings
foreach (string w in result.Warnings)
    Console.WriteLine($"Warning: {w}");
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "qs-excel-options.md" >}}  
```text
---
format: Xlsx
pages: 4
---


## Summary

| Category | FY2024 | FY2025 | FY2026 |
| --- | --- | --- | --- |
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/getting-started/quick-start-guide/QsExcelOptions/qs-excel-options.md)
{{< /tab >}}
{{< /tabs >}}

### What's next?

- [Supported document formats]({{< ref "markdown/net/getting-started/supported-document-formats.md" >}}) — full list of input formats
- [Image handling strategies]({{< ref "markdown/net/developer-guide/advanced-usage/strategy" >}}) — Base64, file system, skip, custom
- [Markdown flavor control]({{< ref "markdown/net/developer-guide/advanced-usage/markdown-flavor.md" >}}) — GitHub vs CommonMark
- [YAML front matter]({{< ref "markdown/net/developer-guide/advanced-usage/front-matter.md" >}}) — for static site generators
