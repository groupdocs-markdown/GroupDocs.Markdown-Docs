---
id: front-matter
url: markdown/net/front-matter
title: YAML front matter
weight: 4
description: "Generate YAML front matter from document metadata for static site generators"
keywords: front matter, YAML, Jekyll, Hugo, Docusaurus, metadata
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## YAML front matter

Enable `IncludeFrontMatter` to extract document metadata into a YAML block at the beginning of the Markdown output. This is commonly used by static site generators like Jekyll, Hugo, and Docusaurus.

### Example

{{< tabs "front-matter-example">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions { IncludeFrontMatter = true };
string md = MarkdownConverter.ToMarkdown("report.docx", options);

Console.WriteLine(md);
// Output:
// ---
// title: "Q3 Report"
// author: "Jane Doe"
// format: Docx
// pages: 12
// ---
//
// # Q3 Report
// ...
```
{{< /tab >}}
{{< /tabs >}}

### Combined with heading offset

{{< tabs "front-matter-combined">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    IncludeFrontMatter = true,
    HeadingLevelOffset = 1
};
MarkdownConverter.ToFile("chapter.docx", "chapter.md", options);
```
{{< /tab >}}
{{< /tabs >}}

### Front matter fields

Only non-empty fields are included:

| Field | Source | Example |
|---|---|---|
| `title` | `BuiltInDocumentProperties.Title` | `"Q3 Report"` |
| `author` | `BuiltInDocumentProperties.Author` | `"Jane Doe"` |
| `format` | Detected file format | `Docx` |
| `pages` | Page or worksheet count | `12` |
