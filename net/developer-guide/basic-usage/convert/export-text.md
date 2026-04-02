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

## Convert Text and XML to Markdown

Use GroupDocs.Markdown to convert TXT, XML, and other text-based formats to clean Markdown.

### Using static method

The simplest way to convert a text file:

{{< tabs "export-text-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
License.Set("GroupDocs.Markdown.lic");

// Convert XML to Markdown string
string markdown = MarkdownConverter.ToMarkdown("data.xml");

// Or save directly to a file
MarkdownConverter.ToFile("data.xml", "data.md");
```
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-text-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("data.xml");
var options = new ConvertOptions
{
    HeadingLevelOffset = 1
};

ConvertResult result = converter.Convert(options);
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/net/getting-started/supported-document-formats" >}}).
