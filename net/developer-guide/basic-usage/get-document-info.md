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

Use `GetDocumentInfo()` or the static `GetInfo()` method to retrieve document metadata without performing a full conversion. This is useful for building file browsers, validation pipelines, and pre-conversion UIs.

### Using static method

{{< tabs "get-info-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

DocumentInfo info = MarkdownConverter.GetInfo("business-plan.docx");

Console.WriteLine($"Format:    {info.FileFormat}");    // Docx
Console.WriteLine($"Pages:     {info.PageCount}");     // 42
Console.WriteLine($"Title:     {info.Title}");         // "Q3 Report"
Console.WriteLine($"Author:    {info.Author}");        // "Jane Doe"
Console.WriteLine($"Encrypted: {info.IsEncrypted}");   // false
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "get-info-static.txt" >}}  
```text
Format:    Docx
Pages:     5
Title:     Meridian Outdoor Co. - Business Plan
Author:    Meridian Outdoor Co.
Encrypted: False
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/get-document-info/GetInfoStatic/get-info-static.txt)
{{< /tab >}}
{{< /tabs >}}

### Using instance method

{{< tabs "get-info-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

using var converter = new MarkdownConverter("cost-analysis.xlsx");
DocumentInfo info = converter.GetDocumentInfo();

Console.WriteLine($"Format:    {info.FileFormat}");
Console.WriteLine($"Pages:     {info.PageCount}");
Console.WriteLine($"Title:     {info.Title}");
Console.WriteLine($"Author:    {info.Author}");
Console.WriteLine($"Encrypted: {info.IsEncrypted}");
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "get-info-instance.txt" >}}  
```text
Format:    Xlsx
Pages:     4
Title:     
Author:    
Encrypted: False
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/get-document-info/GetInfoInstance/get-info-instance.txt)
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
