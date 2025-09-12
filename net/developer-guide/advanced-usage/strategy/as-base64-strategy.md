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

This example demonstrates how to embeds images as Base64 strings directly in the Markdown.

**AdvancedUsage.Strategy.AsBase64Strategy**

```csharp
using (var converter = new MarkdownConverter("example.pdf"))
{
    var options = new DocumentConverterOptions
    {
        ImageExportStrategy = new ExportImagesAsBase64Strategy()
    };

    converter.Convert("output.md", options);
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)     