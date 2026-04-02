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

## Load a password-protected document

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
Console.WriteLine(markdown);
```
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
ConvertResult result = converter.Convert();
Console.WriteLine(result.Content);
```
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
{{< /tabs >}}
