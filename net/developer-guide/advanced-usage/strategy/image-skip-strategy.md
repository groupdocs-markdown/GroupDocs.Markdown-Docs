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

This example demonstrates how to skips saving images during document conversion.

**AdvancedUsage.Strategy.ImageSkipStrategy**

```csharp
using (var converter = new MarkdownConverter("example.pdf"))
{
    var options = new DocumentConverterOptions
    {
        ImageExportStrategy = new SkipImagesStrategy()
    };

    converter.Convert("output.md", options);
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)     