---
id: export-wordprocessing
url: markdown/net/convert/export-wordprocessing
title: Docx to Md
weight: 2
description: "This article demonstrates how to convert Words to Markdown with GroupDocs.Markdown for .NET."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

## Convert Word Documents to Markdown

Use GroupDocs.Markdown to convert DOCX and other Word documents to clean Markdown.

### Using static method

The simplest way to convert a Word file:

{{< tabs "export-word-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
License.Set("GroupDocs.Markdown.lic");

// Convert DOCX to Markdown string
string markdown = MarkdownConverter.ToMarkdown("report.docx");

// Or save directly to a file
MarkdownConverter.ToFile("report.docx", "report.md");
```
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-word-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("report.docx");
var options = new ConvertOptions
{
    ImageExportStrategy = new ExportImagesToFileSystemStrategy("images")
    {
        ImagesRelativePath = "images"
    },
    HeadingLevelOffset = 1
};

ConvertResult result = converter.Convert(options);
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/net/getting-started/supported-document-formats" >}}).
