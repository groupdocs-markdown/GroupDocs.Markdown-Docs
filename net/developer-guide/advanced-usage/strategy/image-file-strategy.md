---
id: image-file-strategy
url: markdown/net/image-file-strategy
title: Save image as file
weight: 2
description: "The listed articles below explain how to saves images to the file system during document conversion."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

## Save images to the file system

Use `ExportImagesToFileSystemStrategy` to save images as separate files during conversion. The Markdown output will contain image references pointing to the exported files.

### Basic usage

{{< tabs "image-file-basic">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    ImageExportStrategy = new ExportImagesToFileSystemStrategy("output/images")
};

MarkdownConverter.ToFile("example.pdf", "output/document.md", options);
```
{{< /tab >}}
{{< /tabs >}}

### Using ImagesRelativePath

By default, image references in the Markdown use the full `ImagesFolder` path. Set `ImagesRelativePath` to produce portable, relative image links:

{{< tabs "image-file-relative">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var strategy = new ExportImagesToFileSystemStrategy("output/images")
{
    ImagesRelativePath = "images"
};

var options = new ConvertOptions
{
    ImageExportStrategy = strategy
};

MarkdownConverter.ToFile("example.pdf", "output/document.md", options);

// Markdown output contains: ![](images/img-001.png)
// Image file saved to:     output/images/img-001.png
```
{{< /tab >}}
{{< /tabs >}}
