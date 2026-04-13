---
id: static-site-generator
url: markdown/net/static-site-generator
title: Generate content for static sites
weight: 2
description: "Convert documents to Markdown with YAML front matter for Jekyll, Hugo, and Docusaurus"
keywords: static site, Jekyll, Hugo, Docusaurus, front matter, YAML
productName: GroupDocs.Markdown for .NET
hideChildren: False
toc: True
---

Static site generators like Jekyll, Hugo, and Docusaurus expect Markdown files with YAML front matter. GroupDocs.Markdown can automatically generate front matter from document metadata.

### Convert with front matter and relative images

{{< tabs "ssg-example">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    IncludeFrontMatter = true,
    HeadingLevelOffset = 1,   // Reserve H1 for the page title
    ImageExportStrategy = new ExportImagesToFileSystemStrategy("content/posts/images")
    {
        ImagesRelativePath = "images"
    }
};

MarkdownConverter.ToFile("annual-report.docx", "content/posts/annual-report.md", options);

// Output file starts with:
// ---
// title: "Annual Report 2025"
// author: "Finance Team"
// format: Docx
// pages: 24
// ---
//
// ## Executive Summary
// ...
```
{{< /tab >}}
{{< tab "annual-report.docx" >}}  
{{< tab-text >}}
`annual-report.docx` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/use-cases/annual-report.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "ssg.zip" >}}  
```text
content/posts/annual-report.md (5 KB)
content/posts/images/img-001.png (4 KB)
content/posts/images/img-002.png (14 KB)
content/posts/images/img-003.png (15 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/use-cases/static-site-generator/SsgExample/ssg.zip)
{{< /tab >}}
{{< /tabs >}}

### Batch-convert a folder for Hugo

{{< tabs "ssg-batch-hugo">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

string inputDir = "documents";
string outputDir = "content/docs";

var options = new ConvertOptions
{
    IncludeFrontMatter = true,
    HeadingLevelOffset = 1,
    ImageExportStrategy = new SkipImagesStrategy() // or file system
};

foreach (string file in Directory.GetFiles(inputDir))
{
    string ext = Path.GetExtension(file).ToLower();
    if (ext is ".docx" or ".pdf" or ".xlsx" or ".epub")
    {
        try
        {
            string outputPath = Path.Combine(
                outputDir,
                Path.GetFileNameWithoutExtension(file) + ".md");

            MarkdownConverter.ToFile(file, outputPath, options);
            Console.WriteLine($"Converted: {Path.GetFileName(file)}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Skipped: {Path.GetFileName(file)} — {ex.Message}");
        }
    }
}
```
{{< /tab >}}
{{< tab "ssg-batch-hugo.zip" >}}  
```text
content/docs/business-plan.md (7 KB)
content/docs/cost-analysis.md (9 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/use-cases/static-site-generator/SsgBatchHugo/ssg-batch-hugo.zip)
{{< /tab >}}
{{< /tabs >}}
