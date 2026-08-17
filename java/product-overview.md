---
id: product-overview
url: markdown/java/product-overview
title: GroupDocs.Markdown for Java overview
linkTitle: Product overview
weight: 1
description: "GroupDocs.Markdown for Java converts documents to clean, structured Markdown with full control over output flavor, image handling, and formatting."
keywords: markdown, PDF, DOCX, XLSX, EPUB, export, LLM, Gen AI, RAG
productName: GroupDocs.Markdown for Java
toc: True
---

## What is GroupDocs.Markdown?

GroupDocs.Markdown is a Java library that converts documents from 20+ formats (PDF, Word, Excel, EPUB, TXT, CHM) into clean, structured Markdown. It uses a custom DOM-based renderer that gives full control over every aspect of the output.

Designed for AI/ML workflows, static site generators, and document processing pipelines — Markdown is the ideal format for language models, text analysis tools, and content management systems.

## Key capabilities

| Capability | Description |
|---|---|
| **20+ input formats** | PDF, DOCX, DOC, XLSX, XLS, CSV, EPUB, MOBI, TXT, CHM, RTF, ODT, and more |
| **Markdown flavors** | [GitHub Flavored Markdown or CommonMark]({{< ref "markdown/java/developer-guide/advanced-usage/markdown-flavor" >}}) |
| **Image handling** | [Base64 embed, file system, skip, or custom]({{< ref "markdown/java/developer-guide/advanced-usage/strategy/" >}}) with relative paths and image replacement |
| **YAML front matter** | [Auto-extract metadata]({{< ref "markdown/java/developer-guide/advanced-usage/front-matter" >}}) for Jekyll, Hugo, Docusaurus |
| **Document inspection** | [Read format, pages, title, author]({{< ref "markdown/java/developer-guide/basic-usage/get-document-info" >}}) without converting |
| **Spreadsheet control** | [Column/row truncation]({{< ref "markdown/java/developer-guide/advanced-usage/spreadsheet-options" >}}), sheet separators, hidden sheet filtering |
| **Heading offset** | [Shift heading levels]({{< ref "markdown/java/developer-guide/advanced-usage/heading-offset" >}}) for content embedding |
| **Async API** | [Non-blocking conversion]({{< ref "markdown/java/developer-guide/advanced-usage/async-api" >}}) for web and serverless |
| **Error handling** | [Specific exception types]({{< ref "markdown/java/developer-guide/advanced-usage/error-handling" >}}) and conversion warnings |

## Quick example

{{< tabs "quick-example" >}}
{{< tab "QuickExample.java" >}}
```java
import com.groupdocs.markdown.*;

public class QuickExample {

    public static void main(String[] args) {
        // One-liner
        String md = MarkdownConverter.toMarkdown("business-plan.docx");
        // # Quarterly Report
        //
        // ## Executive Summary
        //
        // This report covers the key initiatives...

        // With options
        DocumentConvertOptions options = new DocumentConvertOptions();
        options.setFlavor(MarkdownFlavor.GITHUB);
        options.setIncludeFrontMatter(true);
        options.setHeadingLevelOffset(1);

        MarkdownConverter.toFile("business-plan.docx", "quick-example.md", options);
    }
}
```
{{< /tab >}}
{{< tab "business-plan.docx" >}}
{{< tab-text >}}
`business-plan.docx` is a sample file used in this example. Click [here](/markdown/java/_sample_files/business-plan.docx) to download it.
{{< /tab-text >}}
{{< /tab >}}
{{< tab "quick-example.md" >}}  
```text
---
title: "Meridian Outdoor Co. — Business Plan"
author: "Meridian Outdoor Co."
format: DOCX
pages: 5
---

![](data:...;base64,[elided])

**Meridian Outdoor Co. — Business Plan**
[TRUNCATED]
```
[Download full output](/markdown/java/_output_files/product-overview/QuickExample/quick-example.md)
{{< /tab >}}
{{< /tabs >}}

## Platform support

- Windows, Linux, macOS
- Java SE 8 and above
- One JAR for every platform — no native dependencies

## Get started

- [Quick start guide]({{< ref "markdown/java/getting-started/quick-start-guide" >}})
- [Installation]({{< ref "markdown/java/getting-started/installation" >}})
- [Features overview]({{< ref "markdown/java/getting-started/features-overview" >}})
- [API Reference](https://reference.groupdocs.com/markdown/java)
