---
id: image-skip-strategy
url: markdown/java/image-skip-strategy
title: Skip image
weight: 3
description: "The listed articles below explain how to skips saving images during document conversion."
keywords:
productName: GroupDocs.Markdown for Java
hideChildren: False
---

Use `SkipImagesStrategy` when you want to convert a document to Markdown without exporting any images. Image references will be omitted from the output.

### Using static method

{{< tabs "skip-images-static">}}
{{< tab "SkipImagesStatic.java" >}}
```java
import com.groupdocs.markdown.*;

public class SkipImagesStatic {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(new SkipImagesStrategy());

        MarkdownConverter.toFile("business-plan.pdf", "skip-images-static.md", options);
    }
}
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/strategy/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "skip-images-static.md" >}}  
```text
**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan




**Table of Contents**

MeridianOutdoorCo.—BusinessPlan.........................................................................................1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/strategy/image-skip-strategy/SkipImagesStatic/skip-images-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

{{< tabs "skip-images-instance">}}
{{< tab "SkipImagesInstance.java" >}}
```java
import com.groupdocs.markdown.*;

public class SkipImagesInstance {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(new SkipImagesStrategy());

        try (MarkdownConverter converter = new MarkdownConverter("business-plan.pdf")) {
            converter.convert("skip-images-instance.md", options);
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
{{< tab "skip-images-instance.md" >}}  
```text
**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan




**Table of Contents**

MeridianOutdoorCo.—BusinessPlan.........................................................................................1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/strategy/image-skip-strategy/SkipImagesInstance/skip-images-instance.md)
{{< /tab >}}
{{< /tabs >}}
