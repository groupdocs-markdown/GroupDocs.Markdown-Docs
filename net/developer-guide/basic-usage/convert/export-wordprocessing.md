---
id: export-wordprocessing
url: markdown/net/convert/export-wordprocessing
title: Docx to Md
weight: 2
description: "This article demonstrates how to convert Words to Markdown with GroupDocs.Markdown for .NET."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

Use GroupDocs.Markdown to convert DOCX and other Word documents to clean Markdown.

### Using static method

The simplest way to convert a Word file:

{{< tabs "export-word-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

// Convert DOCX to Markdown string
string markdown = MarkdownConverter.ToMarkdown("business-plan.docx");

// Or save directly to a file
MarkdownConverter.ToFile("business-plan.docx", "export-word-static.md");
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-word-static.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-wordprocessing/ExportWordStatic/export-word-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-word-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("business-plan.docx");
var options = new ConvertOptions
{
    ImageExportStrategy = new ExportImagesToFileSystemStrategy("images")
    {
        ImagesRelativePath = "images"
    },
    HeadingLevelOffset = 1
};

converter.Convert("export-word-instance.md", options);
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-word-instance.zip" >}}  
```text
export-word-instance.md (5 KB)
images/img-001.png (4 KB)
images/img-002.jpg (41 KB)
images/img-003.png (14 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-wordprocessing/ExportWordInstance/export-word-instance.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/net/getting-started/supported-document-formats" >}}).
