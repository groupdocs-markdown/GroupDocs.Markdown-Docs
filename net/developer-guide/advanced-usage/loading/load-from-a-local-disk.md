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

## Load a document from a local disk

GroupDocs.Markdown provides two ways to load a file from a local disk: the static one-liner API and the instance-based API.

### Using static method

The simplest approach -- pass a file path and get the Markdown string back:

{{< tabs "load-disk-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Convert a local file to Markdown in one call
string markdown = MarkdownConverter.ToMarkdown("source.docx");

// Or save the result directly to a file
MarkdownConverter.ToFile("source.docx", "output.md");
```
{{< /tab >}}
{{< /tabs >}}

### Using instance API

When you need more control (e.g., conversion options, document info), create a `MarkdownConverter` instance:

{{< tabs "load-disk-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

using var converter = new MarkdownConverter("source.docx");

// Retrieve document metadata
DocumentInfo info = converter.GetDocumentInfo();
Console.WriteLine($"Format: {info.FileFormat}, Pages: {info.PageCount}");

// Convert to Markdown
ConvertResult result = converter.Convert();
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}
