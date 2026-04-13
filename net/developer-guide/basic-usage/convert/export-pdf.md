---
id: export-pdf
url: markdown/net/convert/export-pdf
title: Pdf to Md
weight: 1
description: "This article demonstrates how to convert PDF to Markdown with GroupDocs.Markdown for .NET."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

Use GroupDocs.Markdown to convert PDF documents to clean Markdown.

### Using static method

The simplest way to convert a PDF file:

{{< tabs "export-pdf-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Set license (optional)
if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

// Convert PDF to Markdown string
string markdown = MarkdownConverter.ToMarkdown("business-plan.pdf");

// Or save directly to a file
MarkdownConverter.ToFile("business-plan.pdf", "export-pdf-static.md");
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-pdf-static.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAIAAADHHcVbAAAAA3NCSVQICAjb4U/gAAAMWElEQVR4nO3dUWzV130H8L+nSnsgxYTa5kbEnhJgJpJ98aQseTAxUaoiW1RDSiseykoCNE9boyoIZEWLVImosoZSpeve0Ighax4iDRRpky02oWKbh2aVCralhGBANSAu4Lq5NJ60tz0c8t/lf6/h2jjg/M/nIz8c7v/v3z345atz/v9zTkNpaiwBgFj92aPuAAA8SoIQgKgJQgCiJggBiNo3Mv/+53/9r4tXbi6u1t/v/Pa6tjXzXV1cZTXVVFNNNdVc2poZ2SCcmr4xfv7KQr8y+NPc/97j6uIqq6mmmmqqqebS1szIBuH6tjUNDQ0Xp2988T8LqAIAX1NLOSIEgK+dhsyC+p/87FdpEP7dzm+va613jjVJkvVtax5b8efzXb04fWNBY1U11VRTTTXVXJ
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-pdf/ExportPdfStatic/export-pdf-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-pdf-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

if (File.Exists("GroupDocs.Markdown.lic")) License.Set("GroupDocs.Markdown.lic");

using var converter = new MarkdownConverter("business-plan.pdf");
var options = new ConvertOptions
{
    ImageExportStrategy = new ExportImagesToFileSystemStrategy("images")
    {
        ImagesRelativePath = "images"
    },
    HeadingLevelOffset = 1
};

converter.Convert("export-pdf-instance.md", options);
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/basic-usage/convert/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-pdf-instance.zip" >}}  
```text
export-pdf-instance.md (7 KB)
images/img-001.png (3 KB)
images/img-002.jpg (73 KB)
images/img-003.jpg (76 KB)
```
[Download full output](/markdown/net/_output_files/developer-guide/basic-usage/convert/export-pdf/ExportPdfInstance/export-pdf-instance.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/net/getting-started/supported-document-formats" >}}).
