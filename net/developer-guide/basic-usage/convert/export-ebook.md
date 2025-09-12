---
id: export-ebook
url: markdown/net/convert/export-ebook
title: Epub to Md
weight: 4
description: "This article demonstrates how to convert Ebook to Markdown with GroupDocs.Markdown for .NET."
keywords: 
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

This example demonstrates how to convert Epub to Markdown.


```csharp
using (var converter = new MarkdownConverter("example.epub"))
{
    converter.Convert("output.md", options);
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)     