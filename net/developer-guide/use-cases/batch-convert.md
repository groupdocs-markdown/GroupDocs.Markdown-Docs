---
id: batch-convert
url: markdown/net/batch-convert
title: Batch-convert a folder
weight: 3
description: "Convert all documents in a directory to Markdown"
keywords: batch, folder, directory, multiple files, bulk
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

## Batch-convert a folder

Convert all supported documents in a directory to Markdown files.

### Basic batch conversion

{{< tabs "batch-basic">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

string inputDir = @"C:\Documents";
string outputDir = @"C:\Markdown";

Directory.CreateDirectory(outputDir);

// Get supported extensions
var supported = new HashSet<string>(
    MarkdownConverter.GetSupportedFormats()
        .Select(f => "." + f.ToString().ToLower()));

int converted = 0;
int skipped = 0;

foreach (string file in Directory.GetFiles(inputDir))
{
    string ext = Path.GetExtension(file).ToLower();
    if (!supported.Contains(ext)) continue;

    string outputPath = Path.Combine(
        outputDir,
        Path.GetFileNameWithoutExtension(file) + ".md");

    try
    {
        MarkdownConverter.ToFile(file, outputPath);
        converted++;
        Console.WriteLine($"OK: {Path.GetFileName(file)}");
    }
    catch (Exception ex)
    {
        skipped++;
        Console.WriteLine($"SKIP: {Path.GetFileName(file)} — {ex.Message}");
    }
}

Console.WriteLine($"Done: {converted} converted, {skipped} skipped");
```
{{< /tab >}}
{{< /tabs >}}

### Async batch conversion

{{< tabs "batch-async">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

string inputDir = @"C:\Documents";
string outputDir = @"C:\Markdown";

Directory.CreateDirectory(outputDir);

var files = Directory.GetFiles(inputDir, "*.*")
    .Where(f => new[] { ".docx", ".pdf", ".xlsx", ".epub" }
        .Contains(Path.GetExtension(f).ToLower()))
    .ToArray();

var options = new ConvertOptions
{
    ImageExportStrategy = new SkipImagesStrategy()
};

var tasks = files.Select(async file =>
{
    string outputPath = Path.Combine(
        outputDir,
        Path.GetFileNameWithoutExtension(file) + ".md");

    try
    {
        await MarkdownConverter.ToFileAsync(file, outputPath, options);
        Console.WriteLine($"OK: {Path.GetFileName(file)}");
    }
    catch (Exception ex)
    {
        Console.WriteLine($"SKIP: {Path.GetFileName(file)} — {ex.Message}");
    }
});

await Task.WhenAll(tasks);
```
{{< /tab >}}
{{< /tabs >}}
