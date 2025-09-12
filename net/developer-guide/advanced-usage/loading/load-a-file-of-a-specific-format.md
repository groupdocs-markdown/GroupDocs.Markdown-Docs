---
id: load-a-file-of-a-specific-format
url: markdown/net/load-a-file-of-a-specific-format
title: Load a file of a specific format
weight: 3
description: "This example demonstrates how to load a file of some particular format."
keywords: load a file
productName: GroupDocs.Markdown for .NET
hideChildren: False
---
This example demonstrates how to load a file of some particular format.

**AdvancedUsage.Loading.LoadingFileOfSpecificFormat**

```csharp
// Explicitly specifying the format of a file to load you can spare some time on detecting the format
var loadOptions = new LoadOptions(FileFormat.Spreadsheet);

using (var converter = new MarkdownConverter("source.xls", loadOptions))
{
	// ...
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)     
