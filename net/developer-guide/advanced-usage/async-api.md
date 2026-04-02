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

## Async API

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
string md = await MarkdownConverter.ToMarkdownAsync("report.docx");

// Convert to file
await MarkdownConverter.ToFileAsync("report.docx", "report.md");

// With options
var options = new ConvertOptions { IncludeFrontMatter = true };
string md = await MarkdownConverter.ToMarkdownAsync("report.docx", null, options);

// Get document info
DocumentInfo info = await MarkdownConverter.GetInfoAsync("report.docx");
Console.WriteLine($"{info.FileFormat}, {info.PageCount} pages");
```
{{< /tab >}}
{{< /tabs >}}

### Instance async methods

{{< tabs "async-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

using var converter = new MarkdownConverter("report.docx");

// Convert to string
ConvertResult result = await converter.ConvertAsync();
Console.WriteLine(result.Content);

// Convert with options
var options = new ConvertOptions { HeadingLevelOffset = 1 };
result = await converter.ConvertAsync(options);

// Convert to file
await converter.ConvertAsync("output.md");

// Get document info
DocumentInfo info = await converter.GetDocumentInfoAsync();
```
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
    string md = await MarkdownConverter.ToMarkdownAsync(
        "large-document.pdf",
        cancellationToken: cts.Token);
}
catch (TaskCanceledException)
{
    Console.WriteLine("Conversion timed out.");
}
```
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
