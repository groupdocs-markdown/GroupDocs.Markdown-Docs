---
id: markdown-flavor
url: markdown/net/markdown-flavor
title: Markdown flavor control
weight: 3
description: "Target GitHub Flavored Markdown or CommonMark output"
keywords: markdown flavor, GFM, CommonMark, tables
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## Markdown flavor control

GroupDocs.Markdown supports two Markdown dialects. Set the `Flavor` property on `ConvertOptions` to control the output.

### GitHub Flavored Markdown (default)

GFM supports pipe tables, strikethrough text, and other extensions:

{{< tabs "flavor-gfm">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions { Flavor = MarkdownFlavor.GitHub };
string md = MarkdownConverter.ToMarkdown("report.docx", options);

// Tables are rendered as:
// | Column A | Column B |
// | --- | --- |
// | value1 | value2 |
```
{{< /tab >}}
{{< /tabs >}}

### CommonMark

Strict CommonMark output. Tables are rendered as fenced code blocks since CommonMark has no native table syntax:

{{< tabs "flavor-commonmark">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions { Flavor = MarkdownFlavor.CommonMark };
string md = MarkdownConverter.ToMarkdown("report.docx", options);

// Tables are rendered as:
// ```
// Column A  |  Column B
// value1    |  value2
// ```
```
{{< /tab >}}
{{< /tabs >}}
