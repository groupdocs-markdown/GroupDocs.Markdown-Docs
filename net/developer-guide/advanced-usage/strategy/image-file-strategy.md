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

This example demonstrates how to saves images to the file system during document conversion.

**AdvancedUsage.Strategy.ImageFileStrategy**

```csharp
using (var converter = new MarkdownConverter("example.pdf"))
{
    var options = new DocumentConverterOptions
    {
        ImageExportStrategy = new ExportImagesToFileSystemStrategy("D:\\Images\\")
    };

    converter.Convert("output.md", options);
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)     