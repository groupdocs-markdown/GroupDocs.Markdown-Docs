---
id: load-from-a-stream
url: markdown/net/load-from-a-stream
title: Load from a stream
weight: 2
description: "This example demonstrates how to load a file from a stream."
keywords: load a file from a stream
productName: GroupDocs.Markdown for .NET
hideChildren: False
---
This example demonstrates how to load a file from a stream.

**AdvancedUsage.Loading.LoadFromStream**

```csharp
using (Stream stream = File.Open("source.doc", FileMode.Open, FileAccess.ReadWrite))
using (var converter = new MarkdownConverter(stream))
{
	// ...
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)    