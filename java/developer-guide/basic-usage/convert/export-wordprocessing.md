---
id: export-wordprocessing
url: markdown/java/convert/export-wordprocessing
title: Docx to Md
weight: 2
description: "This article demonstrates how to convert Words to Markdown with GroupDocs.Markdown for Java."
keywords:
productName: GroupDocs.Markdown for Java
hideChildren: False
---

Use GroupDocs.Markdown to convert DOCX and other Word documents to clean Markdown.

### Using static method

The simplest way to convert a Word file:

{{< tabs "export-word-static">}}
{{< tab "ExportWordStatic.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportWordStatic {

    public static void main(String[] args) {
        // Set license (optional)
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        // Convert DOCX to Markdown string
        String markdown = MarkdownConverter.toMarkdown("business-plan.docx");

        // Or save directly to a file
        MarkdownConverter.toFile("business-plan.docx", "export-word-static.md");
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-word-static.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **Table of Contents**

FY2026 Strategic Plan	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-wordprocessing/ExportWordStatic/export-word-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-word-instance">}}
{{< tab "ExportWordInstance.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportWordInstance {

    public static void main(String[] args) {
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        try (MarkdownConverter converter = new MarkdownConverter("business-plan.docx")) {
            ExportImagesToFileSystemStrategy strategy = new ExportImagesToFileSystemStrategy("images");
            strategy.setImagesRelativePath("images");

            DocumentConvertOptions options = new DocumentConvertOptions();
            options.setImageExportStrategy(strategy);
            options.setHeadingLevelOffset(1);

            converter.convert("export-word-instance.md", options);
        }
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-word-instance.zip" >}}  
```text
export-word-instance.md (5 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-wordprocessing/ExportWordInstance/export-word-instance.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/java/getting-started/supported-document-formats" >}}).
