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

MarkdownConverter.ToFile("business-plan.pdf", "output/document.md", options);
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "image-file-basic.zip" >}}  
```text
output/document.md (7 KB)
output/images/img-001.png (3 KB)
output/images/img-002.jpg (73 KB)
output/images/img-003.jpg (76 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/strategy/image-file-strategy/ImageFileBasic/image-file-basic.zip)
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

MarkdownConverter.ToFile("business-plan.pdf", "output/document.md", options);

// Markdown output contains: ![](images/img-001.png)
// Image file saved to:     output/images/img-001.png
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "image-file-relative.zip" >}}  
```text
output/document.md (7 KB)
output/images/img-001.png (3 KB)
output/images/img-002.jpg (73 KB)
output/images/img-003.jpg (76 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/strategy/image-file-strategy/ImageFileRelative/image-file-relative.zip)
{{< /tab >}}
{{< /tabs >}}
