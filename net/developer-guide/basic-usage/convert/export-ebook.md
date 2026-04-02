---
id: export-ebook
url: markdown/net/convert/export-ebook
title: Epub to Md
weight: 4
description: "This article demonstrates how to convert Ebook to Markdown with GroupDocs.Markdown for .NET."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

## Convert eBooks to Markdown

Use GroupDocs.Markdown to convert EPUB, MOBI, and other eBook formats to clean Markdown.

### Using static method

The simplest way to convert an eBook file:

{{< tabs "export-ebook-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
License.Set("GroupDocs.Markdown.lic");

// Convert EPUB to Markdown string
string markdown = MarkdownConverter.ToMarkdown("novel.epub");

// Or save directly to a file
MarkdownConverter.ToFile("novel.epub", "novel.md");
```
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-ebook-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("novel.epub");
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
