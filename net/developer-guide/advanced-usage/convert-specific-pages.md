---
id: convert-specific-pages
url: markdown/net/convert-specific-pages
title: Convert specific pages
weight: 4
description: "This article demonstrates how to convert specific document pages by page number using GroupDocs.Markdown for .NET API."
keywords: Convert page, Convert pages, Convert specific pages
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

## Convert specific pages

Use the `PageNumbers` property of `ConvertOptions` to convert only selected pages (or worksheets) from the source document. Page numbering starts from 1.

### Using static method

{{< tabs "specific-pages-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    PageNumbers = new[] { 1, 3 }
};

// Convert only pages 1 and 3
string markdown = MarkdownConverter.ToMarkdown("sample.docx", options);
Console.WriteLine(markdown);
```
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "specific-pages-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

using var converter = new MarkdownConverter("sample.docx");

var options = new ConvertOptions
{
    PageNumbers = new[] { 1, 3 }
};

ConvertResult result = converter.Convert(options);
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}

### Save specific pages to a file

{{< tabs "specific-pages-file">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    PageNumbers = new[] { 2, 4, 5 }
};

MarkdownConverter.ToFile("report.pdf", "partial-report.md", options);
```
{{< /tab >}}
{{< /tabs >}}
