---
id: as-base64-strategy
url: markdown/net/as-base64-strategy
title: Save image as base64
weight: 1
description: "The listed articles below explain how to embeds images as Base64 strings directly in the Markdown."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

By default, `ConvertOptions` uses `ExportImagesAsBase64Strategy`, which embeds images as Base64 data URIs directly in the Markdown output. This keeps the output self-contained in a single file with no external image dependencies.

### Using static method

{{< tabs "base64-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

// Default behavior -- images are embedded as Base64
MarkdownConverter.ToFile("business-plan.pdf", "base64-static.md");
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "base64-static.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAIAAADHHcVbAAAAA3NCSVQICAjb4U/gAAAMWElEQVR4nO3dUWzV130H8L+nSnsgxYTa5kbEnhJgJpJ98aQseTAxUaoiW1RDSiseykoCNE9boyoIZEWLVImosoZSpeve0Ighax4iDRRpky02oWKbh2aVCralhGBANSAu4Lq5NJ60tz0c8t/lf6/h2jjg/M/nIz8c7v/v3z345atz/v9zTkNpaiwBgFj92aPuAAA8SoIQgKgJQgCiJggBiNo3Mv/+53/9r4tXbi6u1t/v/Pa6tjXzXV1cZTXVVFNNNdVc2poZ2SCcmr4xfv7KQr8y+NPc/97j6uIqq6mmmmqqqebS1szIBuH6tjUNDQ0Xp2988T8LqAIAX1NLOSIEgK+dhsyC+p/87FdpEP7dzm+va613jjVJkvVtax5b8efzXb04fWNBY1U11VRTTTXVXJ
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/strategy/as-base64-strategy/Base64Static/base64-static.md)
{{< /tab >}}
{{< /tabs >}}

### Specifying the strategy explicitly

If you want to be explicit, set `ImageExportStrategy` to a new `ExportImagesAsBase64Strategy`:

{{< tabs "base64-explicit">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    ImageExportStrategy = new ExportImagesAsBase64Strategy()
};

using var converter = new MarkdownConverter("business-plan.pdf");
converter.Convert("base64-explicit.md", options);
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "base64-explicit.md" >}}  
```text
![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAlgAAAC0CAIAAADHHcVbAAAAA3NCSVQICAjb4U/gAAAMWElEQVR4nO3dUWzV130H8L+nSnsgxYTa5kbEnhJgJpJ98aQseTAxUaoiW1RDSiseykoCNE9boyoIZEWLVImosoZSpeve0Ighax4iDRRpky02oWKbh2aVCralhGBANSAu4Lq5NJ60tz0c8t/lf6/h2jjg/M/nIz8c7v/v3z345atz/v9zTkNpaiwBgFj92aPuAAA8SoIQgKgJQgCiJggBiNo3Mv/+53/9r4tXbi6u1t/v/Pa6tjXzXV1cZTXVVFNNNdVc2poZ2SCcmr4xfv7KQr8y+NPc/97j6uIqq6mmmmqqqebS1szIBuH6tjUNDQ0Xp2988T8LqAIAX1NLOSIEgK+dhsyC+p/87FdpEP7dzm+va613jjVJkvVtax5b8efzXb04fWNBY1U11VRTTTXVXJ
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/strategy/as-base64-strategy/Base64Explicit/base64-explicit.md)
{{< /tab >}}
{{< /tabs >}}
