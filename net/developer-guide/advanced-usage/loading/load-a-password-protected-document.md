---
id: load-a-password-protected-document
url: markdown/net/load-a-password-protected-document
title: Load a password-protected document
weight: 4
description: "This example demonstrates how to load a password-protected document."
keywords: load a password-protected document
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

To open a password-protected document, create a `LoadOptions` instance with the file format and set the `Password` property.

{{< tabs "load-password-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var loadOptions = new LoadOptions(FileFormat.Docx)
{
    Password = "secret"
};

// Static one-liner
string markdown = MarkdownConverter.ToMarkdown("protected.docx", loadOptions);
File.WriteAllText("load-password-static.md", markdown);
```
{{< /tab >}}
{{< tab "protected.docx" >}}  
{{< tab-text >}}
`protected.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/loading/protected.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-password-static.md" >}}  
```text
**Confidential Memo**

From: Meridian Outdoor Co. — Strategy Team

Date: 2026-01-15

Subject: FY2026 M&A Targets



[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/LoadPasswordStatic/load-password-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "load-password-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var loadOptions = new LoadOptions(FileFormat.Xlsx)
{
    Password = "secret"
};

using var converter = new MarkdownConverter("protected.xlsx", loadOptions);
converter.Convert("load-password-instance.md");
```
{{< /tab >}}
{{< tab "protected.xlsx" >}}  
{{< tab-text >}}
`protected.xlsx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/loading/protected.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-password-instance.md" >}}  
```text
## Expenses

| Date | Vendor | Category | Amount |
| --- | --- | --- | --- |
| 2026-01-02 | Pacific Freight | Shipping | $2,450.00 |
| 2026-01-05 | Cedar Packaging | Materials | $1,320.50 |
| 2026-01-08 | Highline Textiles | Materials | $8,940.00 |
| 2026-01-12 | Portland Electric | Utilities | $680.25 |
| 2026-01-14 | Backcountry Co-op | Events | $1,200.00 |
| 2026-01-17 | Ridge Media | Marketing | $5,400.00 |
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/LoadPasswordInstance/load-password-instance.md)
{{< /tab >}}
{{< /tabs >}}

### Handling incorrect passwords

If the password is missing or incorrect, a `DocumentProtectedException` is thrown. You can catch it to display a user-friendly message:

{{< tabs "load-password-exception">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

try
{
    string markdown = MarkdownConverter.ToMarkdown("protected.docx");
}
catch (DocumentProtectedException ex)
{
    Console.WriteLine($"Cannot open document: {ex.Message}");
}
```
{{< /tab >}}
{{< tab "protected.docx" >}}  
{{< tab-text >}}
`protected.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/loading/protected.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-password-exception.txt" >}}  
```text
Cannot open document: The document password is incorrect.
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/loading/load-a-password-protected-document/LoadPasswordException/load-password-exception.txt)
{{< /tab >}}
{{< /tabs >}}
