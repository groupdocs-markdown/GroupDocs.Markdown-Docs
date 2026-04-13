---
id: load-from-a-local-disk
url: markdown/net/load-from-a-local-disk
title: Load from a local disk
weight: 1
description: "The following example demonstrates how to load file from local disk."
keywords: load file from local disk
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

GroupDocs.Markdown provides two ways to load a file from a local disk: the static one-liner API and the instance-based API.

### Using static method

The simplest approach -- pass a file path and get the Markdown string back:

{{< tabs "load-disk-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Convert a local file to Markdown in one call
string markdown = MarkdownConverter.ToMarkdown("business-plan.docx");

// Or save the result directly to a file
MarkdownConverter.ToFile("business-plan.docx", "load-disk-static.md");
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-disk-static.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/loading/load-from-a-local-disk/LoadDiskStatic/load-disk-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

When you need more control (e.g., conversion options, document info), create a `MarkdownConverter` instance:

{{< tabs "load-disk-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

using var converter = new MarkdownConverter("business-plan.docx");

// Retrieve document metadata
DocumentInfo info = converter.GetDocumentInfo();
Console.WriteLine($"Format: {info.FileFormat}, Pages: {info.PageCount}");

// Convert to Markdown
converter.Convert("load-disk-instance.md");
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-disk-instance.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/loading/load-from-a-local-disk/LoadDiskInstance/load-disk-instance.md)
{{< /tab >}}
{{< /tabs >}}
