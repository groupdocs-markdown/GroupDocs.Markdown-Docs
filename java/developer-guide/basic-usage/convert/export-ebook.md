---
id: export-ebook
url: markdown/java/convert/export-ebook
title: Epub to Md
weight: 4
description: "This article demonstrates how to convert Ebook to Markdown with GroupDocs.Markdown for Java."
keywords:
productName: GroupDocs.Markdown for Java
hideChildren: False
---

Use GroupDocs.Markdown to convert EPUB, MOBI, and other eBook formats to clean Markdown.

### Using static method

The simplest way to convert an eBook file:

{{< tabs "export-ebook-static">}}
{{< tab "ExportEbookStatic.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportEbookStatic {

    public static void main(String[] args) {
        // Set license (optional)
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        // Convert EPUB to Markdown string
        String markdown = MarkdownConverter.toMarkdown("business-plan.epub");

        // Or save directly to a file
        MarkdownConverter.toFile("business-plan.epub", "export-ebook-static.md");
    }
}
```
{{< /tab >}}
{{< tab "business-plan.epub" >}}  
{{< tab-text >}}
`business-plan.epub` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/business-plan.epub) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-ebook-static.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **Table of Contents**


[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-ebook/ExportEbookStatic/export-ebook-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-ebook-instance">}}
{{< tab "ExportEbookInstance.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportEbookInstance {

    public static void main(String[] args) {
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        try (MarkdownConverter converter = new MarkdownConverter("business-plan.epub")) {
            ExportImagesToFileSystemStrategy strategy = new ExportImagesToFileSystemStrategy("images");
            strategy.setImagesRelativePath("images");

            DocumentConvertOptions options = new DocumentConvertOptions();
            options.setImageExportStrategy(strategy);
            options.setHeadingLevelOffset(1);

            converter.convert("export-ebook-instance.md", options);
        }
    }
}
```
{{< /tab >}}
{{< tab "business-plan.epub" >}}  
{{< tab-text >}}
`business-plan.epub` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/business-plan.epub) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-ebook-instance.zip" >}}  
```text
export-ebook-instance.md (5 KB)
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-ebook/ExportEbookInstance/export-ebook-instance.zip)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/java/getting-started/supported-document-formats" >}}).
