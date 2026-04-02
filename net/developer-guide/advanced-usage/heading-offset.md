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

## Heading level offset

Use `HeadingLevelOffset` to shift all heading levels in the output by a fixed number. This is useful when embedding converted content inside a larger document where top-level headings are already in use.

### Example

{{< tabs "heading-offset-example">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions { HeadingLevelOffset = 2 };
string md = MarkdownConverter.ToMarkdown("chapter.docx", options);

// Source: # Title     → Output: ### Title
// Source: ## Section  → Output: #### Section
// Heading levels are clamped to the range 1-6.
```
{{< /tab >}}
{{< /tabs >}}
