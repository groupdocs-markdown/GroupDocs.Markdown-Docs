---
id: as-base64-strategy
url: markdown/java/as-base64-strategy
title: Save image as base64
weight: 1
description: "The listed articles below explain how to embeds images as Base64 strings directly in the Markdown."
keywords:
productName: GroupDocs.Markdown for Java
hideChildren: False
---

By default, `DocumentConvertOptions` uses `ExportImagesAsBase64Strategy`, which embeds images as Base64 data URIs directly in the Markdown output. This keeps the output self-contained in a single file with no external image dependencies.

### Using static method

{{< tabs "base64-static">}}
{{< tab "Base64Static.java" >}}
```java
import com.groupdocs.markdown.*;

public class Base64Static {

    public static void main(String[] args) {
        // Default behavior -- images are embedded as Base64
        MarkdownConverter.toFile("business-plan.pdf", "base64-static.md");
    }
}
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "base64-static.md" >}}  
```text
**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan

![](data:...;base64,[elided])


**Table of Contents**

MeridianOutdoorCo.—BusinessPlan.........................................................................................1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/strategy/as-base64-strategy/Base64Static/base64-static.md)
{{< /tab >}}
{{< /tabs >}}

### Specifying the strategy explicitly

If you want to be explicit, pass a new `ExportImagesAsBase64Strategy` to `setImageExportStrategy`:

{{< tabs "base64-explicit">}}
{{< tab "Base64Explicit.java" >}}
```java
import com.groupdocs.markdown.*;

public class Base64Explicit {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(new ExportImagesAsBase64Strategy());

        try (MarkdownConverter converter = new MarkdownConverter("business-plan.pdf")) {
            converter.convert("base64-explicit.md", options);
        }
    }
}
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "base64-explicit.md" >}}  
```text
**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan

![](data:...;base64,[elided])


**Table of Contents**

MeridianOutdoorCo.—BusinessPlan.........................................................................................1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/strategy/as-base64-strategy/Base64Explicit/base64-explicit.md)
{{< /tab >}}
{{< /tabs >}}
