---
id: load-from-a-local-disk
url: markdown/java/load-from-a-local-disk
title: Load from a local disk
weight: 1
description: "The following example demonstrates how to load file from local disk."
keywords: load file from local disk
productName: GroupDocs.Markdown for Java
hideChildren: False
---

GroupDocs.Markdown provides two ways to load a file from a local disk: the static one-liner API and the instance-based API.

### Using static method

The simplest approach -- pass a file path and get the Markdown string back:

{{< tabs "load-disk-static">}}
{{< tab "LoadDiskStatic.java" >}}
```java
import com.groupdocs.markdown.*;

public class LoadDiskStatic {

    public static void main(String[] args) {
        // Convert a local file to Markdown in one call
        String markdown = MarkdownConverter.toMarkdown("business-plan.docx");

        // Or save the result directly to a file
        MarkdownConverter.toFile("business-plan.docx", "load-disk-static.md");
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-disk-static.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **Table of Contents**

FY2026 Strategic Plan	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/loading/load-from-a-local-disk/LoadDiskStatic/load-disk-static.md)
{{< /tab >}}
{{< /tabs >}}

### Using instance API

When you need more control (e.g., conversion options, document info), create a `MarkdownConverter` instance:

{{< tabs "load-disk-instance">}}
{{< tab "LoadDiskInstance.java" >}}
```java
import com.groupdocs.markdown.*;

public class LoadDiskInstance {

    public static void main(String[] args) {
        try (MarkdownConverter converter = new MarkdownConverter("business-plan.docx")) {
            // Retrieve document metadata
            DocumentInfo info = converter.getDocumentInfo();
            System.out.println("Format: " + info.getFileFormat() + ", Pages: " + info.getPageCount());

            // Convert to Markdown
            converter.convert("load-disk-instance.md");
        }
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}  
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/developer-guide/advanced-usage/loading/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "load-disk-instance.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **Table of Contents**

FY2026 Strategic Plan	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/developer-guide/advanced-usage/loading/load-from-a-local-disk/LoadDiskInstance/load-disk-instance.md)
{{< /tab >}}
{{< /tabs >}}
