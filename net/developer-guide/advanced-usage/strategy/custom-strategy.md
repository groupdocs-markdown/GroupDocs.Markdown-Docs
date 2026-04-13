---
id: custom-strategy
url: markdown/net/custom-strategy
title: Save image by custom strategy
weight: 4
description: "The listed articles below explain how to user control how images are saved when a document is saved to Markdown format."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

Use `CustomImagesStrategy` with the `IImageSavingHandler` interface for full control over how each image is saved during conversion. You can rename files, redirect output to a custom stream, or replace image content entirely.

### Rename images with IImageSavingHandler

Implement `IImageSavingHandler` to customize saving logic for each image:

{{< tabs "custom-strategy-rename">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Implement the IImageSavingHandler interface
public class RenameHandler : IImageSavingHandler
{
    private int _index;

    public void Handle(CustomImageSavingArgs args)
    {
        args.SetOutputImageFileName($"img_{_index}_{args.ImageFileName}");
        _index++;
    }
}

// Use the handler with CustomImagesStrategy
var handler = new RenameHandler();
var options = new ConvertOptions
{
    ImageExportStrategy = new CustomImagesStrategy("output/images", handler)
};

MarkdownConverter.ToFile("business-plan.docx", "output/document.md", options);
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "custom-strategy-rename.zip" >}}  
```text
output/document.md (5 KB)
output/images/img_0_img-001.png (4 KB)
output/images/img_1_img-002.jpg (41 KB)
output/images/img_2_img-003.png (14 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/strategy/custom-strategy/CustomStrategyRename/custom-strategy-rename.zip)
{{< /tab >}}
{{< /tabs >}}

### Replace image content with SetReplacementImage

Use `SetReplacementImage` to substitute the original image with different content (e.g., a watermarked version or a placeholder):

{{< tabs "custom-strategy-replace">}}
{{< tab "C#" >}}
```csharp
using System.IO;
using GroupDocs.Markdown;

public class WatermarkHandler : IImageSavingHandler
{
    public void Handle(CustomImageSavingArgs args)
    {
        // Replace the original image with a custom placeholder
        Stream placeholder = File.OpenRead("placeholder.png");
        args.SetReplacementImage(placeholder);
        args.SetOutputImageFileName("placeholder.png");
    }
}

var handler = new WatermarkHandler();
var options = new ConvertOptions
{
    ImageExportStrategy = new CustomImagesStrategy("output/images", handler)
};

MarkdownConverter.ToFile("business-plan.docx", "output/document.md", options);
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "custom-strategy-replace.zip" >}}  
```text
output/document.md (5 KB)
output/images/placeholder.png (14 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/strategy/custom-strategy/CustomStrategyReplace/custom-strategy-replace.zip)
{{< /tab >}}
{{< /tabs >}}
