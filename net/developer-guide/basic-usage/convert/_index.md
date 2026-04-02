---
id: convert
url: markdown/net/convert
title: Convert files to various formats
weight: 1
description: "Artcles listed in this page explain the common usage scenarios when documents are stored in a local drive and you want to manage them using GroupDocs.Markdown API"
keywords: common usage
productName: GroupDocs.Markdown for .NET
hideChildren: False
structuredData:
    showOrganization: True
---

**[GroupDocs.Markdown](https://products.groupdocs.com/markdown/net)** provides a quick and easy way to convert documents into clean, structured Markdown. The library offers two approaches: **static methods** for one-line conversions and an **instance API** for more control.

### Static methods (simplest)

Call `MarkdownConverter.ToMarkdown()` to get a Markdown string, or `MarkdownConverter.ToFile()` to write directly to disk:

{{< tabs "static-methods" >}}
{{< tab "C#" >}}
```csharp
string md = MarkdownConverter.ToMarkdown("report.docx");
MarkdownConverter.ToFile("report.docx", "report.md");
```
{{< /tab >}}
{{< /tabs >}}

### Instance API

Create a [MarkdownConverter](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/markdownconverter/) instance for advanced scenarios such as inspecting metadata before converting or reusing a loaded document:

{{< tabs "instance-api" >}}
{{< tab "C#" >}}
```csharp
using var converter = new MarkdownConverter("report.docx");
ConvertResult result = converter.Convert(new ConvertOptions { HeadingLevelOffset = 1 });
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}

### Conversion options

Use [ConvertOptions](https://reference.groupdocs.com/markdown/net/groupdocs.markdown/convertoptions/) to customize the output -- select specific pages, control image handling, choose a Markdown flavor, add YAML front matter, and more. For loading customization, use [LoadOptions](https://reference.groupdocs.com/markdown/net/groupdocs.markdown.options.load) to specify file format or provide a password.

These documentation articles explain how to convert files from the most popular formats:
