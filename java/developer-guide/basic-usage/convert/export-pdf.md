---
id: export-pdf
url: markdown/java/convert/export-pdf
title: Pdf to Md
weight: 1
description: "This article demonstrates how to convert PDF to Markdown with GroupDocs.Markdown for Java."
keywords:
productName: GroupDocs.Markdown for Java
hideChildren: False
---

Use GroupDocs.Markdown to convert PDF documents to clean Markdown.

### Using static method

The simplest way to convert a PDF file:

{{< tabs "export-pdf-static">}}
{{< tab "ExportPdfStatic.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportPdfStatic {

    public static void main(String[] args) {
        // Set license (optional)
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        // Convert PDF to Markdown string
        String markdown = MarkdownConverter.toMarkdown("business-plan.pdf");

        // Or save directly to a file
        MarkdownConverter.toFile("business-plan.pdf", "export-pdf-static.md");
    }
}
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-pdf-static.md" >}}  
```text
**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan

![](data:...;base64,[elided])


**Table of Contents**

MeridianOutdoorCo.—BusinessPlan.........................................................................................1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-pdf/ExportPdfStatic/export-pdf-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-pdf-instance">}}
{{< tab "ExportPdfInstance.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportPdfInstance {

    public static void main(String[] args) {
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        try (MarkdownConverter converter = new MarkdownConverter("business-plan.pdf")) {
            ExportImagesToFileSystemStrategy strategy = new ExportImagesToFileSystemStrategy("images");
            strategy.setImagesRelativePath("images");

            DocumentConvertOptions options = new DocumentConvertOptions();
            options.setImageExportStrategy(strategy);
            options.setHeadingLevelOffset(1);

            converter.convert("export-pdf-instance.md", options);
        }
    }
}
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}  
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-pdf-instance.zip" >}}  
```text
export-pdf-instance.md (7 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-pdf/ExportPdfInstance/export-pdf-instance.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/java/getting-started/supported-document-formats" >}}).
