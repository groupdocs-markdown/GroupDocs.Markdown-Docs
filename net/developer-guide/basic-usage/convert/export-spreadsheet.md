---
id: export-spreadsheet
url: markdown/net/convert/export-spreadsheet
title: Xlsx to Md
weight: 3
description: "This article demonstrates how to convert Spreadsheet to Markdown with GroupDocs.Markdown for .NET."
keywords: 
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

This example demonstrates how to convert XLSX to Markdown.

```csharp
using (var converter = new MarkdownConverter("example.xlsx"))
{
    converter.Convert("output.md", options);
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)     