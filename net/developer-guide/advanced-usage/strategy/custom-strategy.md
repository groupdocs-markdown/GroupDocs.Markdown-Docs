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

## Custom image saving strategy

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

MarkdownConverter.ToFile("document.docx", "output/document.md", options);
```
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

MarkdownConverter.ToFile("document.docx", "output/document.md", options);
```
{{< /tab >}}
{{< /tabs >}}
