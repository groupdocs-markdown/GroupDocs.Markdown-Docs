---
id: export-text
url: markdown/net/convert/export-text
title: Xml to Md
weight: 5
description: "This article demonstrates how to convert Text to Markdown with GroupDocs.Markdown for .NET."
keywords: 
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

This example demonstrates how to convert Xml to Markdown.

```csharp
using (var converter = new MarkdownConverter("example.xml"))
{
    converter.Convert("output.md", options);
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)     