---
id: export-pdf
url: markdown/net/convert/export-pdf
title: Pdf to Md
weight: 1
description: "This article demonstrates how to convert PDF to Markdown with GroupDocs.Markdown for .NET."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

## Convert PDF to Markdown

Use GroupDocs.Markdown to convert PDF documents to clean Markdown.

### Using static method

The simplest way to convert a PDF file:

{{< tabs "export-pdf-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
License.Set("GroupDocs.Markdown.lic");

// Convert PDF to Markdown string
string markdown = MarkdownConverter.ToMarkdown("business-plan.pdf");

// Or save directly to a file
MarkdownConverter.ToFile("business-plan.pdf", "business-plan.md");
```
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-pdf-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("business-plan.pdf");
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
