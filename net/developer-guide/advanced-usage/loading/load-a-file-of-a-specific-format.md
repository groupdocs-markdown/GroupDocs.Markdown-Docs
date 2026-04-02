---
id: load-a-file-of-a-specific-format
url: markdown/net/load-a-file-of-a-specific-format
title: Load a file of a specific format
weight: 3
description: "This example demonstrates how to load a file of some particular format."
keywords: load a file
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

## Load a file of a specific format

By default, GroupDocs.Markdown detects the file format automatically from the file extension or stream content. When you want to skip auto-detection or the file extension is missing, specify the format explicitly using `LoadOptions`.

{{< tabs "load-specific-format">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Explicitly specify the format to skip auto-detection
var loadOptions = new LoadOptions(FileFormat.Xlsx);

using var converter = new MarkdownConverter("source.xlsx", loadOptions);
ConvertResult result = converter.Convert();
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}

### Available FileFormat values

The `FileFormat` enum includes the following values:

| Category | Values |
|---|---|
| Word Processing | `Doc`, `Docx`, `Docm`, `Dot`, `Dotx`, `Dotm`, `Rtf`, `Odt`, `Ott` |
| Spreadsheet | `Xlsx`, `Xls`, `Xlsb`, `Xlsm`, `Csv`, `Tsv`, `Ods`, `Ots` |
| PDF | `Pdf` |
| E-book | `Epub`, `Mobi` |
| Text | `Txt` |
| Help | `Chm` |

You can also retrieve supported formats programmatically:

{{< tabs "load-supported-formats">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

IReadOnlyList<FileFormat> formats = MarkdownConverter.GetSupportedFormats();
foreach (FileFormat fmt in formats)
    Console.WriteLine(fmt);
```
{{< /tab >}}
{{< /tabs >}}
