---
id: export-wordprocessing
url: markdown/net/convert/export-wordprocessing
title: Docx to Md
weight: 2
description: "This article demonstrates how to convert Words to Markdown with GroupDocs.Markdown for .NET."
keywords: 
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

This example demonstrates how to convert DOCX to Markdown.


```csharp
using (var converter = new MarkdownConverter("example.docx"))
{
    converter.Convert("output.md", options);
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)     