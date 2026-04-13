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
MarkdownConverter.ToFile("business-plan.docx", "specific-pages-static.md", options);
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "specific-pages-static.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/convert-specific-pages/SpecificPagesStatic/specific-pages-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "specific-pages-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

using var converter = new MarkdownConverter("business-plan.docx");

var options = new ConvertOptions
{
    PageNumbers = new[] { 1, 3 }
};

converter.Convert("specific-pages-instance.md", options);
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "specific-pages-instance.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/convert-specific-pages/SpecificPagesInstance/specific-pages-instance.md)
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

MarkdownConverter.ToFile("business-plan.pdf", "specific-pages-file.md", options);
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "specific-pages-file.md" >}}  
```text
**Table of Contents**

Meridian Outdoor Co. — Business Plan .........................................................................................1FY2026 Strategic Plan.................................................................................................................1Table of Contents.............................................................................................................................2

1. Executive Summary..................................................
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/convert-specific-pages/SpecificPagesFile/specific-pages-file.md)
{{< /tab >}}
{{< /tabs >}}
