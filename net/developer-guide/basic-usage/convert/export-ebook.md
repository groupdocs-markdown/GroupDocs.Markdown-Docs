---
id: export-ebook
url: markdown/net/convert/export-ebook
title: Epub to Md
weight: 4
description: "This article demonstrates how to convert Ebook to Markdown with GroupDocs.Markdown for .NET."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

Use GroupDocs.Markdown to convert EPUB, MOBI, and other eBook formats to clean Markdown.

### Using static method

The simplest way to convert an eBook file:

{{< tabs "export-ebook-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

// Convert EPUB to Markdown string
string markdown = MarkdownConverter.ToMarkdown("business-plan.epub");

// Or save directly to a file
MarkdownConverter.ToFile("business-plan.epub", "export-ebook-static.md");
```
{{< /tab >}}
{{< tab "business-plan.epub" >}}  
{{< tab-text >}}
`business-plan.epub` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/business-plan.epub) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-ebook-static.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQsAAABQCAYAAAAOa1DSAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAOxAAADsQBlSsOGwAAEHlJREFUeJzt3XlwG9d9wPHvLhYncRIA71sUKUqULFqHbR2xlUqx3dxOk0kzzbR2/2hnOnU7STr9r800f6SdTv9Ims60406OiXPUrq1YdeLEhyzLsiRKIi1SFy/xvm+QAHED/QMSKIgADSUZ05J+n7+0j2/3Pexb/bD78N4+ZbLvVBIhhPgAGkAymSQWSxCLx3PnVECv6dB0unRSPJ4gEo3l3EVVVYwGLb2dSCSJxuIkEonsRSgKek2HTqem02LxONFo7nrpdCoG/a1lJG6UkT0GKoqCXq9Dp66WEY3FicVyl6HpVPS3lBFPJIhG4yST2ctQVQW9pqGqCpDf+dU0HXrtTs6tgkGvoSirZURjceLx7OdW2k/a77dpv4
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-ebook/ExportEbookStatic/export-ebook-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-ebook-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("business-plan.epub");
var options = new ConvertOptions
{
    ImageExportStrategy = new ExportImagesToFileSystemStrategy("images")
    {
        ImagesRelativePath = "images"
    },
    HeadingLevelOffset = 1
};

converter.Convert("export-ebook-instance.md", options);
```
{{< /tab >}}
{{< tab "business-plan.epub" >}}  
{{< tab-text >}}
`business-plan.epub` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/business-plan.epub) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-ebook-instance.zip" >}}  
```text
export-ebook-instance.md (5 KB)
images/img-001.png (4 KB)
images/img-002.jpg (35 KB)
images/img-003.png (13 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-ebook/ExportEbookInstance/export-ebook-instance.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/net/getting-started/supported-document-formats" >}}).
