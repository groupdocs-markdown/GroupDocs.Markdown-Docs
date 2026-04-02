---
id: as-base64-strategy
url: markdown/net/as-base64-strategy
title: Save image as base64
weight: 1
description: "The listed articles below explain how to embeds images as Base64 strings directly in the Markdown."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

## Embed images as Base64

By default, `ConvertOptions` uses `ExportImagesAsBase64Strategy`, which embeds images as Base64 data URIs directly in the Markdown output. This keeps the output self-contained in a single file with no external image dependencies.

### Using static method

{{< tabs "base64-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Default behavior -- images are embedded as Base64
string markdown = MarkdownConverter.ToMarkdown("example.pdf");
Console.WriteLine(markdown);
```
{{< /tab >}}
{{< /tabs >}}

### Specifying the strategy explicitly

If you want to be explicit, set `ImageExportStrategy` to a new `ExportImagesAsBase64Strategy`:

{{< tabs "base64-explicit">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    ImageExportStrategy = new ExportImagesAsBase64Strategy()
};

using var converter = new MarkdownConverter("example.pdf");
ConvertResult result = converter.Convert(options);
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}
