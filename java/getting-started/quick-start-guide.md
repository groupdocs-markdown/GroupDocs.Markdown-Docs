---
id: quick-start-guide
url: markdown/java/quick-start-guide
title: Quick start guide
weight: 0
description: "Get started with GroupDocs.Markdown for Java in minutes — convert documents to Markdown with a single line of code"
keywords: quick start, getting started, convert, example
productName: GroupDocs.Markdown for Java
hideChildren: False
toc: True
---

This guide shows you how to convert documents to Markdown with GroupDocs.Markdown for Java. You'll have working code in under 2 minutes.

### How it works

{{< mermaid class="text-center" >}}
flowchart LR
    A["Input Document\n(DOCX, PDF, XLSX, EPUB, ...)"]
    B["MarkdownConverter"]
    C["Markdown Output\n(.md file or string)"]
    A --> B --> C
{{< /mermaid >}}

### Prerequisites

1. Add the GroupDocs repository and the dependency to your `pom.xml` (see [Installation]({{< ref "markdown/java/getting-started/installation.md" >}}) for Gradle, Kotlin, Ivy, and Sbt):

```xml
<repositories>
  <repository>
    <id>GroupDocs Artifact Repository</id>
    <url>https://releases.groupdocs.com/java/repo/</url>
  </repository>
</repositories>

<dependencies>
  <dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-markdown</artifactId>
    <version>latest-version</version>
  </dependency>
</dependencies>
```

2. Import the package:
```java
import com.groupdocs.markdown.*;
```

### Example 1: Convert Word to Markdown

The simplest conversion — one line of code:

{{< tabs "qs-word-to-md">}}
{{< tab "QsWordToMd.java" >}}
```java
import com.groupdocs.markdown.*;

public class QsWordToMd {

    public static void main(String[] args) {
        // Convert a Word document to Markdown
        String markdown = MarkdownConverter.toMarkdown("business-plan.docx");

        // Or save directly to a file
        MarkdownConverter.toFile("business-plan.docx", "qs-word-to-md.md");
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "qs-word-to-md.md" >}}  
```text
![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**

FY2026 Strategic Plan


# **Table of Contents**

FY2026 Strategic Plan	1
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/getting-started/quick-start-guide/QsWordToMd/qs-word-to-md.md)
{{< /tab >}}
{{< /tabs >}}

### Example 2: Convert PDF with image export

Save a PDF to Markdown with images extracted to a folder:

{{< tabs "qs-pdf-with-images">}}
{{< tab "QsPdfWithImages.java" >}}
```java
import com.groupdocs.markdown.*;

public class QsPdfWithImages {

    public static void main(String[] args) {
        ExportImagesToFileSystemStrategy strategy =
                new ExportImagesToFileSystemStrategy("output/images");
        strategy.setImagesRelativePath("images");

        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setImageExportStrategy(strategy);

        MarkdownConverter.toFile("business-plan.pdf", "output/report.md", options);

        // Images saved to output/images/
        // Markdown references: ![](images/img-001.png)
    }
}
```
{{< /tab >}}
{{< tab "business-plan.pdf" >}}
{{< tab-text >}}
`business-plan.pdf` is a sample file used in this example. Click [here](/markdown/java/_sample_files/business-plan.pdf) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "qs-pdf-with-images.zip" >}}  
```text
output/images/img-001.jpg (10 KB)
output/images/img-002.jpg (39 KB)
output/images/img-003.jpg (25 KB)
output/images/img-004.jpg (16 KB)
output/images/img-005.jpg (44 KB)
output/images/img-006.jpg (20 KB)
output/images/img-007.jpg (648 bytes)
output/images/img-008.jpg (48 KB)
output/report.md (7 KB)
```
[Download full output](/markdown/java/_output_files/getting-started/quick-start-guide/QsPdfWithImages/qs-pdf-with-images.zip)
{{< /tab >}}
{{< /tabs >}}

### Example 3: Convert Excel with options

Convert a spreadsheet with column truncation and front matter:

{{< tabs "qs-excel-options">}}
{{< tab "QsExcelOptions.java" >}}
```java
import com.groupdocs.markdown.*;

public class QsExcelOptions {

    public static void main(String[] args) {
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setMaxColumns(8);
        options.setMaxRows(50);
        options.setIncludeFrontMatter(true);
        options.setFlavor(MarkdownFlavor.GITHUB);

        try (MarkdownConverter converter = new MarkdownConverter("cost-analysis.xlsx")) {

            // Inspect before converting
            DocumentInfo info = converter.getDocumentInfo();
            System.out.println("Worksheets: " + info.getPageCount());

            // Convert
            DocumentConvertResult result = converter.convert("qs-excel-options.md", options);

            // Check warnings
            for (String w : result.getWarnings()) {
                System.out.println("Warning: " + w);
            }
        }
    }
}
```
{{< /tab >}}
{{< tab "cost-analysis.xlsx" >}}
{{< tab-text >}}
`cost-analysis.xlsx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/cost-analysis.xlsx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "qs-excel-options.md" >}}  
```text
---
format: XLSX
pages: 4
---


## Summary

| Category | FY2024 | FY2025 | FY2026 |
| --- | --- | --- | --- |
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/getting-started/quick-start-guide/QsExcelOptions/qs-excel-options.md)
{{< /tab >}}
{{< /tabs >}}

### What's next?

- [Supported document formats]({{< ref "markdown/java/getting-started/supported-document-formats.md" >}}) — full list of input formats
- [Image handling strategies]({{< ref "markdown/java/developer-guide/advanced-usage/strategy" >}}) — Base64, file system, skip, custom
- [Markdown flavor control]({{< ref "markdown/java/developer-guide/advanced-usage/markdown-flavor.md" >}}) — GitHub vs CommonMark
- [YAML front matter]({{< ref "markdown/java/developer-guide/advanced-usage/front-matter.md" >}}) — for static site generators
