---
id: async-api
url: markdown/net/async-api
title: Async API
weight: 8
description: "Use async methods for non-blocking document conversion in web apps and serverless"
keywords: async, await, asynchronous, web, serverless, Task
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

All static and instance methods have async counterparts. File I/O is truly asynchronous — source files are read and output files are written using async streams. CPU-bound conversion runs on the thread pool.

{{< alert style="info" >}}
The async API is available on .NET 6.0+ and .NET Framework 4.6.2+.
{{< /alert >}}

### Static async methods

{{< tabs "async-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Convert to string
string md = await MarkdownConverter.ToMarkdownAsync("business-plan.docx");

// Convert to file
await MarkdownConverter.ToFileAsync("business-plan.docx", "report.md");

// With options
var options = new ConvertOptions { IncludeFrontMatter = true };
string md = await MarkdownConverter.ToMarkdownAsync("business-plan.docx", null, options);

// Get document info
DocumentInfo info = await MarkdownConverter.GetInfoAsync("business-plan.docx");
Console.WriteLine($"{info.FileFormat}, {info.PageCount} pages");
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "report.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/async-api/AsyncStatic/report.md)
{{< /tab >}}
{{< /tabs >}}

### Instance async methods

{{< tabs "async-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

using var converter = new MarkdownConverter("business-plan.docx");

// Convert to string
await converter.ConvertAsync("async-instance.md");

// Convert with options
var options = new ConvertOptions { HeadingLevelOffset = 1 };
ConvertResult result = await converter.ConvertAsync(options);

// Convert to file
await converter.ConvertAsync("async-instance.md");

// Get document info
DocumentInfo info = await converter.GetDocumentInfoAsync();
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "async-instance.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAYAAABIf1IMAAAABHNCSVQICAgIfAhkiAAADcJJREFUeJzt3VFo3VWeB/BfF2EfdJraSWKkpovabiokaRZcfWiM4jCS0mELjvgwzlZt16fdlUFpKbLCgDKELQ7Oum+yNdYdH4StCLMkdBexSfow7sC0SUA7TZVJW0zbWI1OF/ap+xD+/97k/u/Nze1JbJLPBwo9/3vu/Z1/L5Qv55x7/uumJkauBQAAyfzZdz0AAIDVRsACAEhMwAIASEzAAgBI7Jaii//67/8dZ89dSlbkH576Qdy7+Y4F+6Wqq5566qmnnnrqqbdc9YoUBqyJyYsxevrcDQ2q1LdX/6+mfqnqqqeeeuqpp5566i1XvSKFAWvL5jti3bp1cXbyYvzpf+v/cACAtWhZZrAAANaSdUUHjf7sF7+eE7D+/qkfxL2t9a1BRszOiN12658v2O
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/async-api/AsyncInstance/async-instance.md)
{{< /tab >}}
{{< /tabs >}}

### Cancellation

All async methods accept a `CancellationToken`:

{{< tabs "async-cancellation">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var cts = new CancellationTokenSource(TimeSpan.FromSeconds(30));

try
{
    await MarkdownConverter.ToFileAsync(
        "professional-services.pdf",
        "async-cancellation.md",
        cancellationToken: cts.Token);
}
catch (TaskCanceledException)
{
    Console.WriteLine("Conversion timed out.");
}
```
{{< /tab >}}
{{< tab "professional-services.pdf" >}}  
{{< tab-text >}}
`professional-services.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/professional-services.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "async-cancellation.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAIAAADHHcVbAAAAA3NCSVQICAjb4U/gAAAMWElEQVR4nO3dUWzV130H8L+nSnsgxYTa5kbEnhJgJpJ98aQseTAxUaoiW1RDSiseykoCNE9boyoIZEWLVImosoZSpeve0Ighax4iDRRpky02oWKbh2aVCralhGBANSAu4Lq5NJ60tz0c8t/lf6/h2jjg/M/nIz8c7v/v3z345atz/v9zTkNpaiwBgFj92aPuAAA8SoIQgKgJQgCiJggBiNo3Mv/+53/9r4tXbi6u1t/v/Pa6tjXzXV1cZTXVVFNNNdVc2poZ2SCcmr4xfv7KQr8y+NPc/97j6uIqq6mmmmqqqebS1szIBuH6tjUNDQ0Xp2988T8LqAIAX1NLOSIEgK+dhsyC+p/87FdpEP7dzm+va613jjVJkvVtax5b8efzXb04fWNBY1U11VRTTTXVXJ
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/async-api/AsyncCancellation/async-cancellation.md)
{{< /tab >}}
{{< /tabs >}}

### ASP.NET Core example

{{< tabs "async-aspnet">}}
{{< tab "C#" >}}
```csharp
[ApiController]
[Route("api/[controller]")]
public class ConvertController : ControllerBase
{
    [HttpPost("to-markdown")]
    public async Task<IActionResult> ConvertToMarkdown(IFormFile file)
    {
        using var stream = file.OpenReadStream();
        using var converter = new MarkdownConverter(stream);

        ConvertResult result = await converter.ConvertAsync(
            new ConvertOptions { Flavor = MarkdownFlavor.GitHub });

        return Content(result.Content, "text/markdown");
    }
}
```
{{< /tab >}}
{{< /tabs >}}
