---
id: get-document-info
url: markdown/net/get-document-info
title: Get document info
weight: 2
description: "Retrieve document metadata such as format, page count, title, and author without converting"
keywords: document info, metadata, page count, file format
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## Get document information

Use `GetDocumentInfo()` or the static `GetInfo()` method to retrieve document metadata without performing a full conversion. This is useful for building file browsers, validation pipelines, and pre-conversion UIs.

### Using static method

{{< tabs "get-info-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

DocumentInfo info = MarkdownConverter.GetInfo("report.docx");

Console.WriteLine($"Format:    {info.FileFormat}");    // Docx
Console.WriteLine($"Pages:     {info.PageCount}");     // 42
Console.WriteLine($"Title:     {info.Title}");         // "Q3 Report"
Console.WriteLine($"Author:    {info.Author}");        // "Jane Doe"
Console.WriteLine($"Encrypted: {info.IsEncrypted}");   // false
```
{{< /tab >}}
{{< /tabs >}}

### Using instance method

{{< tabs "get-info-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

using var converter = new MarkdownConverter("spreadsheet.xlsx");
DocumentInfo info = converter.GetDocumentInfo();

Console.WriteLine($"Worksheets: {info.PageCount}");
Console.WriteLine($"Title: {info.Title}");

// Decide based on metadata
if (info.PageCount > 100)
{
    Console.WriteLine("Large document — consider using PageNumbers.");
}

ConvertResult result = converter.Convert();
Console.WriteLine(result.Content);
```
{{< /tab >}}
{{< /tabs >}}

### DocumentInfo properties

| Property | Type | Description |
|---|---|---|
| `FileFormat` | `FileFormat` | Detected file format (e.g., `FileFormat.Docx`) |
| `PageCount` | `int` | Number of pages or worksheets |
| `Title` | `string` | Document title from metadata |
| `Author` | `string` | Document author from metadata |
| `IsEncrypted` | `bool` | Whether the document is password-protected |
