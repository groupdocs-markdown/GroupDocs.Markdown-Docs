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

## Load a document from a stream

When the source document is not a file on disk (e.g., downloaded from a network, read from a database, or received as an upload), you can pass a `Stream` directly to the `MarkdownConverter` constructor.

The stream is copied internally, so you may close it immediately after creating the converter.

{{< tabs "load-stream-example">}}
{{< tab "C#" >}}
```csharp
using System.IO;
using GroupDocs.Markdown;

using Stream stream = File.OpenRead("source.docx");
using var converter = new MarkdownConverter(stream);

ConvertResult result = converter.Convert();
Console.WriteLine(result.Content);
```
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
ConvertResult result = converter.Convert();
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}
