---
id: convert
url: markdown/java/convert
title: Convert files to various formats
weight: 1
description: "Artcles listed in this page explain the common usage scenarios when documents are stored in a local drive and you want to manage them using GroupDocs.Markdown API"
keywords: common usage
productName: GroupDocs.Markdown for Java
hideChildren: False
structuredData:
    showOrganization: True
---

**[GroupDocs.Markdown](https://products.groupdocs.com/markdown/java)** provides a quick and easy way to convert documents into clean, structured Markdown. The library offers two approaches: **static methods** for one-line conversions and an **instance API** for more control.

### Static methods (simplest)

Call `MarkdownConverter.toMarkdown()` to get a Markdown string, or `MarkdownConverter.toFile()` to write directly to disk:

{{< tabs "static-methods" >}}
{{< tab "StaticMethods.java" >}}
```java
import com.groupdocs.markdown.*;

public class StaticMethods {

    public static void main(String[] args) {
        String md = MarkdownConverter.toMarkdown("business-plan.docx");
        // # Quarterly Report
        //
        // ## Executive Summary
        //
        // This report covers the key initiatives...

        MarkdownConverter.toFile("business-plan.docx", "static-methods.md");
    }
}
```
{{< /tab >}}
{{< /tabs >}}

### Instance API

Create a [MarkdownConverter](https://reference.groupdocs.com/markdown/java/com.groupdocs.markdown/markdownconverter/) instance for advanced scenarios such as inspecting metadata before converting or reusing a loaded document:

{{< tabs "instance-api" >}}
{{< tab "InstanceApi.java" >}}
```java
import com.groupdocs.markdown.*;

public class InstanceApi {

    public static void main(String[] args) {
        try (MarkdownConverter converter = new MarkdownConverter("business-plan.docx")) {
            DocumentConvertOptions options = new DocumentConvertOptions();
            options.setHeadingLevelOffset(1);

            converter.convert("instance-api.md", options);
        }
    }
}
```
{{< /tab >}}
{{< /tabs >}}

### Conversion options

Use [DocumentConvertOptions](https://reference.groupdocs.com/markdown/java/com.groupdocs.markdown/convertoptions/) to customize the output -- select specific pages, control image handling, choose a Markdown flavor, add YAML front matter, and more. For loading customization, use [LoadOptions](https://reference.groupdocs.com/markdown/java/com.groupdocs.markdown/loadoptions/) to specify file format or provide a password.

These documentation articles explain how to convert files from the most popular formats:
