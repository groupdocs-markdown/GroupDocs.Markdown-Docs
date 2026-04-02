---
id: error-handling
url: markdown/net/error-handling
title: Error handling
weight: 7
description: "Handle conversion errors with specific exception types"
keywords: error handling, exceptions, password, format, error
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## Error handling

All `Convert()` methods throw on failure. Use standard try/catch with specific exception types:

{{< tabs "error-handling-example">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

try
{
    string md = MarkdownConverter.ToMarkdown("file.docx");
    Console.WriteLine(md);
}
catch (DocumentProtectedException)
{
    Console.WriteLine("Wrong or missing password.");
}
catch (InvalidFormatException)
{
    Console.WriteLine("File is corrupt or unsupported.");
}
catch (GroupDocsMarkdownException ex)
{
    Console.WriteLine($"Conversion failed: {ex.Message}");
}
```
{{< /tab >}}
{{< /tabs >}}

### Exception types

| Exception | When thrown |
|---|---|
| `DocumentProtectedException` | Document is password-protected and no password or wrong password was provided |
| `InvalidFormatException` | File is corrupt or has an unrecognized format |
| `GroupDocsMarkdownException` | General conversion error |

### Conversion warnings

Non-fatal issues are reported via `ConvertResult.Warnings`:

{{< tabs "warnings-example">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

using var converter = new MarkdownConverter("data.xlsx");
ConvertResult result = converter.Convert(new ConvertOptions { MaxRows = 10 });

Console.WriteLine(result.Content);

foreach (string warning in result.Warnings)
    Console.WriteLine($"Warning: {warning}");
```
{{< /tab >}}
{{< /tabs >}}
