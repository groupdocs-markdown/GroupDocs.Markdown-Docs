---
id: export-text
url: markdown/java/convert/export-text
title: Xml to Md
weight: 5
description: "This article demonstrates how to convert Text to Markdown with GroupDocs.Markdown for Java."
keywords:
productName: GroupDocs.Markdown for Java
hideChildren: False
---

Use GroupDocs.Markdown to convert TXT, XML, and other text-based formats to clean Markdown.

### Using static method

The simplest way to convert a text file:

{{< tabs "export-text-static">}}
{{< tab "ExportTextStatic.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportTextStatic {

    public static void main(String[] args) {
        // Set license (optional)
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        // Convert XML to Markdown string
        String markdown = MarkdownConverter.toMarkdown("llms-tech.xml");

        // Or save directly to a file
        MarkdownConverter.toFile("llms-tech.xml", "export-text-static.md");
    }
}
```
{{< /tab >}}
{{< tab "llms-tech.xml" >}}  
{{< tab-text >}}
`llms-tech.xml` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/llms-tech.xml) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-text-static.md" >}}  
```text
Attention-based neural architecture that underpins most modern large language models.

2017

Attention Is All You Need


Language modeling

Machine translation
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-text/ExportTextStatic/export-text-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API with options

For more control, use the instance API:

{{< tabs "export-text-instance">}}
{{< tab "ExportTextInstance.java" >}}
```java
import com.groupdocs.markdown.*;

import java.io.File;

public class ExportTextInstance {

    public static void main(String[] args) {
        if (new File("GroupDocs.Markdown.lic").exists()) {
            License.set("GroupDocs.Markdown.lic");
        }

        try (MarkdownConverter converter = new MarkdownConverter("llms-tech.xml")) {
            DocumentConvertOptions options = new DocumentConvertOptions();
            options.setHeadingLevelOffset(1);

            converter.convert("export-text-instance.md", options);
        }
    }
}
```
{{< /tab >}}
{{< tab "llms-tech.xml" >}}  
{{< tab-text >}}
`llms-tech.xml` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/basic-usage/convert/llms-tech.xml) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "export-text-instance.md" >}}  
```text
Attention-based neural architecture that underpins most modern large language models.

2017

Attention Is All You Need


Language modeling

Machine translation
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/basic-usage/convert/export-text/ExportTextInstance/export-text-instance.md)
{{< /tab >}}
{{< /tabs >}}

For the full list of input formats, see the [supported formats page]({{< ref "markdown/java/getting-started/supported-document-formats" >}}).
