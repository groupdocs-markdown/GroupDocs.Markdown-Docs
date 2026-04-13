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

All `Convert()` methods throw on failure. Use standard try/catch with specific exception types:

{{< tabs "error-handling-example">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

try
{
    MarkdownConverter.ToFile("annual-report.docx", "error-handling-example.md");
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
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "error-handling-example.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/error-handling/ErrorHandlingExample/error-handling-example.md)
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

using var converter = new MarkdownConverter("cost-analysis.xlsx");
ConvertResult result = converter.Convert("warnings-example.md", new ConvertOptions { MaxRows = 10 });

foreach (string warning in result.Warnings)
    Console.WriteLine($"Warning: {warning}");
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}  
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "warnings-example.md" >}}  
```text
## Summary

| Category | FY2024 | FY2025 | FY2026 |
| --- | --- | --- | --- |
| Parts and materials | $1,325,000.00 | $1,480,000.00 | $1,620,000.00 |
| Manufacturing equipment | $900,500.00 | $980,000.00 | $1,050,000.00 |
| Warehousing | $420,000.00 | $510,000.00 | $590,000.00 |
| Shipping | $380,000.00 | $445,000.00 | $520,000.00 |
| Marketing | $250,000.00 | $340,000.00 | $480,000.00 |
| R&D | $180,000.00 | $230,000.00 | $310,000.00 |
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/error-handling/WarningsExample/warnings-example.md)
{{< /tab >}}
{{< /tabs >}}
