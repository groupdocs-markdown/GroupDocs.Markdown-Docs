---
id: image-skip-strategy
url: markdown/net/image-skip-strategy
title: Skip image
weight: 3
description: "The listed articles below explain how to skips saving images during document conversion."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

## Skip images during conversion

Use `SkipImagesStrategy` when you want to convert a document to Markdown without exporting any images. Image references will be omitted from the output.

### Using static method

{{< tabs "skip-images-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    ImageExportStrategy = new SkipImagesStrategy()
};

string markdown = MarkdownConverter.ToMarkdown("example.pdf", options);
Console.WriteLine(markdown);
```
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "skip-images-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    ImageExportStrategy = new SkipImagesStrategy()
};

using var converter = new MarkdownConverter("example.pdf");
ConvertResult result = converter.Convert(options);
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}
