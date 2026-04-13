---
id: load-from-a-stream
url: markdown/net/load-from-a-stream
title: Load from a stream
weight: 2
description: "This example demonstrates how to load a file from a stream."
keywords: load a file from a stream
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

When the source document is not a file on disk (e.g., downloaded from a network, read from a database, or received as an upload), you can pass a `Stream` directly to the `MarkdownConverter` constructor.

The stream is copied internally, so you may close it immediately after creating the converter.

{{< tabs "load-stream-example">}}
{{< tab "C#" >}}
```csharp
using System.IO;
using GroupDocs.Markdown;

using Stream stream = File.OpenRead("business-plan.docx");
using var converter = new MarkdownConverter(stream);

converter.Convert("load-stream-example.md");
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-stream-example.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/LoadStreamExample/load-stream-example.md)
{{< /tab >}}
{{< /tabs >}}

### Stream with LoadOptions

If the stream does not have a file extension for automatic format detection, specify the format explicitly via `LoadOptions`:

{{< tabs "load-stream-options">}}
{{< tab "C#" >}}
```csharp
using System.IO;
using GroupDocs.Markdown;

using Stream stream = File.OpenRead("document");
var loadOptions = new LoadOptions(FileFormat.Docx);

using var converter = new MarkdownConverter(stream, loadOptions);
converter.Convert("load-stream-options.md");
```
{{< /tab >}}
{{< tab "load-stream-options.md" >}}  
```text
| HOME BASED |  |  |
| --- | --- | --- |
|  |  |  |
| PROFESSIONAL SERVICES |  |  |
|  | Business Plan |  |



|  | TABLE OF CONTENTS TOC \o "1-3" \h \z \u  HYPERLINK \l "_Toc9437451" Introduction	 PAGEREF _Toc9437451 \h 3  HYPERLINK \l "_Toc9437452" 1.	Executive Summary	 PAGEREF _Toc9437452 \h 5  HYPERLINK \l "_Toc9437453" 2.	Company Overview	 PAGEREF _Toc9437453 \h 6  HYPERLINK \l "_Toc9437454" 3.	Business Description	 PAGEREF _Toc9437454 \h 7  HYPERLINK \l "_Toc9437
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/loading/load-from-a-stream/LoadStreamOptions/load-stream-options.md)
{{< /tab >}}
{{< /tabs >}}
