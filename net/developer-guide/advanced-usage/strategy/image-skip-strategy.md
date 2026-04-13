---
id: image-skip-strategy
url: markdown/net/image-skip-strategy
title: Skip image
weight: 3
description: "The listed articles below explain how to skips saving images during document conversion."
keywords:
productName: GroupDocs.Markdown for .NET
hideChildren: False
---

Use `SkipImagesStrategy` when you want to convert a document to Markdown without exporting any images. Image references will be omitted from the output.

### Using static method

{{< tabs "skip-images-static">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    ImageExportStrategy = new SkipImagesStrategy()
};

MarkdownConverter.ToFile("business-plan.pdf", "skip-images-static.md", options);
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "skip-images-static.md" >}}  
```text
**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan

**Table of Contents**

Meridian Outdoor Co. — Business Plan .........................................................................................1FY2026 Strategic Plan.................................................................................................................1Table of Contents.............................................................................................................................2

1. E
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/strategy/image-skip-strategy/SkipImagesStatic/skip-images-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "skip-images-instance">}}
{{< tab "C#" >}}
```csharp
using GroupDocs.Markdown;

var options = new ConvertOptions
{
    ImageExportStrategy = new SkipImagesStrategy()
};

using var converter = new MarkdownConverter("business-plan.pdf");
converter.Convert("skip-images-instance.md", options);
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/net/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "skip-images-instance.md" >}}  
```text
**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan

**Table of Contents**

Meridian Outdoor Co. — Business Plan .........................................................................................1FY2026 Strategic Plan.................................................................................................................1Table of Contents.............................................................................................................................2

1. E
[TRUNCATED]
```
[Download full output](/markdown/net/_output_files/developer-guide/advanced-usage/strategy/image-skip-strategy/SkipImagesInstance/skip-images-instance.md)
{{< /tab >}}
{{< /tabs >}}
