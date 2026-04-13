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

Use GroupDocs.Markdown to convert TXT, XML, and other text-based formats to clean Markdown.

### Using static method

The simplest way to convert a text file:

{{< tabs "export-text-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

// Convert XML to Markdown string
string markdown = MarkdownConverter.ToMarkdown("llms-tech.xml");

// Or save directly to a file
MarkdownConverter.ToFile("llms-tech.xml", "export-text-static.md");
```
{{< /tab >}}
{{< tab "llms-tech.xml" >}}  
{{< tab-text >}}
`llms-tech.xml` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/llms-tech.xml) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-text-static.md" >}}  
```text
Attention-based neural architecture that underpins most modern large language models.

2017

Attention Is All You Need


Language modeling

Machine translation
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-text/ExportTextStatic/export-text-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-text-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("llms-tech.xml");
var options = new ConvertOptions
{
    HeadingLevelOffset = 1
};

converter.Convert("export-text-instance.md", options);
```
{{< /tab >}}
{{< tab "llms-tech.xml" >}}  
{{< tab-text >}}
`llms-tech.xml` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/llms-tech.xml) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-text-instance.md" >}}  
```text
Attention-based neural architecture that underpins most modern large language models.

2017

Attention Is All You Need


Language modeling

Machine translation
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-text/ExportTextInstance/export-text-instance.md)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/net/getting-started/supported-document-formats" >}}).
