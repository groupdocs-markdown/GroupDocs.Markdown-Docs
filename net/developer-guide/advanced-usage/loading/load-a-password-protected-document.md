---
id: load-a-password-protected-document
url: markdown/net/load-a-password-protected-document
title: Load a password-protected document
weight: 4
description: "This example demonstrates how to load a password-protected document."
keywords: load a password-protected document
productName: GroupDocs.Markdown for .NET
hideChildren: False
---
This example demonstrates how to load a password-protected document.

**AdvancedUsage.Loading.LoadPasswordProtectedDocument**

```csharp
// Specify the password
var loadOptions = new LoadOptions
{
	Password = "123"
};

using (var converter = new MarkdownConverter("source.xls", loadOptions))
{
	// ...
}
```

## More resources
### GitHub examples
You may easily run the code above and see the feature in action in our GitHub examples:
*   [GroupDocs.Markdown for .NET examples](https://github.com/groupdocs-markdown/GroupDocs.Markdown-for-.NET)    
