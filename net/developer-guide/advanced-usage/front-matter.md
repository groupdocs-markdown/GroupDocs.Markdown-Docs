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

Enable `IncludeFrontMatter` to extract document metadata into a YAML block at the beginning of the Markdown output. This is commonly used by static site generators like Jekyll, Hugo, and Docusaurus.

### Example

{{< tabs "front-matter-example">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions { IncludeFrontMatter = true };
MarkdownConverter.ToFile("business-plan.docx", "front-matter-example.md", options);
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
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "front-matter-example.md" >}}  
```text
---
title: "Meridian Outdoor Co. — Business Plan"
author: "Meridian Outdoor Co."
format: Docx
pages: 5
---

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/front-matter/FrontMatterExample/front-matter-example.md)
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
MarkdownConverter.ToFile("annual-report.docx", "front-matter-combined.md", options);
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "front-matter-combined.md" >}}  
```text
---
title: "Meridian Outdoor Co. — Annual Report 2025"
author: "Elena Márquez, CFO"
format: Docx
pages: 6
---

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1Ld
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/front-matter/FrontMatterCombined/front-matter-combined.md)
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
