---
id: heading-offset
url: markdown/net/heading-offset
title: Heading level offset
weight: 5
description: "Shift all heading levels in the Markdown output"
keywords: heading, offset, heading level, embed
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

Use `HeadingLevelOffset` to shift all heading levels in the output by a fixed number. This is useful when embedding converted content inside a larger document where top-level headings are already in use.

### Example

{{< tabs "heading-offset-example">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions { HeadingLevelOffset = 2 };
MarkdownConverter.ToFile("annual-report.docx", "heading-offset-example.md", options);

// Source: # Title     → Output: ### Title
// Source: ## Section  → Output: #### Section
// Heading levels are clamped to the range 1-6.
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "heading-offset-example.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/heading-offset/HeadingOffsetExample/heading-offset-example.md)
{{< /tab >}}
{{< /tabs >}}
