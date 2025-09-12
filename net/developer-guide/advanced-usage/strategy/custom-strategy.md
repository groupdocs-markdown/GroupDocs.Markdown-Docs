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

This example demonstrates how to user control how images are saved when a document is saved to Markdown format.

**AdvancedUsage.Strategy.CustomStrategy**

```csharp
using (var converter = new MarkdownConverter("example.pdf"))
{
	var options = new DocumentConverterOptions
	{
		ImageExportStrategy = new CustomImagesStrategy("D:\\Images\\", RenameImageHandler),
	};

    converter.Convert("output.md", options);
}

int _index = 0;
private static void RenameImageHandler(CustomImageSavingArgs args)
{
    args.SetOutputImageFileName($"rename_{_index}_{args.ImageFileName}");
    _index++;
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)     